---
title: "[SOLVED] Xp and Ubuntu 7.04 problems"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by gavshouse on 2007-07-20
ok ive install windows XP on my 80GB with a 60GB partitions and ive installed Ubuntu on the rest also ive got 800mb for a swap with grub on, the first time i install ubuntu it didnt work, so i installed it again worked fine then i tried to install beryl but that went wrong so i formated the Ubuntu partition and install it again but its not working, ive filmed what happened and will post links to them,

1st Try
[UPDATE] video one here [http://www.gavssite.com/1st.mov]("http://www.gavssite.com/1st.mov")
This is what happen the first time grub loaded up and ubuntu started it went to the logo and got about 40% then it went to something that looked like DOS and said something about superblock and it had a dashed line and a % was going up then it said something about the file system check connected errors on the rest of the partition and and it had "fail" in the right hand corner, and then restarted my PC, now it did this before but worked fine after it restarted but this time it loaded up the ubuntu log and got all the way across then went black with a white line in the left hand corner then its went all black but the monitor was on then after about 5mins i turned it off and tried again

2nd Try

Ok it started up ok the Ubuntu logo appeared and was loading, loaded fine then a white line appeared in the left hand corner again, it then put some message on which i cant really make out in the video i think its might say "starting ???? unix printing system : ????" then the screen went black after 10mins i restarted

3rd Try

ok it started ok logo and loading image, ok it loaded fine again, then the white line appeared again in the left hand corner, then the screen went black again.

My mate says it could be the disc, i will check it after this, windows XP loads fine as im writing this on it, i will try one more time after this, also i will upload the videos onto my server and post links to them 

PC specs

1.92Ghz AMD 
Mother Board  K7S8X (if this helps)
1GB Ram
80GB HDD
256MB ATI Graphics Card

it runs fine in live i have ran ubuntu in live for along time since around 6 so i cant see why its different, and ive ran it before it was just i edited something to get beryl working and it went wrong please help

---

### Post by ddrichardson on 2007-07-20
It doesn't sound like the disk  but you can check using the "Check install media" option during Live CD boot.

---

### Post by gavshouse on 2007-07-20
i check it about 2mins ago its fine

---

### Post by ddrichardson on 2007-07-20
There are a few reports on the net about this happening with certain types of blank media. But then you've been running the live system. Try another Ubuntu install with the Ubuntu partition being formated during install.

---

### Post by gavshouse on 2007-07-20
> **ddrichardson said:**
> There are a few reports on the net about this happening with certain types of blank media. But then you've been running the live system. Try another Ubuntu install with the Ubuntu partition being formated during install.

thats what ive done twice now, but before i had it working so... ?

---

### Post by ddrichardson on 2007-07-20
If the disc had a problem, it would most likely hang in the same place. This is more indicative of a problem with the hard drive. Post the links so I've more info.

---

### Post by gavshouse on 2007-07-20
im uploading them now my brother is hogging the bandwidth only uploading at 16kb/s first video is nearly done 78%, i could run a killdisc if i had one and then install XP and ubuntu but id like to get this to work, i mean this OS is suppose to be stable

---

### Post by gavshouse on 2007-07-20
first video [http://www.gavssite.com/1st.mov]("http://www.gavssite.com/1st.mov")

---

### Post by ddrichardson on 2007-07-20
OK I've seen that now, when it gets to the blinking cursor in the top corner, can you use <CTRL><ALT><F2> to open a virtual terminal?

---

### Post by gavshouse on 2007-07-20
> **ddrichardson said:**
> OK I've seen that now, when it gets to the blinking cursor in the top corner, can you use <CTRL><ALT><F2> to open a virtual terminal?

ok if i can what should i do

---

### Post by ddrichardson on 2007-07-20
Check /var/log/boot to see if there are any problems. Also try doing it during the uSplash boot screen - you may get more information on what's hanging.

---

### Post by gavshouse on 2007-07-20
ok im not sure if this is what you said but i just started pressing random buttons and this came up, i thought it was a login so i tried to log in
[http://gavssite.com/1.jpg](http://gavssite.com/1.jpg)

other images below

[http://gavssite.com/2.jpg](http://gavssite.com/2.jpg)
[http://gavssite.com/3.jpg](http://gavssite.com/3.jpg)

---

### Post by alienexplorers on 2007-07-20
Have you tried the alternate CD to load Ubuntu.  If not try it. If it works it should automatically setup grub for dual boot.

---

### Post by gavshouse on 2007-07-20
> **ddrichardson said:**
> Check /var/log/boot to see if there are any problems. Also try doing it during the uSplash boot screen - you may get more information on what's hanging.

wowo im a newb with this i dont understand

---

### Post by gavshouse on 2007-07-20
> **alienexplorers said:**
> Have you tried the alternate CD to load Ubuntu.  If not try it. If it works it should automatically setup grub for dual boot.

grub is setup fine, ive only got 1 CD the cd is fine

---

### Post by ddrichardson on 2007-07-20
Yes that helps - seems to be related to resizing partitions with gparted, check out these:

[https://bugs.launchpad.net/ubuntu/+bug/103148]("https://bugs.launchpad.net/ubuntu/+bug/103148")
[http://ubuntuforums.org/showthread.php?t=385869]("http://ubuntuforums.org/showthread.php?t=385869")

There's also a suggestion that its related to power management, try pressing F6 prior to boot and adding the noacpi option.

---

### Post by gavshouse on 2007-07-20
hmm seems werid tho that this is only affecting me the second time i install it maybe if i just keep installing it one time it will be right like last time

---

### Post by gavshouse on 2007-07-20
im going to try this people say "
Mine does, too. Well, not hang exactly. It gets to that part, I get a black screen with my cursor. Then it hangs indefinitely, until I press Control-Alt-Backspace, at which point everything loads perfectly" 

so if i try this i might be able to get into it still i dont want to do this every time i want to login

but this person says "Since the latest Feisty update this problem has been fixed for me. However now my wired network connection is gone, only wireless works." so if i can get on and update maybe everything will work

---

### Post by gavshouse on 2007-07-20
ok the alt-crtl-backspace didnt work again im not sure what im doing here "try pressing F6 prior to boot and adding the noacpi option." prior to the boot so whens grubs on, the bios do you want me to go into the setup, 

i think i will sit it out and see what happens for about 15mins max because on the other thread people are saying it does boot but its takes along time

---

### Post by gavshouse on 2007-07-20
OMG this is pecking my head maybe i should just wait for ubuntu 7.10 is coming out for 18 October 2007 lol, everything in them other links you gave me ive tried, i think i will download 6.10 and install that

---

### Post by gavshouse on 2007-07-21
it loads !!! after 14minutes and 32seconds i got into the login screen after i typed my user and password it went all slow and crashed though so im stuck again

---

### Post by ddrichardson on 2007-07-21
Out of interest, have you experienced any problems in Windows, like drives needing to be checked for consistancy? Only people often mention that Windows is fine when the truth is it doesn't check out much during booting - it tends to wait for problems rather than scan for them earlier.

Random problems are often related to hard drive problems, I'd hate you to lose in data so it may be worthwhile downloading the disk diagnostic tools from your hard disk manufacturer.

Don't want to be chasing your tail after a symptom rather than a fault ;-)

---

### Post by gavshouse on 2007-07-21
im gd with windows its fine, all drivers, drives, codex, hardware is working perfect i scanned my HDD its fine, i will do i de-frag tonight

I was going to order a 160Gb HDD for a slave but i will set it as master then and install XP and ubuntu on that and see what happens but id like to get it too work on my 80GB i cant see why its not working

---

### Post by ddrichardson on 2007-07-21
Right then.

fsck exit status 3 is a combination of errors found and corrected (exit status 1) and reboot required (exit status 2), hence 1+2=3. And it doesn't reappear so no worries there.

Try downloading and burning a new copy - this seems spurious to me. It worked before and if the drives and hardware haven't changed the most likely thing is the installation media being damaged but not enough to trip a disk check.

---

### Post by gavshouse on 2007-07-21
> **ddrichardson said:**
> Right then.

fsck exit status 3 is a combination of errors found and corrected (exit status 1) and reboot required (exit status 2), hence 1+2=3. And it doesn't reappear so no worries there.

Try downloading and burning a new copy - this seems spurious to me. It worked before and if the drives and hardware haven't changed the most likely thing is the installation media being damaged but not enough to trip a disk check.

ok ive only got DVD's so im going to burn 7.04 to a dvd i would think it would work i installed XP of a dvd instead of a cd because i didnt have any

---

### Post by ddrichardson on 2007-07-21
As long as it's bootable it's fine.

---

### Post by gavshouse on 2007-07-21
ok im burning now i hope this works, i will get back to you in about 1hour then. thanks for your help, still it would be great to find out why this is happening

---

### Post by gavshouse on 2007-07-21
nope its not worked same errors are coming up

---

### Post by ddrichardson on 2007-07-21
Check your PM's

---

