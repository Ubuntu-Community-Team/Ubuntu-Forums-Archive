---
title: "Trying Ubuntu without partitioning or using Live CD"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by detheridge on 2007-05-31
Just a quick one for people who are new to Ubuntu and either don't want the hassle of repartitioning or using the Live CD.

Try VirtualBox ([www.virtualbox.com](www.virtualbox.com)). Install this software to your Windoze machine, create a Virtual Machine (one button click and a wizard) and install Ubuntu to your virtual machine. I will be placing a tutorial on these forums soon. 

It will allow you to use Ubuntu whilst running Windoze or vice versa Windoze within Ubuntu.

A cracking piece of software and whats more its free !!

Dave

---

### Post by starcraft.man on 2007-05-31
Ummm, just a thought but it's a lot easier IMO to put a CD in the tray and reboot to live CD then install and configure a fully functional VM then install a guest OS into it (which would be the same as actually installing it, just in a virtual container no?). Not to mention a good majority of people download and use the live CD anyway >.>

Oh and, the average (I'm assuming thats who your targeting) user in my experience (not absolute, but I know a lot of windows users) doesn't know about a VM/how it works.

---

### Post by Premium_User on 2007-05-31
What kind of junkola website is that? There is no Q&A section. No download link to this software you speak of.

A waste of space and time. Don't click the link.

---

### Post by Lucifiel on 2007-05-31
LOL... I believe the threadstarter got the link wrong.

It should be [http://www.virtualbox.org/](http://www.virtualbox.org/)

Anyways, Vbox can be a pain to setup.

---

### Post by ep2011 on 2007-05-31
It is so much simplar to use the LiveCD. If they don't have a cd they can burn, they can always use Wubi.

---

### Post by Premium_User on 2007-05-31
Thanks for the proper link Lucifiel. I am currently in the process of trying to get 7.04 to detect my mouse in Virtual PC. 

Everything worked great with 6.10.

have nanoed the xorg config file to no avail.

Haven't a clue to what could have changed in the latest release that would cause the mouse to fail.

---

### Post by starcraft.man on 2007-05-31
> **Premium_User said:**
> Thanks for the proper link Lucifiel. I am currently in the process of trying to get 7.04 to detect my mouse in Virtual PC. 

Everything worked great with 6.10.

have nanoed the xorg config file to no avail.

Haven't a clue to what could have changed in the latest release that would cause the mouse to fail.

Maybe MS decided to not be nice with Linux? :p

Uhhhh, just my opinion/experience but don't use Virtual PC... never liked that VM, I always found it slow and well not very good when I used it. Give Virtual Box (just recently started and I am happy :D) a spin, requires some manual tweaking of options (only initially) but is much superior. Or VMware, been using them for ages and can't say I ever had a prob. :)

---

### Post by Premium_User on 2007-05-31
> **starcraft.man said:**
> Maybe MS decided to not be nice with Linux? :p

Uhhhh, just my opinion/experience but don't use Virtual PC... never liked that VM, I always found it slow and well not very good when I used it. Give Virtual Box (just recently started and I am happy :D) a spin, requires some manual tweaking of options (only initially) but is much superior. Or VMware, been using them for ages and can't say I ever had a prob. :)

I never had a problem with Virtual PC until I updated Ubuntu :( to 7.04.

Actually I am running a quad boot system on this machine.

3 Linux Flavors, 1 XP.  

I just need the ability to quickly access Linux when
I have to use winbloze.

I've used VMware. My opinion is not as optimistic about it.

I may give VirtualBox a try later.

Just a quck question for you since you seem familiar with VirtualBox;
Can you use the virtual hard drives that are made with 
Virtual PC or are they incompatible? That would be a big
determining factor for me whether to replace what I have now.

#I may just have to revert to 6.10 from the terminal with what I have
#now if I want to continue to use the desktop support of Gnome.

---

### Post by starcraft.man on 2007-05-31
Not sure if Virtual Box can read the MS format for Virtual PC, I've never tried it (only been using Virtual Box recently). Give it a shot though, worst that happens is it doesn't read at all.

What was your problem with VMware though? I got to say on my old p4 with just a gig of regular ram I've always gotten top performance (practically native) out of it (both when I used it as server and later workstation). Which version was it and what happened? Just curious >.>.

Anyway, IMO, Virtual Box is much superior to the experiences I've had with Virtual PC, and don't ya wanna get away from MS products anyway? Just a thought...

---

### Post by Premium_User on 2007-05-31
VMware ran so slow and had little bugs...  when I used it. Just looked at their site. Looks like they have came far since I last used it a few years ago. 

"don't ya wanna get away from MS products anyway? Just a thought..."
That supposed to be a joke? I've only recently started using "MS products"!
My current employer utilizes proprietary software that unfortunately doesn't 
cooperate well with nix.

Anyhow, I have found that the latest kernel 2.6.20-16-generic is causing my problem.
I revert to the kernel 2.6.17-10-generic which will detect the mouse.

It appears 7.04 will run on the virtual machine fine this way. Time to change the
menu.lst. I don't want to compile a kernel in the virtual sandbox. =LoL=

---

### Post by bromix on 2007-05-31
In my opinion, if you still want to use windoze, yet be able to access Linux quickly, the best route would be to use two separate computers.  Two options for doing this would be to use two boxes, and use a KVM switch to share montior, keyboard, speakers and mouse.  I've seen that work wonderfully for what you say you want to do.  There is also an open source project called Synergy ([http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/))  It allows you almost the same functionality, except it uses two monitors.  Set it up....move your mouse off the edge of one OS's screen, and bam...you have functionality on the second OS's display.    I just feel that one of these options would allow you to have full utilization of system resources for each independent OS when you choose to use it.

---

### Post by Premium_User on 2007-05-31
Very good points. But would be costly and use more energy than one needs.
Just my thought at a glance. Thanks for the suggestion, I got things working the
way I need with the new interface now :P

---

### Post by aysiu on 2007-06-01
What about Wubi?

---

### Post by ep2011 on 2007-06-01
> **aysiu said:**
> What about Wubi?

Yes, I suggested this before. Except the problem with Wubi is then they will need to restart their computer to boot into Linux. This is the problem as they already have a quad-boot system, they just need a virtual PC ubuntu set up.

---

