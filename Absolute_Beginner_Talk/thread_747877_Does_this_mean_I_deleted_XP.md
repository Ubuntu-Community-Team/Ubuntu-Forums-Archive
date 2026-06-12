---
title: "Does this mean I deleted XP?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by noskillz on 2008-04-07
This is the result of sudo fdisk -l in the terminal. XP didn't show up in the GRUB boot menu. Does this mean I deleted XP?


/dev/sda1   *           1       11485    92253231   83  Linux
/dev/sda2           11486       11978     3960022+   5  Extended
/dev/sda5           11486       11978     3959991   82  Linux swap / Solaris

---

### Post by AnLGP on 2008-04-07
I'm not 100% sure; but I had a problem that windows wouldn't boot.  It showed up, but wouldn't boot all the way.  All I had to do was configure a file, but yours may be a different scenario.

---

### Post by Dynaflow on 2008-04-07
If Windows was the preinstalled OS on your computer, it would have probably been on sda1 (unless you moved it with gparted or something for some reason).  It looks to be gone.  How did you go about installing?

---

### Post by SunnyRabbiera on 2008-04-07
hoo boy you might have.
What did you do when installing linux, did you tell it to half your drive or did you tell it to use all your disk space?
if you deleted windows by accident, you have my sympathies as I know you intended to dual boot and XP is pretty hard to re install if you dont have a installer disk

---

### Post by noskillz on 2008-04-07
I burned the Ubuntu iso to a disc and did it that way. I used the partition using free space option. XP was the original OS. So it looks like I'm SOL?

---

### Post by riven0 on 2008-04-07
> **noskillz said:**
> 
/dev/sda1   *           1       11485    92253231   83  Linux
/dev/sda2           11486       11978     3960022+   5  Extended
/dev/sda5           11486       11978     3959991   82  Linux swap / Solaris


Definitely looks deleted. fdisk -l usually picks up on all partitions without trouble.

---

### Post by SunnyRabbiera on 2008-04-07
> **noskillz said:**
> I burned the Ubuntu iso to a disc and did it that way. I used the partition using free space option. XP was the original OS. So it looks like I'm SOL?

yeh, you might have screwed it up installing Ubuntu.
Like I said you have my sympathies...
what did you use XP for by the way, we may be able to suggest some alternatives for your favorite software and you can use Ubuntu as your main OS until you find a way to get XP back.
Hey I messed up dual booting once myself so I fully understand if you get a little mad over this.
we are all beginners at some point.

---

### Post by noskillz on 2008-04-07
I really need to go back to XP. I guess I'll have to find my disk. Is there anything I can do without it? I can use linux in the mean time but somehow I have to get xp back.

---

### Post by SunnyRabbiera on 2008-04-07
well what do you use your computer for may i ask?
Its a good thing that you have a backup disk, next time I suggest you do some reading on dual booting before trying again.
Did you research dual booting before attempting giving ubuntu a shot?

---

### Post by noskillz on 2008-04-07
I use it for school mostly, but I do play the occasional game. I really hope I have the disk. I'm at school and it is in my hometown (which is just an hour away). Any suggestions on what to do if i can't find it?

---

### Post by SunnyRabbiera on 2008-04-07
you may have to buy XP again... i would suggest something else but its a little... illegal, actually its very much illegal so i cant discuss it in full here :D
I hope you do find your backup disk, like i said I once did something like this myself.
Now what kind of games do you play on your computer?
web games or some games from the store or something?
gaming is not that good in Linux right now so we might not be able to help you there.
now for school what do you use your computer for?
do you do writing projects and such?

---

### Post by noskillz on 2008-04-07
Games that come from the store that Linux won't run. I'll be fine until i know if I have that disk or not. I might check out that "alternative method" you mentioned.

---

### Post by SunnyRabbiera on 2008-04-07
well there might be some that might be able to run under wine, but it depends...
But please note I encourage you to buy XP rather then illegally download it, but those are the only two ways to get XP back if you cant find your backup disk.

---

### Post by mjp216 on 2008-04-07
Who cares if you deleted XP?? Ubuntu is god!

---

### Post by bumanie on 2008-04-07
If that's the output of fdsik -l you have definitely got rid of your windows partition. You could try and restore it via test disk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) It is a good partition/data recovery program (live cd). Download test disk and burn it at school if you can so that you don't disturb the drives on your computer. To recover windows, you will get rid of ubuntu, but you can reinstall it once windows is recovered.

---

### Post by Daveg4otu on 2008-04-07
You can use a borrowed disk to install  a trial install - lasts for30 days before it locks you out .

If within that 30 days you can get hold of your XP  Product serial number(the 25 digit  PID - looks like this.....ABCD1 EFGH2 IJKL3 45MNO 6PQR7)...then you can activate the install provided that it is the same version as your PID version (ie;if the copy is XP Pro  your PID must be for Pro etc etc)

---

### Post by AndrewEsther on 2008-04-07
you use it for school? so word processing, spreadsheets, some slide presentations, the occasional .pdf file.. maybe some .mp3's, CS and WoW

get WINE and dump windows... if I wasn't so dependent on windows to keep my aging parents from killing themselves due to frustration at performing the most basic computing tasks, I probably would have switched to linux a long time ago. unfortunately for me, almost everyone seems to sign their soul over to microsoft as soon as they're given a choice.

---

### Post by hyper_ch on 2008-04-07
WoW works perfectly in Linux :)

Btw, as you are still at school it might be your school is participating in the MSDNAA. Check out here:   [http://www.msdnaa.net/search/schoolsearch.aspx](http://www.msdnaa.net/search/schoolsearch.aspx)

If your school is participating, you might download a fresh copy of WinXP, win 2000, Vista from them.

---

### Post by apostate on 2008-04-07
> **noskillz said:**
> I use it for school mostly, but I do play the occasional game. I really hope I have the disk. I'm at school and it is in my hometown (which is just an hour away). Any suggestions on what to do if i can't find it?

Use Linux?

I mean, if you are saying that you use the PC to write papers, surf the web, check email....seriously.

Not trying to be snide, I know this was a mistake, but in terms of what can you do with your PC now....you can use it for anything you want. Shoot, you can play your games on it most likely, given a modicum of effort.  Linux isn't the runner up, it's a powerful UNIX-like OS that you can use for all sorts of stuff. It may do more now than it did before. What exactly are you missing?

---

### Post by darren1270 on 2008-04-07
Is there a COA on the side of your case somewhere?  If so... no problem... Just look at the COA and it'll be more than likly XP Home OEM.... Just get a OEM disk from someone and use your key that's on the case... What brand of PC is it?  EX: If it's a dell or something then pretty much any dell disk will work for you.  Gotta remember the key is not tied to the CD...!

Good Luck!

---

### Post by coolen on 2008-04-07
If you don't have XP CDs, go to a computer store. My friend works in one, and he says they'll hand OEM discs to someone if they've bought a system with XP preinstalled. You don't pay for the copy of Windows, you pay for the license.

Might not work in all cases, but there are stores out there with that policy.

---

