---
title: "XP killed my Ubuntu? (2 separate drives)"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Heavy Light 117 on 2008-02-16
First post (new to ubuntu)

I bought a new Hard drive to install ubuntu and everything was fine and dandy. Yesterday however I was in ubuntu and I tried to access my xp hard drive. It told me that it couldn't access it so I restarted my computer. (for a couple days I was able to boot up to either one)

It didn't restart :(

XP drive made skipping noises so I doubled checked by hooking them up separately to another computer. The ubuntu drive worked and could be seen by my sister's computer but the xp drive was dead. 

So here's my question... If the OS's were in separate drives why would it not allow me to boot up from just the Ubuntu drive if the xp had failed? 

Thanks in advance everybody

p.s. They were Sata drives and were not in any type of raid

---

### Post by stryder73 on 2008-02-16
In response to the XP drive, MS updates seem to botch things up really good sometimes.  I had it happen awhile back where I went through hell correting things due to one little security update.  The quickest way I've found so far if the HD "should" be fine, is to first load up with the XP install disc then choose "R" for repair, select drive, (normally "1 for C:\windows"), and then run a "chkdsk /p" at the c prompt.

For the issue about the computer not loading into Ubuntu, I haven't a clue past some setting being off in your bios prefs of startup drives since the drive ran fine on the other system.

---

### Post by mikeyphi on 2008-02-16
> **Heavy Light 117 said:**
> First post (new to ubuntu)

I bought a new Hard drive to install ubuntu and everything was fine and dandy. Yesterday however I was in ubuntu and I tried to access my xp hard drive. It told me that it couldn't access it so I restarted my computer. (for a couple days I was able to boot up to either one)

It didn't restart :

Did you have to select the drive via BIOS or via a GRUB page?
If via GRUB then it's probable that GRUB was installed on the windows drive - that would explain why neither OS was available!!

---

### Post by Heavy Light 117 on 2008-02-16
> **mikeyphi said:**
> Did you have to select the drive via BIOS or via a GRUB page?
If via GRUB then it's probable that GRUB was installed on the windows drive - that would explain why neither OS was available!!

I did it via the Grub but I made sure to select the new drive as a full install.

---

### Post by Heavy Light 117 on 2008-02-16
> **stryder73 said:**
> In response to the XP drive, MS updates seem to botch things up really good sometimes.  I had it happen awhile back where I went through hell correting things due to one little security update.  The quickest way I've found so far if the HD "should" be fine, is to first load up with the XP install disc then choose "R" for repair, select drive, (normally "1 for C:\windows"), and then run a "chkdsk /p" at the c prompt.

For the issue about the computer not loading into Ubuntu, I haven't a clue past some setting being off in your bios prefs of startup drives since the drive ran fine on the other system.

What I don't understand is why it would mess up while I was in Ubuntu. As for the drive I'm pretty sure its done for. My POST won't even show the drive in my sata list.

---

### Post by fbmx24 on 2008-02-16
I would do what Stryder73 said ," The quickest way I've found so far if the HD "should" be fine, is to first load up with the XP install disc then choose "R" for repair, select drive, (normally "1 for C:\windows"), and then run a "chkdsk /p" at the c prompt"  

  Try this first to see if the drive possibly failed or if it is just a software problem.

---

### Post by Heavy Light 117 on 2008-02-16
> **fbmx24 said:**
> I would do what Stryder73 said ," The quickest way I've found so far if the HD "should" be fine, is to first load up with the XP install disc then choose "R" for repair, select drive, (normally "1 for C:\windows"), and then run a "chkdsk /p" at the c prompt"  

  Try this first to see if the drive possibly failed or if it is just a software problem.

I think I might do this, however I'm thinking twice when it comes to installing xp again. If it works I might just use it to store my media files in ubuntu. 

thanks for the help guys.

---

### Post by fbmx24 on 2008-02-16
You dont have to reinstall XP, just see if when you enter recovery console to fix the Xp installation if you HDD shows up. If it does you know your HDD is ok and it is a software problem.

---

### Post by Heavy Light 117 on 2008-02-16
> **fbmx24 said:**
> You dont have to reinstall XP, just see if when you enter recovery console to fix the Xp installation if you HDD shows up. If it does you know your HDD is ok and it is a software problem.

If it doesn't show up in my bios when i connect it, is it more likely to show up in the xp setup menu?

---

### Post by Heavy Light 117 on 2008-02-16
I ran the xp setup and it loaded everything until the last second it bsod on me. So I'm pretty sure now the hard drive is dead. The sound it makes is very odd and it sounds like its skipping. Its a steady pattern from when I first push the power button to when I turn it off. 

I guess I'm going to return it.

---

### Post by fbmx24 on 2008-02-16
Its worth a shot to try the xp recovery just to see if it does show up. If not we can go from there. Its just easier to see if it failed or not before changing things on the system.

---

### Post by Heavy Light 117 on 2008-02-16
> **fbmx24 said:**
> Its worth a shot to try the xp recovery just to see if it does show up. If not we can go from there. Its just easier to see if it failed or not before changing things on the system.

Yeah the hard drive in question is messed up. XP recovery shuts down and on my bios menu the drive is not listed but the sata port 4 (the one its connect to) is diffrent.

 Usually when it doesn't have anything connected it gives you an option to enable or disable. On the other hand if something is connected it shows you the model number and the spec. In my case it doesn't show either, it just shows a blank space. 

Oh well we tried. 

Thanks again everybody

---

