---
title: "question about install and live cd"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by gmhikin03 on 2006-05-16
well first off im a complete noob when it comes to anything dealing with linux.  so ill give you my background.  ive been using windows since i dont know when.  i knew of linux but did not know how to go about installing it, and was a bit scared off by the fact that it is more command line heavy that xp.  so a few months ago a friend lent me a copy of knoppix to try out.  so i ran the live cd and liked what i saw, but also figured there were some things i couldn't do with knoppix.  so i started looking around for a distro to install.  i stumbled apon ubuntu, and requested some of the cd's.  when they came i tried using the live cd, but all it gave me was an "Failed to start the X server" error, and took me to the terminal.  so after that i just put the cd away and figured it wasn't going to work.

last week or so a friend of mine wanted to know if i would be interested in building a file/ftp/(possibly web server).  i told him i would help as long as we install a linux distro.  since i already had 5 copies of ubuntu the choice was obvious.  so i dug out my cd's and tried the live cd again.  gave me the same "failed to start the X server" error.  i found these forums and started looking for a fix.  i tried a few of the things i found but no luck.  i do believe it is my nvidia graphics card though.  just not sure how to make it work.  

since my computer wasn't working i stuck the cd in my parents very old compaq and after 10-15 minutes i get the gnome desktop.  something i was very pleased to see.  the gui seems very user friendly, but i definitely plan on learning more commands for the terminal.

now that ive seen what ubuntu is like im planning on installing it on our machine.  but i had a few questions first.
1.  how much disk space does ubuntu need?
2.  will we need to install any packages right off the bat?
3.  should we have it hooked up to the broadband when we first start the install?
4.  what does apt stand for? ( i think i know how to use it, just wasn't sure what it stood for )

i think thats all.  i just want to thank anybody who can help me out.  this forum should be a good place for me to figure my way around ubuntu.

g

---

### Post by mostwanted on 2006-05-16
[QUOTE=gmhikin03]well first off im a complete noob when it comes to anything dealing with linux.  so ill give you my background.  ive been using windows since i dont know when.  i knew of linux but did not know how to go about installing it, and was a bit scared off by the fact that it is more command line heavy that xp.  so a few months ago a friend lent me a copy of knoppix to try out.  so i ran the live cd and liked what i saw, but also figured there were some things i couldn't do with knoppix.  so i started looking around for a distro to install.  i stumbled apon ubuntu, and requested some of the cd's.  when they came i tried using the live cd, but all it gave me was an "Failed to start the X server" error, and took me to the terminal.  so after that i just put the cd away and figured it wasn't going to work.

last week or so a friend of mine wanted to know if i would be interested in building a file/ftp/(possibly web server).  i told him i would help as long as we install a linux distro.  since i already had 5 copies of ubuntu the choice was obvious.  so i dug out my cd's and tried the live cd again.  gave me the same "failed to start the X server" error.  i found these forums and started looking for a fix.  i tried a few of the things i found but no luck.  i do believe it is my nvidia graphics card though.  just not sure how to make it work.  

since my computer wasn't working i stuck the cd in my parents very old compaq and after 10-15 minutes i get the gnome desktop.  something i was very pleased to see.  the gui seems very user friendly, but i definitely plan on learning more commands for the terminal.

now that ive seen what ubuntu is like im planning on installing it on our machine.  but i had a few questions first.
1.  how much disk space does ubuntu need?
2.  will we need to install any packages right off the bat?
3.  should we have it hooked up to the broadband when we first start the install?
4.  what does apt stand for? ( i think i know how to use it, just wasn't sure what it stood for )

i think thats all.  i just want to thank anybody who can help me out.  this forum should be a good place for me to figure my way around ubuntu.

g[/QUOTE]


1) 1.8 GB according to this page: [http://wiki.linuxhelp.net/index.php/Ubuntu](http://wiki.linuxhelp.net/index.php/Ubuntu). But that's the default graphical install, you can also install it with a command-line interface only if you need it to be smaller.

2) Well since you want to make it into a server, you'll need to install some server programs. You can install the programs you need very easily (look at my sig), though I'm not sure what to install for ftp servers. Apache would be the obvious choice for a web server .

3) That is a good idea. The installer will automatically check for updates when it's done installing.

4) Advanced Package Manager (it's used in the programs Synaptic, apt-get, aptitude, etc.)

---

### Post by Sef on 2006-05-16
> 1. how much disk space does ubuntu need?

Mine is installed on a 20 GB HD.  But you can do with less.  Below 20 GB, it would be hard to have a home partition.

> 2. will we need to install any packages right off the bat?

It will work once installed, but you may want to install the restricted formats.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

> 3. should we have it hooked up to the broadband when we first start the install?

Yes, it will go much better if installed to broadband when installing.

> 4. what does apt stand for? ( i think i know how to use it, just wasn't sure what it stood for )

Not sure.  

Edit: Found what it stand for.  It stands for 'advanced packaging tool'.

[http://forum.freespire.org/showthread.php?p=1882]("http://forum.freespire.org/showthread.php?p=1882")

---

### Post by gmhikin03 on 2006-05-16
thanks guys.  i appreciate it.  you wouldn't happen to know how to get the live cd to work.

here's my system specs.
dell 2400
p4 2.66Ghz
win xp
gig of ram
chaintech geforce 5200 pci (dual monitors connected)

if you need anything else let me know.

---

### Post by Engnome on 2006-05-16
Your computer should boot the live cd automatically if configured properly. Just start with it in the cd-rom drive. If it doesnt work you have to configure bios to boot cd first. That is different from one computer to another so I cant help you with that.

---

### Post by mostwanted on 2006-05-16
[QUOTE=Engnome]Your computer should boot the live cd automatically if configured properly. Just start with it in the cd-rom drive. If it doesnt work you have to configure bios to boot cd first. That is different from one computer to another so I cant help you with that.[/QUOTE]

His problem is not that it doesn't boot, but that it doesn't set up his graphics card correctly (e.g. the "failed to start X server" message).

---

### Post by gmhikin03 on 2006-05-16
ive done that.  it will go through all the setup then it will show the ubuntu logo with a progress bar.  at the bottom of the screen it shows what its doing.  ex: loading blah.........ok (not sure of the exacts)
loading blah.........ok
after those scroll by, i get a blue screen with the error message "Failed to start the X server"  with what i think is the terminal, it shows ubuntu@ubuntu

---

### Post by 3rdalbum on 2006-05-16
At the boot menu, type *expert* and hit Enter.

Now the Live CD "installer" will ask you all kinds of weird and wonderful questions. The defaults are all okay, except when it asks you if you want to autoconfigure your video card.

Say "No" and then select "vesa" from the menu. You can probably autodetect your monitor; if it still doesn't work try not autodetecting it, and instead doing "Simple" configuration. (which is very simple).

The X server will probably start.

If you decide to install Ubuntu, the installer might get your configuration right... or it might not. The "expert" mode of the installer doesn't let you set your video card, so you'd have to do:

```

sudo nano /etc/X11/xorg.conf

```

Change the "driver" value to "vesa", save changes, and restart X.

---

### Post by gmhikin03 on 2006-05-16
3rdalbum  i must thank you.  im writing this reply from ubuntu.  i think im going to dual boot sometime soon.  that should be fun.

---

