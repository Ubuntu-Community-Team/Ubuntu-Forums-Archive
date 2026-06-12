---
title: "Arch is Pretty Kewl"
date: 2008-06-18
forum: Arch and derivatives
---

### Post by Fred_E _krugar on 2008-06-18
Howdy folks I just installed Arch for the fist time and seems pretty good thus far. I have even played a few rounds of Counter Strike Source on it. Runns it a little better than my Kubuntu mini install.


Ok here is the question. Now that I have it installed is there any way I can make a install disk of my setup?? If so can someone plz show me the way.

---

### Post by mrsteveman1 on 2008-06-18
Yea arch is cool, especially rolling updates (even the kernel, yea its awesome).

But I don't like their policy of not configuring anything by default, even when it makes perfect sense to do so.

---

### Post by Fred_E _krugar on 2008-06-18
The reason I ask about a custom install disk is because I like to dork my OS'es up beyond repair. And it takes a little longer to install Arch than it does for other distros. Sometimes I just do not have the extra time.

---

### Post by Methuselah on 2008-06-18
> **mrsteveman1 said:**
> Yea arch is cool, especially rolling updates (even the kernel, yea its awesome).

But I don't like their policy of not configuring anything by default, even when it makes perfect sense to do so.

Indeed.
I just backed up my home folder and installed it and I'm about to go back to ubuntu. Direct rendering in X is on (though strangely glxgears is reporting framerate but the gears aren't animating) which is something that never worked in ubuntu. However, so many other things are out of whack and I'll have to figure out the archway to configure it. 

I'm not really scared of that since I did it with FreeBSD. 
However, that knowledge doesn't directly transfer and I just realised I don't have the time to fiddle with a partially working machine right now.

My current plan is to put ubuntu back on my main machine and continue playing with arch on a second machine that I don't NEED to use. That way when I make the plunge again, I'll know all the configuration steps by heart.

Pretty cool system though, and I do love how the structure is very transparent.

---

### Post by mrsteveman1 on 2008-06-19
With regards to the install disk question, you can always just image the drive somewhere and then you can copy it back over to reinstall.

For instance you could dd the partition and pipe the output through gzip to end up with a small image that can be easily put right back. This of course requires the partition to stay the same size and would be an exact binary copy.

The other thing you could do is simply make a compressed tarball of root after setting things up the way you want, you unpack it and you have basically a complete system. This would work on any partition on any system (as long as root is mounted by label or the device names for the drives are the same).

As far as modifying an actual install disk that's more complicated. To include custom modifications you would have to add packages to the CD and have the installer install them at the same time as the rest of the system. Not impossible of course, if you have a specific set of things you want to change in config files on the system, you can just put those files in a full path tar.gz file (which is what arch packages are) and unpack that package to root after doing a normal install.

Any of that sound like what you want?

---

### Post by Barrucadu on 2008-06-19
Unless you really want to fiddle around with making your own installation disc, I recommend you do what I do. I have a series of scripts that install and partially configure an Arch system - different scripts depending on what I want to achieve.
It's incredibly easy to do if you have a basic knowledge of bash.

---

### Post by Fred_E _krugar on 2008-06-19
> **Barrucadu said:**
> Unless you really want to fiddle around with making your own installation disc, I recommend you do what I do. I have a series of scripts that install and partially configure an Arch system - different scripts depending on what I want to achieve.
It's incredibly easy to do if you have a basic knowledge of bash.
 

Welp thats not me lol, wanna help??

---

### Post by Barrucadu on 2008-06-19
Well, it would just be a script along the lines of this...

```
#!/bin/bash
pacman -Sy pacman
pacman -Syu

adduser
pacman -S sudo
nano /etc/sudoers

pacman -S xorg mesa libgl xf86-video-vesa
Xorg -configure
mv /root/xorg.conf.new /etc/X11/xorg.conf
nano /etc/X11/xorg.conf
```

And so on, and so forth...

---

### Post by Fred_E _krugar on 2008-06-19
> **Barrucadu said:**
> Well, it would just be a script along the lines of this...

```
#!/bin/bash
pacman -Sy pacman
pacman -Syu

adduser
pacman -S sudo
nano /etc/sudoers

pacman -S xorg mesa libgl xf86-video-vesa
Xorg -configure
mv /root/xorg.conf.new /etc/X11/xorg.conf
nano /etc/X11/xorg.conf
```

And so on, and so forth...


Ok here is a stupid question when during the installation would I use this?? Or exactly what do I do with it?

I am sorry for the stupid but I have a feeling I am about to dork the Arch system up . It has run too smoothly for two days........Need to break....it<-----------That was the little voice in my head...

---

### Post by Barrucadu on 2008-06-20
Well, you would write your script, containing the commands you run after installation. You would then install Arch on a new machine, reboot into Arch, and run you script.
It's just a list of commands you run after installing (ie: the commands in the beginners guide), so you run it after installing.

---

### Post by mips on 2008-06-20
> **Barrucadu said:**
> Well, you would write your script, containing the commands you run after installation. You would then install Arch on a new machine, reboot into Arch, and run you script.
It's just a list of commands you run after installing (ie: the commands in the beginners guide), so you run it after installing.

The 3rd time I installed Arch I said to myself that I should do that. Never did though although it is so simple to do, just record all your commands you used during installation.

Anyway, getting my new pc on Saturday so hopefully this time round I will do that.

---

### Post by handy on 2008-06-22
> **Fred_E _krugar said:**
> 
Howdy folks I just installed Arch for the fist time and seems pretty good thus far. I have even played a few rounds of Counter Strike Source on it. Runns it a little better than my Kubuntu mini install.


Ok here is the question. Now that I have it installed is there any way I can make a install disk of my setup?? If so can someone plz show me the way.

Arch is simpler than most other distro's & after your initial install, you will have started to become familiar with (even having created some of them yourself) the Arch config' files.  If you stuff up your Arch install, you really should be able to repair it a LOT easier than more cumbersome distro's like Ubuntu, which as wonderful as they are, they are overly complex, especially when compared to Arch.

The thing that this rests on is that you can access the internet for help, from the Arch Forum, & the Ubuntu Arch sub-forum.  If you don't have a duel boot setup, or another machine handy, being able to access the internet via liveCD will certainly suffice.

When you trash it & fix it (as opposed to reinstalling it) you usually learn the most about your system, & make the next trashing less likely, plus, if it does occur, it is usually an easier job for you to fix, due to your growing familiarity.

I think that most of us have learned by trashing & repairing our way out of trouble.

That's how it works for me anyway.  :)

---

### Post by MONODA on 2008-06-24
you could try clonezilla.

---

### Post by mips on 2008-06-24
> **mips said:**
> The 3rd time I installed Arch I said to myself that I should do that. Never did though although it is so simple to do, just record all your commands you used during installation.

Anyway, getting my new pc on Saturday so hopefully this time round I will do that.

Guess what, I never bothered. Going through the setup is so fast and everytime you do it you have to read less as you go on memory.

---

### Post by Fred_E _krugar on 2008-06-24
> **mips said:**
> Guess what, I never bothered. Going through the setup is so fast and everytime you do it you have to read less as you go on memory.


Yes I suppose you are right.

---

### Post by Fred_E _krugar on 2008-06-24
Do you guys reckon yall can show me the directions to install arch onto a fakeraid??

---

### Post by handy on 2008-06-25
> **Fred_E _krugar said:**
> Do you guys reckon yall can show me the directions to install arch onto a fakeraid??

Go to Arch Wiki, if you want to know about Arch stuff.

The benefit of this Ubuntu sub-forum, is that you will most likely get quicker answers on simple stuff.

For raid see [***_here_***]("http://wiki.archlinux.org/index.php/Special:Search?search=raid&go=Go")?

---

### Post by Fred_E _krugar on 2008-06-26
ok here is another problem how do you install AUR packages??


Nevermind I figurd it out

---

### Post by MONODA on 2008-06-26
check out yaourt: http: //archlinux.fr/yaourt-en
also, cehck out kdemod: [http://kdemod.ath.cx/](http://kdemod.ath.cx/)

---

### Post by Fred_E _krugar on 2008-06-26
Yeah I installed the kdemod from the ftp install.

---

### Post by finferflu on 2008-06-29
Arch is very easy to fix even if you have messed it up. There are users who claim installs lasting for years. For example, I had installed just about anything on my old computer, and I thought my system was slowing down, so I reinstalled Arch to do a comparison, and the new system felt exactly the same. Amazing stuff.

---

