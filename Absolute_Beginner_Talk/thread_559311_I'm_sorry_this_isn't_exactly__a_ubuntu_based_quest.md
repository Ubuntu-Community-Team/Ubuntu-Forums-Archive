---
title: "I'm sorry this isn't exactly  a ubuntu based question, probably more hardware wise"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by downgrade on 2007-09-25
So here is my problem. My files keep corrupting. And my system is maybe a year old.

I have had to reinstall many games several times because data files keep corrupting. It only seems to be my gaming files, i at least don't notice anything else getting affected (it happened to WoW MANY times... and just now i was running magic the gathering online in VMware on an XP install and just got a corruption error.

So I started what I think is logical, assumed the hard drive. I have badblocks'ed it many times now, never getting a single error, i had this problem since i was using only windows at which time i didn't get any fdisk errors... never had any hard facts to prove it was the hard drive (and frankly I like my 500gb sata II hard drive and dont want to drop the cash on getting a new one because i assume the  return policy is up and without proof i doubt the manufacturer will take it back).

so i moved onto the memory because that made sense too, these files getting accessed a bunch. I have 2 gig's corsair memory. Something with a big fancy pink X painted on them, they werent the cheapo kind but they werent the extreme high end, i guess budget gaming maybe? Any way I have dod memtest86 multiple times, 20+ passes on some occasions, never a single error...

I have run this system on different OS'es with the same problem. Before in windows I did some research and I have an NVIDIA board and I heard that under windows it has you install some firewall crap that i dont know if it has something to do with built into the board or its just software that ships with it, but I don't think that ubuntu would install that for me, i'd hope not because people said it corrupted their downloads... but as far as i can tell these arent downloads that are corrupting, they are files i installed there and used (usually they are video things like textures or pictures) before and suddenly are corrupt.

Oh wait that reminds me, where as it is a game file its not a file used in a game, there were times when my cd copies of WoW, part of the file would corrupt as well and I would have to retransfer them from the cd, files that i installed from more then once...

so to me i would assume hard drive if i had tests to prove that was the case, but I dont so I dont want to buy a new hard drive (or wait for my old one to go across the country and back) to find out i didnt need to bother and still have the problem

any help please? thank you.

---

### Post by randywilharm on 2007-09-25
Windows is just a bucket of problems

I have Vista "ultimate"  with an Nvidia 8500GT  but I also subscribe to Norton (anti-virus)

In a worst-case scenario you might have to reformat the hard drive
Do you have HIJACK THIS ?? It is freeware and it will tell you if there is an entry
placed in your computer that should'nt be there. You'd be surprised what might be there.

Try to work with Linux. Once problems are solved in Linux(ubuntu or anything else)
they just don't fly back at you like Microsoft.

---

### Post by hessiess on 2007-09-25
are you dual booting with xp and using the ext3 drivers? ive found thay do nothing but currupt the partition

---

### Post by Ant_Merlin on 2007-09-25
Hi, not quite clear but hav you been running XP without any firewalls or anything? A firewall is essential for any system (linux is built into the program) if you have been browsing the internet without or using filesharing software then you very well may have a number of viruses. at least run a virus scanner, you can run free online ones.And if you keep using XP, get a firewall, a free one would be fine.

---

### Post by downgrade on 2007-09-25
To the first comment:
Yeah when I was using WinXP I used hijack this for a different problem but that was the only thing it found.  However I have been running straight Ubuntu for a while now but recently installed WinXP in VMware.

Second Post:
I didn't specifically install any ext3 drivers however if they install by default then I guess so because I didn't touch anything with ext3 drivers what so ever

Third Post:
WHEN I ran WinXP I was running a firewall, however my motherboard shipped with a firewall that as I remember for some reason I think it was built into some of the onboard memory, but my more logical side thinks thats nonsense but since I had that little bit of a doubt I threw that out there. When I was running WinXP I uninstalled the program (or drivers if it was actually built in) because I had heard other people saying it corrupted downloads, but I am not talking about downloads so really it shouldn't have anything to do with my problem, sorry for the confusion.

So to cap up. I am running Ubuntu 7.04 64bit version, I have mem86tested my ram a lot with not even one error, I have badblocked at least a few times (once accidentally using a destructive method making me reinstall everything but i have done a nondestructive since then too) and never got a single badblock from it.

I dont know if this qualifies as to evidence that those pieces of hardware are fine but I don't think it's software simply because I have had many different configurations and the same things happen.

I'd also like to point out i only seem to notice my gaming files corrupting, which leads me to believe those tests aren't very accurate because gaming usually puts a bit more load on the hardware so maybe they are straining at the high end and so maybe getting corrupted there. That possible? And if that was the case how do I figure out what is the problem?

Thanks for all and any help.

---

### Post by Ant_Merlin on 2007-10-08
> WHEN I ran WinXP I was running a firewall, however my motherboard shipped with a firewall that as I remember for some reason I think it was built into some of the onboard memory, but my more logical side thinks thats nonsense but since I had that little bit of a doubt I threw that out there. When I was running WinXP I uninstalled the program (or drivers if it was actually built in) because I had heard other people saying it corrupted downloads, but I am not talking about downloads so really it shouldn't have anything to do with my problem, sorry for the confusion.

Hi, ok you may not be talking about downloads but if you have surfed the net or downloaded anything without a firewall installed AT THE TIME or anti virus software in windows then you may have a virus or number of viruses. That is what I was trying to get at.
While you are now using Ubuntu, you are using Windows XP VMware? you need a firewall installed if you are running this. There is only a few ways for files to be modified or currupted without your intervention. Ubuntu is very secure and these files will not be changed natively. However if you have an installation of XP, VMware or not a virus could cause this behaviour. The other main cause is a failing Hard Drive.
Check your computer for virus and install antivirus, firewall for your windows install.

---

### Post by Conradle on 2007-10-08
**Downgrade** - what make and model is the motherboard? There was an issue with the nVidia 680i chipset corrupting data. Update your BIOS.

---

### Post by downgrade on 2007-10-08
Hmm I am using a KN9 Ultra, it uses the NFORCE 570 Ultra chip, but I will still check that out. Thanks a bunch!

EDIT: Since that last post i went through the hassle of updating my bios without a floppy drive because most of the newer nvidia chipsets had "ActiveArmor" which was intended as a firewall before anything hit the cpu so that the cpu wouldn't have to be burdened as much but many people reported it causing corruption, i haven't had any corrutption since, but I had on many occasions good streaks and bad so we will see but I think it's fixed. Thank you guys (and girls?)

---

