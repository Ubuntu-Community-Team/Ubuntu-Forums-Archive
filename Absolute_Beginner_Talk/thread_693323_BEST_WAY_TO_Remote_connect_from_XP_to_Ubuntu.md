---
title: "BEST WAY TO: Remote connect from XP to Ubuntu?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-10
What is the best way to remotely connect from a WinXP box to an Ubuntu box?

I currently am only aware of two options:
[LIST=1]
[*][VNC]("https://help.ubuntu.com/community/VNC")
[*][FreeNX]("https://help.ubuntu.com/community/FreeNX")
[/LIST]

Are there any others?
What do you use and why?

**_EDIT_**: Not just command line (putty/ssh) access but **Graphic (GUI) desktop** access

---

### Post by p_quarles on 2008-02-10
PuTTY. I use that to connect via SSH.

---

### Post by amingv on 2008-02-10
On the (few) occasions I've needed it, I use SSH. (I carry Putty in my pen drive, it's pretty much all I need.)

<edit>Man, he beat me to it</edit>

---

### Post by BassKozz on 2008-02-10
i should've prefaced by saying **_Graphic (GUI) DESKTOP_** connecting, not just command line

---

### Post by p_quarles on 2008-02-10
> **B/-\ssKozz said:**
> i should've prefaced by saying **_Graphic (GUI) DESKTOP_** connecting, not just command line
You can use PuTTY to forward an X session, so that stipulation isn't necessary.

---

### Post by BassKozz on 2008-02-10
> **p_quarles said:**
> You can use PuTTY to forward an X session, so that stipulation isn't necessary.

isn't that just the same as VNC or SSH tunnelling VNC ?
If not can you please explain:confused:

---

### Post by p_quarles on 2008-02-10
> **B/-\ssKozz said:**
> isn't that just the same as VNC or SSH tunnelling VNC ?
If not can you please explain:confused:
It's the same, except that you don't need VNC. ;)

---

### Post by BassKozz on 2008-02-10
> **p_quarles said:**
> It's the same, except that you don't need VNC. ;)
Still confused... would you mind posting a link to a tutorial on this? or explain how this works?

---

### Post by amingv on 2008-02-10
[http://www.math.umn.edu/systems_guide/putty_xwin32.html](http://www.math.umn.edu/systems_guide/putty_xwin32.html)

And

[http://the.earth.li/~sgtatham/putty/0.54/htmldoc/Chapter3.html](http://the.earth.li/~sgtatham/putty/0.54/htmldoc/Chapter3.html)

---

### Post by BassKozz on 2008-02-10
> **amingv said:**
> [http://www.math.umn.edu/systems_guide/putty_xwin32.html](http://www.math.umn.edu/systems_guide/putty_xwin32.html)

And

[http://the.earth.li/~sgtatham/putty/0.54/htmldoc/Chapter3.html](http://the.earth.li/~sgtatham/putty/0.54/htmldoc/Chapter3.html)

Ahh yes, good ole [Xming]("http://www.straightrunning.com/XmingNotes/"), I remember playing around with this a while back [I couldn't get it to display the whole desktop]("http://ubuntuforums.org/showthread.php?t=618984"), only individual apps... Is this alternative (Xming) better then VNC and/or FreeNX ?

p.s. **p_quarles**, is Xming what you were referring too or is there another alternative?

---

### Post by p_quarles on 2008-02-10
> **B/-\ssKozz said:**
> p.s. **p_quarles**, is Xming what you were referring too or is there another alternative?
You need to install some kind of X server on the remote machine before this is possible, yes. Cygwin is one popular choice, and that's what I had in mind. Once you have an X server with SSH forwarding enabled, you can remote into it from a *nix box by running:
```
ssh -X username@server
```

---

### Post by BassKozz on 2008-02-11
Anyone:
What makes forwarding an Xsession via SSH/Putty better then VNC or FreeNX (or another alternative)?

---

### Post by hyper_ch on 2008-02-11
For what reason do you need to connect?

---

### Post by BassKozz on 2008-02-11
I use my laptop to connect to my desktop while  I am away from the desk... even if I am in my own house but i don't feel like going to my office,  I like to access my desktop remotely.

My Lappy runs XP
My Desktop will soon be running Ubuntu 64-bit.

---

### Post by p_quarles on 2008-02-11
I wouldn't say it's "better," it's just a preferred option for many people. The main reasons: 1) SSH is an established and very secure remote shell protocol; 2) You can install X on pretty much any client machine; 3) If you're already running an SSH server, there's no point in adding another daemon for something that SSH itself can accomplish.

---

### Post by BassKozz on 2008-02-11
> **p_quarles said:**
> I wouldn't say it's "better," it's just a preferred option for many people. The main reasons: 1) SSH is an established and very secure remote shell protocol; 2) You can install X on pretty much any client machine; 3) If you're already running an SSH server, there's no point in adding another daemon for something that SSH itself can accomplish.
All Very good points that I didn't think of before =D>
Ok I am sold by going this route, but I still have a question for ya p_quarles,
you said:
> **p_quarles said:**
>  You can install X on pretty much any client machine
What's the best X client to use on a WinXP machine?

I've heard mention of Xming, and you mentioned Cygwin, and I've also heard of [Win32]("http://www.starnet.com/products/xwin32/") (but a license costs $225 :shock:)...
Why did you recommend Cygwin?  
Is it possible to install this on a USB flash drive so I can remotely connect to my machine via SSH/Cygwin from a USB drive w/out leaving data/traces on the host OS?

---

### Post by p_quarles on 2008-02-11
I mentioned Cygwin just because it's the only one I've used. For all I know, the others may be better. Personally, though, I like Cygwin because it gives you all the GNU utilities in a Windows environment.

I *haven't* tried this, but it does look like there's a portable Cygwin:
[http://www.dam.brown.edu/people/sezer/software/cygwin/](http://www.dam.brown.edu/people/sezer/software/cygwin/)

---

### Post by amingv on 2008-02-11
> **B/-\ssKozz said:**
> Anyone:
What makes forwarding an Xsession via SSH/Putty better then VNC or FreeNX (or another alternative)?

Not to mention a client is very lightweight (did I mention I carry Putty on my pendrive?). I usually don't need an X session, just something where I can type apt-get upgrade in my server...

---

### Post by BassKozz on 2008-02-11
> **hyper_ch said:**
> For what reason do you need to connect?

To better answer your question:
I just built a new rig with a Q6600 proc overclocked to 3.6ghz, and 8gigs of ram... 
I will be using this as my virtualization server.
My plan is to run multiple guest operating systems within Ubuntu 64-bit using [VirtualBox]("http://www.virtualbox.org/"), and I will give each guest OS a piece of the resources...

_For Example:_
Host OS - Ubuntu 64-Bit - 2GB Ram
Guest OS #1 - WinXP - 2GB Ram
Guest OS #2 - Windows Vista - 2GB Ram
Guest OS #3 - Other? - 2GB Ram

This way I can consolidate some of my Boxes into this one ServerBox (my office has over 8 beige boxes laying around and i NEED to CONSOLIDATE)...

So rather then remotely connecting to each one of these Guest OS's I would like to connect to my main HOST OS (Ubuntu 64-bit) so that I can manage all of them from one session :D
So far it looks like Cygwin is the way to go, time to do some reading ;)

---

### Post by BassKozz on 2008-02-11
:BUMP:
Anyone else want to chime in?

---

### Post by JoshuaRL on 2008-02-11
> **B/-\ssKozz said:**
> Is it possible to install this on a USB flash drive so I can remotely connect to my machine via SSH/Cygwin from a USB drive w/out leaving data/traces on the host OS?

Ooooooooooooooooooooo.  Methinks you could do some dastardly stuff with that if so.  Of course, maybe not.

---

### Post by BassKozz on 2008-02-11
> **JoshuaRL said:**
> Ooooooooooooooooooooo.  Methinks you could do some dastardly stuff with that if so.  Of course, maybe not.

dastardly ???

I was simply looking for a way to connect to my machines while away from home without leaving a trace of how/where I connected too... incase someone tried to logon to my machines after I stepped away from the machine.

---

### Post by daflame on 2008-02-12
> **B/-\ssKozz said:**
> dastardly ???

I was simply looking for a way to connect to my machines while away from home without leaving a trace of how/where I connected too... incase someone tried to logon to my machines after I stepped away from the machine.

I post a vote for FreeNX, but I'm slightly biased as I run a FreeNX forum:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

FreeNX uses the same SSH/X port forwarding, but also adds amazing compression techniques to reduce bandwidth consumption and improve responsiveness while still maintaining very high color depths for a better at the desk experience.

However, as you mentioned you want zero footprint, so you would have to delete the login session behind you or point the user session or .nx folder at least to a flash drive.  I'm not sure if the nxclient can run off of a flash drive or not.  I'm sure it would work if you rebooted on a bootable flash install of linux though.

---

