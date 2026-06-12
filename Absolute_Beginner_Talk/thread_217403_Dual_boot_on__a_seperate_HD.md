---
title: "Dual boot on  a seperate HD?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by monkieie on 2006-07-17
Hi,

this may seem like a daft q. but can I install Linux -not on a seperate partition - but on a second HD? Will the grub then see both OS, even though they are installed on entirely different hard-drives? Would I need to have them both on the primary IDE or is it irrelevant to the question in hand?

The thing is, I want to keep XP and Linux entirely seperate from each other - I've spent enough sleepless nights enough, occupied with Windows without having to re-install all that rubbish again...:mad:

---

### Post by ProjectGod on 2006-07-17
yeah GRUB should see both. its prefered to keep the to oses on separate hard disk al together. linux doesnt really mind where you put it on. you could even whack it on an extended logical partition, although not recommended. primary master, slave, secondary master slave... all of them work fine.

P.S we sure love our animals dont we! :D

---

### Post by monkieie on 2006-07-17
we certainly do love our animals! :mrgreen: 

Thanx a lot mate, that'll be one of my next steps then. At the mo. I have Kubuntu running on an old 500Mhz K6-2 but wanted to whack Ubuntu onto my primary PC with a bit more power :p 

PS - THAT is what I love about these forums - a more speedy reply you just couldn't hope for 8)

---

### Post by mbenja01 on 2006-07-17
> **monkieie said:**
> Hi,
The thing is, I want to keep XP and Linux entirely seperate from each other - I've spent enough sleepless nights enough, occupied with Windows without having to re-install all that rubbish again...:mad:


[SIZE="3"]That was my idea entirely, I have used linux in the past, but have kinda shyed away from it for the last couple years, not because of disinterest, but because I needed to keep the family computer accesible and user friendly for *all* the family. I just installed ubuntu on my slave drive, with windows xp on the master, not knowing, because the drive was pulled from a junk emachine, the slave drive has 10 gigs on the master, so I have allocated more space to ubuntu then to my original XP, ha. Everything works fine though, Grub loads up perfectly, I have my easy select menu at start up and my system loads up sweet and quick. I really love this version of linux, by far the best one I have used yet. The only issue I had, was with my wireless network card, ubuntu recognized the card fine, and after configuring my WEP settings I was easily connected, but unknown to me, the driver that is running the card in linux flashes the led lights on the back of the card instead of keeping them solid. I, being used to windows, thought the connection was intermitent, but, after I reset the router and saw the lights still flashing I decided to give the browser a go ahead, I loaded up a page and bam! It came up in a flash, just as all the others aftewards, I guess Ubuntu just has a different set of codes for the LED lights on the card, so, I won't be confused anymore.

now, I am getting ready to install a compiler so I can config and make files as I have in the past.


happy linux user,
matt

[/SIZE]

---

### Post by monkieie on 2006-07-17
yes I wanted to keep the main drive for XP because we use loads of apps there, but I never really have trusted Windows - although XP certainly was an improvement. I have an "older" 30Gb drive which I want to whack in there and will myself primarily use that for Linux - and also to archive all of the data from the second XP partition. The family can then keep their partition ;)

---

### Post by Edho on 2006-07-17
Yes... works fine.

My master is 30 Gb.... with Win Xp.
My slave is 8 Gb ......with Ubuntu (gnome)

During install of Ubuntu on the hd b (its the second harddidk), grub sees win xp on hd a (the first disk) and put a bootloader on the MBR of the hd a.

When you later messing up the grub bl,both windows and Ubuntu is not bootable anymore.
Then you need the win xp install cd to boot and have to place the MBR of windows again with the command fxmbr.

So at least you can boot windows again.

Note:
After a while i devided the masterdisk in partitions...with the linux program Qparted.
1-Ntfs for windows operation-system
2-Fat32 for data, reachable for both, Win and Ubuntu.

---

### Post by Aggienator on 2006-07-17
This setup does work well, but if you then remove the disk with Linux on Grub will have problems. I had this setup up with MEPIS on the slave drive and had problems when removing the Linux disk ([see this thread]("http://ubuntuforums.org/showthread.php?p=1261913")). To gaurd against this I suggest you get [GAG bootloader]("http://gag.sourceforge.net") and have a GAG floppy to hand in case you want to remove the slave and still boot to windows.

---

### Post by monkieie on 2006-07-17
cheers that's really handy to bear in mind. I wasn't intending on pulling the HD for linux at any time in the near future but you just never know ;) 

Your tip could well save me a lot of hassle in time to come and - like was mentioned in your own thread - it's a good idea to have the GAG floppy hand anyway.

---

