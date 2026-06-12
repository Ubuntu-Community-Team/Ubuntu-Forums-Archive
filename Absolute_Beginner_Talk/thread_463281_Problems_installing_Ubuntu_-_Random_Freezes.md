---
title: "Problems installing Ubuntu - Random Freezes"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by sraborg on 2007-06-03
Alright guys. First off, I want everyone to know that I'm a total noobie at linux. I'm a Windows guy that has been trying very hard to learn linux off and on for the past year and half. I've tried several distros and I always seem to come back to ubuntu.

Anyways, here's my current situation. I just installed the latest version of Ubuntu (Fiesty? I think) and I'm having all sorts of performace issues. Basically, the unit I have constantly freezes at random times (These are complete freezes - I Cannot even move the mouse cursor). I opened the "system monitor" and I notice that my CPU usuage randomly spikes up (its all over the place - I've seen it jump from 10% to 70% ro 40% within seconds). I'm not sure whats causing this issue, but it happens why I have nothing opened and I'm just navigating through the menus. 

Any assistance on this issue would be most helpful. Here are the specifications I have currently on my unit.

2-year-old Alienware Laptop

Processor: Intel Pentium 4 3.8ghz
Graphics Card: ATI X00 Mobile - (Pretty sure thats what it is)
Memory: 2 Gigs of Ram

Also, I really think the best way I could learn Linux is to compare it to Windows. If anyone could tell me the Ubuntu equivalents for the following I'd really appreciate it.

- Device Manager

- Task Manager

- System Configuration Utility (MSCONFIG)

- Event Viewer

Thanks for any and all help,
Sean

---

### Post by AAM on 2007-06-04
do your freezes mean you have to re-boot?

checked your RAM?

---

### Post by benner on 2007-06-04
the freezing issue is a big pain in the %#@ and no one seems to have solved it.  as far as i can tell, it happens with ubuntu/kubuntu/xubuntu, happens with 32 and 64 systems, it happens with nvidia, ati and intel video cards etc... nobody knows why it happens.  one thread suggests is is because of the 'cool and quiet' setting on some motherboards.  it isn't.  some suggested that it was a network card issue.  turned out that it wasn't that either.  on  my machine, it comes and goes.  i went almost a month without a crash and then had 3 in an hour yesterday.  no idea why.  i still haven't found a solution.  disheartening to say the least.  i said goodbye to windows 6 months ago and have no alternative except to restart my machine when it happens and swear a little.  i hope you have a better experience than me.  when i gave up windows, i chose to give up using pirated software so i don't want to go back on  my promise to myself.  i think there are folks with other distros that have these problems too.  i come back and check the forums every week or so to see if anyone got it.  good luck.

---

### Post by AAM on 2007-06-05
are you running Beryl? I switched mine off and it seemed to make a difference to the freezing

---

### Post by benner on 2007-06-05
sometimes my system freezes at the ubuntu splash screen while the progress bar is still loading and the system isn't even ready for login.  sometimes I go a week.  i just installed a 32-bit last night to see if my system ran smoother.  i've had 3 freezes on a fresh install in the last 3 hours.  ridiculous.  if you see the number of posts that are out there I can't believe that no one has a clue about this one.

---

### Post by tgalati4 on 2007-06-05
It would be helpful to know the construction of the Alienware laptop.  If the video chip is attached using ball-grid-array solder then it's possible that some warpage or thermal cycling of the motherboard is causing intermittent graphic behavior.  This manifests itself as a freeze, yet the system appears to still be running.

It would be helpful if the system in connected via a wired network, then ssh into it from another machine and when it freezes, use the remote terminal to see the processes (top or htop) and dmesg to see what is going on.  If nothing apears unusual, then at least you can issue a sudo shutdown -h now command to safely bring the system down.

I think the widespread nature of the problem may be due to the this common construction technique, not the distribution used.  It seems to happen on new hardware, as older hardware can't run Beryl.

---

### Post by BHelts on 2007-06-05
a complete freeze like that, where nothing works, including the cursor, is a hardware problem.  it will happen in windows, linux, osx or bsd.  check your ram, check your hard drive.  those two are the most probable culprits, after that you are looking at a motherboard problem.

---

### Post by testube_babies on 2007-06-07
My 3-year-old Alien has the same problems.  It failed memtest, so I got new memory.  Random freezes still occurred.  Turns out I've got motherboard issues!  Hooray.  Alienware wants to charge up the $#@! for a new board, so I'm just living with it.  One of these days I'll eBay it off for parts or something.  Now it's just sitting behind my desk looking sleek.  I hope your problem isn't as serious as mine!

---

### Post by sraborg on 2007-06-07
Hi, thanks for all the quick replies. I'm quite impressed with this forum. 

Anyways, just to clear things up. FIrst off, all these issues occurred after a clean install of ubuntu. Nothing else was installed. Beryl was not installed. These were complete complete freezes. 

Regarding remoting in to the unit via a hardwired connection using SSH. Well, unfortunately, I'm not familiar with linux enough to do this.

After reading the posts, I'm started to question if this is a hardware issue myself. I called up Alienware Tech Support and they seem to think its some kind of power issue. I found out my unit was still in warranty, so I'll probably be going that route with this issue. 

Thanks for all the quick replies,
Sean

---

