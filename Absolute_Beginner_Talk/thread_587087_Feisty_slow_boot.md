---
title: "Feisty: slow boot"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2007-10-22
Since upgrading from Edgy to Feisty on 29 August, I have very slow bootup.

About 3 minutes from boot screen to login screen...

This is an oldish desktop with AMD Athlon XP 3000+ 2.16GHz & only 256Mo RAM.

I am dual booting with XP SP and that takes about 35seconds from boot to login.

I went through several threads with similar titles, but did not see any obvious thing to try. (There was a reference to dual booting & FAT32 but I couldn't find that one).

I would very much appreciate any "absolute beginner-level" advice.

Thanks in advance!

---

### Post by Pumalite on 2007-10-22
Gnome and KDE are pretty heavy for your system. With 256 MB of RAM I'd go with Xubuntu.

---

### Post by Daveth on 2007-10-22
which lives here

[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by sailor2001 on 2007-10-22
gksudo gedit /boot/grub/menu.lst    change timing to a second or 2 and then save

---

### Post by 2CV67 on 2007-10-23
Thanks for those suggestions.

My menu.lst timeout is only 3 seconds, so I don't think that is my problem.

I will certainly look at Xubuntu - is this just a light-desktop version with all the other functionalities of Ubuntu?

Nonetheless, I am surprised that Feisty takes 3 minutes to boot when "bloated" XP does it in 35 sec on the same machine.
I thought much of the appeal of Ubuntu was that it would outperform XP on any given platform?
Edgy did not take so long (no figures).
Surely this points to a problem somewhere?
Or is Ubuntu progressively bloating up too? (To be avoided at all costs!)

Thanks again!

---

### Post by emredmrl on 2007-10-23
I have the same slow booting problem. But when I turn the wireless switch off,it takes less ubuntu to boot. I think it has got something to do with wireless drivers.

---

### Post by Romin-1 on 2007-10-23
I think one point that was overlooked is that Windoze is only booting a dozen or so services whereas Linux is booting the entire operating system.

Correct me if I'm wrong fellas,

Jon

---

### Post by 2CV67 on 2007-10-23
emredmrl: Last year with Edgy I had & fixed a problem of "Slow Boot & Slow Opening of Applications with Internet connexion"

[http://ubuntuforums.org/showthread.php?t=323151](http://ubuntuforums.org/showthread.php?t=323151)

Now with Feisty the Internet connexion does not make any difference.

---

### Post by 2CV67 on 2007-10-23
Installed & ran bootchart (attached).

I can't interpret this very well, but it looks as though the main time delay is in checking file system...

Help?

---

### Post by 2CV67 on 2007-10-23
Switched to Xubuntu (by installing Xubuntu Desktop via Synapt...) but no difference to boot time, still over 3 minutes.

Can anybody suggest what is happening on the bootchart from the previous post?

Thanks!

---

### Post by Pumalite on 2007-10-23
As far as I can tell, the OS is looking for a piece of your hardware that at the end, doesn't find and only then starts loading your system. So the question is: is everything working properly in your system?

---

### Post by Qwerty_ on 2007-10-23
[http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

Don't know if that will help you.

---

### Post by 2CV67 on 2007-10-23
I removed the "quiet splash" items from menu.lst but the boot time still stays over 3 min.

On the other hand, after it says "checking file systems" it now shows 2 lines about "Wireless...INIT failed & ...SCANNING failed" which stay there for a long time before activity resumes, so I suppose my problem is there somewhere?

The WLAN is working though, as soon as I sign on.

I am out of my depth here...

---

### Post by sugarland2k on 2007-10-23
Add some memory if you can.  The best single way to increase performance on a PC for minimal cost.  Minimum 256 MB of RAM is absolute minimum required to run the desktop install CD for Ubuntu and at least 320MB of RAM is mentioned in some areas.  Your PC will thank you.

Good luck

---

### Post by 2CV67 on 2007-10-24
I am looking at doubling the memory, in spite of the fact that one of the reasons for shifting to Ubuntu was to avoid having to upgrade my old PC... (sigh!).

But back to my slow boot problem (see bootchart in post #9) - does this really look like a RAM problem or is it, as I suspect, something else, specific, that will still be there after a RAM upgrade?

Thanks for any pointers!

---

### Post by hyper_ch on 2007-10-24
> **sugarland2k said:**
> Add some memory if you can.  The best single way to increase performance on a PC for minimal cost.  Minimum 256 MB of RAM is absolute minimum required to run the desktop install CD for Ubuntu and at least 320MB of RAM is mentioned in some areas.  Your PC will thank you.

Good luck

Actually it's 64 MB for xubuntu ;) and I think even less for DSL

---

### Post by realvz on 2007-10-24
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by overlord_david on 2007-10-24
I have a slow boot too. 

But it's probably just because my computer is 7 years old. I have 1.8GHZ processing, over 600RD Ram... But unfortunately its a dell. >_> 8100

On top of that it seems I'm unable to get my GeForce 2 to work. So no games at all for me. ;_;

But anyway you guys, how do you post a new topic? I see no option anywhere.

I wanted to post a topic asking what you have to do to change the alert sound effects on Pidgin 2.2.1 
What I had before Pidgin 2.0.0 made perfectly hearable sounds. But now that I've deleted it and replaced it. All I get is a tiny console beep, which I can't hear at all pretty much. T_T;

---

### Post by hyper_ch on 2007-10-24
7 years ago there were no 1.8 Ghz computers ;)

---

### Post by overlord_david on 2007-10-24
Yes there was.

Its a Dell 8100 1.8 GHZ pentium 3. It was built in 2000 and came with the worst OS in the history of Microsoft.

---

### Post by 2CV67 on 2007-10-24
To make a new post - use the "Make New Post" button.... ;)

Getting back to my slow boot problem, what can I use to diagnose where the problem is?

As I said previously, things seem to get hung up after 28 seconds with lines saying:
ubuntu/wireless/at76/at76c503c:2522:asserting dev > istat ==INIT failed
& as above but :2492: & ==SCANNING failed

These stay an the screen for a long time, then things get moving again OK.

What can I use to dig deeper here?

Thanks

---

### Post by 2CV67 on 2007-10-24
I see that the File System Scan should only occur every 30 boots, whereas mine occurs every time, which maybe explains a lot.
I suppose I could put up with a 3 minute boot one time in 30 but not every time!
Does this match the bootchart in post #9?

I also see that it should only occur more often after a "dirty" shut-down, whereas all mine are "clean" as far as I know.

Suggestions please?

Thanks

---

### Post by 2CV67 on 2007-10-24
I tried installing AutoFsck which should shift the file scanning from boot to shut-down, with option to skip.

First shut-down, it checked all the files (3 or 4 minutes) and next boot was 45 sec instead of 3 min, which looked like some progress.
Subsequently however, shut downs were quick but boots were back to 3 min, mainly scanning hda1.

Any explanations?

Next I got into fstab & changed the last entry in the hda1 line from 1 to 0.

Now I have 45 second boots every time, which is OK for me.

I notice it is still "checking file systems" at every boot, but it skips hda1.

I don't need to go any further than that, but I would like to know why it is deciding to check file systems every boot.
I guess that suggests something wrong somewhere?

---

### Post by P4man on 2007-10-24
Im just guessing here.. do you have a FAT32 or NTFS partition that is "dirty" (not properly shut down) ? Try booting windows and chkdsk your disks. Shut it down nicely, then retry ?

---

### Post by 2CV67 on 2007-10-24
Thanks for the suggestion.
I have not had any "dirty" shut-downs recently, but I did run checkdisc on my Windows C disc & External HD.
They both showed OK.
Shut down was normal.

Booting to Ubuntu still 42 seconds (which is OK for me) & still briefly showing "Checking File Systems"

Is there some place I should be able to see a marker for whatever is triggering the checking?

---

