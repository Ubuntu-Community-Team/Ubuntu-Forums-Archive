---
title: "How do you install software that I downloaded directly i.e. not from  &quot;add/Remove&quot;"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-01-19
I recently downloaded an evaluation copy of VMware workstation but now I don't know how to install it. I have gotten too used to just using add/remove or synaptic or whatever. Anyway, I extracted the files to my desktop and when I look at them there is a neat little folder called "vmware-install.pl". When I double-click on it I am asked if I want to run it in terminal or just run it. No matter what I click nothing seems to happen. When I click on "run in terminal" it appears that for a brief moment a terminal window starts to open but then it goes away and nothing more happens.

---

### Post by bwhite82 on 2008-01-19
From a terminal:
> sh vmware-install.pl or
> ./ vmware-install.pl
You may have to put sudo in front of those depending on where VMWARE wants to install things.

-Cheers

---

### Post by boriquajake on 2008-01-19
Also, I did search for and find a how-to for installing stuff in Ubuntu but the instructions did not seem to work. I am sure I did something wrong. Here is what I tried to follow:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Anyway, I would appreciate any help at all.

---

### Post by nick_h on 2008-01-19
This article on [How to install ANYTHING in Ubuntu!](http://monkeyblog.org/ubuntu/installing/) may be useful.

---

### Post by boriquajake on 2008-01-19
> **nick_h said:**
> This article on [How to install ANYTHING in Ubuntu!](http://monkeyblog.org/ubuntu/installing/) may be useful.

Dude, I just found that article and it does look useful. Thanks.

---

### Post by aysiu on 2008-01-19
Any reason in particular you're using VMWare Workstation? Just curious. *vmware-player* and *virtualbox* are in the repositories and can be installed with Synaptic Package Manager or Adept.

---

### Post by boriquajake on 2008-01-19
> **aysiu said:**
> Any reason in particular you're using VMWare Workstation? Just curious. *vmware-player* and *virtualbox* are in the repositories and can be installed with Synaptic Package Manager or Adept.

It is sort of complicated but the short of it is I have two things that I need to do that are pretty mission critical. I want to be able to use a GPS map software like Delorme Street Atlas or Microsoft Streets and Trips,  and second, I need to be able to use my EVDO card. All the info I have been able to find seems to indicate that neither of the map programs I need will work under WINE, and after many, many hours of struggle I have given up on getting my EVDO card to work under Linux and I thought that maybe it would work on a virtual machine.

I would love to use  virtualbox but I couldn't get it to work at all. (It would not let me install an OS on the virtual machine, something about a kernel not being available) and VMware Player would not install from add/remove  (something about i386, I didn't understand) and when I finally got VMware Server installed and working with a fresh (and legitimate) copy of Windows installed it wouldn't recognize either my CD drive, so I couldn't install the map software, or the PCMCIA slot for my EVDO card. In desperation I downloaded Workstation to see if it was more successful than Server.

In short, HELP ME PLEASE!! I AM DYING HERE!:)

---

### Post by boriquajake on 2008-01-19
> **Soldierboy said:**
> From a terminal:
 or

You may have to put sudo in front of those depending on where VMWARE wants to install things.

-Cheers


Well, the results of pasting "sh vmware-install.pl" into terminal are:

```
sh: Can't open vmware-install.pl
```

and the results of pasting "./ vmware-install.pl" were:


```
bash: ./: is a directory

```

I don't understand either, but I do appreciate you trying to help.

---

### Post by bwhite82 on 2008-01-19
You need to be in the same directory as the installer or point to it:

> sudo sh /downloadedDIR/vmware-install.pl

---

### Post by boriquajake on 2008-01-19
> **Soldierboy said:**
> You need to be in the same directory as the installer or point to it:

You were right, I needed to point to the correct directory, but even when I did I got:

> sh: Can't open /home/jake/vmware-install.pl


I get the feeling I don't quite have what it takes to use Linux. :(

---

### Post by Sinkingships7 on 2008-01-19
may i suggest you use virtualbox? i just got it set up with windows xp and it works flawlessly. it's easy to use, yet has all the features you need, including an equivalent to vmware tools, so you shouldn't have any integration problems.

---

### Post by nikoPSK on 2008-01-19
there is generally a readme, and as asiyu mentioned there are debs in the repos. :)

---

### Post by boriquajake on 2008-01-19
> **Sinkingships7 said:**
> may i suggest you use virtualbox? i just got it set up with windows xp and it works flawlessly. it's easy to use, yet has all the features you need, including an equivalent to vmware tools, so you shouldn't have any integration problems.

I would love to use virtaulbox but as I mentioned above I can't seem to get it to allow me to install an OS on the virtual machine it creates.  Maybe I am doing something obviously stupid. Check out the screenshot.

---

### Post by oldos2er on 2008-01-19
Usually there's an INSTALL or README file that tells you what to do.

 If I'm not mistaken, a *.pl file is written in Perl. I'd try running "sudo perl vmware-install.pl" in a terminal.

---

