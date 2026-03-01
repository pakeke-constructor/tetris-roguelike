

# Tetris-Roguelike Deckbuilder Game:

Plays like tetris. 
However, you edit your "deck of pieces" over time, which is bunch of tetris-pieces.
- (take inspiration from deckbuilder mechanics)

upgrade your blocks, get new blocks, get crazier upgrades, do combos, create synergies.

See https://store.steampowered.com/app/3908810/Stackflow/ as a (poorly made) example





## GAME LOOP:
- Play tetris level, until placed the required number of pieces. (pieces speed up over time)
- Once complete => Receive rewards from level (see Level-Select)
- Then, enter shop. Buy/upgrade stuff
- Choose a new level. (See Level-Select). REPEAT FROM STEP-1.



## Currencies:
The idea is to have 3 currencies:
- Red currency
- Blue currency
- Green currency
(I'll explain why below)



## Pieces and Blocks:
"Pieces" are the things that fall down on the screen. 
Can be L shaped, Plus-shaped, etc.

Pieces are made out of multiple blocks.
eg:
```
[ ][ ][ ]
      [ ]
```
or
```
[ ][ ]
   [ ][ ]
```
```lua
Piece = {
    blocks = Map<(x,y), Block>,
    rotation = 0 or 1 or 2 or 3
}
```


## Blocks:
Blocks are seperate objects.

They have color, sigil, and material.
can be 3 different colors: RED, BLUE, or GREEN.

When a block is destroyed, it *earns* the currency of whatever color it is.
(Eg: 3 red-blocks destroyed will earn +3 RED currency)

```lua
Block = {
    sigil = SigilType,
    color = "RED" or "BLUE" or "GREEN",
    material = MaterialType
}
```

### Blocks: (Materials)
Block-materials are like little simple "modifiers" to blocks.

### Blocks: (Sigils)
Block-sigils are like 



- Tetris-area is made "wider" over time. (eg starts 5 wide -> becomes 12 wide lategame)

- players should be able to to modify individual pieces. Like adding a red block to a piece



## VISUAL STYLE:
Casual pixelart, dull color-palette, (similar to SNKRX, or Tiny-Rogues)

For juice/animations,
- try to use render primitives
- 





## Level-select (Bounty Board)
Procedurally generated levels, each with a unique risk/reward profile.
Three "wanted" posters on a board. Each has codename, a reward, and modifier fine-print.
(Middle poster is default => generally easiest/most normal)
### Level Examples:
- LV-ALFA: +$20, slow speed, all RED blocks disabled
- LV-BRAVO: 2 rare perks, medium speed
- LV-CHARLIE: +$100, fast speed, blue blocks earn double

Nuance in the modifiers makes level choice meaningful.
Adds risk/reward: e.g. player might think:
"Hmm, I could go to the hard-level, and get an amazing reward... but I might lose"









