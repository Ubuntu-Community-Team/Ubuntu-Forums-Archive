---
title: "Command prompt instead of a GUI[Resolved]"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by thisguy41487 on 2007-05-09
Ok, I just installed Linux and I have NO Idea what's going on. When it loads, it goes directly to a command prompt (sudo?) (No desktop, no OS, no NOTHING... just a command prompt) I've been looking around to see if this is supposed to happen or not, but I've found no documentation on it of any kind. how do I get to that lovely desktop that the demo shows? what do I have to do? how do I do it?!?! please help because I'm dumb and frustrated!

---

### Post by Adramelech on 2007-05-09
Do you have any error messages?
Did you remember installing the server version instead of the desktop one?

---

### Post by Hishgraphics on 2007-05-09
Did you install Ubuntu? Or some other distro?

---

### Post by thisguy41487 on 2007-05-09
the only error message I got happened after it arrived at the command prompt screen. it's a display issue of some sort, and it says for me to restart once I fix it.. I don't believe I got the server version. the command prompt asks for my login and password (which I figured out) but from there I don't know what to do. is there a way to get to something where I can at least use a mouse??

---

### Post by thisguy41487 on 2007-05-09
> **Hishgraphics said:**
> Did you install Ubuntu? Or some other distro?

yep, I got it from the ubuntu website.

---

### Post by rickycodie on 2007-05-09
the display is called x its the windows manager for ubuntu and most other distro's. 
try this
[http://ubuntuforums.org/showthread.php?t=410400&highlight=restoring+x](http://ubuntuforums.org/showthread.php?t=410400&highlight=restoring+x)
if it doesn't work then try to reinstall. a good idea is to always run the disk check before installing.

---

### Post by Adramelech on 2007-05-09
wirte on the commnad prompt:

sudo /etc/init.d/gdm start

And paste here any error you get

---

### Post by Sef on 2007-05-09
Read [Psychocat's Nox]("http://www.psychocats.net/ubuntu/nox") for help in getting Ubuntu desktop running.

---

### Post by thisguy41487 on 2007-05-09
> **Adramelech said:**
> wirte on the commnad prompt:

sudo /etc/init.d/gdm start

And paste here any error you get

says : -bash: sudo /etc/init.d/gdm:  No such file or directory

---

### Post by Sef on 2007-05-09
> says : -bash: sudo /etc/init.d/gdm: No such file or directory

It seems like you did a server install.   Just follow the link in my last post (#8) and that should get you a working GUI.

---

### Post by thisguy41487 on 2007-05-10
ok, so I'm following this page saying to put in this command: *sudo apt-cdrom add* and the error comes up with: *E: failed to mount the cdrom*

---

### Post by Sef on 2007-05-10
Is that computer connected to the internet?  If so, then skip that step.

---

### Post by thisguy41487 on 2007-05-10
ok, so I did some stuff (set up correct graphical configurations and whatnot) and then put in the [sudo /etc/init.d/gdm start] and then says:

        *Starting GNOME Display Manager...                                                              [OK]



then it does nothing.. just puts another command prompt underneath.

---

### Post by Sef on 2007-05-10
Have you done this:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

?

---

### Post by Adramelech on 2007-05-10
when you run it, it runs on another terminal, terminal 7, to switch to terminal 7 press:

Ctrl +Alt +F7

---

### Post by thisguy41487 on 2007-05-10
> **Sef said:**
> Have you done this:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

?

yes. and everything finished with no error.... but still no graphical log on. I tried ctrl+alt+F7, but it brings up  a blue screen with a white text box surrounded by... some kind of characters: 
 
     *The X Server is Now Disabled. Restart GDM when it is configured correctly*.

then I tried ctrl+alt+backspace but it does nothing....

---

### Post by Adramelech on 2007-05-10
restart the computer and tell me if the blue screen reporting errors appears

---

### Post by thisguy41487 on 2007-05-10
> **Adramelech said:**
> restart the computer and tell me if the blue screen reporting errors appears

well, no blue screen this time..... in fact... there is no command prompt... or anything...... after the Ubuntu loading screen, it the screen goes black... but my monitor is still active... which means it is being sent something.. .but it's got nothing to show... at least I think s0..... oh, I try pushing ctrl+alt+F1, but it still stays blank... nothing happens..

---

### Post by Adramelech on 2007-05-10
Ctrl+Alt+F1 should give you a command prompt.

Try booting in recovery mode and type

sudo dpkg-reconfigure -phigh xserver-xorg

Dont freak out if nothing appears when you are typing your password, is the normal behaviour.

---

### Post by thisguy41487 on 2007-05-10
> **Adramelech said:**
> Ctrl+Alt+F1 should give you a command prompt.

Try booting in recovery mode and type

sudo dpkg-reconfigure -phigh xserver-xorg

Dont freak out if nothing appears when you are typing your password, is the normal behaviour.

Well, it seems that when the screen goes blank, all functions, including keyboard, stop working. just runs on the blank screen. I've reconfigured my graphical stuff like.. 5 times already.. and I can't figure out what is going on... heheh. Its probably because I live in Alaska.. the penguin doesnt like me. XD... video card maybe?? I'm using an AGP Sapphire radeon 9200 SE Atlantis. I guess I can try my little nVidia geforce of lesser value

---

### Post by umarvlie on 2007-05-10
Can you make sure you have downloaded and burned the live CD for the DESKTOP version of Ubuntu?

If so, what happened when you booted from the Live CD?

---

### Post by thisguy41487 on 2007-05-10
ha ha!
    ok, so it ends up that I think Linux didn't like my ATi card. I put in my geforce mx4000 and lo and behold. POP up the graphical login.thanks for all the help!!

---

### Post by Sef on 2007-05-10
> ok, so it ends up that I think Linux didn't like my ATi card.

Many GNU/Linuxers don't like ATI because it is often hard to get it to work right.

---

### Post by odelay on 2007-05-10
Many other people have had similar problems with the Feisty desktop CD & ATI drivers.

If you want to give the 9200 another shot with Feisty this worked for me (taken from the forums):

>  When the screen goes blank and the CD spins down, do the following:

   1. Press CTRL+ALT+F6
   2. Type:
      sudo apt-get update
      sudo apt-get install xorg-driver-fglrx
      sudo aticonfig --initial
      sudo startx

Basically you're installing the non-vesa drivers (which are broken) to allow you to use the LiveCD to install Ubuntu.  After that successfully finishes you're going to want to follow these instructions again to install the fglrx drivers permanently.

For some reason, I thought this bug only applied to newer ATI xXXX cards (like x1400, etc.)...so I could be diagnosing this incorrectly.

Good luck.

---

