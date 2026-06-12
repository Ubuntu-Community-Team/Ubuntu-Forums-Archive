---
title: "Unable to resize NTFS (Windows) partition"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by quicksilver1024 on 2007-06-16
I'm getting this error message when I try to resize my Windows partition to make room for Ubuntu:

"check filesystem on /dev/sda1 for errors and (if possible) fix them"

Is it basically telling me to run CHKDISK? Is there such a thing without having to boot into Windows or going into DOS?

Thanks.

---

### Post by overdrank on 2007-06-16
> **quicksilver1024 said:**
> I'm getting this error message when I try to resize my Windows partition to make room for Ubuntu:

"check filesystem on /dev/sda1 for errors and (if possible) fix them"

Is it basically telling me to run CHKDISK? Is there such a thing without having to boot into Windows or going into DOS?

Thanks.

Hi boot to windows and run scandisk to fix the errors and then try to install again.:popcorn:

---

### Post by quicksilver1024 on 2007-06-16
I was afraid you'd say that.

Okay...going to do that now :)

---

### Post by overdrank on 2007-06-16
> **quicksilver1024 said:**
> I was afraid you'd say that.

Okay...going to do that now :)

Sorry ;)

---

### Post by bren on 2007-06-16
and then run defrag twice

it'll take a few minutes but trust me its faster to do it now :)

bren

---

### Post by quicksilver1024 on 2007-06-16
I've already run defrag a bunch of times before I ran chdsk, so do I still have to run defrag again? I am running o&o defragger btw (commercial software).

Bad news, I tried to resize again and it doesn't work. Same error message:

"The following operation could not be applied to disk:

Resize /dev/sda1 from 74.52 GiB to 34.18 GiB

See the details for more information"

HELP! I want to finish installing it today :(

---

### Post by quicksilver1024 on 2007-06-16
I read some threads and some people were getting the same problem as I did (though they did not specify what kind of error message they received).

I will try to burn the Gparted LiveCD and work off of that. Hope this works!

---

### Post by quicksilver1024 on 2007-06-17
Okay. I have managed to install Ubuntu with my partitioning plan. However, the problem was that there were bad sectors on my HD and thus the windows partition couldn't be resized. I have used the resize with bad sector option and it worked fine.

After I have installed Ubuntu and have restarted, GRUB worked perfectly but once Ubuntu was selected to run. It hangs after a few seconds on the loading screen. After, the screen shows a MS-DOS like interface (is this the terminal?) and after a few lines that scrolls too quickly to follow, I am asked for user name and password. I type it in (same as what I had done during the install) but it says permission denied (or something on those lines since the screen scrolled too quickly to follow).

Can someone please help me?!

I'm almost there!

---

### Post by quicksilver1024 on 2007-06-17
I have tried the noapic option and it didn't work. Then, I removed quiet and splash from kernel so that I could get a clearer understanding of what was happening behind the loading screen.

I get this warning many times throughout the loading:

warning: fake start-stop-daemon called, doing nothing

Here are a few lines just before the loading hangs:

*Starting deferred execution scheduler atd
warning: fake start-stop-daemon called, doing nothing

*starting periodic command scheduler crond
warning: fake start-stop-daemon called, doing nothing
.
.
.
.
*Running local boot scripts (/etc/rc.local)

The last line seems to last indefinitely....


Any help would be appreciated :(

Thanks.

---

### Post by meborc on 2007-06-17
you had bad sectors on you hdd... maybe those bad sectors are playing a part in this? sorry for not helping...

---

### Post by quicksilver1024 on 2007-06-17
mmm...so I have to buy a new HD? 
T__T

---

