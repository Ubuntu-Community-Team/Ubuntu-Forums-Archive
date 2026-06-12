---
title: "Can someone help me move to linux for good"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by mad_max0204 on 2007-12-02
First of all I wanna say hello to everyone since this is my first post.
Second, I visited this forum from time to time and I really liked the community.
I'm a pretty much old Linux user but its been years since I used one (don't hate me coz of this). I was trying to make a move from Win to Suse 10.2 but since its heavy and very consuming I went for Ubuntu.
Downloaded Ubuntu 7.10 x64 some time ago, roasted it and I booted up the machine. First of all I got that Kernled loaded msg and computer freezing until I gave it custom boot parameters (nolapci acpi=off). I have a NF570SLI mother board, AMD 4200+ X2 proc, 2GB ram, ATI 1950pro pcie graphics, KWorld TV Tuner and 4 sata disks (2x500GB, 2x320GB). I inserted one old 40gigs pata drive just to install Ubuntu and try to make at least something work. Installation went quite nice and I liked it from the start. Fast loading Ubuntu and light GNOME. Nice combination.
After that I have had a nightmare trying to make my gfx card work like its supposed to. After some time I managed to get fglrx and 3d to work but I dont know was it right. Ofcourse there is no way on the world to get that TV tuner to work. I gave up after some time. Decided to see how compiz runs and I managed to start it. It slowed system so much and effects were nowhere to be seen. Okay I probably made a mistake with drivers or something. Next thing is trying to play HD content. That was a nightmare too. There no way to install Mplayer because it has some dependencies which can't be solved. Great. Sound worked so its like 2 out of 5.
I know I'm not the guru but its just frustrating not being able to make things work that just get recognized in stupid Windows. Funny thing is that I really want to move to linux its just that I cant make everything work.

What are your suggestions ??

Anyone with the similar configuration that has everything working ??


Thanks for your replies.


Max

PS. And yeah I forgot something. I'm a multimedia addict so HD movies, music and music videos are something that must work :)

---

### Post by Dark_X on 2007-12-02
Did you install XGL?  That should help with the compiz problem.

---

### Post by mad_max0204 on 2007-12-02
Yeah I did with apt-get.

---

### Post by Dark_X on 2007-12-02
And it didn't work?  Did you install the ati drivers from the restricted driver manager?

---

### Post by mad_max0204 on 2007-12-02
Heh yes. I installed ATI drivers from restricted driver manager and system updated them to last. Then I installed XGL with the apt-get and rebooted. There was some blocking but basically XGL worked. Started compiz from terminal and that was it. Only efects I got were slow and buggy.

---

### Post by daengbo on 2007-12-02
What are your problems with MPlayer? I just install from the repos. Can you give the error message during install?

---

