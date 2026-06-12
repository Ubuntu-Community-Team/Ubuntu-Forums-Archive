---
title: "Edgy, yes. Fiesty, I don't think so"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Rhaddad on 2007-04-20
Well, like many of you. I was pumped for this new ubuntu "easy to use". Only one problem, I can't even install it. I tried live CD ( it didn't boot up, gave me the message; failed to start the x server (your graphical user interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? ), then tried the alternate, worked perfectly the splash screen came up on boot, then I also got the message, failed to start the x server (your graphical user interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?. I have installed this new version so many times, and it's getting on my nerves. I had ubuntu edgy, and attempted to do an upgrade, but it failed miserably, so I had to get a window's ext reader and export all the folder's.

Will I be able to use the new Ubuntu, or not? 

I have a dell inspiron 9400 2gig ram, duo core2.0 ghz, ATI 128mb Video card.

---

### Post by rich.bradshaw on 2007-04-20
That shouldn't happen... 

Try going to your BIOS on your computer and setting your video memory to 8MB. I had to do that on my Dell ages ago to get Linux to boot and have kept it like that ever since.

---

### Post by Rhaddad on 2007-04-20
8mb, are you sure? wouldn't that stuff up windows?

---

### Post by Drunner611 on 2007-04-20
Did you check for errors on your cd?

---

### Post by Rhaddad on 2007-04-20
Yea, no erors.

---

### Post by Seisen on 2007-04-20
Sometimes it doesn't recognize your graphics card correctly from the Live-CD, especially with the Edgy Live Cd, which I had problems with. What i did was use Dapper to upgrade to Edgy and then upgrade to Feisty. Pain in the a%^ yes, but it worked. You can also go into the change your xorg.conf file to get it to work and then get your graphics card to work.

---

### Post by Rhaddad on 2007-04-20
Yes, but i was useing alternate, how do i edited the xorg.conf file, and what do i edit in it?

Is fiesty worth it, I mean i can't even install it, I'm pretty annoyed at the moment. I don't know what to do

Does anyone recon a bios update will fix it?

---

### Post by Seisen on 2007-04-20
Type this in the terminal

```
sudo vim /etc/X11/xorg.conf
```

Hold down the shift + I keys and it should say insert in white letters.

Scroll down with the arrow keys until you see this

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"

```

change the driver to "vesa" and then hit the Escape button and then do this

```
:wq
``` 

it will then write the file and then save it. Reboot and it should working now. After that you can fix your graphics card problems to get the right driver to work.

This might help to get your ATI card working.

[http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

---

### Post by Kobalt on 2007-04-20
Or you can try to install/resintall the drivers for your card.
Press Ctrl+Alt+F1 to access a command line then install the drivers for your card with : ```
sudo aptitude install xorg-driver-fglrx
```
Then enter ```
sudo aticonfig --initial
``` to set up your xorg.conf file properly.

Finally reboot, and hopefully you can access a graphical session properly.

---

### Post by Devastator9 on 2007-04-20
I used the Sticky for installing ATI X**** from Absolute Beginner Talk.
I used the Alternate CD in text mode installer. Just follow the guide.
Worked Great for me.

Dev

---

### Post by Rhaddad on 2007-04-20
I'll try that sticky.

It allready is on vesa?

---

### Post by stump138 on 2007-04-20
sometimes aticonfig will make the situation worse :(

try this first:

make a backup!
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

install the fglrx drivers:
sudo aptitude update && sudo aptitude install xorg-driver-fglrx

edit xorg.conf 
sudo nano /etc/X11/xorg.conf
find where it says "ati" under the device section and replace that with "fglrx"
save and exit

reboot or restart x
by startx

---

### Post by Rhaddad on 2007-04-20
I did the sticky tutorial, it worked. Now I'm posting this from the NEW UBUNUT!

---

