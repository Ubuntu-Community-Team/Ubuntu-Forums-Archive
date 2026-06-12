---
title: "G3 install - No X?"
date: 2009-01-10
forum: Apple Hardware Users
---

### Post by DurocShark on 2009-01-10
I just installed 8.10 on a G3 iBook w/640mb. After the undiscovered CDROM issue (solved by another thread) it installed successfully. 

Now, however, it just boots to the console. No GUI. If I drill down to /usr/X11R6/bin/ and run X11 I get "The program 'X11' is currently not installed." 

Did I miss a step during the installation?

---

### Post by dadozgb on 2009-01-10
> **DurocShark said:**
> I just installed 8.10 on a G3 iBook w/640mb. After the undiscovered CDROM issue (solved by another thread) it installed successfully. 

Now, however, it just boots to the console. No GUI. If I drill down to /usr/X11R6/bin/ and run X11 I get "The program 'X11' is currently not installed." 

Did I miss a step during the installation?

To start x server do startx. Maybe you x server isn't installed or it is not configured. Try in console dpkg -l | grep xorg

---

### Post by DurocShark on 2009-01-10
Thanks. Nothing. :(

I'm reinstalling and watching the options to see if I missed anything.

---

### Post by avtolle on 2009-01-10
You might also want to look at [https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3) for some additional information.

---

### Post by DurocShark on 2009-01-12
I didn't want to leave this thread hanging. Lost internet at home over the weekend.

The issues in the G3Knowns page don't seem to apply unfortunately. 

I've downloaded Gutsy and am going to try that and see if it works.

---

### Post by tiresia on 2009-01-12
> **DurocShark said:**
> I just installed 8.10 on a G3 iBook w/640mb. After the undiscovered CDROM issue (solved by another thread) it installed successfully. 

Now, however, it just boots to the console. No GUI. If I drill down to /usr/X11R6/bin/ and run X11 I get "The program 'X11' is currently not installed." 

Did I miss a step during the installation?

Most probably, you didn't choose the option to install the Desktop.

---

### Post by DurocShark on 2009-01-12
> **tiresia said:**
> Most probably, you didn't choose the option to install the Desktop.


You know I reinstalled this several times and never saw an option for that... At what point does it come up?

---

### Post by tiresia on 2009-01-12
Honestly, I don't remember anymore... I made so many Installation in the last times, of different Distos, that I am not sure

If it works, as I think, as the Debian Installer, you will install first the basic system. After that you will get a list of options, and you will be asked if you want to install a Desktop Envaironment (you must select it by hitting 'the Space bar').

---

### Post by ajmctaggart on 2009-01-14
Well, since you've got a "server" install going for you it seems, 

Did you try to install from the console?

This is assuming you can get network connection, that may be a different post if you cannot...

sudo apt-get update
```
sudo apt-get install ubuntu-desktop
```?

or something to that effect, it's been awhile...

---

### Post by DurocShark on 2009-01-14
> **ajmctaggart said:**
> Did you try to install from the console?

```
sudo apt-get install ubuntu-desktop
```?

or something to that effect, it's been awhile...

No internet at home. I have to bring stuff from work or the library. (Long story involving wives and money.)

I figured my problem out though. I somehow grabbed the server iso instead of the desktop one. Doh!

I got the right ISO now, but haven't had a chance to play with it yet. Gutsy didn't install. I got the half-white screen, did the command that is supposed to fix it and just got a solid black screen. Ugh. 

I'm running Ubuntu in my MacBook here as a virtual machine in VMWare Fusion and it runs great. So I'm hoping to replicate that in my old G3 for my son to use.

---

### Post by ajmctaggart on 2009-01-14
That sounded about right,

and it's always a long story...always...

---

### Post by DurocShark on 2009-01-19
I'll call this resolved. 8.04 Desktop works fine. I could smack myself.

Now, if I could figure out why it won't set the display higher than 800x600...

---

### Post by NewsAndHistory on 2009-01-19
My computer has almost the exact same specs as yours.[B]

How did you get Ubuntu to detect your CD-ROM?
[/B][B]Would you send me a link to the forum-thread, in which Ubuntu-user(s) helped you get that problem resolved?

[/B]I'm having the same problems with my iBook G3. I'm trying to install one of the Ubuntu spin-offs: Xubuntu 8.10 Intrepid on it.

As far as I've read & experienced, Xubuntu Intrepid is highly-recommended for iBook G3-users, but Debian Lenny works much better on iBook G3 compared to other Debian-based distros.

---

### Post by DurocShark on 2009-01-19
When installing, switch terminals (ctrl-alt F1 or ctrl-alt-fn F1) and type "modprobe ide-scsi" per this: [http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

That worked perfectly.

---

### Post by NewsAndHistory on 2009-01-20
Thanks for your help!

---

