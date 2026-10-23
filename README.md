# Inclementpatch Field Guide

Open `index.html` in a modern browser. The Pokédex is a self-contained static site with no build step or network dependency.

## Features
- Search by name, Pokédex number, type, ability, or wild location.
- Filter by type, ability, and location.
- Sort ascending or descending by number, total stats, HP, Attack, Defense, Special Attack, Special Defense, or Speed.
- Pokémon detail panel with in-game front sprites, types, parsed abilities, base stats, encounter tables, level-up moves, TM/HM compatibility, egg moves, and defensive type matchups.
- Night mode styling and locally bundled sprite assets for offline use.
- Separate searchable and filterable battle move library, with learned moves linking directly to the library.
- Interactive Hoenn encounter map with area encounter lists and Pokémon location search.
- Searchable berry-tree encounter library with separate groups for Sprouted, Taller, Flowering, and Berries growth stages.
- Boss Battles library with Gym Leader and Elite Four sprites, three randomized versions per battle set, held items, moves, and Totem, Alpha, Shadow, or Primal markers.
- Villain Battles library with all nine requested antagonists, in-game trainer sprites, all numbered encounters, three randomized team versions, held items, moves, and boost markers.
- Responsive layout, keyboard focus, and Escape to close the mobile detail view.

## Data provenance
Generated from the Inclementpatch source repository at the time of export. Inputs: `src/data/pokemon/base_stats.h`, `src/data/text/species_names.h`, `include/constants/species.h`, `include/constants/pokemon.h`, `include/constants/abilities.h`, and `src/data/wild_encounters.json`, `src/data/pokemon/level_up_learnsets.h`, `src/data/pokemon/level_up_learnset_pointers.h`, `src/data/pokemon/tmhm_learnsets.h`, `src/data/pokemon/egg_moves.h`, and `src/data/region_map/region_map_entries.h`, `data/maps/*/map.json`, `graphics/interface/region_map_affine.png`, and `src/data/battle_moves.h`, `src/data/text/move_descriptions.h`, and the type-effectiveness table in `src/battle_util.c`, plus berry-tree encounter groups from `src/data/wild_encounters.json` and leader party records from `src/data/trainer_parties.h`, `src/data/trainers.h`, and `src/data/items.h`. The source repository was read only. Front sprites are copied from `graphics/pokemon/*/front.png` into `assets/pokemon/`; trainer portraits are copied from `graphics/trainers/front_pics/` into `assets/trainers/`. Villain battle teams are embedded from `src/data/trainer_parties.h` and `src/data/trainers.h`.

This is an exported snapshot; rerun the extraction when game data changes. Ability parsing uses the first abilities initializer where compile-time conditionals provide alternate builds.


Move lists are embedded in the static site snapshot and can be searched by move name. Level-up entries retain source levels; TM/HM entries retain item numbers.

Type matchups are combined against both defensive types and follow the repository’s Gen 7 steel-resistance chart setting. Ability-based immunities are not included in the matchup groups.

Battle move metadata and descriptions are embedded from the source snapshot in `src/data/battle_moves.h` and `src/data/text/move_descriptions.h`.

The encounter map uses the bundled custom schematic in `assets/map/hoenn-schematic.svg`, source region-map section coordinates, and wild encounter records grouped through each map’s `region_map_section`.

Encounter map location lists group wild encounter data by each individual map. City houses, labs, Pokémon Centers, routes, caves, and other maps are kept separate where the map metadata has encounter data; map warp events link encounter-bearing destinations.
