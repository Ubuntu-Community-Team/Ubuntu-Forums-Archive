---
title: "iTunes in WINE"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-11-27
Hi,

I downloaded iTunes and installed it using WINE. The thing is, when I try to open it nothing happens. It look like it's going to load, then does nothing. Any suggestions?

CosmicFlux

---

### Post by Nano Geek on 2007-11-27
> **CosmicFlux said:**
> Hi,

I downloaded iTunes and installed it using WINE. The thing is, when I try to open it nothing happens. It look like it's going to load, then does nothing. Any suggestions?

CosmicFluxRun it in the command-line and tell us what it says.
```
wine /path/to/itunes/exe/file
```

---

### Post by CosmicFlux on 2007-11-27
wine: cannot find '/path/to/itunes/exe/file'

---

### Post by BrettA on 2007-11-27
He means:

/home/usr/.wine/drive_c/Program Files/iTunes/iTunes.exe
(Or something along those lines)

as a path. usr = your username

When checking path be sure to enable to see hidden files/folders.

---

### Post by atomkarinca on 2007-11-27
/path/to/itunes/exe/file should be replaced with the path of the itunes' exe file. it should be something like ~.wine/drive_c/Program\ Files/Itunes/something exe. So the first thing, open up a terminal and type (for this specific example):

```
wine .wine/drive_c/Program\ Files/Itunes/something.exe
```

If it doesn't start up, just post back the output.

---

### Post by Nano Geek on 2007-11-27
Also, iTunes 7.3 and below have been confirmed to work with WINE. Above that is not possible as far as I know.

---

