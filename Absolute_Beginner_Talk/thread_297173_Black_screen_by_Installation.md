---
title: "Black screen by Installation"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by DerBiber on 2006-11-10
I have a Problem with Ubuntu 6.10.
Downloaded the 1 CD version and bootet from it.
Than i have the menu where i can choose from boot from cd/install
or boot in graphic safe mode or something like that.
At every option of this i get the loading screen with the Ubuntu graphic. But then i just get a black screen. Nothing else happens then. 

I have a Athlon 2500+ @ 3200 +
256 MB DDR Ram
Geforce FX 5200
Epox 8RDA+ Mainboard.

Can anyone help me?
Sry for bad English, i am from Germany.

---

### Post by DerBiber on 2006-11-10
No one can help me, or suggest what the problem is?

---

### Post by Velotix on 2006-11-10
[It just so happens that someone else has a near-identical problem](http://www.ubuntuforums.org/showthread.php?t=295686).

In your case, when configuring xorg, select "nv" from the list of drivers instead of "ati" and that should do the trick. The "nv" driver works fine on my GeForce 7900GS. ^^

Good luck!

---

### Post by DerBiber on 2006-11-10
I open the Textfile and theres nothing in it!
Just a blank file? What did i wrong? Or what could be wrong here?
I thought i did it right...

---

### Post by Velotix on 2006-11-10
As you haven't installed Ubuntu yet you'll be wanting the code:

```
sudo dpkg-reconfigure xserver-xorg
```

Run that from the command line. If you're at your blank screen, use <Ctrl><Alt><F1> to (hopefully) get the prompt to appear. Once you're finished changing the video card driver, you'll then need to reboot X with:

```
startx
```

If startx doesn't work (like it didn't for me once), follow the instructions thrown up by the error message and then try again - it should say something about deleting a temporary file. (Coincidentally this procedure also reset my keyboard layout settings for some reason.)

---

### Post by DerBiber on 2006-11-10
I followed the wizard coming up there and for gaphics i chose vesa.
But i'm not shure what to do after wizard...
Startx works... it does something...
But what then? I am still in the console...?
What will i have to do then to install?
If i completly restart the Computer it doesent work.

EDIT: oh, yes if its helping i have to say something else.
If the wizard trys to detect the Video hardware or graphics Card he say that he cannot recognize it (something like that). So i type manually VESA . Is this right?

---

### Post by Velotix on 2006-11-10
> In your case, when configuring xorg, select "nv" from the list of drivers instead of "ati" and that should do the trick. The "nv" driver works fine on my GeForce 7900GS. ^^

Quoting my own post there: **you want the "nv" driver, not anything else, so type "nv" instead of "vesa"**. Try other drivers only if "nv" doesn't work, but there's very little chance of that happening.

Oh, and because you're running from the CD, nothing is saved, so if you restart the PC you're back at square one. That's why you have to do this the hard way.

---

### Post by DerBiber on 2006-11-11
Um sorry, this is my first time with linux...
So how can i continue the installation after this wizard when i'm back to the console?

---

### Post by DerBiber on 2006-11-11
Pleas someone tell me this...
I think it's maybe just a simple command?
Or am i wrong?

---

### Post by Velotix on 2006-11-12
If you still aren't loading up the desktop, there's probably a problem with your CD. :???: It happens.

When burning the ISO file to CD, make sure to do the following:

1) Burn FROM the .iso file to the CD as opposed to BURNING the .iso file to CD. .iso files are images of CDs, so they work in a similar way to .zip files. ^^

2) Burn the CD at a slow speed - faster CD speeds tend to introduce errors on the CD, which is something you can't afford and might be causing your problems. :/

---

