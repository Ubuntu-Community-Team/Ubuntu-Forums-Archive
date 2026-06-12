---
title: "Executing a .bin file"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-12-03
Hi,

I'm trying to install Google Earth. I've downloaded the binary file for Linux but I'm unsure how to execute it. Can anyone help?

Cosmic

---

### Post by FuturePilot on 2007-12-03
First cd to the directory where it's located
```
cd /path/to/file/
```
Then make it executable
```
chmod +x GoogleEarthLinux.bin
```
Then run it
```
./GoogleEarthLinux.bin
```

---

### Post by elliotjreed on 2007-12-03
open the terminal...

click and drag the .bin file on it, remove the ' ' 's and hit enter.

If that don't work, use the 'sudo' command in front!

---

### Post by elliotjreed on 2007-12-03
... yes, or that!

Use the above method (the one above my original, that is!!!) ... it will work all the time!

---

### Post by CosmicFlux on 2007-12-04
OK, thanx!

---

### Post by mmcmonster on 2007-12-04
> **FuturePilot said:**
> First cd to the directory where it's located
```
cd /path/to/file/
```Then make it executable
```
chmod +x GoogleEarthLinux.bin
```Then run it
```
./GoogleEarthLinux.bin
```


Remember that you need to be in "sudo" mode to install a file.  The last line should be:
```
sudo ./GoogleEarthLinux.bin
```It will then prompt for your password, prior to running the installation program.

---

### Post by Vadi on 2007-12-04
Next time, you can just right-click on the file, select properties, select the permissions tab, and check off the exectuable box at the bottom :)

---

