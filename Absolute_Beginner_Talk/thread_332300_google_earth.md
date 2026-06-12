---
title: "google earth"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by RHS on 2007-01-05
I downloaded google earth to my desktop and have "googleearthlinux.bin" on my desktop.  What do I do now?  I am runnng ubuntu 6.06  Thanks!!

---

### Post by taurus on 2007-01-05
```
chmod 755 googleearthlinux.bin
./googleearthlinux.bin
```

---

### Post by RHS on 2007-01-05
I entered the first line and it responded "chmod....: no such file or directory.
what do I do?

---

### Post by obsidion on 2007-01-05
> **taurus said:**
> ```
chmod 755 googleearthlinux.bin
./googleearthlinux.bin
```


  That will only install it to your present users home directory, if you want to install globally then it is 
sudo ./GoogleEarthLinux.bin

---

### Post by obsidion on 2007-01-05
> **RHS said:**
> I entered the first line and it responded "chmod....: no such file or directory.
what do I do?


  How did you try to do it ?, you need to do it from a terminal.

---

### Post by taurus on 2007-01-05
> **RHS said:**
> I entered the first line and it responded "chmod....: no such file or directory.
what do I do?

You probably saved it to ~/Desktop so you need to change to that directory first before you can run those two commands.

```
cd ~/Desktop
```

---

### Post by RHS on 2007-01-05
I entered cd ~/Desktop, then return, then sudo ./GoogleEarthLinux.bin then it responded command not found.  now what??

---

### Post by taurus on 2007-01-05
What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by RHS on 2007-01-05
total 21164
drwxr-xr-x  6 randy randy     4096 2007-01-05 20:45 .
drwxr-xr-x 32 randy randy     4096 2007-01-05 18:54 ..
drwxr-xr-x  2 randy randy     4096 2007-01-05 18:41 AFF
drwxr-xr-x  3 randy randy     4096 2007-01-05 14:25 Flickr
-rw-r--r--  1 randy randy 21618415 2007-01-05 20:45 GoogleEarthLinux.bin
drwxr-xr-x  2 randy randy     4096 2007-01-05 19:09 HomeClips
drwxr-xr-x  2 randy randy     4096 2007-01-05 19:09 IloveBeach
randy@randy-laptop:~$

---

### Post by Efwis on 2007-01-05
try this in terminal

```
cd ~/Desktop
sh GoogleEarthLinux.bin
```

If this doesn't work then download Automatix2 and it will install it for you. It is the same version as the one you downloaded.

---

### Post by taurus on 2007-01-05
```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

p.s.  It's better to install it in your own $HOME directory than on the system...

---

### Post by obsidion on 2007-01-05
> **RHS said:**
> I entered cd ~/Desktop, then return, then sudo ./GoogleEarthLinux.bin then it responded command not found.  now what??

  You didn't chmod it did you ?

Try chmod a+x GoogleEarthLinux.bin
then try the sudo ./Getc again

 A note here, in a terminal you don't need to type out things like GoogleEarthLinux.bin in full each time hitting the tab key after a few letters will autocomplete.

---

