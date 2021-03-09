# show player choices

Displays a list of up to five options for the player to choose between and pauses until they make a choice.
The list allows the player to move through the options using the UP/DOWN buttons and select an option using the A button.
The game will continue running as long as this block is run in the background or in a start cutscene block.

```sig
story.showPlayerChoices("say hello", "say goodbye")
```

## Parameters

* **choice1**: a [string](/types/string) that contains a choice for the player to choose between
* **choice2**: a [string](/types/string) that contains a choice for the player to choose between
* **choice3**: an optional [string](/types/string) that contains a choice for the player to choose between
* **choice4**: an optional [string](/types/string) that contains a choice for the player to choose between
* **choice5**: an optional [string](/types/string) that contains a choice for the player to choose between

## Example #example

## Example #example

In this example, we show how you could do a character selection scene at the beginning of a game.
We give the player three choices for a job, and then change the text and character image based on their choice.

```blocks
let sprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . b b b b b b b . . . .
    . . . . . 3 3 3 3 3 3 b . . . .
    . . . . . 1 3 3 3 1 3 b . . . .
    . . . . . 3 3 3 3 3 3 3 . . . .
    . . . . . 3 3 3 3 3 3 3 . . . .
    . . . . a a a b a a a a a . . .
    . . . a . a c b a a a a . a . .
    . . . a . a a b a b b a . a . .
    . . . a . a c b a a a a . a . .
    . . . a . a a b a a a a . a . .
    . . . . . e e e e e e e . . . .
    . . . . . c c c c c c c . . . .
    . . . . . c . . . . . c . . . .
    `, SpriteKind.Player)
sprite.setPosition(80, 40)
scene.setBackgroundColor(13)
story.startCutscene(function () {
    story.printDialog("Hey there!", 80, 90, 50, 150, 15, 1, story.TextSpeed.VeryFast)
    story.printDialog("Welcome to your first day at the Adventurer's Guild!", 80, 90, 50, 150, 15, 1, story.TextSpeed.VeryFast)
    story.printDialog("What job are you signing up for?", 80, 90, 50, 150, 15, 1, story.TextSpeed.VeryFast)
    story.showPlayerChoices("Warrior", "Wizard", "Bard")
    if (story.checkLastAnswer("Warrior")) {
        sprite.setImage(img`
            . . . . . . . . . . . . . . . .
            . b . . . . . . . . . . . . . .
            . b . . . . . . . . . . . . . .
            . b . . . b b b b b b b . . . .
            . b . . . 3 3 3 3 3 3 b . . . .
            . b . . . 1 3 3 3 1 3 b . . . .
            . b . . . 3 3 3 3 3 3 3 . . . .
            6 6 6 . . 3 3 3 3 3 3 3 . . . .
            . a a a a a a b a a a a a . . .
            . 6 . . . a c b a a a a . a . .
            . . . . . a a b a b b a . a . .
            . . . . . a c b a a a 6 6 6 6 6
            . . . . . a a b a a a 6 b b b 6
            . . . . . e e e e e e 6 b b b 6
            . . . . . c c c c c c c 6 b 6 .
            . . . . . c . . . . . c . 6 . .
            `)
        story.printDialog("Ha, ha, ha, nice! More of the smashin' stuff type, are ya?", 80, 90, 50, 150)
        story.printDialog("We've got lots of that type around here", 80, 90, 50, 150)
        story.printDialog("Make yourself at home!", 80, 90, 50, 150)
    } else if (story.checkLastAnswer("Wizard")) {
        sprite.setImage(img`
            . . . . . . . . 8 . . . . . . .
            . . . . . . . 8 8 8 . . . . . .
            . . . . . . 8 8 8 8 8 . . . . .
            . . . . . . 8 8 8 8 8 . . . . .
            . . . . . 8 8 8 8 8 8 8 . . . .
            . . . . 8 8 8 8 8 8 8 8 8 . . .
            . 2 . . . 3 3 3 3 3 3 b . . . .
            . e . . . 1 3 3 3 1 3 b . . . .
            . e . . . 3 3 3 3 3 3 3 . . . .
            . e . . . 3 3 3 3 3 3 3 . . . .
            . e 6 6 6 6 4 6 6 6 6 6 6 . . .
            . e . . . 6 8 6 6 6 6 6 . 6 . .
            . e . . . 6 8 6 6 6 6 6 . 6 . .
            . e . . . 8 8 8 6 6 6 6 . 6 . .
            . e . . . 8 8 8 6 6 6 6 . 6 . .
            . e . . . 8 8 8 6 6 6 6 . . . .
            . . . . . 8 8 8 6 6 6 6 . . . .
            . . . . . 8 8 8 6 6 6 6 . . . .
            `)
        story.printDialog("WHOA THAT'S SO COOL!", 80, 90, 50, 150)
        story.printDialog("So you can do like spells and incantations and such?", 80, 90, 50, 150)
        story.printDialog("No foolin'!? Well I'm sure you'll have no trouble handling yourself here", 80, 90, 50, 150)
    } else if (story.checkLastAnswer("Bard")) {
        sprite.setImage(img`
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . f f
            . . f f . . . . . . . . . . f .
            . . f . . b b b b b b b . . f .
            . . f . . 3 3 3 3 3 3 b . f f .
            . f f . . 1 3 3 3 1 3 b . f f .
            . f f . . 3 3 3 3 3 3 3 . . . .
            . . . . . 3 3 3 3 3 3 3 . . . .
            . . . a a a a b a a a a a . . .
            e 6 6 e . a c b a a a a . a . .
            e . a e . a a b a b b a . a . .
            e 6 6 e . a c b a a a a . a . .
            . e e . . a a b a a a a . a . .
            . . . . . e e e e e e e . . . .
            . . . . . c c c c c c c . . . .
            . . . . . c . . . . . c . . . .
            `)
        story.printDialog("Oh, nice! Everyone is always so serious around here", 80, 90, 50, 150)
        story.printDialog("We could really use a ballad or two to lighten the mood", 80, 90, 50, 150)
    }
})

```

```package
arcade-storytelling=github:riknoll/arcade-storytelling
```