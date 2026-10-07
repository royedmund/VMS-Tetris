# VMS Tetris for VT terminals

A Pascal Tetris game for VMS and serial VT100-compatible terminals, by Chris R. Guthrey, University of Waikato, New Zealand, dated 3 July 1990.

Original acknowledgements: contributing authors of the Interact library, `CCC_REX`, `CCC_LDO` and `CCC_SIMON`.

## Requirements and build order

This is VMS-specific Pascal and MACRO source, not a portable Free Pascal program. You need a compatible VMS Pascal compiler, MACRO assembler, linker and system Pascal environments. The game depends on the supplied Interact library.

Start in the transferred project's root directory on VMS:

```text
$ SET DEFAULT [.LIBRARY]
$ @BUILD
$ SET DEFAULT [-]
$ COPY [.LIBRARY]INTERACT.PEN []
$ COPY [.LIBRARY]INTERACT.OLB []
$ @BUILD
$ RUN TETRIS
```

The library build generates `INTERACT.PEN`, `INTERACT.OLB` and `UTIL.OLB`. The top-level build expects `INTERACT.PEN` and `INTERACT.OLB` in its working directory, so the copies above make that dependency explicit. Both build procedures delete intermediate files in their current directory; run them only in the project directories.

**Validation limit:** this sequence has been checked against the included command files, but has not been executed on VMS during this documentation review. Compatibility with newer VMS architectures/compiler releases remains to be tested. Keep all three `tetintro*.dat` files beside `TETRIS.EXE`: the program locates them through its `IMAGE_DIR` logical name.

## Repository layout

| Location | Purpose |
| --- | --- |
| [tetris.pas](tetris.pas) | Main game |
| [tetshapes.pas](tetshapes.pas) | Shape definitions and Pascal environment |
| [build.com](build.com) | Game compile/link procedure |
| [library/](library/) | Interact/utility sources and their build procedure |
| `tetintro1.dat`–`tetintro3.dat` | Runtime introduction data |
| `tetris.$package` / `library/library.$package` | Historical package manifests; some listed distribution names differ from this checkout |
| JPG files | VT420 and DECterm screenshots |
| [LICENSE](LICENSE) | Repository licence text; retain the original source/library credits |

The game/library split is appropriate. Preserve VMS filenames and relative directory relationships; generated `.OBJ`, `.PEN`, `.OLB` and `.EXE` files belong to a local build rather than the source collection.
