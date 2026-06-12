---
title: "help deciding whether to switch"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by jhlewis21 on 2006-11-17
I've been thinking about switching to linux from windows xp for a while.  I really like ubuntu and even downloaded the iso and booted to os from the cd and liked the way it worked even more.  I just have a couple concerns about switching.  The first being that I would be running it on a laptop and was wondering if I could possibly run into any issues, i.e. wireless, etc.  I also have an ipod was would want to still be able to add/manage my music on it.  Lastly I was wondering about software compatibility, like can you make all or most software that works with windows work on linux.  Basically, I want to switch, but am just a little hesitant and want some experienced linux users to talk me into/feel more comfortable switching.

Thanks,

Josh

---

### Post by bodhi.zazen on 2006-11-17
> **jhlewis21 said:**
> I've been thinking about switching to linux from windows xp for a while.  I really like ubuntu and even downloaded the iso and booted to os from the cd and liked the way it worked even more.  I just have a couple concerns about switching.  The first being that I would be running it on a laptop and was wondering if I could possibly run into any issues, i.e. wireless, etc.

If the live CD runs without hardware problems you should be fine. Some people have dificulty with wireless.

> I also have an ipod was would want to still be able to add/manage my music on it.

ipod should be fine. Try [amarok](http://amarok.kde.org/)


> Lastly I was wondering about software compatibility, like can you make all or most software that works with windows work on linux.

For the most part, no. You can try wine, but it is hit and miss.

You should try [Linux native programs](http://doc.gwos.org/index.php/AppHelper) first.

> Basically, I want to switch, but am just a little hesitant and want some experienced linux users to talk me into/feel more comfortable switching.

Keep in mind Linux is not Windows and there is a steep learning curve. Perhaps dual boot for a while.

You will learn faster if you do not dual boot, but learn and somve your problems if you can.

> Thanks,

Josh

Welcome. This may also help: [url=http://pcmech.com/show/os/917/
]Windows to Linux Migration guide[/url]

---

### Post by b_martinez on 2006-11-17
> **jhlewis21 said:**
> I've been thinking about switching to linux from windows xp for a while.  I really like ubuntu and even downloaded the iso and booted to os from the cd and liked the way it worked even more.  I just have a couple concerns about switching.  The first being that I would be running it on a laptop and was wondering if I could possibly run into any issues, i.e. wireless, etc.  I also have an ipod was would want to still be able to add/manage my music on it.  Lastly I was wondering about software compatibility, like can you make all or most software that works with windows work on linux.  Basically, I want to switch, but am just a little hesitant and want some experienced linux users to talk me into/feel more comfortable switching.

Thanks,

Josh

Without the use of an emulator, it will be impossible to get Windows software running in Linux. There are , however, many programs for Linux. Depends on what you need, I guess. If I were you, I would stick to the Live-CD for a while. I'm confident that you will opt to install in time, and given some time to become acquainted with Linux (Ubuntu, in this case) you will have an uneventful installation. Some of the most common problems new user have with the installation are centered around the partitioning and re-sizing of the hard drive. Boot into Ubuntu, and spend some time here learning what you need.
Better to take it slow than to hose your system and hate Linux forever.
hth
Bill

---

### Post by adamkane on 2006-11-17
Most Windows power users will not be comfortable with a 100% switch. No one can tell you if it is a good idea or not. Only you know what you want to do. You will have frustrations.

Ubuntu is for those who do not have access to another OS, or is for those who do not want to use a proprietary OS. Simple as that.

---

### Post by mediax on 2006-11-17
Dual booting is always an option to consider.

That way, you've got the "security blanket" of Windows to fall back on for anything you aren't able to get working in Ubuntu - which from my personal experience is pretty much limited to games, although everyone's needs are different.

---

### Post by leetrefz on 2006-11-17
I tried to set up a dual boot three days ago. When I went to boot windows it gave me a blue screen so I deleted its partition. I'm on a toshiba satellite A70, a certifiably bad laptop. I'm having what I consider very few problems and so far am loving it. I am spending a lot of time in this forum, but am getting great help and learning quick. Most files from windows can be opened and edited with linux based programs, like word, powerpoint, mp3s, AACs, whatever. I think it' pretty much true that whatever you can do with windows you can do with linux, it just takes learning how. i think there will be no problems with your music collection. It is possible to get Skype and Google Earth, among other things, from the PLF repository. If you have the time to do the reading and research I'd dive right in & single boot, just to force yourself to learn it, I think in the end you'll be glad you did. Otherwise if you really need to be absolutely sure you can get something maybe tricky done at the drop of a hat do a double boot. for me all that took was making an ext3 partition and a 256mb swap partition near the beginning with partition magic (qtparted on your live cd will do, better perhaps) installing to them and wee, the dual boot was automatically painlessly set up in something called the grub menu. I had to ask here just now how to get the now non-existant windows off that menu.

---

### Post by qpieus on 2006-11-17
> **jhlewis21 said:**
> I've been thinking about switching to linux from windows xp for a while.  I really like ubuntu and even downloaded the iso and booted to os from the cd and liked the way it worked even more.  I just have a couple concerns about switching.  The first being that I would be running it on a laptop and was wondering if I could possibly run into any issues, i.e. wireless, etc.  I also have an ipod was would want to still be able to add/manage my music on it.  Lastly I was wondering about software compatibility, like can you make all or most software that works with windows work on linux.  Basically, I want to switch, but am just a little hesitant and want some experienced linux users to talk me into/feel more comfortable switching.

Thanks,

Josh
I just switched to linux earlier this year. I had a lot of your same concerns. I was lucky enough to have a spare computer that I could install ubuntu on to mess around with and learn it a little bit before "taking the plunge". After a couple of months I determined I could handle it full time. I've been pleased ever since. I'll make some comments on your concerns.

laptop: I don't have one, but sometimes there's issues with wireless, as you mention, and touchpads. Did your wireless and pad work when you used the live cd? If yes, then you shouldn't have any problems. I also suggest searching the forum here for your wrieless card and see if anyone else had problems/solutions.

ipod: no problems here for me. I use amarok. It works beautifully with my ipod (4th gen? - it does photos but no video). Amarok does not support photo transfer to the ipod though. There are apps that do that, but I've not played with them as I don't put photos on the ipod.

windows software: some windows stuff can be used with a program called wine. This is not a perfect solution though - wine won't run everything and sometimes it'll run something but there will be little glitches that show up sometimes. I use wine for a CD catalog program I have all my disks catalogged in and Agent newsreader. Both of these apps work perfectly from what I can tell. Summary here is that don't expect wine to work on everything. If it does, feel fortunate. That being said, you should be able to find linux equivalents for just about everything you need. I only use wine for this cd catalog program because it's already got all my cds in its database. There is a linux equivalent app that looks really good, I'm just not gonna spend the time rescanning all my disks. You can also install Vmware server (its free). This is virtualization program that you can install windows inside of. It works really well. This way, you can run native windows apps inside a virtual windows PC inside a window on your linux. Pretty cool.

The other people here making comments are spot on. Dual boot, mess around with linux for a while, learn the ropes, see what equivalent programs are available. Soon you'll find yourself using the windows half of your machine less and less.

Good luck and have fun!

---

### Post by fatneck on 2006-11-17
Dual boot, definitely...! When you power up the machine it will default into Ubuntu so that 'helps' to get you in the environment you want to be in, ie you have to make more effort to go back into Windows. This means (if your're like me) you will just get on and fix any Ubuntu issues you have.

I had the usual laptop wireless and ATI driver issues but now that they are sorted I rarely go into Windows. Even so, I will not be removing it, although I may try and shrink its partition a bit :-)

Good luck.

---

### Post by jhlewis21 on 2006-11-17
Thanks to everyone for their input.  Looking around the forum I can see that any issues that I may have with switching, it will be no problem getting them solved.

---

