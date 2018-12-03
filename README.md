# The Game Design Language

## Introduction

This project is based on a conversation between [Jesse Friedman](okofish) and [Chris Wilson](@wilson428) at the 2018 Wolfram Technology conference. The topic was whether it would be possible to create a community for people to write bots that play well defined games and compete against other users' programs.

The basic structure is reasonably simple: Any given game--the example we were using was [Mancala](https://en.wikipedia.org/wiki/Mancala)--has both a vocabulary for the public state (how many stones are in each position on the board and whose turn it is)--a set of rules, and a vocabulary for expressing a move. For each turn, a "player" receives the state of the board (which may or may not be the entire state of the board or just some of it, depending whether it is a game of complete information) as a JSON endpoint and responds with a JSON file that describe the move it wishes to make. This way, the bots themselves live locally and to not need to be hosted on a central server.

## The GDL Models

We conceived of a view related models to begin:

+ **Board**: A spatial description of the game, accounting for anything from a linear path of squares (Monopoly) to a hexagonal grid (Hex) and so forth. While games traditionally have a fixed geometry, even if the state of a square may change, it is possible that the size of the board can change during the game.

+ **Player**: An individual competing in the game.

+ **Piece**: Any token that has significance and may have a location on the board.

Possible addition:

+ **Card**: Any shuffled set of instructions that may change the state of the game either immediately or when a bot chooses to play them. It is conceivable cards can be considered a subset of pieces, though the randomness may be tricky.

## Technical overview

Jesse, what's your preferred approach to relational models? I usually go with something like Mongoose, but you're the expert.