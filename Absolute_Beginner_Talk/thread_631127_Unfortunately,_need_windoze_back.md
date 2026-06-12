---
title: "Unfortunately, need windoze back"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by zabien1970 on 2007-12-04
Ok friends, here's my sit.
 About 9 months ago I decided to try linux, did my research, chose ubuntu, decided to do a dual boot but screwed up, wiped windows, no prob. pure linux, thats how you learn and have been extremely happy except for one minor problem, I bought a dell inspiron 6000 laptop which works perfectly for me but I also bought a photo 964 all in one printer which is listed as a paperweight :(
 I currently can't afford a new printer so I contacted Dell and recieved a new xp disc (after 4 months)
 So now I need to know how to reinstall windows hopefully without screwing up my current setup in a dual boot mode
 Also, how to print stuff I have in ubuntu over.
 ?

---

### Post by skymera on 2007-12-04
ok i would partition a space for XP in ubuntu, use gparted in the live CD.
then install XP.

but once you install XP you will need to install the grub boot loader again

---

### Post by KhaaL on 2007-12-04
Exactly what Sykmera said. XP likes to write over the bootloader of any OS and therefore you should make backups and prepare for the worst, just in case.

---

### Post by skymera on 2007-12-04
even when it does write over, its very simple to get it back :)
a 5min job, if that.

forgot, Good Luck :)

---

### Post by zabien1970 on 2007-12-04
Actuallly I should ask this differently, I am still learning and need my hand held through alot of this.
 So here we go:
 If I wipe my system, install windows xp, then install ubuntu, which I believe is the recommended way everything should work.
 Unfortunately I know I will lose everything I've modified or added since I installed.
 From what I've read I could back all this up but I don't know how
 So what I'm asking is:
 
 How do I take my mods. ie. codecs to get my dvd player working, stuff to get compiz working, my history, blah, blah blah, anything that wasn't installed off the live cd and save them to a backup cd so when I reinstall I can reinstall them?
 Is this possible or do I have to start all over again?

---

### Post by hyper_ch on 2007-12-04
basically you'll just have to save the whole /home folder to another place. That should backup your user settings and files.

---

### Post by indytim on 2007-12-04
One of many possible solutions :) :

1.  Through the repositories, get a hold of Partimage and install.
2.  Using Partimage, backup your Linux-related partitions ( you can size it to fit either a CD or a DVD - the ideal situation is to dump the Partimage output to an external).
3.  Use GParted to size your NTFS , swap and ext3 partitions before installing XP.
4.  In the XP installation, designate the NTFS partition for ops installation.
5.  Boot to a Live CD and install Partimage.
6.  While in the Live CD, re-install your Lx stuff in the appropriate partition (#3 above).
7.  Re-install GRUB.
8.  Boot to Lx and adjust your fstab to the new partition id's.

There are some details behind each of the above.  A forum search or other members of the collective should be able to help - unfortunately, I'm off to work shortly.

Good Luck,

IndyTim

---

### Post by zabien1970 on 2007-12-04
That's pretty much what I was thinking, 3 questions though
 1) It took me awhile to set up xorg for things like tapping on my touchpad, will these be saved?
 2) My dvd codecs, are they in the home folder or do I have to reinstall to watch movies again?
 3) Since I'm gonna wipe my system doing this how do I save this to cd-rom, I've never done this before

 I was also thinking of trying gutsy, any advice?

---

### Post by hums07 on 2007-12-04
Installing XP is as simple as skymera said:
1. Make a new partition using gparted in liveCD.
2. Install XP on the new partition (be careful not to install on other partitions - especially where Ubuntu is!).
3. Install grub using liveCD. Installing grub won't change either your XP or your Feisty.
Done!
Now you have dual boot system, your Feisty will run as usual with all your settings.

---

### Post by zabien1970 on 2007-12-04
As I said I basically need my hand held through this, since burning the ubuntu live cd I haven't backed up anything or burned anything.
  I have been playing in the terminal though so if someone could give me the codes to bring up my /home folder, and any other folders that may be important and then the code to burn them I could start this.
 Then I could reinstall the dreadful xp, reinstall ubuntu, and hopefully reinstall my folders from the cd

---

### Post by zvacet on 2007-12-04
> If I wipe my system, install windows xp, then install ubuntu, which I believe is the recommended way everything should work.

It is recommended because that way you install grub and everything is O.K.But if you have ubuntu allready installed and you want to install win you will have to reinstall grub.It is not very hard to do.So,take **skymera´s** advice and shrink Ubuntu partition and install windows.To reinstall grub look [here](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub).For Gutsy upgrade look [here](https://help.ubuntu.com/community/GutsyUpgrades).

---

### Post by zabien1970 on 2007-12-04
hums07, sorry, was typing while you posted.
I've always read here it's better to have windows installed first and that was my concern.
I know I can do what you're suggesting but will that work ok?
also, I've never used gparted, any tips?

---

### Post by zabien1970 on 2007-12-04
First I want to apologize, I have been following these forums for a long time and I don't want to seem rude.
 But, I am a little stubborn and at the same time have an idea of what I want to do.
 I would like to save my /home directory to a cd-rom
 Then Install windows
 Next, try to dualboot ubuntu and see if I can do it this time without wiping windows, not that it was bad but untill I get a new printer I'll survive
 Then reinstall my /home directory

 I have modified my fiesty install and have read that an upgrade is not recomended so I will first burn a new iso, this I know how to do.
 Unfortunately what I am stuck on is saving things I already have, this is what I need help with
 Once I open the terminal what commands do I enter to accomplish this?
 I hope I'm not sounding unappreciative for the suggestions everyones offered so far

---

### Post by bdcheung on 2007-12-04
Should the NTFS partition for XP be *before* or *after* the Linux partiiton?

---

