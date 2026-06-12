---
title: "can't log in, and cant mount hda1 from live session"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-09-17
Evidently my hard drive is full, and it won't let me log in. I ttried every option in 'change session' to no avail. (I have dapper installed, but only have a breezy live cd.)

I figured I could mount the hard drive from a live session, and dump some of the garbage. (Worst thing is that I know I have about 130 megs in my trash bin...) All I need to do is figure out how to delete this, and I should be OK...

Any help would be appreciated!

---

### Post by Papa-san on 2006-09-17
Is there a way to get into this HD by some sort of bootup endaround? Any way to empty the trashwithout actually logging in?

---

### Post by Papa-san on 2006-09-17
Here's what it says:

"GDM could not write to your authorization file. This could mean that you are out of disk space, or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."

Seeing as how it is a 5 gig hard drive, the space thing is quite likely...

---

### Post by bodhi.zazen on 2006-09-17
In that case, change to tty1 with Ctrl-Alt-F1

Can you log in via cli ?

If so, remove away.......

---

### Post by Najand on 2006-09-17
OK... Boot Normally...
Push Alt+Ctrl+F1
Login in terminal
and then ```

sudo aptitude clean

```
would help you clean cached files of your apt packjage manager...
Then you will have enough space to login and cleaning your system.

---

### Post by Papa-san on 2006-09-17
> **bodhi.zazen said:**
> In that case, change to tty1 with Ctrl-Alt-F1

Can you log in via cli ?

If so, remove away.......

I don't know how to log in via cli, nor do I even know what it is... LOL

When do I do the Ctrl-Alt-F1 thing?

---

### Post by bodhi.zazen on 2006-09-17
:lol:

cli = command line interface.

hit Ctrl-Alt-F1 to change to "tty1"

If you see a login prompt enter your user name and password.

You can then run the **sudo aptitude clean** as above or start deleting files.

delete command = rm <path/file.name>

to remove a directory rm -R ,/path/directory>.

take care, there is no undelete .....

You may want to re-try your gui after the aptitude clean:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by Papa-san on 2006-09-17
Thanks,

I got it taken care of!

I went ahead and deleted my music files. I don't know why I even put them on here. I guess it doesn't matter, I have almost all the CD's anyways... ;) 

This is one of the things AZZ was talking about in regards to the usability of ubuntu for us windows converts... A windows OS has something like a safeguard to avoid this kind of thing for us dummies!


Anyways, Thanks again!

---

### Post by bodhi.zazen on 2006-09-17
Glad to be of service.

FYI: This type of thing can happen in Windows. With windows the is no support of the quality of the Ubuntu forums.

As you become more familiar with Linux you will laugh at how easy this was to fix.

Familiarity is part of ease of use. How much experience do you have with Windows?

---

### Post by Papa-san on 2006-09-18
I've used windows (DOS) since 1990. I had used nothing else until April of this year, when I formatted my hard drive and installed Ubuntu.

As to the support here, there is absolutely NO question of that. I won't go back to windows! I just need to figure out how to install Biblical Greek fonts and keyboard layout, and I will be all set. (Other than a need for a bigger hard drive) lol

---

