---
title: "Search &amp; Theme issues"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Equiflux on 2007-11-23
**_Intro:_**
I'll start by saying: I'm new to this community and Ubuntu/Linux. (first post) I like doing graphic/web design so I decided to use Ubuntu Studio.

**_not Intro:_**
 I like everything so far, however, there's 2 things that bug me:
-The search feature in the file browser doesn't work. The error message I get says:  
 > 
The folder contents could not be displayed.
The name org.freedesktop.Tracker was not provided by any .service files

-I like the login window and loading/bootup graphic for Ubuntu Studio Feisty Fawn better than Gutsy's. 

---
So then, how would I go about solving these problems?

also:
Does wine(the emulator) have sandbox-like features?

---

### Post by Equiflux on 2007-11-23
bump

---

### Post by Equiflux on 2007-11-25
bump

---

### Post by Majorix on 2007-11-25
Hi. Good choice with Ubuntu Studio, I have the same OS :)

About your search problem, you could try this:
```
sudo updatedb && locate *filename_and_maybe_wildcard*
```

Sorry I don't know how to change the boot screen or what sandbox is.

---

### Post by Equiflux on 2007-11-25
Ahh thanks for the reply! So does this return search results in the Terminal? 

> filename_and_maybe_wildcard
-what is the proper way to use a wildcard? Do I type a directory name and then the wildcard character?
  -also what is the wildcard character?

---

### Post by Majorix on 2007-11-26
Wildcard character in Ubuntu is * (asterisk).
If you type the full name for the file you are looking for, then you don't have to use the wildcard. But if you don't know the fullname but a few characters, combine wildcard with the characters you know when searching.

Like this:
You have a file called Ubuntu_GutsyGibbon.iso. Say you are looking for it, but don't know the fullname, but you are sure that it starts with Ubuntu. Then you do this:
```
sudo updatedb && locate Ubuntu*
```
This will list all files and directories on your system that start with Ubuntu so you can pick the correct one.
You can also do this if you are sure the file is an iso:
```
sudo updatedb && locate Ubuntu*.iso
```
And finally, if you know the fullname but not the location, you can search without a wildcard:
```
sudo updatedb && locate Ubuntu_GutsyGibbon.iso
```

Hope it helps :)

---

### Post by Equiflux on 2007-11-30
Alrighty, thanks.

Now then: Does anyone know how I can change the loading screen?

---

