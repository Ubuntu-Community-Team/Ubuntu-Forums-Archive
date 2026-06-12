---
title: "Ubuntu gets slower and slower..."
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by rene100 on 2006-07-24
When I first boot ubuntu it runs nice and speedy, but the longer my system stays running (regardless of whether i am using it) the slower it becomes, until it's painful even to surf the web.  This occurs over the span of several hours  I've done everything I can possibly do to speed things up including:

upgraded to 686 kernel
switched to ipv4 from 6
ran faster-ubuntu script
reduced swappiness and then eliminated swapping (i'm on 1 gig ram, still have 250+ available)
made sure dma was active

well I can't remember everything but i've done everything I can possibly do.  Am I forced to have to shut down my pc every couple of hours to get it to work decently under linux?

---

### Post by JoWilly on 2006-07-24
When it slows down, have you checked the cpu activity with the system monitor ?

Is there any process that starts using the cpu or ram abnormally ?

---

### Post by The Noble on 2006-07-24
Sounds like you have a program that is whoring up your memory. It amazing that you are using 768 meg Ram ALL THE TIME. I personally am using 183 meg right now, with amarok, firefox (4 tabs), and kTorrent. Do you have Azureus running? Limwire? Frostwire? Anything that uses Java? Those apps can take quite a lot of Ram and cpu power, especially the longer they are in use. The second, although less likely alternative, is a memory leak. Check you system monitor under System/Administration and see which programs are using the most memory.

I do have a little bit more difficult way in regaining all those resources. Reinstall ubuntu and do a server install. Install through apt only what you want, like the GUI. Then build the system from there. I have heard of people using as little as 84 meg of Ram after doing something like that. The more you install, though, the slower your computer will run.


EDIT: Also, use the ram checker on the install CD. It makes sure you Ram isn't defective. It can take several hours to complete, so start at night.

---

### Post by rene100 on 2006-07-24
I did check CPU usage and nothing was abnormally high, memory on the other hand is strange. I just rebooted my PC, I have firefox, terminal and nautilus open and this is what top outputs:

top - 23:58:32 up 9 min,  2 users,  load average: 0.37, 0.44, 0.31
Tasks:  82 total,   7 running,  75 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3% us,  1.3% sy,  0.0% ni, 97.5% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1034384k total,   485372k used,   549012k free,     7820k buffers
Swap:   618460k total,        0k used,   618460k free,   338844k cached

---

### Post by VirtuAlex on 2006-07-25
looks normal

---

### Post by dtfinch on 2006-07-25
I was going to say run top, but that's already been suggested. Still, there's a little disk intensive job that runs for maybe 5-15 minutes once a day called slocate (appears in process list as updatedb) that I usually move from /etc/cron.daily to /etc/cron.weekly. It'll run every night, or if you turn your computer off each night, every day maybe a half hour after you log on.

I usually download Firefox directly from Mozilla, rather than use the one in the repositories. Mozilla's build is noticeably faster, though not as much as a few months ago.

For running Thunderbird, I use a shell script which contains the following:
#!/bin/sh
MOZ_DISABLE_PANGO=1 mozilla-thunderbird

Ubuntu's Thunderbird is also slower than the official Mozilla build, as in the message list scrolls at less than one frame per second on my system, but disabling Pango makes up for almost the entire difference.

I've had issues with Ubuntu slowing down and freezing altogether on one of my systems, but it was a timer issue, with the additional symptom of the system clock falling way behind.

I have the system monitor panel applet running so I can notice whenever something's going on.

---

### Post by IrishGangsta on 2006-07-25
wut about xubuntu...isnt it a light weight version and u could use gnome on it. there fore making it run smoother

or am i wrong.

---

### Post by Hikaru79 on 2006-07-25
> **IrishGangsta said:**
> wut about xubuntu...isnt it a light weight version and u could use gnome on it. there fore making it run smoother

or am i wrong.

You're mostly wrong. All the different versions of Ubuntu -- Kubuntu, Xubuntu, etc -- are essentially identical in every way except for the packages they install by default. They even connect to the exact same apt repositories. Therefore, if you take Xubuntu and install Gnome, that's the exact same thing as installing regular Ubuntu and adding XFCE.

Of course, if you just LEAVE it with only XFCE, then you may get a performance increase. XFCE is indeed more lightweight than Gnome. However, your problem is unusual, and there is probably a problem that can be fixed that will allow your computer to run Gnome fine as well.

---

### Post by lopzided on 2006-08-02
> I've done everything I can possibly do to speed things up including:

upgraded to 686 kernel
switched to ipv4 from 6
ran faster-ubuntu script
reduced swappiness and then eliminated swapping (i'm on 1 gig ram, still have 250+ available)
made sure dma was active


what is this 'faster-ubuntu script' you speak of?  i've looked everywhere and can't find anything about it....

---

