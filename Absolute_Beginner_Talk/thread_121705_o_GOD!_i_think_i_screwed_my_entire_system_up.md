---
title: "o GOD! i think i screwed my entire system up"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by shrimants on 2006-01-25
I installed the full version of ubuntu up until the point where it said to remove the CD and reboot to make sure there wasnt any errors. i did and when it reboot, it gave me an error. it said disk error,  please insert boot disk. I was trying to install on a 10 gig hard drive out of an xbox, which i had unlocked and it was being recognized fine beforehand by windows. now, its getting stuck at setting up partitioner at 41% and worse, I CANT BOOT WINDOWS!!

all of my parents' and sister's and my files were on there, like 37 gigs. also, when i try to load just windows without the other HD in, it says GRUB error 21 or something. what do i do? i am really freaked out because there was a lot of files on there and we dont have the original XP cd. we used my dad's from his workplace, since he took it there once to get it reformatted. please help! i think im gonna die.

---

### Post by kaamos on 2006-01-25
Boot with a windows cd, enter the recovery console and try the command "fixmbr".

---

### Post by shrimants on 2006-01-25
ok, some progress. i dont know what i did but now the grub is loading. when i try to load ubuntu, it says cannot load bin/something.sh and then ID1 pauses for 5 minutes and id4 for 5 minutes. also, when i try to load microsoft, the screen is just black. i only have the home edition upgrade cd, not the base software professional CD that is on my comp. should i still try to do what u said?

---

### Post by HJThis on 2006-01-25
Hello,shrimants

Please have a look here maybe of help

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)

Best of luck

---

### Post by HJThis on 2006-01-25
Hi,shrimants

What helped me was i made everything from Auto Mode to
LBA Mode & have not had the problem again.

Best of luck

---

### Post by shrimants on 2006-01-25
yes, thats what i did for getting the grub to work, and now i have done the fixmbr thing. now if i boot normally, it says DISK BOOT FAILURE, PLEASE INSERT BOOT DISK AND PRESS ENTER. i will try to reinstall the ubuntu OS on the disk, and hopefully, it will go correctly this time. if you could continue to give insight, please do, because the files on the computer are vital. thank you.

---

### Post by az on 2006-01-25
You said you installed on an Xbox 10gig drive, but you have 37 gigs of data on it?

I don't understand.  

As for "unlocking" an Xbox Hdd, you just format it.

Can you boot the live cd?

Are you talking about two hard drives?  Them can you enter your bios and tell it that the 10 gig drive does not exist (NONE) and then see if you boot into your other drive?

---

### Post by HJThis on 2006-01-25
Hi,shrimants

Now if you can get to windows i would do as you 
just said but if you no longer have Windows i would
install Windows first then install Linux.

& just let linux auto load Grub it's what
i have done without one problem

Best of luck

---

### Post by shrimants on 2006-01-25
yes, two hard drives, the original has i think 50 gb total. the xbox one is 10 gb total. i used some special tools i had to unlock it, and then used windows to reformat. im trying to install just the base system now. is there a way to boot windows to the last working condition? and also, where do i set everything from auto to LBA? in my BIOS?

---

### Post by shrimants on 2006-01-25
its stuck at 41% during the setiing up of disk partictioner. the proces says scanning drives.

---

### Post by scole on 2006-01-25
Here you go as long as you didnt screw with your windows partition this will work. Use the directions at my thread here to remove ubuntu completely and start over you should be able to go right into windows form there. If you remove all the linux partitions and it still dosent work disconnect the Xbox Hdd and try again. Heres the link for my thread on how to fix this [http://ubuntuforums.org/showthread.php?p=634214#post634214](http://ubuntuforums.org/showthread.php?p=634214#post634214)

---

### Post by scole on 2006-01-25
Also just a tip if you want to play it safe take out your hard drive with windows on it and pop it to a slave and put it in another computer preferably one with a dvd or cd burner or you could copy the the hdd of the computer you put it in. This is the safest way to play around and try to fix everything so you wont lose everything.

---

### Post by HJThis on 2006-01-25
Hey,scole

Wow just had to say a big thank you this
is sweet downloading as i click :)

Best of luck

---

### Post by scole on 2006-01-25
Can never say no to a pat on the back :) lol Works great doesn't it? It saved my skin when I found it out.

---

