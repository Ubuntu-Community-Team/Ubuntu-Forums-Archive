---
title: "initramfs livecd booting problem."
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by arpeggi on 2007-10-11
hey guys. i was trying to boot the livecd 'ubuntu-7.04-desktop-i386' on my dell laptop when i got the following error when trying to select the top option on the menu (can't remember the exact wording but it's something about installing or running ubuntu)

```

/bin/sh: can't access tty; job control turned off
(initramfs)
```


and then i'm shtuck.  i search for some other threads and it suggested pressing F6 and then adding break=top to the beginning of the list - i don't actually know how to do this :S

i don't want to install ubuntu for now. i've still got vista on my computer but was hoping to give ubuntu a test run. any help would be appreciated :)

_system specs._
dell vostro 1500
intel core2duo 2.0ghz
2046MB ram
nvidia GeForce 8600M GT

---

### Post by overdrank on 2007-10-11
> **arpeggi said:**
> hey guys. i was trying to boot the livecd 'ubuntu-7.04-desktop-i386' on my dell laptop when i got the following error when trying to select the top option on the menu (can't remember the exact wording but it's something about installing or running ubuntu)

```

/bin/sh: can't access tty; job control turned off
(initramfs)
```


and then i'm shtuck.  i search for some other threads and it suggested pressing F6 and then adding break=top to the beginning of the list - i don't actually know how to do this :S

i don't want to install ubuntu for now. i've still got vista on my computer but was hoping to give ubuntu a test run. any help would be appreciated :)

_system specs._
dell vostro 1500
intel core2duo 2.0ghz
2046MB ram
nvidia GeForce 8600M GT

Hi and yes if you follow those instructions it will just allow the live cd to continue ( so you won't be installing unless you want to)
Hi when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add break=top before the -- then press enter. When you receive the error again type modprobe piix then hit enter and then type exit then hit enter again this should continue the livecd to boot. 
You may also try to use graphics safe mode. Good luck!

Edit and  I might also have you checksum the disc
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by cowkiller on 2007-10-11
I had the very same problem on my HP laptop, and after trying many times editing the kernel line, I found that the easiest and fastest way was installing in text mode from an alternate Cd. You can find it at the Ubuntu download page.

Once you install it, maybe you'll have graphic issues, but that's a piece of cake :P

---

### Post by arpeggi on 2007-10-11
this is the right place to try it without installing it right?

cheers for the info :D

---

### Post by wpshooter on 2007-10-11
> **arpeggi said:**
> this is the right place to try it without installing it right?

cheers for the info :D

NO, the alternate is NOT a live CD.

---

### Post by arpeggi on 2007-10-11
> **wpshooter said:**
> NO, the alternate is NOT a live CD.

no the one im trying at the moment? pretty sure it is...

---

### Post by wpshooter on 2007-10-11
> **arpeggi said:**
> no the one im trying at the moment? pretty sure it is...

DESKTOP = LIVE CD = TRY IT BEFORE YOU INSTALL IT

ALTERNATE = TEXT BASED INSTALL - NOT = TRY IT BEFORE YOU INSTALL IT.

---

### Post by arpeggi on 2007-10-11
right so i got another error message. passed all that bit nicely.
it went through all the text [ok] and stuff. then it pops up this blue screen with a grey box in the middle.
i can't fully remember what it said and my phone camera came out all blurry.

does this mean anything to you guys or should i go back and write some of it down?

---

### Post by cowkiller on 2007-10-11
yeahh don't panic about that ^^

these are the graphic issues I mentioned.
if you press ok in that window you are in text mode. Now type

sudo nano /etc/X11/xorg.conf

look for the line where your graphic driver and change whatever it's there (It should be "nv" or "nvidia"  if it's a nvidia and "ati" or "radeon" if it's an ATI card) and change this value for "vesa". Save, exit and reboot. 

After it you'll be able to use a graphic enviroment to properly install your graphic card. try using [this program]("http://www.albertomilone.com/nvidia_scripts1.html") 

Good luck!

***** EDIT *****
You'll notice that there's also a text mode installer for the Envy script. You can use it if switching to vesa doesn't work. 
Anyway, I'm assuming that you've got ATI or Nvidia card

---

### Post by arpeggi on 2007-10-11
> **cowkiller said:**
> yeahh don't panic about that ^^

these are the graphic issues I mentioned.
if you press ok in that window you are in text mode. Now type

sudo nano /etc/X11/xorg.conf

look for the line where your graphic driver and change whatever it's there (It should be "nv" or "nvidia"  if it's a nvidia and "ati" or "radeon" if it's an ATI card) and change this value for "vesa". Save, exit and reboot. 

After it you'll be able to use a graphic enviroment to properly install your graphic card. try using [this program]("http://www.albertomilone.com/nvidia_scripts1.html") 

Good luck!

***** EDIT *****
You'll notice that there's also a text mode installer for the Envy script. You can use it if switching to vesa doesn't work. 
Anyway, I'm assuming that you've got ATI or Nvidia card

not meaning to be a noob but what do you mean by 'change this value for "vesa".'?  i've got an nvidia geforce 8600M GT. and how do i save and exit?

if i screw this up at any point and need to hard reset my laptop is there any risk of lasting damage (hardware or files on windows side)?

---

### Post by cowkiller on 2007-10-11
You've got the same card as me ^^

Ok let's see.... firstly, you won't change anything that won't allow you to access to text mode again, so don't worry about any damage. 

You have to edit the file that manages the X windows interface. For that, use nano, a text mode editor.  Type the command I told before:

sudo nano /etc/X11/xorg.conf

It will ask for the root password. Use it. You have set it in the installation process.
You'll see that the file data is organized in Sections. Look for 

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

aand change it to "vesa". It  should look like this after changing it

Section "Device"
    Identifier     "vesa"
    Driver         "vesa"
EndSection

and Reboot


(please correct me in case there's any mistake)

after this save pressing Ctrl+o and exit pressing Ctrl+x. Reboot and you'll be directed to the graphic interface hopefully.

---

### Post by arpeggi on 2007-10-11
okay i tried this again. it took me through to the same kinda point. and nothing happened. it just gave me that flashing cursor line and when i pressed it key it appeared. a command prompt i guess.  i typed exit hoping it'd take me out. and it took me to what looked like a general ubuntu command prompt.

gah i didn't even write down what it said. i guess i'll try it again.

---

### Post by arpeggi on 2007-10-11
ok so i chose run in safe graphics mode from the boot menu. and i'm in right now! 
terrible resolution but that's work in progress.  so i'm trying to install envy and i get this error:

```
dependency is not satisfiable  
```

anyone know what this is? could it be because i'm using the livecd? thanks!

btw ubuntu is looking SLICK even at this resolution

---

### Post by cowkiller on 2007-10-11
Once you've installed Ubuntu you shouldn't have to use the Livecd anymore

Hmmm... I'd suggest to install the nvidia driver manually... 
try following this thread:

[http://ubuntuforums.org/showthread.php?p=3491642](http://ubuntuforums.org/showthread.php?p=3491642)

There are many other howtos about this issue, just do a little search around if this one can't help. In no time you'll have Ubuntu running properly... and if you think it's slick, wait and see it running Compiz and kiba-dock, for example. It's just amazing!

---

### Post by arpeggi on 2007-10-11
deleted.

---

### Post by arpeggi on 2007-10-11
i tried that. i logged out. pressed CTRL+ALT+F1. then i didn't know how to log back in again xD.

any tips?

---

### Post by Shazaam on 2007-10-11
arpeggi...
It looks like you got the livecd to boot to the desktop before you did ctrl+alt+f1 right? Reboot the livecd and choose safe graphics mode and you should be back to the desktop. AFAIK you can't install anything to Ubuntu without installing Ubuntu to your drive(s) first. I could be wrong though, especially if you burnt Ubuntu to a cdrw and chose multi-session cd.

---

### Post by arpeggi on 2007-10-16
does gutsy come with a livecd version? will my graphics card issues be solved in that?

---

