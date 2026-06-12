---
title: "A few question about switching to Kubuntu"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by kpel on 2007-05-21
I've been using Ubuntu 7.04 since slightly before it's release.   I've become comfortable with Linux since then and started running KDE alongside GNOME to get a feel for both environments.  I'd like to switch over to Kubuntu because, in **my opinion**, it offers a higher degree of customization.  Of course, I'm also the kind of person that can spend hours happily playing with options, but I digress.

Unfortunately I have the KDE and GNOME apps all stuffed in the same menus, so it's made telling some things apart a bit difficult.  Here are the questions, and my apologies if some of them have been answered before; I know some have and I can't seem to find the threads now.

1.  Synaptic Package Manager.  Is it available with Kubuntu as well, and if not, can I install it seperately later?  If that's the case, will it work?

2.  Beryl+Emerald in Kubuntu.  I know it works (it is right now) but it seems to have some issues loading for the first time.  Do other people have this issue or is it caused by the fact that it was originally installed and set up under GNOME?

3.  Restriced drivers manager.  I *think* I read that it was not included with Kubuntu.  Assuming it is not will I have any problem updating to the nvidia-glx-new drivers?

4.  How the heck do I mount extra drives in Kubuntu?  It's easy under GNOME, but I haven't been able to figure out how to do it (without using the terminal) under KDE.

---

### Post by Rotaj on 2007-05-21
There should be the option of adding the KDE desktop to Ubuntu thru synaptic or aptitude(add/remove). I can't remember which. The desktop manager is the primary difference between the various flavors of Ubuntu.

---

### Post by Terl on 2007-05-21
> **Rotaj said:**
> There should be the option of adding the KDE desktop to Ubuntu thru synaptic or aptitude(add/remove). I can't remember which. The desktop manager is the primary difference between the various flavors of Ubuntu.

Rotaj is right.  All the kubuntu "stuff" is available through synaptic.  You can download what you need and change your windows manager from gdm to kdm and set yourself up the "easy" way.  Granted, you will have extra stuff on your pc, but if you have not tried kde much it may be good to keep gnome available.

---

### Post by Honayo on 2007-05-21
> Rotaj is right. All the kubuntu "stuff" is available through synaptic. You can download what you need and change your windows manager from gdm to kdm and set yourself up the "easy" way. Granted, you will have extra stuff on your pc, but if you have not tried kde much it may be good to keep gnome available.

I've had Dapper Ubuntu on this machine as a dual boot with XP for a long time now. I used synaptic to install the KDE desktop shortly after the initial install and like the look and feel better than Gnome. Just my 2 cents though.

---

### Post by kpel on 2007-05-22
Thanks for the replies guys, but you kinda missed the point (maybe I wasn't clear enough).  I have been using KDE for awhile now (installed via Synaptic on top of Ubuntu).  I've messed with my system so much in that time that I want to just wipe it all out and install Kubuntu fresh.  That's where the questions come in, as I don't want to have GNOME and all the associated applications installed.  Can I jump between GNOME and KDE to get the things accomplished that I want to?  Sure.  But it's a hassle and not something I want to do, which is why my questions are specific to a clean Kubuntu install.

---

### Post by kohl62 on 2007-05-22
Kubuntu comes with Adept package manager, similar to Synaptic.  Can always also use apt-get in terminal.
Restricted driver repositories are also available.  As for "extra" drive mounting, on KDE desktop there is an icon in the task bar that looks like a computer (system menu), click on it, then click on storage media and it will show all of your connected drives (cdrom, floppy, hd's, etc.)  Hope that helps.

I've been using KDE for a few years and personally prefer it to Gnome, but I did install the gnome desktop the other day just to take a look at it again.  KDE will remain my personal favorite, but nothing wrong with gnome.

---

### Post by Terl on 2007-05-22
> **kpel said:**
> Thanks for the replies guys, but you kinda missed the point (maybe I wasn't clear enough).  I have been using KDE for awhile now (installed via Synaptic on top of Ubuntu).  I've messed with my system so much in that time that I want to just wipe it all out and install Kubuntu fresh.  That's where the questions come in, as I don't want to have GNOME and all the associated applications installed.  Can I jump between GNOME and KDE to get the things accomplished that I want to?  Sure.  But it's a hassle and not something I want to do, which is why my questions are specific to a clean Kubuntu install.

Ohhhhhhhh :p  Silly me,....

Yes, just install Kubuntu straight off.  I did that the other day to see what it was like and aside from having the fun of getting used to different menus and a few different programs it was not too bad.  I had no trouble getting my nvidia card up and running.  I never actually used restricted drivers manager for anything.  I would install my drivers and after restarting X I would get a balloon message about it being used.

You don't have to leave kde to use a gnome app or vice versa.  As long as you have the supporting packages installed you can be in gnome and use kde games.  I guess I got confused by that part of your question.  I do agree with your idea of having a cleaner system.

I have since moved back to the gnome desktop - I just like it better than KDE.  Nothing wrong with KDE just a preference thing I guess :) One of the best things about Linux...don't like the desktop?  Just get a new one.

---

### Post by kpel on 2007-05-22
> Kubuntu comes with Adept package manager, similar to Synaptic.

Ah.  I thought it was something like that, but I was having trouble telling because I had both listed.

> As for "extra" drive mounting, on KDE desktop there is an icon in the task bar that looks like a computer (system menu), click on it, then click on storage media and it will show all of your connected drives (cdrom, floppy, hd's, etc.) Hope that helps.

Hm, that's a problem then.  Doing that shows me the contents of /media, which are *already* mounted.  I have three other HDs which aren't shown (and aren't mounted).  It's probably something simple, I guess I'll figure that one out later today when I do the install.


> I had no trouble getting my nvidia card up and running. I never actually used restricted drivers manager for anything. I would install my drivers and after restarting X I would get a balloon message about it being used.

That's exactly what I wanted to know.  Since the only restricted driver I use is the nvidia driver the manager seemed kinda useless to me, but I wanted to be sure the restricted drivers would work.  I do love Beryl.

> You don't have to leave kde to use a gnome app or vice versa. As long as you have the supporting packages installed you can be in gnome and use kde games.

Yeah, I figured that one out not too long ago.  Then I found myself using more KDE programs in GNOME than I was GNOME based applications.  There's a few GNOME applications that I'll grab once I do the Kubuntu install when I wake up later.  Maybe while I'm at it I'll do the smart thing and create a seperate /home partition.

---

