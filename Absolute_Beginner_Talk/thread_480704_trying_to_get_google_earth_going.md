---
title: "trying to get google earth going"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by reston5 on 2007-06-21
`GoogleEarthLinux.bin' saved 

chmod +x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory

if followed the tutorial still no luck

---

### Post by kostkon on 2007-06-21
Why don't you just add the [medibuntu]("http://medibuntu.org/") repository to your *sources list* and then install *Google Earth* through *Synaptic*. I don't know if you will get the very last version, you will have to check, but that's an easy solution; and you will get the option of automatic updates.

I hope I helped you somehow

---

### Post by homergreg on 2007-06-21
If you do an "ls" in the directory that you are currently in, do you see GoogleEarthLinux.bin?  You need to be in the directory that GoogleEarthLinux.bin resides, or you need to indicate the path to the file with your CHMOD command

---

### Post by paparucino on 2007-06-21
> **reston5 said:**
> `GoogleEarthLinux.bin' saved 

chmod +x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory

if followed the tutorial still no luck

Try this from a terminal
```

updatedb  ###it takes some minutes
locate GoogleEarthLinux.bin ### GoogleEart should be enough

```
cd to the directory shown, repeat the chmod and run the installer.

---

### Post by mwacky on 2007-06-25
What about sudo?

sudo /path/to/file/GoogleEarthLinux.bin

Try using tab key to automatically populate shell.

---

### Post by kspn on 2007-06-25
> **reston5 said:**
> `GoogleEarthLinux.bin' saved 

chmod +x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory

if followed the tutorial still no luck

The command you were looking for is 
```
./GoogleEarthLinux.bin
```

---

