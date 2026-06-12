---
title: "boot (X) problem on mac g3"
date: 2008-06-03
forum: Apple Hardware Users
---

### Post by F4l3 on 2008-06-03
I have installed kubuntu hardly on a mac g3. all worked fine. I have read somewhere in this forum that I had to reboot and press Ctrl+Alt+F1 to arrive to a shell. I pressed that three keys a lot of times... but nothing happened...whatI'm doing wrong?

Thank you

---

### Post by cyberdork33 on 2008-06-03
why do you need to get to a console. Can you not just use a terminal in Gnome?

---

### Post by F4l3 on 2008-06-03
I have to change the resolution of xorg.conf... and until I'll not do this, I will not be able to start X.

---

### Post by hpp3 on 2008-06-03
I don't know why that key combo doesn't work (ctrl-alt-F2,3,4 or up to 6 should work as well...) but you should be able to open a terminal and edit your X config with 'sudo nano /etc/X11/xorg.conf' 
Logout and log in and your changes should be made.

If that doesn't work, something more is wrong...

---

### Post by F4l3 on 2008-06-03
My only problem is tha Ctrl+Alt+Fx doesn't work...

---

### Post by F4l3 on 2008-06-03
Ok, I found the problem. 
When I boot, it starts the bootspash and than it crush completle the comupter that will not be able to start load linux. I have tried: Linux nosplash and Linux append="nosplash". But the problem is the same. How can I boot linux without bootspash?

---

### Post by hpp3 on 2008-06-03
Try one of these at the yaboot prompt:

linux 1
linux single

That will put you into single-user mode, which is a terminal screen with a root prompt.

---

### Post by stream303 on 2008-06-03
Which G3 mac do you have?  Is it an iMac or PowerMac and which model?  How much ram is on board?

[http://www.everymac.com/](http://www.everymac.com/)

Have you also tried this at the second stage of the yaboot boot: prompt

```
Linux video=ofonly
or
Linux nosplash video=ofonly
```

---

### Post by F4l3 on 2008-06-03
tomorrow morning I'll try all the previous suggestions.

the pc is this one: [http://www.everymac.com/systems/apple/imac/stats/imac_350_indigo.html](http://www.everymac.com/systems/apple/imac/stats/imac_350_indigo.html)

---

### Post by F4l3 on 2008-06-04
thank you, both work fine :)

---

### Post by stream303 on 2008-06-04
The toughest part with Hardy (or any of the newer Linux distros) is that with the new "bulletproof" xorg.conf, there's not much of an example in it. :)  Our cards just don't feed back the right info during configuration...

By far the biggest challenge is to get your monitor frequencies right, so you'll have to edit in something like this for the G3's:

```
Section "Monitor"
        Identifier  "Configured Monitor"
        HorizSync    58-62
        VertRefresh  75-117
EndSection
```

as per:
[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

You may also have to add a custom Modules section at the end similar to this as well:

```
Section "Module"
   Disable "glx"
   Disable "dri"
EndSection
```

Then to tweak it depending if you have an ATI or a Radeon, check:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

Frustrating, but when that G3 comes alive, it is a marvelous thing...

---

### Post by F4l3 on 2008-06-04
> **stream303 said:**
> The toughest part with Hardy (or any of the newer Linux distros) is that with the new "bulletproof" xorg.conf, there's not much of an example in it. :)  Our cards just don't feed back the right info during configuration...

By far the biggest challenge is to get your monitor frequencies right, so you'll have to edit in something like this for the G3's:

```
Section "Monitor"
        Identifier  "Configured Monitor"
        HorizSync    58-62
        VertRefresh  75-117
EndSection
```

as per:
[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

You may also have to add a custom Modules section at the end similar to this as well:

```
Section "Module"
   Disable "glx"
   Disable "dri"
EndSection
```

Then to tweak it depending if you have an ATI or a Radeon, check:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

Frustrating, but when that G3 comes alive, it is a marvelous thing...
I was able to make this changing and in fact if I type 'sudo startx' it works. The problem, actually, is: how can I start the computer in a way in which X start automatically? I tried 'Linux' and 'Linux nosplash' but both gave me back the same problem of the first post (monitor shuted down and simil stand-by of the machine).
Thank you to all of view that are using your time to help me

---

### Post by F4l3 on 2008-06-04
> **stream303 said:**
> The toughest part with Hardy (or any of the newer Linux distros) is that with the new "bulletproof" xorg.conf, there's not much of an example in it. :)  Our cards just don't feed back the right info during configuration...

By far the biggest challenge is to get your monitor frequencies right, so you'll have to edit in something like this for the G3's:

```
Section "Monitor"
        Identifier  "Configured Monitor"
        HorizSync    58-62
        VertRefresh  75-117
EndSection
```

as per:
[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

You may also have to add a custom Modules section at the end similar to this as well:

```
Section "Module"
   Disable "glx"
   Disable "dri"
EndSection
```

Then to tweak it depending if you have an ATI or a Radeon, check:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

Frustrating, but when that G3 comes alive, it is a marvelous thing...
I was able to make this changing and in fact if I type 'sudo startx' it works. The problem, actually, is: how can I start the computer in a way in which X start automatically? I tried 'Linux' and 'Linux nosplash' but both gave me back the same problem of the first post (monitor shuted down and simil stand-by of the machine).
Thank you to all of view that are using your time to help me

---

### Post by stream303 on 2008-06-05
Wow - sounds like you are missing the GDM login, or it is misconfigured somehow.

You can try loading it again:
```
sudo apt-get install gdm
```

and if that still doesn't work, perhaps try reconfiguring it:
```
sudo dpkg-reconfigure gdm
```

---

### Post by F4l3 on 2008-06-05
nope
it crush way before the start of kdm. It crush as soon as it have ended to load the kernel (I think it try to load X)

---

### Post by F4l3 on 2008-06-05
> **F4l3 said:**
> nope
it crush way before the start of kdm. It crush as soon as it have ended to load the kernel (I think it try to load X)
fixed, now there is the bug you described. I'll have to reconfigure kdm :)

---

### Post by stream303 on 2008-06-05
Now this is interesting - Scientia reports that doing

```
sudo dpkg-reconfigure xserver-xorg
```

actually helped him get over much the same issue.  With Hardy's new x server, this doesn't work like it did in the past allowing you to manually specify your card info, but it seemed to help.

It does write a new xorg.conf, so be sure to backup your existing custom-modified one first.

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
```

Maybe try that xorg reconfiguration, and apply your mods again.

If your /etc/apt/sources.list file looks like it points to ports.ubuntu.com, perhaps update your software

```
sudo apt-get update
then
sudo apt-get upgrade
```

I can't be sure that Kubuntu for PPC doesn't have issues, so perhaps try Ubuntu as a reference installation, then if that works and you want Kubuntu, you can later install it by installing kubuntu-desktop, and switching to it at the next login.

I know I'm throwing out a lot of "perhaps" scenarios. :)

---

### Post by F4l3 on 2008-06-05
I'm trying ;)

In every case the only difference between kubuntu and ubuntu is only the DE, than everything up to Xorg are the same, than I don't see how this can influence my problems :)

---

### Post by stream303 on 2008-06-06
You are quite right.  I guess I'm thinking along the lines of edge-cases, where the Kubuntu build may be differing every so slightly from Ubuntu, or like the case of Xubuntu only releasing a beta for Hardy..  It is a reach, I admit. :)

On a side note, did you have to force the r128 driver in the device section, or does your /var/log/Xorg.0.log show that it is picking up the ATI Rage 128 by itself?

---

