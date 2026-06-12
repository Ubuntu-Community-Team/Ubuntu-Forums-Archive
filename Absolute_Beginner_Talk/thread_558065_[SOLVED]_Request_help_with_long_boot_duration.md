---
title: "[SOLVED] Request help with long boot duration"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by m9ke on 2007-09-23
I am seeing very long boot times as a result of powering down my system with the power switch.  

Here is the story:
 - Tried to Hibernate (desktop, Feisty) by clicking Hibernate in the Shutdown Screen.
 - Could not un-Hibernate because lost all display
 - Space bar, tab, return, arrow keys and mouse clicks did not make the system responsive.
 - Had to power down system with power switch.
 - Now, here is what I see after pressing the Power button:

1. Screen requesting I press F1
2. Screen telling me Grub in loading
3. Ubuntu screen with progress bar-no disk activity audible; wait about 2 minutes
4. After about 2 minutes audible disk activity and progress bar proceeds normally
5. About 40 seconds later login screen appears.

The symptom of the problem is the lengthy duration of #3 above.  Can anyone suggest a way to improve this situation?  Something is not right!

---

### Post by cmnorton on 2007-09-23
If you having to force the system down, your long boot time might be due to a forced file system check. Run dmesg and look at /var/log/messages. Running dmesg will provide boot messages, and /var/log/messages might give you a clue as to what is happening during hibernation and after.

---

### Post by st33med on 2007-09-23
It could be that your network card is scanning for networks. To prevent it from doing that:
```
sudo gedit /etc/network/interfaces
```
And comment out every line except for lines with 'lo' by adding a '#' before each line.

Keep that file written down in case wireless/Ethernet doesn't work.

---

### Post by st33med on 2007-09-23
Also, you might want to [follow this HOWTO]("http://ubuntuforums.org/showthread.php?t=471855").

---

### Post by m9ke on 2007-09-23
cmnorton, thanks for your reply!  Ran dmesg and got many lines of output, maybe too many to post here.

One interesting one is
```
[  145.654024] PM: Resume from disk failed.
```

Is there anything specific I should look for in the output of dmesg?

wrt: /var/log/messages
Same story, massive output.  Anything specific I should look for?

I only attempted Hibernation once; had to hard shutdown after that one try.  Shut down works normally now.  The only issue is the long booting.

---

### Post by st33med on 2007-09-23
Look at my last post.

---

### Post by m9ke on 2007-09-23
st33med, sorry I missed your post.  It looks like we were both posting to this thread at about the same time.

Anyway, this long boot problem happened immediately after I shut the computer off with the power switch instead of the normal way.  

My theory is that this hard shutdown caused (or is related to) the sudden appearance of the long booting problem.

Do you think shutting down the computer with the power switch instead of the proper way might cause my NIC to start scanning more than it would if I had shut down normally?

---

### Post by m9ke on 2007-09-23
It was time for a fsck when I just restarted.  Here are the logs:

From /var/log/fsck/checkroot
```
Log of fsck -C -a -t ext3 /dev/sda1 
Sun Sep 23 19:03:16 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sda1: clean, 126654/2403744 files, 827801/4803427 blocks

Sun Sep 23 19:03:16 2007
----------------
```

From /var/log/fsck/checkfs:
```
Log of fsck -C -R -A -a 
Sun Sep 23 19:03:16 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1: clean, 5462/61063168 files, 21141728/122096000 blocks

Sun Sep 23 19:03:16 2007
----------------
```

These logs look pretty uneventful to me. sda1 is my boot disk; sdb1 is a separate physical hard disk where I keep data.

Plus, after this fsck completed  the part of the boot process I describe in my original post (item #3) decreased in duration from about 2 minutes to about 30 seconds.  I rebooted again and confirmed that the #3 item in the boot process went from about 2 minutes to about 30 seconds.

This is what I observed, but I don't know *why* the boot duration got shorter.  I don't know what the options listed in the fsck logs do (-C -a -t in /var/log/fsck/checkroot) and (-C -R -A -a in /var/log/fsck/checkfs).  

Because the symptom of 2 extra minutes boot time (well, 1.5 minutes extra) happened every time before the fsck and went away immediately after I am tempted to think some kind of repair was done.

Even though the immediate symptom seems to be gone, I would be interested to learn why this happened the way it did.  

Anyone?

---

### Post by m9ke on 2007-09-24
Did some searching on the web, and decoded the fsck options.  Here is what I found:

From /var/log/fsck/checkroot (this is my boot drive):
```
Log of fsck -C -a -t ext3 /dev/sda1
```
These options mean:
-C means display completion bars.  Yup, saw that.
-a means automatically repair filesystem without user interaction.  Yup, this is probably why my boot duration went down.
-t specifies the type of filesystem to be checked.

From /var/log/fsck/checkfs (this is my second hard drive):
```
Log of fsck -C -R -A -a
```
-C means display completion bars.  Yup, saw that.
-R     tells fsck when checking all file systems with the -A flag, skip the root file system (in case it's already mounted read-write). 
-A  tells fskc to walk through the /etc/fstab file and try to check all file systems in one run.
-a -a means automatically repair filesystem without user interaction.

Got this info at [http://maconlinux.net/linux-man-pages/en/fsck.8.html](http://maconlinux.net/linux-man-pages/en/fsck.8.html)

Case closed.  File system(s) got repaired by fsck.

Cheers,
m9ke

---

