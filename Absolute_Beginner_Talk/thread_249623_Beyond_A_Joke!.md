---
title: "Beyond A Joke!"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-02
I have just about had ENOUGH of this!

I am not talking about Ubuntu in general, in fact I LOVE UBUNTU! 

In the past month I have reinstalled Ubuntu/Kubuntu 5 times as I keep getting "Signal out of range" when I boot up after installing something or changing something.

Can someone PLEASE help me get back in to change the resolution!!

Russty.

---

### Post by taurus on 2006-09-02
Maybe your horizontal and vertical values are off in /etc/X11/xorg.conf!  You can configure your X (including your monitor) again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Russty of Oz on 2006-09-02
> **taurus said:**
> Maybe your horizontal and vertical values are off in /etc/X11/xorg.conf!  You can configure your X (including your monitor) again with

```
sudo dpkg-reconfigure xserver-xorg
```

But how do I get into Ubuntu to do that?

---

### Post by eternalis on 2006-09-02
Go to Applications-->Accessories-->Terminal and type that in.

---

### Post by taurus on 2006-09-02
Just wait for it to completely boot up.  Then press <Ctrl><Atl>F2 at the same time to get to a second console.  Then, log in with your username and password and run that command to configure your X again.  

Can you even boot your machine at all?

---

### Post by taurus on 2006-09-02
> **eternalis said:**
> Go to Applications-->Accessories-->Terminal and type that in.
He CAN'T boot into GUI so that is not going to work!!!  He has to do it from a console...

---

### Post by bulldog on 2006-09-02
I even think he see's nothing at all.
When you get signal out of range you see a black screen with nothing on it.

Strange that it will work with a new install and then stops working.

The answer should be in what you're changing before it fails.

---

### Post by Russty of Oz on 2006-09-02
Ctrl+Alt+F2 doesn't do anything.  Sigh!

The machine does boot, and I can get into windows.  Just not Ubuntu.  Can I get in using the recovery mode?

---

### Post by Russty of Oz on 2006-09-02
> **bulldog said:**
> I even think he see's nothing at all.
When you get signal out of range you see a black screen with nothing on it.

Strange that it will work with a new install and then stops working.

The answer should be in what you're changing before it fails.

All I did yesterday was make some changes to the repository settings (multiverse or whatever) so I can play DVD's.  Last night it was all working well, I could even play DVD's at last.

---

### Post by taurus on 2006-09-02
Yes, you can boot into the recovery mode from GRUB and run that command again...  The recovery mode will drop you into a shell right away.

---

### Post by Russty of Oz on 2006-09-02
> **taurus said:**
> Yes, you can boot into the recovery mode from GRUB and run that command again...  The recovery mode will drop you into a shell right away.

when I do that it says;

Package 'xserver-org' is not installed and no info is available

Now what??

---

### Post by taurus on 2006-09-02
Check your typing...  It's

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Russty of Oz on 2006-09-02
How embarrassing!  Yes I did make a typo error.

All was going well until it got to the color depth bit where I couldn't go any further as it wanted an input from me (in the recovery section)and I couldn't click the OK  on the xserver screen.  

I have to go out now so will have to try again later.

Russty.

---

### Post by taurus on 2006-09-02
Just pick 24 for your color depth!

---

### Post by Russty of Oz on 2006-09-02
Well, when I select 24 the xorg screen moves up and the black screen appears at the bottom with the following, waiting for an input from me

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20060903132234
root@russty-desktop:~#

so what do I put in now?

Anyone?

---

### Post by bodhi.zazen on 2006-09-03
This is not an error message, just a warning. Actually you tole you OS to overwrite xorg.conf so this is confirmation the command did it's thing.

Try ```
sudo gdm
``` and lets see what you got.

---

### Post by Russty of Oz on 2006-09-03
> **bodhi.zazen said:**
> This is not an error message, just a warning. Actually you tole you OS to overwrite xorg.conf so this is confirmation the command did it's thing.

Try ```
sudo gdm
``` and lets see what you got.

HORRAY!  That did the trick!

However.... after login, I got the following error and warning, 

[B]Internal Error
Failed to initalize HAL![/B]

and

[B]Power Manager
This program cannot start until you start the dbus system service
It is strongly recommended you reboot after starting messagebus[/B]

So, do these mean anything important, or should I just ignore them?


I am glad this thread will remain here, as I am sure I will need it again. 

Russty

---

### Post by Anduu on 2006-09-03
A reboot and starting Ubuntu normally will get rid of those messages...

---

### Post by Russty of Oz on 2006-09-03
Yes, that is ok now. Although my screen did not respond to my mouse on the first two reboots. Strange! The mouse pointer would move around the screen but I couldn't click anything.  So I rebooted a third time and it's Ok (for now).  

Thanks everyone for your help.  You saved the day!

Russty.

---

