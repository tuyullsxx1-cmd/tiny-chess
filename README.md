# Tiny Chess — Iteration 2 Engine

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/tuyullsxx1-cmd/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard)
[![reward](https://make.fun/badge/tiny-chess-01/tuyullsxx1-cmd/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01)

A chess engine in a single file for the tiny-chess-01 bounty on make.fun.
The whole engine lives in `main.py`: at most 4,096 bytes, Python 3.13
standard library only, deterministic, at most 10 seconds per move.

## Design

- 0x88 board representation with full legal move generation.
- Tapered evaluation with piece-square tables in the correct orientation.
- Alpha-beta search with PVS inside the search and a full-window search
  at the root, so a bound score is never mistaken for an exact score.
- Transposition table keyed by Zobrist hash, killer moves, MVV-LVA ordering.
- Null-move pruning, late-move reductions, futility pruning, delta pruning.
- A 40-entry white-only opening book for the known ply-8 positions.
- Iterative deepening to a fixed budget of 80,000 nodes per move.

## Measured result

A local 3-trial gauntlet against the kit anchors scored a mean Elo of 1,213.3 (trials 1,364 / 997 / 1,279), above the 1,154 practice floor.

## How to run

python3 -P -s main.py

## Files

- `main.py` — the packed engine (4,038 bytes).
- `README.md` — this file.
- `LICENSE` — MIT license.
- `.makefun/owner.json` — the entry wallet.
