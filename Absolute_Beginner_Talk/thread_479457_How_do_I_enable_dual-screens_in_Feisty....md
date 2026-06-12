---
title: "How do I enable dual-screens in Feisty..."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Peet42 on 2007-06-20
**...using the GUI only?** (Actually "Ubuntu Studio")

I have searched the forums, and found screeds of files to copy and edit using a shell and SUDO.  But...

The machine I'm connected to the web with *isn't* the machine I'm trying to set up, and remembering huge screeds of text while I disconnect the monitors from this machine and connect them to the other one is a no-no.

All I want to know is how to reach the equivalent of the "Graphics card and monitor" dialog on my SUSE system where I can check a box to activate the second monitor.  If this can't be done in Ubuntu, then tell me that now so I can give up, please.

Ta.

---

### Post by earobinson on 2007-06-20
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174) or if you have an nvidia card you can use ```
sudo nvidia-settings
```

---

### Post by Peet42 on 2007-06-20
Okay...  That link takes me to a series of other links, each being a list of files to edit.  That doesn't really answer the question I asked.

Is there a GUI in Ubuntu where I can check a single box to enable Xinerama or similar?  If there isn't, please say so.  Links to text files I have to edit by hand really don't help, sorry.

---

### Post by earobinson on 2007-06-20
do you have an nvidia card? if so look at my quote

---

### Post by Peet42 on 2007-06-20
I *do* have an nVidia card, just not in that machine.  I can't even swap it into that machine as it's a PCI-E, and that machine only takes PCI or AGP.  Currently it's fitted with a dual-head ATI 9600 AGP.

---

### Post by spivee69 on 2007-06-20
As far as I know, there is no graphical interface to setting up your graphics card for twinview or xinerama.  (somebody please correct me if I'm wrong).

If you don't want to have to "remember huge screeds of text" etc, you might be able to open a VNC or ssh session to the other machine (assuming you have network connectivity between them).

Also, if you can get to a terminal window, the 'sudo nvidia-settings' command recommended by earobinson will probably configure your twinview automatically, and I wouldn't think that should be too difficult to remember.  It worked when I used it, but as with anything, it's not 100%.

I believe there is a project underway to create a GUI interface ([here]("https://wiki.ubuntu.com/DisplayConfigGTK")) but it is not yet included in the distributions.

---

### Post by Peet42 on 2007-06-20
Thanks, spivee69, that was what I was beginning to suspect. ](*,)

I don't have network connectivity at the moment - if I did I would have shared this modem (I've lost my broadband for a month - don't ask... :-() and been able to copy'n'paste from the forums.

At the moment, though, it looks as if to use both my screens I'll have to wipe Ubuntu and install another copy of SUSE.  I find it irritating how "friendly" Ubuntu is touted as being, right up until you actually try to *do* something, then it's all "Just open a shell and 'SUDO....' - if Micro$oft tried something like that they'd be ridiculed to hell and back.

Never mind.  I'll no doubt try again when your next major version is released...  I'm a sucker like that.;)

---

