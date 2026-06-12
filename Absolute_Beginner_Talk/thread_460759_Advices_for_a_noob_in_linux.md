---
title: "Advices for a noob in linux"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by arielb_86 on 2007-06-01
Let me start by saying that i still have no clue what linux is appart from being a free OS....ive look at some of the ubuntu capabilities and i love it. not only it looks clean but it also has a lot of free software.

Now the question
I have an HP Pavilion laptop dv5226ca
Specs:
Intel Core Duo T2050
1536MB DDR2 667MHz
120GB SATA (5400RPM)
Intel Graphics Media Accelerator 950
Super Multi 8X DVD±R/RW w/ Double Layer

I am wondering wether or not someone has installed ubuntu in a similar or same laptop and whether or not everything works fine...i have widescreen but ive read around here that its possible to have the correct resolution. what about the wireless device?

Also my laptop came with extra function buttons like the HP quick play....will ibe able to somehow program them to get them to do something in ubuntu if i press on them?

Thanks!
Ariel

---

### Post by finer recliner on 2007-06-01
[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

### Post by khardbored on 2007-06-01
I believe those items are supported. As far as your lappys function buttons, not too sure. But everything else should be tip top. As for your specific question on the wireless, you didn't actually post a card. :P I looked up your model and found that it uses a ntel® PRO/Wireless 3945ABG which is fully supported via the ipw3945 driver. Which, if im not mistaken, is included with Feisty Fawn!

---

### Post by Inxsible on 2007-06-01
I installed it on my laptop wireless and everything. As you can see i have a HP laptop. widescreen 17" resolution works too.

I have my media buttons configured. My Quickplay button opens my mail client Thunderbird. DVD button opens Rhythmbox and the play stop etc buttons do what they are supposed to do.

---

### Post by arielb_86 on 2007-06-01
> **Inxsible said:**
> 
I have my media buttons configured. My Quickplay button opens my mail client Thunderbird. DVD button opens Rhythmbox and the play stop etc buttons do what they are supposed to do.

How where you able to set them up? Do you need any specific extra package?
Also quick noob question: any quick easy tutorial on linux? Ive been reading posts and what to write in the console and i would like to have a better idea of what am i writting:p

Thanks

---

### Post by Inxsible on 2007-06-01
> **arielb_86 said:**
> How where you able to set them up? Do you need any specific extra package?
Also quick noob question: any quick easy tutorial on linux? Ive been reading posts and what to write in the console and i would like to have a better idea of what am i writting:p
 
Thanks
 
No you do not need any special packages.
 
Go to System --> Preferences --> Keyboard Shortcuts
 
You will see Desktop and Sound as the 2 major drop-downs. Expand them and change the shortcuts the way you want them. If you dont have Beryl, then you might see another drop down -- i think its called Window Manager, or something to that effect. For media buttons, you will need to look into Sound, of course.

---

### Post by arielb_86 on 2007-06-01
what about the dual boot with windows, how do you find it?
You didnt encounter any problems when you go back(IF) to windows?

Im just scared to do the dual boot and get errors in windows or something? like if u go back to windows the hp buttons will work as normally opening the hp quick play and stuff?

---

### Post by Inxsible on 2007-06-01
> **arielb_86 said:**
> what about the dual boot with windows, how do you find it?
You didnt encounter any problems when you go back(IF) to windows?
 
Im just scared to do the dual boot and get errors in windows or something? like if u go back to windows the hp buttons will work as normally opening the hp quick play and stuff?
 
Oh yeah ! 
 
Windows has nothing to do with what we change in Linux. These settings are stored in the OS and not on the hardware (i.e. the buttons) directly. So, if you log into Windows, they will do what they currently do in Windows, like QuickPlay etc. etc.

---

### Post by drowner on 2007-06-01
> **arielb_86 said:**
> what about the dual boot with windows, how do you find it?
You didnt encounter any problems when you go back(IF) to windows?

Im just scared to do the dual boot and get errors in windows or something? like if u go back to windows the hp buttons will work as normally opening the hp quick play and stuff?

Dual-booting should not affect your windows hotkeys in anyway.

Linux does not change the way windows handles your keyboard, and other peripherals, it has its own setup.

---

### Post by arielb_86 on 2007-06-01
sweet and sorry to bother again but is there any quick easy tutorial for linux command line(in particular the one i will use with Ubuntu) i would like to understand what im writing if possible...

Thanks! (gotta love the linux community, so much nicer than the windows one)

---

### Post by Sethalos on 2007-06-01
I have almost the same laptop and it runs Ubuntu fine. I haven't bothered with the Hotkeys at all, but everything else runs smoothly.

I thought about dual booting, but ended up just using VirtualBox to host my WinXP OS and run what I needed through there. It works excellent that way.

Good luck

---

### Post by drowner on 2007-06-01
> **arielb_86 said:**
> sweet and sorry to bother again but is there any quick easy tutorial for linux command line(in particular the one i will use with Ubuntu) i would like to understand what im writing if possible...

Thanks! (gotta love the linux community, so much nicer than the windows one)

[www.linuxcommand.org](www.linuxcommand.org) 

But, don't worry too much.

The way i learnt was to ask, and to try and work out what everything i needed to type in meant.

You will learn with practice.

---

### Post by phr0ze on 2007-06-01
It seems you haven't tried the CD yet? When I want to find out if my system will work with ubuntu, I boot the CD. With Ubuntu and many other linux flavors you can boot the CD and use the system without making any changes to your harddrive. This is called the Live CD. Ubuntu has it's Live CD and Install CD in one disk.

After you try the live CD, come back and tell us what isn't working right. I doubt it'll be much.

When you are ready to install Ubuntu, click the install button on the desktop of the live CD. On Step 4 the installer will ask you about partitioning. If it goes smoothly, there will simply be a slider bar for you to pick how to divide the space on the drive. I'd leave it in the middle. This will automatically create the right partitions and set windows up to dual boot! Super Easy.  Some people aren't lucky and they don't get the simple slider.

Good luck.

---

### Post by arielb_86 on 2007-06-06
i tried the live cd and i love it. it worked pretty neat. Haven't tried everything though but screen, wireless and bla bla worked pretty right of the bat.

few quick questions:
1. will the installation create a dual boot with xp?
2. i was able to enable the desktop effects...so then what is beryl? edit: dont worry about this one, i found the website:p
3. will 10-15 gigs of space will be enough? im not really planning to install much more than what it already has
4. any advices on what should i be checking with the live cd?
5. how come you guys don't become angry with all the noobs questions:p in other forums people would be like....."Google it" "search in the forums"....i love the support of linux!:D

Thanks!

---

### Post by freebeer on 2007-06-06
> **arielb_86 said:**
> 
few quick questions:
1. will the installation create a dual boot with xp? 

Yes it can do that quite easily.  You might want to read up a bit on the process so that you're prepared for it.

> 
3. will 10-15 gigs of space will be enough? im not really planning to install much more than what it already has


Ubuntu will run within that amount of space quite easily.  You may want to consider partitioning that space into seperate /, swap and /home partitions.  This is why I recommended reading a bit on the process so that you have a plan.  :D

> 
5. how come you guys don't become angry with all the noobs questions:p in other forums people would be like....."Google it" "search in the forums"....i love the support of linux!:D 

Nice of you to notice! :D  It's actually this Ubuntu forum that seems to be so friendly and helpful.  I've been on others (for other distros) and they were not as open or helpful as this one.

Good luck!

---

### Post by arielb_86 on 2007-06-06
for the partition i have already partitioned my hard drive
C: for windows xp
d: for around 40 gigs for just data

my idea is partition again the d drive and use that space for ubuntu.
makes sense?

---

### Post by Inxsible on 2007-06-06
read more about partitioning here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
 
and installing here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by sailor2001 on 2007-06-06
3. will 10-15 gigs of space will be enough? im not really planning to install much more than what it already has 

My box is really loaded with everything I can think of and more (including beryl) and have only 4.4gig right now..........there is no bloat in linux like there is in windows

---

### Post by arielb_86 on 2007-06-06
i have a new question. since i will have 3 partitions....ive seen people running like a virtual drive to use windows from ubuntu....can that mounted virtual drive be the partition with windows???

and if so...any tutorial around here?
thanks!

---

### Post by LinuxLoserr on 2007-06-06
Alright. Well, I can't really answer that question for you, but you should search around in these forums, you'll probably find some sort of tutorial. I'm not really good with partitions, and what not.

---

### Post by jimrz on 2007-06-06
> **arielb_86 said:**
> i have a new question. since i will have 3 partitions....ive seen people running like a virtual drive to use windows from ubuntu....can that mounted virtual drive be the partition with windows???

and if so...any tutorial around here?
thanks!

you probably also have restore or whatever partition that would have been setup by hp. you can only run 4 basic partions on a single drive, so when you make your new partition for ubuntu make  an extended partition (if you do not already have one) first and then make your ubuntu and partitions (/ + /home [if you want it seperate, and I believe this is a good idea] + linux swap) within the extended partition, which can contain many partitions.

welcome and have fun with it.

---

