---
title: "Burning Issues?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by houseisland on 2006-09-22
Bad pun for thread title.  Sorry.

:rolleyes: 

It is coaster city all around.  I can't burn anything in any application tried, CDs or DVDs.  Burns sometimes run for what would seem to be an adequate length of time but they are unreadable.  Or they sometime "complete" in a second or two. Or they fail completely.

I am running Dapper on a Shuttle XPC: North Bridge Via KM400 VT8378, South Bridge Via VT8237 / 1.3 GHz T-Bird / 512 Mb DDR400 / SATA hard drive / LG GSA-H10N IDE DVD burner.

The burner is new and works flawlessly in Windows.

Searching forums I see that I am not alone.  There are others with similar problems.  I am not yet familiar enough with Ubuntu to troubleshoot this problem with much success.

:confused: 

Suggestions would be most welcome.

Thanks.

---

### Post by fstab on 2006-09-23
What burning programs have you tried?  I recommend GnomeBaker... or K3b if you're using KDE.

---

### Post by houseisland on 2006-09-24
> **fstab said:**
> What burning programs have you tried?  I recommend GnomeBaker... or K3b if you're using KDE.

What plugins need to be installed to get Gnomebaker make audio CDs?  MP3 Ogg etc. to Wav?

Thanks.

---

### Post by nudnik on 2006-09-24
See here: 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and here: 

[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

Addtionally, make sure the "DMA" option is enabled in the interface with the burner. Where this is located escapes me at the moment, I am sure somene will post the relevant information.

I would recommend K3B if you can get things operational. It is very much like Nero and is the most functional of the burning programs.

---

### Post by xmastree on 2006-09-24
Firstly, invest in a couple of RW discs to practice on. Unless you like coasters, that is... Even a failed burn can be re-used.

The DMA thing, [this post](http://www.ubuntuforums.org/showpost.php?p=1527268&postcount=27) has the info you need. Although, not having DMA enabled really only affects speed. They still burn, but slowly, so I don't think that's your problem.

> What plugins need to be installed to get Gnomebaker make audio CDs? MP3 Ogg etc. to Wav?I wouldn't use Gnomebaker, try **[Serpentine]("http://s1x.homelinux.net/projects/serpentine/")** (It's probably already installed). That's the app which opens if you click the 'burn audio CD' which pops up when you insert the blank. If it doesn't, use Alt-F2 and type serpentine in the box to launch it.

Assuming you can play the mp3 files, I guess you have the codecs in. I don't know what you actually need, I have all the codecs in and mine works fine.

But that's not Gnomebaker, I've had nothing but trouble with that app.

---

### Post by xpod on 2006-09-24
K3b for me.Burning an ISO is as easy as "right click" the iso and chose "write to disk"..
And even burning some data was`nt much more difficult......I STILL get my fair share of coasters though:D

EDIT:Not sure about tunes mind you

---

### Post by houseisland on 2006-09-24
Well nothing burning related in the native first install of Dapper was working at all previously (even with all the codec stuff added in).  Didn't matter what I tried.  I had momentarily given up on the problem with the native apps and was trying other ones such GnomeBaker, which didn't work either.

I went back and tried Serpentine today, and now it works.  There have been serveral updates to the system since the last time I tried it.  I have figure out how to get to close the burn session so that the CDs can be played in devices other than computers.

GnomeBaker still doesn't work, though -- comes up and says that required plugins are not installed.

What challenges are involved in getting K3b working in Gnome?

---

### Post by nudnik on 2006-09-24
> GnomeBaker still doesn't work, though -- comes up and says that required plugins are not installed.

What challenges are involved in getting K3b working in Gnome?

GnomeBaker never works...under any circumstances :mrgreen: 

There should be no challenges getting K3b to work under Gnome. Just install it from the repositories using synaptic or type "sudo apt-get install K3b" in the terminal.

Lastly, remember to beware of Scottish penguins. They have annexed London and their undergarments are in question. (No telling what's under that kilt):mrgreen: :mrgreen:

---

### Post by houseisland on 2006-09-25
> **nudnik said:**
> Lastly, remember to beware of Scottish penguins. They have annexed London and their undergarments are in question. (No telling what's under that kilt):mrgreen: :mrgreen:

Ochh. The wee evil things.  Feathers McGraw in a kilt!

---

### Post by 3rdalbum on 2006-09-25
Have you tried running your burning program as root? I had minor troubles until I set up the burning apps to run as root. Yeah, it's hardly an elegant solution, but it works for me.

---

### Post by xmastree on 2006-09-25
> **houseisland said:**
> What challenges are involved in getting K3b working in Gnome?Just install it with Synaptic, it will install a shedload of other stuff but it's easy.

You might need to run it as root though.

---

### Post by beanco on 2007-01-19
> **3rdalbum said:**
> Have you tried running your burning program as root? I had minor troubles until I set up the burning apps to run as root. Yeah, it's hardly an elegant solution, but it works for me.


I have installed k3b  based on this thread,.

But what dos it mean, rather, how to run as root?

robi,
 a newbie that is lost in the wilderness of linux, but oh is it fun

---

