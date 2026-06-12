---
title: "a xubuntu install on a 5-year old box that uses part of its RAM for video memory"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by aji_889 on 2008-04-05
Hello. 

I am planning to install the lightest ubuntu variant (xubuntu) on a unit that still uses a P4VMM2 motherboard from ECS. It's got a 40GB HDD, an Intel Celeron(R) 1.7GHz processor, and 256MB of DDRAM I (I don't know about the speed, sorry). 

At a glance, the unit seems to just barely meet minimum requirements. But actually, some RAM is being allocated for video memory, which causes my machine to run sluggish. I think Windows XP recognizes just 233 MB of RAM and third-party Task Manager replacements report that I'm often taking 80%-100% of it when starting/running everyday applications.

I would like to know if this hardware state is going to affect a xubuntu installation adversely or if a xubuntu install is even POSSIBLE at this state. Recent attempts with the GNOME Live CD of OpenSUSE 10.3 went badly in this case, since the absence of a video card causes the GUI to stop loading when the Live CD boots. 

Any takes on steps I can take to make the installation possible? 

Please go easy on a total Linux noob. Though any help would be appreciated.

---

### Post by Paqman on 2008-04-05
I think the minimum requirement for a Xubuntu LiveCD install is 128MB isn't it? You could always try the alternate install CD if that doesn't work.

I run Xubuntu on a 1.5GHz Celeron laptop, and it's extremely snappy. Even get some nice desktop bling like dropshadows and AWN from the built-in compositor. I have got 512MB RAM, though.

---

### Post by stefangr1 on 2008-04-05
I agree with the above. Xubuntu should run fine, even Ubuntu should work "normally". The only thing is you could spend a few euro's to pick up some extra second hand ram, since that will improve performance notably.

---

### Post by DarKnyht on 2008-04-05
I can attest that I have run both Ubuntu and Xubuntu on a similar machine (Compaq Presario 722 Laptop, 1.4 Celeron, 256 MB RAM originally, S3 graphics).  Ubuntu was a little sluggish and Xubuntu ran fine.  

I have since opted to put the max memory into it (384 MB), and am currently running Ubuntu using Xfm4 for the window manager (it allows compositing with my integrated S3 graphics card).  The only problems I have run into have been with my wireless card when I update versions, and of course the headaches I create when I tweak the system.

Some things you will want to do though is reduce the amount of memory Firefox and Open Office use for cache.  There are other posts that explain how to do this.

---

