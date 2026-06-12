---
title: "Continuous iSight Problem (MacbookPro5,5 running 10.04 Lucid)"
date: 2011-02-01
forum: Apple Hardware Users
---

### Post by Anon7-2521 on 2011-02-01
I have a mid-2009 13" MacBook Pro (5,5) running Ubuntu 10.04 Lucid Lynx. I've been having this problem for some time now.

EVERY TIME I restart or shut down the computer and then restart it, my iSight does not work. In order to fix it, I have apt-get install isight-firmware-tools, reboot then apt-get remove isight-firmware-tools and then reboot again. I have no idea why this keeps happening or how to fix it. Has anyone else had this problem? Thanks.

Anon7

---

### Post by Anon7-2521 on 2011-02-08
BUMP

Anyone?

---

### Post by ronbirrell on 2011-02-10
Please check this reply I posted a few weeks ago resolving this problem on my mbp 5.5

[http://ubuntuforums.org/showpost.php?p=10343126&postcount=17](http://ubuntuforums.org/showpost.php?p=10343126&postcount=17)

Regards
Ron

---

### Post by persofit on 2011-02-13
Hello, 
I am new to Linux and also have the same problem on my iMac intel 2 core the same built-in webcam problem and tried this fix, all went good until I got to the install AMD folder part (it wouldnt install) so I tried to install the i386 folder that installed ok but the webcam still doesnt work. 
any ideas?
Thanks so much.
Michael

---

### Post by Anon7-2521 on 2011-02-15
> **ronbirrell said:**
> Please check this reply I posted a few weeks ago resolving this problem on my mbp 5.5

[http://ubuntuforums.org/showpost.php?p=10343126&postcount=17](http://ubuntuforums.org/showpost.php?p=10343126&postcount=17)

Regards
Ron

No offense, but did you even read my post? The iSight firmware tools aren't working. 

If anyone has an actual fix, that would be great.

---

### Post by ronbirrell on 2011-02-17
No offence taken.  Yes I did read your post.  You stated you did an apt-get install isight-firmware tools, which installs an outdated version.  Nowhere did you state that you downloaded the isight-firmware-tools from the mactel link i gave.  Isight would not work for me with the default ift which ubuntu installed on my mbp 5.5, but did so after upgrading to the version from the link mentioned.  If you have indeed installed the ift from the mactel link after following the other steps i listed in my post, and it is still not working, then I don't know the answer.

---

### Post by agestrada on 2011-02-24
I'm having the same problem. Installed the new driver and still have issues after suspending or restarting the laptop.

Check links below to get a clearer idea and find a fix:

[HTML] http://bersace03.free.fr/ift/[/HTML]
[HTML] https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight[/HTML]

---

