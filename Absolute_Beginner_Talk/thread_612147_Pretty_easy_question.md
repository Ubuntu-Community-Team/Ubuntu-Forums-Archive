---
title: "Pretty easy question"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by OisinT on 2007-11-13
I just upgraded to Gusty and on update I noticed that my desktop shortcuts for Azureus, Firefox and Thunderbird don't work anymore.
Anyone know why this is?  I managed to put firefox and thunderbird back on the desktop, but i can't find Azureus to make a shortcut.
Also I changed the firefox and thunderbird icons in Fiesty, but now that I've upgraded the icons are HUGE... like massive.  Only problem is I can't remember where the icons are located so that I can resize them.

thanks

---

### Post by carlosjuero on 2007-11-13
> **OisinT said:**
> I just upgraded to Gusty and on update I noticed that my desktop shortcuts for Azureus, Firefox and Thunderbird don't work anymore.
Anyone know why this is?  I managed to put firefox and thunderbird back on the desktop, but i can't find Azureus to make a shortcut.
Also I changed the firefox and thunderbird icons in Fiesty, but now that I've upgraded the icons are HUGE... like massive.  Only problem is I can't remember where the icons are located so that I can resize them.

thanks
You shoudl be able to right click the shortcuts and select an option to scale them down to a good size. For Azeurus - it is normally put into the Applications -> Internet menu, for azeurus try typing this in to find it:
```

whereis azeurus

```

I will also reiterate not to do the rm command; that will destroy your folder structure.

---

### Post by OisinT on 2007-11-13
> **carlosjuero said:**
> You shoudl be able to right click the shortcuts and select an option to scale them down to a good size. For Azeurus - it is normally put into the Applications -> Internet menu, for azeurus try typing this in to find it:
```

whereis azeurus

```

I will also reiterate not to do the rm command; that will destroy your folder structure.

thats the weird thing.. when i tried to do that it either jumped from being tiny tiny tiny to huge.

```
oisint@OisinT1:~$ whereis azeurus
azeurus:
oisint@OisinT1:~$ 


```

---

### Post by carlosjuero on 2007-11-13
> **OisinT said:**
> thats the weird thing.. when i tried to do that it either jumped from being tiny tiny tiny to huge.

```
oisint@OisinT1:~$ whereis azeurus
azeurus:
oisint@OisinT1:~$ 


```
hmm... looks like you will need to try reinstalling azeurus - something might have gotten broken. See if the ```
sudo apt-get reinstall azeurus
``` fixes it or not.

As for the resizing, that is an odd issue - it might be because the files are .jpg rather than .svg for the custom icons? Don't have much experience in resizing icons on the desktop, I keep my desktop just about as bare as possible (with the exception of a few icons to connect to my file server via NX).

---

### Post by OisinT on 2007-11-13
```
oisint@OisinT1:~$ sudo apt-get reinstall azeurus
[sudo] password for oisint:
E: Invalid operation reinstall
oisint@OisinT1:~$ 

```


maybe just try install?

---

### Post by carlosjuero on 2007-11-13
> **OisinT said:**
> ```
oisint@OisinT1:~$ sudo apt-get reinstall azeurus
[sudo] password for oisint:
E: Invalid operation reinstall
oisint@OisinT1:~$ 

```


maybe just try install?
yeah, try install - maybe try removing it first. I could have sworn there was a reinstall option :/ sorry about that.

so do ```
sudo apt-get remove azeurus
sudo apt-get install azeurus
```

---

### Post by OisinT on 2007-11-13
strange:

```
oisint@OisinT1:~$ sudo apt-get remove azeurus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package azeurus
oisint@OisinT1:~$ sudo apt-get install azeurus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package azeurus

```

---

### Post by philinux on 2007-11-13
If you upgraded azureus will not be installed, you will have to install.

This is becasue as part of the upgrade the sources list was modified to exclude any non free stuff.

But you config files if any in your home folder will be intact.

your sources list may also need amending

---

### Post by carlosjuero on 2007-11-13
> **OisinT said:**
> strange:

```
oisint@OisinT1:~$ sudo apt-get remove azeurus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package azeurus
oisint@OisinT1:~$ sudo apt-get install azeurus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package azeurus

```
Spelling error :/

azureus is the proper package name

---

### Post by OisinT on 2007-11-13
> **carlosjuero said:**
> Spelling error :/

azureus is the proper package name

haha thanks... been a long day!


thx for your help!

---

### Post by carlosjuero on 2007-11-13
> **OisinT said:**
> haha thanks... been a long day!


thx for your help!
Yep - thats what lots of us like doing :)

Sorry it took me so long to catch on to the spelling, I don't use azureus but when I tried to test the install on my file server I figured out I was spelling it wrong :/

---

### Post by OisinT on 2007-11-13
it's strange, now that it's installed when i try to open it.. it loads, but then quickly disappears.
tried restarting, reinstalling, etc... still does the same thing

---

### Post by carlosjuero on 2007-11-13
> **OisinT said:**
> it's strange, now that it's installed when i try to open it.. it loads, but then quickly disappears.
tried restarting, reinstalling, etc... still does the same thing
Try removing the configuration/settings folder for it. It is in your Home folder, open up Nautilus to there, press Ctrl + H and look for a folder named something like **.azureus** (note the period in front). Rename/remove it and then try restarting the program to see if that helps.

---

### Post by OisinT on 2007-11-14
> **carlosjuero said:**
> Try removing the configuration/settings folder for it. It is in your Home folder, open up Nautilus to there, press Ctrl + H and look for a folder named something like **.azureus** (note the period in front). Rename/remove it and then try restarting the program to see if that helps.

It didn't work again when I tried reinstalling it... after a lot of searching it seems pretty common.
I'm going to try Deluge, only problem with that is I can't figure out how to set up automatically downloading shows via RSS.


thanks for all your help :guitar:

---

