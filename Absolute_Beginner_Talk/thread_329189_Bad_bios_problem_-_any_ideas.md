---
title: "Bad bios problem - any ideas?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-01-01
Hi there, basically, have had a huge problem over the last two days and havent the faintest what to do about it:

1/ On booting up, the bios no longer loads properly and doesnt recognise all my harddrives properly, instead of recognising my main SATA HDD (Which it has never had any problems with before) It comes up with a whole string of rubbish (see the attached images)

2/ If it manages to boot correctly, I get Grub error 21, which If i restart again (and it works properly) I get grub error 16. Grub error 21 allows me to open grub up, at which point I can change where it boots ubuntu from from hd(0,0) (which is where it always used to be) to hd(1,0) and it boots without problem, although after booting up on loading applications it freezes and no longer works.

PC Specs:
Primary HDD - SATA 200GB
Secondary HDD - IDE 20GB
AMD 64 3200+
512MB DDR RAM
ATI Radeon 9800 pro

What has happened? Is it a problem with my drives or with bios? Does anyone have any ideas?

Thanks for your help,
Il

---

### Post by bigken on 2007-01-01
give this a shot 1st pull the cmos battery and leave out for five or so minutes

---

### Post by jvc26 on 2007-01-01
@bigken thanks for the advice, I did that, reset the cmos and have been confronted with a new couple of error messages on resuming (see attached file) This appears (as my bios has failed its checksum that the bios is corrupt? How does this happen, and how can I fix it? I also have 2 options now, F1 to continue, or DEL to enter setup... any ideas?
Thanks again for your help,
Il

---

### Post by bigken on 2007-01-01
try F1 see what happens

---

### Post by bigken on 2007-01-01
you might have to set the time and dates in the bios

---

### Post by jvc26 on 2007-01-01
Right, just running through this a few times to see whether it is fixed:

Whats happening now is once I press F1 it gets to loading grub, then I get the stage 2 error 15.

Grub then loads as a window, which allows me to change the hd(0,0) to hd(1,0) as the root for the linux kernel and then Ubuntu boots fine, havent had chance to check out the firefox/other application crashes yet, but will do that when I have a spare moment.

2 last questions: If i boot a couple more times and get no error spat back out at me from bios can I presume that at least for the moment that problem has gone away? And secondly is it now just a matter of going to my grub menu.lst and altering the hd(0,0) to hd(1,0) as I have in the past to sort out GRUB?

Thanks very much for your help, much appreciated,
Il

---

### Post by moma on 2007-01-01
You may try to upgrade (flash) the BIOS. 

Download the latest BIOS-version from the mother-board manufacture's website. The new BIOS is normally packed as a DOS .exe files so you will need a DOS boot disk. See: [http://www.bootdisk.com/](http://www.bootdisk.com/)

You must not run Windows, Linux or any other OS when you flash the BIOS. Use the DOS-boot disk.

---

### Post by bigken on 2007-01-01
yep its fixed if you get past the bios without any errors anything think after that is software related ;)

you might find the super grub disc might help you its in my signature

---

### Post by bigken on 2007-01-01
in reply to the bois flash most new motherboards can be flashed in windows 
but why flash it when its working ?

---

### Post by jvc26 on 2007-01-01
Alas I spoke too soon! I now have a massive error message as shown (attached) but it is no longer the bios which is causing problems... its now the swap filesystem check which comes up every 30 mounts or so, as you can see I have the root command line up now... what do I do now? (am writing this from our other computer)
Thanks again,
Il

---

### Post by bigken on 2007-01-01
it looks like the hdd has gone bad can you pull from the pc and mount it as a slave on another pc

---

### Post by Bartender on 2007-01-01
Wow, I've never seen the characters in a BIOS screen go all alien like yours.  That is truly weird.

Some motherbaords - not very many - have a backup EPROM or CMOS or whatever they call  the little chip that stores the BIOS data in case the first one gets fried doing a BIOS flash.

You don't happen to have one of those boards, do you?  

I hope this isn't the problem, but I gotta wonder if the CMOS chip is dying...

---

### Post by moma on 2007-01-01
Run the fsck (filesystem check) command manually.

# [COLOR="Green"]fsck /dev/sda1[/COLOR]

You may need to answer to several questions.
If you get more than 10 questions about inodes, then interrupt the check. Linux kernel may have got wrong disk-values from the damaged BIOS.

---

### Post by bigken on 2007-01-01
> **Bartender said:**
> Wow, I've never seen the characters in a BIOS screen go all alien like yours.  That is truly weird.

Some motherbaords - not very many - have a backup EPROM or CMOS or whatever they call  the little chip that stores the BIOS data in case the first one gets fried doing a BIOS flash.

You don't happen to have one of those boards, do you?  

I hope this isn't the problem, but I gotta wonder if the CMOS chip is dying...

these characters are quite common in a corrupted bios but are usually easliy solved by shorting the bios or removing the cmos battery ;)

---

### Post by jvc26 on 2007-01-01
Hi there guys, thanks again for your help, learning not to speak too soon about things working, but I'm now back to a point where Ubuntu boots and logs in fine.

Ran fsck, got up a few questions, not many:
Inodes that were part of a corrupted orphan linked list found. Fix(y)?
Block bitmap differences -(numbers) Fix(y)?
Free blocks count wrong for group Fix(y)?
Then 3 Inode count ones...

Does this mean that my HDD is on its last legs? (Its done this once before a while back) or is this just a random messup like my bios?

Thanks again for your help,
Il

---

### Post by bigken on 2007-01-01
dont know if its a bad drive but better safe than sorry backup your data  on a regular  basis  ;)

---

### Post by jvc26 on 2007-01-01
Thanks very much for your help all,
Il

---

### Post by mumushi on 2007-01-01
> **Illuvator said:**
> Hi there guys, thanks again for your help, learning not to speak too soon about things working, but I'm now back to a point where Ubuntu boots and logs in fine.

Ran fsck, got up a few questions, not many:
Inodes that were part of a corrupted orphan linked list found. Fix(y)?
Block bitmap differences -(numbers) Fix(y)?
Free blocks count wrong for group Fix(y)?
Then 3 Inode count ones...

Does this mean that my HDD is on its last legs? (Its done this once before a while back) or is this just a random messup like my bios?

Thanks again for your help,
Il

please try this first... disconnect your hard drive. the data cable and the power then turn your pc on . it should display none during start up and complains there is no hdd. leave it that way for 5 minutes then turn it off for another 5. after dong so reconnect your hdd and power on your pc. go to the bios and set the things you need to set like time/date.. etc... 

if this does not work let us know.

---

