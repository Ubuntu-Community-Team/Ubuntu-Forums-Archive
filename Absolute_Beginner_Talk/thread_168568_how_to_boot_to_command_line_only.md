---
title: "how to boot to command line only?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by annda on 2006-04-30
i've been searching the forums but it seems most people have the opposite problem: they WANT to boot to X right away.

I, on the other hand, would like to boot to CL and start X if/when i want to. i have a laptop and battery usage is of some concern. also, i'd like to control what my box does.

in other distros i had the option 'use X as default boot option' or so during installation. i don't recall seeing that in ubuntu (or have i been to anxious to install).

what do i need to do/modify to boot w/out X as default?

---

### Post by rado_london on 2006-04-30
Use this:
```
sudo init 3
```
After reboot you will be in CL.

---

### Post by Tedd on 2006-04-30
How would one go about going back to the GUI after booting to command line?

---

### Post by annda on 2006-04-30
unfortunately, **rado_london**'s advice doesn't work. to switch the boot runlevel 3 permanently I'll probably need to edit something. what? it's still a mystery to me. can somebody help me along that path?

i figure i could still use the startx command combined with an appropriately modified .Xauthority file to get to the desired X environment (which has worked with other distros for me).

---

### Post by TLE on 2006-04-30
[This thread]("http://www.ubuntuforums.org/showthread.php?t=105968&highlight=changing+runlevel") has some nice solutions for that.

Oh by the way, Kudos.! for searching before you posted. Just thought I would share: I found it by searching for "changing runlevel" but offcourse if you don't know that that *could* be part of the solution then there is really no way you would know to search for it ;) I hope it helps

---

### Post by jpkotta on 2006-04-30
I understand where you're coming from.  I used to to this before I got Ubuntu, and I just never really cared afterwards for some reason.  Anyway, I haven't done this for Ubuntu, but I can give you some hints.

It is a good idea to get an idea of what runlevels are.  They are basically overall system modes.  There is a runlevel for booting, one for shutting down, one for recovery, a normal usage one, etc.  We're going to change which runlevel to end up in after a normal boot, and make that runlevel not start X.

In /etc/inittab, look for the following line:
```
# The default runlevel.
id:2:initdefault:

```
Change it to 3 (or 4 if you hate odd numbers).

Read this: [http://en.wikipedia.org/wiki/Run_level#Debian_Linux_runlevels](http://en.wikipedia.org/wiki/Run_level#Debian_Linux_runlevels).  You don't have to worry about messing up runlevel 3 because you can always change inittab to use 2 again.  

Use an administration tool like BUM to prevent X from starting at boot in runlevel 3.  I don't know what exactly to turn off, but a pretty good bet is gdm and anything with 'X' in it.  Do not disable xinetd if you see that.  Alternatives to BUM are sysvconfig and sysv-rc-conf, which you may like better because they are text mode.  Don't use update-rc.d, that's for installation.

Another resource: [http://rute.2038bug.com/node35.html.gz](http://rute.2038bug.com/node35.html.gz)

---

### Post by Nequeo on 2006-04-30
[EDIT] Never mind. jpkotta beat me to it. [/EDIT]

---

### Post by annda on 2006-04-30
being as impatient as i am, i modified the /etc/inittab but it got me nowhere.

following **TLE**'s helpful link I modified /etc/X11/default-display-manager and commented out gdm.

now it works beautifully. thanks a lot!

i promise to read on about what i just did with your help so that maybe i can help someone else.

---

