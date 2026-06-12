---
title: "Computer messed up severely"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Taters on 2007-10-07
I tried to install openSUSE, and all went smoothly until it tried to start up. The screen became a massive mess of random colors. My guess is that the cd was screwed up.

This wouldn't really matter, but it won't allow me to access Ubuntu. 

I'm running the (Ubuntu) live-cd now, and I can see my files, they are still untouched but I don't have access to them. I want my computer back. In SUSE I can run in safe mode, and I get a command line, but thats it. Should I delete SUSE from here? Can I?

Please help.

---

### Post by HermanAB on 2007-10-07
That is a display driver problem.

For a new user, it is best to try another distribution.  An experienced user may be able to sort it out, but it may take an inordinate amount of time since it is hard to fix something when you can't see a durn thing.  

Note that each distro has their own installation scripts and while they all have hundreds of machines in their labs to test with, nobody has everything ever produced on the planet.  So shop around a bit and try Mandriva, Fedora, Mepis, Ubuntu and so on.  Chances are that one of them will work perfectly with zero problems right out of the box.

Mandriva 2008 will be available in a few days - Ooooooh, shiny, new... drool... ;)

Cheers,

H.

---

### Post by Taters on 2007-10-07
You don't understand, I can access ubuntu!

I want my files!

I can't delete the stupid SUSE files off right now.... I knot there is a bit of coding that allows users to delete any file...

Does anyone know what it is?

I'm starting to get frantic....

edit: No one is responding.... This is what I'm going to do then: install ubuntu again over open suse. 

please help

---

### Post by jingo811 on 2007-10-07
wait I might have an Ace up my sleeve........*digging through my old threads*

---

### Post by Taters on 2007-10-07
I'm really starting to hate SUSE. I tried to install Ubuntu over it and it denied me.


I hope you find something.


I'm going crazy.

EDIT: I think its gone! please be gone!

---

### Post by jingo811 on 2007-10-07
I'm not sure what your question is you're kind of asking many questions all at once.
But if you can access a Command Line Interface terminal in your random colored operating system then this might fix your screen maybe...
If you can't acces a CLI try these 2 key combinations in your random colored mode.
Ctrl+Alt+Backspace
or
Ctrl+Alt+F2

Then you should have CLI to look at your filesystem and stuff.

========================================================
========================================================

[COLOR="Sienna"][SIZE="4"]1.[/SIZE][/COLOR]
$ **nano /etc/X11/xorg.conf**

[COLOR="Sienna"][SIZE="4"]2.[/SIZE][/COLOR]
In Nano editor
**Ctrl+w** ,  
[COLOR="Sienna"]
[SIZE="4"]3.[/SIZE][/COLOR]
type in this when it asks for Search:
**section "device"**
press ENTER.

[COLOR="Sienna"][SIZE="4"]4.[/SIZE][/COLOR]
Then you should see something like this replace value for Driver into "vesa" instead of "ati".
**"vesa"**

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection
```

[COLOR="Sienna"][SIZE="4"]5.[/SIZE][/COLOR]
**Ctrl+x**, and save your change.

[COLOR="Sienna"][SIZE="4"]6.[/SIZE][/COLOR]
Then reboot
**sudo shutdown -r now**

See what happens.

---

### Post by Taters on 2007-10-07
Thank you.

But in Ubuntu or SUSE?

I was denied.... I'll try it again in open suse

---

### Post by jingo811 on 2007-10-07
I've only done that procedure on Ubuntu and Debian.  But SuSe should have its /etc/xorg.conf file in the same filesystem path.
So the answer to your question Ubuntu or SuSe is.  Do it on the operating system that have the colors all messed up.

Maybe we should begin from scratch again. ( The numbers not related to my previous guide! )

**1.**
Is your personal files in /home directory?
Is /home on its own partition or is it in the same partition as your Ubuntu ( / = root )?

**2.**
Can you describe how your harddisk(s) looks like, that is how things are partitioned?
Do this command and show ppl how your harddrive is setup.
```
$sudo fdisk -l
```

**3.**
What problem are you mainly trying to solve here?  Your screen, your Ubuntu, your SuSe, your personal data?
Try to sort your problems in order and not do everything at once.  Then ppl can better give you solutions because I have to leave soon.

---

### Post by floke on 2007-10-07
What do you mean, you were denied?
What can deny you from installing an OS into a partition?

---

