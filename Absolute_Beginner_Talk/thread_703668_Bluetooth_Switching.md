---
title: "Bluetooth Switching"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Law506 on 2008-02-21
I got me a nice little dual boot of XP and Ubuntu 7.10 going.  I have XP basically on the principle that I cannot get my Lexmark to print inside of Ubuntu, but that is a whole other story.

I have a bluetooth mouse & keyboard that I can get to work with either OS, but once I switch from XP to Linux or vica versa the later OS I choose is unable to detect the bluetooth components and I have to hook up a USB keyboard & mouse and reaquire the bluetooth.  Is there something that I missed in the setup on either OS or is there just a glitch?

Another question, is there a way to get bluetooh going upon startup, so at the Grub screen I can scroll through the options?  I believe this is a BIOS thing and if that is the case I will just keep searching in there for the right option. 

Thanks.

---

### Post by linuxwizard on 2008-02-21
Look over this

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by Law506 on 2008-02-21
I did, that is the original page that I used for reference back when I first got into Ubuntu.  Thanks though, I will give it another look just in case.

---

### Post by Law506 on 2008-02-21
Alright.. I am now on hour 5 or so.

I have read many forums on bluetooth setup,

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

[http://ubuntuforums.org/showthread.php?t=599899&highlight=bluetooth+boot&page=2](http://ubuntuforums.org/showthread.php?t=599899&highlight=bluetooth+boot&page=2)

and some others, but I cannot get my computer to detect my mouse or keyboard.   I have gotten the mouse to work when I used both of those below while in the system.  I just restarted bluetooth services and it eventually came on.

HIDD_OPTIONS:"-i connect <mouse add> --server"
HIDD_OPTIONS:"--connect <mouse add> --server"

When I did this on my last install of Ubuntu I had no problems.. but this time something is strange.

Any other links or advice would be much appreciated.

---

### Post by steveneddy on 2008-02-21
Have you tried [Blueman]("http://blueman.tuxfamily.org/") ?

---

### Post by Law506 on 2008-02-22
Not to sure what was the problem... just decided to do a reinstall and everything works like a charm now.

Must of done something to mess something up at a previous instance.

Thanks for the help.

---

