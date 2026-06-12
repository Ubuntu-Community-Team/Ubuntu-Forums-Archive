---
title: "how network connection to windows network?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by dazza000 on 2008-01-28
Hi
Im new.
How do I install ubuntu so that I can have a network connection to other windows based computers?
I have already installed ubuntu but I can't seem to get ubuntu to talk to any other computer. 
help
david

---

### Post by derred on 2008-01-28
> **dazza000 said:**
> Hi
Im new.
How do I install ubuntu so that I can have a network connection to other windows based computers?
I have already installed ubuntu but I can't seem to get ubuntu to talk to any other computer. 
help
david

What exactly are you looking for? File sharing? 
If you'd post a bit more details about your existing setup I'm sure it would be much appreciated.

---

### Post by jesrani on 2008-01-28
you have to install "samba". You can do this using Synaptic Package Manager or apt-get command. If you go to the Tips and Tutorials section, you will see a How To on this. ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605))
You can also search the forums and you should be able to get detailed instructions.

---

### Post by mikeyphi on 2008-01-28
> **dazza000 said:**
> Hi
Im new.
How do I install ubuntu so that I can have a network connection to other windows based computers?
I have already installed ubuntu but I can't seem to get ubuntu to talk to any other computer. 
help
david

System/Administration/Shared Folders....you will get a prompt to install Samba...follow instruction...then click ADD - accept the suggestion of your Home folder (unless you want something else)
Under the General Properties tab- enter the workgroup name as used in windows....check the box 'this computer is a Wins server'

In Network - enable and under properties, setup the connection to the network (address, workgroup name etc.)

---

