---
title: "Ubuntu killed my XP! (Or hopefully not..)"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by maob on 2007-05-16
I've been using windows ever since I can remember, so I'm a total Linux-Noob..

Anyway, I got my Ubuntu LTS CDs in the mail and I tried installing it to my computer. Since I already have XP in my box, I decided to slap an old 10Gig hard-drive in my box, making it the secondary master. Then I installed Ubuntu using the LiveCD.

Everything worked fine, except that when I try loading XP, my window flickers a nasty blue and shows a string of white text--perhaps and error message--which I cannot read because the unit automatically restarts.

Can anyone tell me where I went wrong or what the problem is?

---

### Post by Steve H on 2007-05-16
Did you say you setup your new drive as a Secondary **Master**? why not slave?? 

Anyway thats not the issue?  Have you tried using your XP disk to get in to Recovery console? It may be just a case of running

```
fixmbr
```

From your cmd line in XP recovery console. Maybe try running

```
chkdsk c: /F
```

To see if your disk has any bad data on it.

Hope that helps.

Can you boot in to Ubuntu??

:)

---

### Post by Big_Croc7 on 2007-05-16
Not sure what the problem is, but I can try to help :-)
Does Ubuntu run ok from the hard disk? If so, it might be a problem with Grub (this is the Ubuntu bootloader, which takes control of the system right at the beginning).  If you can get into Ubuntu, can you post your menu.lst file here?
Open a terminal and type
```
gedit /boot/grub/menu.lst
```
then copy and paste that file here.

---

### Post by maob on 2007-05-16
Yup, Ubuntu works fine. So fine it's becoming too scary for me--since I know that somewhere in my box is my XP screaming for justice.. :D

**Steeve:**
Yup, I thought of that too. I guess as a long time windows user, it's just natural for me to get my XP cd everytime there's a problem--and I know you'll believe me when I say I get problems on my machine everytime.. :D

The unfortunate thing is that when I tried running the cd, the computer doesn't boot from it! I mean, I tried everything! I made it my primary boot device, but it didn't work! Now I naturally had the though pattern of "hey, maybe ubuntu screwed my dvd-drive too!" but then I sanely told myself that it ubuntu couldn't have damaged my drive since it's what i used to install it. You wouldn't kill the one who brought you into the world, ryt?

Okay, so now that I'm being too chatty, I guess my dvd-drive got broken and now my system can't boot with my XP CD. (Hmm, can that actually explain why I can't mount my drive in Ubuntu?..)

Note to self: buy a new dvd-drive asap (perhaps an LG DVD-Rewriter with LightScribe--ah, would that work with Ubuntu?) and try steeve's tip..

**Big_Croc7:**
Here's my grub menu (of course, I just picked out the juicy part):

```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdc1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

-------

P.S.
*"Did you say you setup your new drive as a Secondary Master? why not slave??"*

Haha, actually I again had a bad case of thinking something while typing something else.. I actually slapped the other drive as a **secondary slave** (surprise!).. I've already fitted another HD as a secondary slave for backup data.. I guess it was a case of bad judgement for me to have made my dvd-drive the secondary master (another surprise?!)

---

### Post by Steve H on 2007-05-16
maob, I can't see anything that stands out as being wrong in your grub entries. I'm not at home right now so I can't dig through all my notes and stuff but a few things occur to me. It might sound daft but you said you put this new drive in as Secondary master/slave, as a matter of practice I always put my HDD on the primary IDE channel and my cd/dvd drives on the secondary IDE channel. I always put the Windows drive as the Primary Master (it doesn't like being anywhere else) and Ubuntu as the Slave. CD-RW or DVD-RW should always be Masters as well, but on the secondary IDE channel. This is just something I think makes good practice.

Also if you have been digging around in your beige box then it might be worth checking everything is seated properly and you haven't knocked any memory or cables. I have lost count of the times I have been faced with a BSOD in Windows caused by a badly seated meory module or loose IDE cable.

I have a few other ideas but I need to be at home to check my notes and stuff, so if you don't manage to get it fixed then let me know and I'll dig out some more suggestions.

Hope that helps.

:)

---

### Post by maob on 2007-05-16
Yeah, that's what I thought too when I examined my grub file. I'm might be a Linux Noob, but a little light reading on the Grub sure gives me an idea that mine is not bad as it looks.

There's another thing I forgot to mention.. I also installed Norton Systemworks in my XP installation. One of the products included is Norton GoBack, which is a recovery application for XP. Previous to installing Ubuntu, my computer boots this way: after the preliminary BIOS data displays, my computer loads Norton GoBack and then loads WindowsXP..

Now I'm not sure about Symantec and what type of programming they used for Norton GoBack, but since it starts before I see my XP startup screen, I guess Go Back may have altered the startup process as well.

Do you think that this could be the problem? Or could it have helped the problem? Are there any other users who are unable to boot XP because of Symantec, Norton or any other antivirus and data protection programs?..

:confused:

---

### Post by Big_Croc7 on 2007-05-17
Yes, that's almost certainly the culprit ;-)

If you don't mind not using GoBack, at least for now, try running windows recovery console (from the cd - we'll get there in a sec!) and run fixboot (*not* fixmbr); fixmbr writes to the master boot record (one per drive), which will overwrite grub.  fixboot writes to the _partition_ boot sector, so hopefully that will reinstall XP's bootloader, bypassing GoBack, and leaving Grub intact.

Right, then we've got to try to boot from the cd... I'm thinking on that one at the moment!

EDIT: mmm just to check, what make is your PC? Some of the larger vendors sometimes use proprietary systems that don't work properly as regards bios settings etc.  certainly some Dell PCs don't behave properly.  I had to deal with one that wanted to boot from a recovery partition on the hard disk regardless of the bios setting... most irritating!

---

### Post by maob on 2007-05-17
I knew it! After all my years of using Windows, my personal intuitive powers regarding the system and it's problems has somehow grown and developed.. :D

Now, yup, I don't mind not having Norton GoBack.. Come to think about it, I only used it once before--and it didn't work back then.. Maybe, as a Windows user, I just want to have the assurance that it anything goes wrong (and we know it will), I have a third party program to rescue me..

Okay, I'm logging out of Ubuntu now.. I'll post if there are any updates..

---

### Post by gn2 on 2007-05-17
Every prospective user of Ubuntu should be encouraged to study this before attempting a dual-boot installation...

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by kittyhawk63 on 2007-05-17
> Steve H:
[I always put the Windows drive as the Primary Master (it doesn't like being anywhere else) and Ubuntu as the Slave.]
Well, may I say, with only one HDD attached, I first install Windows XP on the attached HDD set as Master. After install, I set it to Slave.  I then attach and set my other HDD as Master and then install Linux. I leave it set as Master. I have never had any problems doing it this way. Linux finds the Windows' HDD and installs the boot command into GRUB.
I use Avast as a virus checker in Windows XP. I have used AVG. Neither give me any problem while installing.
kh

---

### Post by maob on 2007-05-18
Okay, updates..

First, since my DVD-Drive got busted, I bought a new drive--a spanking DVD+/-R Rewriter from LG (with LightScribe support).. I cost me around 1900Php (which is roughly $60).. i slapped it unto my box and tried to figure out why my computer doesn't start (which is apparently due to the fact that this new drive was against slavery..)

Okay, so now I boot through my XP cd and got to the recovery console.. I tried Coc's **fixboot** idea and run fixboot through the console.. I restarted the computer and tada!... It didn't work..

So I went for the second idea, which Steeve pointed out, so I again got to the recovery console and I run **fixmbr**.. After a few seconds of black screen madness, it finished and I rebooted my computer.

Oh my god! It worked!.. Or at least that's what I though for the moment.. The Grub didn't load (which should be right, since fixmbr would have messed up the Grub) and XP started.. All was well until...

**autochk cannot be found!**

Okay, so now, there were problems with the installation itself.. Hmm, what went wrong? Well, I don't know..

And because I was getting excited with all these action-packed scenes of WindowsXP and Ubuntu installations (this isn't sarcasm..), I decided to do something that I have always wanted to do before..

I shut down my PC, went to my dealer and got a copy of WindowsXP 64Bit Edition.. Yup, I am running a 64Bit pc (which I don't think is a culprit in this situation, right?) but my WindowsXP isn't a 64Bit edition.. Thank god that my dealer is also my dear friend--he gave me a genuine windows copy for the price of none.. :D

[B]Okay, so you know the story.. I have an XP box, I installed Ubuntu, XP couldn't boot, tried Croc's and Steeve's ideas and ended up reinstalling my XP with a 64bit edition..

Now I need the final chapters for this story, so I can finally put to rest the soul of my old XP: now that I have reinstalled my XP to a 64bit edition, is there a way for me to return my existing Ubuntu installation--the Grub loader of which was wiped out by fixmbr?..[/B]

I'm soooo excited.. :p

---

### Post by gn2 on 2007-05-18
There are many ways to replace Grub, here's an easy one: [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by Steve H on 2007-05-18
Moab, the easiest way to repair grub is to boot into the Ubuntu Live CD, 

Start a terminal

type

```
$sudo grub

$find /boot/grub/stage1

$root (hd1,0)

$setup (hd0)

$quit
```

then reboot in to what should be your grub menu.

N.B. make sure that find /boot/grub/stage1 actually returns (hd1,0) or similar. If not just replace the relevant entry with your particular return.

Hope that helps.

:)

---

### Post by maob on 2007-05-20
Okay, so here is the update..

Last time I posted, I reinstalled my XP system and ended up messing the Grub. Well, I followed Steeve's instructions of how to reinstall the grub..

And finally.. Tada! I have the perfect Ubuntu and XP dual boot system.. Thanks guys!

:D

---

### Post by Steve H on 2007-05-22
No problem.....here to help!!

:p

---

