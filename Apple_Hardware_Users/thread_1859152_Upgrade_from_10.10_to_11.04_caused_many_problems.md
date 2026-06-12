---
title: "Upgrade from 10.10 to 11.04 caused many problems"
date: 2011-10-13
forum: Apple Hardware Users
---

### Post by resuser on 2011-10-13
Hello,

I am a relatively new Linux user, and have recently installed Ubuntu on my Apple PowerBook G4 667 Gigabit Ethernet (Onyx) laptop. I had gotten Xorg configured, and everything was working well under Xubuntu 10.10 PowerPC. Last night I upgraded to 11.04, and since then I have been noticing some severe issues.

1) CPU usage is really high. A typical output from top follows:

Tasks: 142 total,   1 running, 140 sleeping,   0 stopped,   1 zombie
Cpu(s): 62.7%us, 35.3%sy,  0.0%ni,  1.0%id,  0.0%wa,  1.0%hi,  0.0%si,  0.0%st
Mem:   1023604k total,   398132k used,   625472k free,    50564k buffers
Swap:   860156k total,        0k used,   860156k free,   132724k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
17387 user      20   0 11796 4080 3312 S 18.5  0.4   2:34.72 gvfs-gdu-volume    
17397 root      20   0 16036 3936 3260 S 10.4  0.4   1:32.63 udisks-daemon      
  644 root      20   0  205m  34m 9604 S  9.4  3.5   0:45.16 Xorg               
  264 root      18  -2  3560 1036  428 S  9.1  0.1   1:49.87 udevd              
  388 messageb  20   0  4272 1632  876 S  6.5  0.2   0:54.84 dbus-daemon        
16928 user      20   0  107m  12m 9.8m S  3.2  1.2   0:23.18 xfce4-fsguard-p    
20078 user      20   0  117m  15m  11m S  3.2  1.5   0:01.74 xfce4-terminal     
16918 user      20   0 26384 9644 8092 S  2.9  0.9   0:25.91 xfce4-systemloa    
    1 root      20   0  3892 2024 1440 S  1.6  0.2   0:18.98 init               
16909 user      20   0 25120 8020 6652 S  1.6  0.8   0:23.30 xfce4-cpugraph-    
  240 root      20   0  3036  828  648 S  1.3  0.1   0:16.63 upstart-udev-br    
  251 root      16  -4  4224 1696  348 S  1.3  0.2   0:09.78 udevd              
    6 root      -2   0     0    0    0 S  1.0  0.0   0:11.59 rcu_kthread        
19144 root      20   0     0    0    0 S  1.0  0.0   0:00.39 kworker/0:1        
16896 user      20   0  106m 9580 6884 S  0.6  0.9   0:04.51 xfce4-power-man    
17532 user      20   0 27356 8384 6952 S  0.6  0.8   0:05.61 Thunar             
20465 user      20   0  3328 1380 1084 R  0.6  0.1   0:00.43 top                
user@user-laptop:~$ 

2) I notice two Bootstrap volumes sitting on my desktop. They are not in the fstab file, the contents of which are displayed below.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/hda3 during installation
UUID=9da8797f-d3e0-47b4-856c-4950c15d5fd7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/hda4 during installation
UUID=2a648e15-79db-4df5-95e5-7f56a82c4f26 none            swap    sw              0       0

Also, when I kill the gvfs-gdu-volume process, the Bootstrap volumes go away, but the CPU usage problem does not. It drops to about 70% and a never-ending supply of udev processes creep in to fill the #1 cpu usage spot. That is, I can kill them 'til the cows come home, but there is always a udev process eating ~10% CPU, and idle CPU usage hovers around 60%-70%.

3) I cannot switch to TTY1-TTY6. CTRL-ALT-F1 through CTRL-ALT-F6 yields a black screen each time. CTRL-ALT-F7 always brings me back to X.

Has anyone noticed similar issues? Is there any more information I can provide that would help diagnose these problems, tests I could run, etc? Thanks for your help!

---

### Post by rsavage on 2011-10-13
Your the third person I know of with this.  See the answer by axion on this post [http://askubuntu.com/questions/58488/x-does-not-want-to-start-at-all-no-screens-have-a-usable-configuration](http://askubuntu.com/questions/58488/x-does-not-want-to-start-at-all-no-screens-have-a-usable-configuration) .

---

### Post by rsavage on 2011-10-13
Don't know if this is your bug [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/780266](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/780266) .

---

### Post by resuser on 2011-10-13
Thank you for the reply, rsavage, but the link you posted is for an Xorg related problem, which I am not experiencing. X starts just fine, the problem is that I have no non-X terminals to log into.

Also, the bug report is not mine.

---

### Post by rsavage on 2011-10-13
Both links contain fixes (well workarounds really) for your udev problem.  Honestly, I don't know why I bother sometimes!

---

### Post by resuser on 2011-10-13
I'm not sure why you bother either. The workaround:

nano /etc/udev/rules.d/my.rules
KERNEL=="sr1", ACTION=="change", WAIT_FOR="nothing"

 in the bug report thread doesn't seem to have any effect, and the "sudo stop udev" workaround seems a little ham-handed, especially in light of this new piece of information I discovered about 5min ago:

Inserting a cd-rom into the drive causes idle CPU usage to fall to normal levels (~10%-20%). 

Any ideas why that might be? Is there a way to dig deeper to find out what udev is actually doing, and what it has to do with a CD being inserted?

The mystery of the missing TTY's and the fact that 11.04 deems it wise to mount my Bootstrap partitions remain.

---

### Post by rsavage on 2011-10-13
> **resuser said:**
> I'm not sure why you bother either. 
You seriously still expect help?

---

### Post by rsavage on 2011-10-13
Since this affects other people I continued to have a quick look into this. There are other bugs that have been reported against udev such as [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/801853](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/801853) . The reported fix in reply 1 is interesting because I've looked into hal polling before. There is a known problem with automounting with many mac drives. I thought this was maybe caused by hal polling being disabled. So I wonder if you have it enabled?
 
 
> **resuser said:**
> 
Any ideas why that might be? Is there a way to dig deeper to find out what udev is actually doing, and what it has to do with a CD being inserted?To monitor udisks try the command:
 
udisks --monitor
 
To monitor udev try either:
 
udevadm monitor 
udevadm monitor --environment
 
 
> **resuser said:**
> 
The mystery of the missing TTY's
I get bad corruption on TTYs under natty (i have a radeon card). Text is almost unreadable. Perhaps you have it worse? EDIT: you probably don't have the radeonfb framebuffer loaded anymore.
 
 
> **resuser said:**
> 
and the fact that 11.04 deems it wise to mount my Bootstrap partitions remain.
I remember it did this to me. I assumed it was something thunar did (is thunar the source of your problematic polling?). Let people know if you find the solution.
 
> **resuser said:**
> 
The workaround:
 
nano /etc/udev/rules.d/my.rules
KERNEL=="sr1", ACTION=="change", WAIT_FOR="nothing"
 
in the bug report thread doesn't seem to have any effect
That's because your cdrom drive is hdc not sr1.

---

### Post by rsavage on 2011-10-14
I've been thinking some more about what I said yesterday about the TTYs. Now I remember correctly, actually I only got corruption when I stopped the xorg server. Presumably there is some sort of switch in drivers/framebuffers at that point? 
 
What I do know is that in 11.04 kernel mode setting is turned off on my radeon card. In 10.04/10.10 it is turned on. So I reckon you could try either of these yaboot parameters:
 
radeon.modeset=1
video=radeonfb:1024x768-24@60 (or whatever resolution you want)
 
 
For your udev problem: If you can't find a solution then there is always an upgrade to 11.10. I notice it is out now.

---

### Post by Ms. Daisy on 2011-10-14
I've got 11.04 Xubuntu on my G4 Emac, rsavage has gone WAY out of his way to help me get this far (THANK YOU!)

I've got a bootstrap mounted on the desktop as well.  Xubuntu responds as quickly as molasses pours.

CPU info:
Tasks: 146 total,   5 running, 141 sleeping,   0 stopped,   0 zombie
Cpu(s): 77.8%us, 21.9%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    635500k total,   467068k used,   168432k free,    34564k buffers
Swap:  1687984k total,        0k used,  1687984k free,   204756k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                          
  688 root      20   0  316m  57m 7588 S 19.7  9.2   0:34.58 Xorg                                                             
17469 user  20   0  379m  72m  33m R 11.1 11.7   0:46.45 firefox                                                          
15471 root      20   0 16036 3936 3260 S 10.5  0.6   0:39.94 udisks-daemon                                                    
15585 user  20   0 11660 3952 3316 S  9.9  0.6   0:37.87 gvfs-gdu-volume                                                  
15258 user  20   0  128m  15m  11m R  7.3  2.4   0:28.40 update-notifier                                                  
  314 messageb  20   0  4428 1836  876 S  6.4  0.3   0:25.71 dbus-daemon         

Sounds to me like we're having the same problem.

---

### Post by rsavage on 2011-10-15
Fix? [http://ubuntuforums.org/showpost.php?p=11346831&postcount=56](http://ubuntuforums.org/showpost.php?p=11346831&postcount=56) 

Fingers crossed!

---

### Post by Ms. Daisy on 2011-10-15
> **resuser said:**
> Inserting a cd-rom into the drive causes idle CPU usage to fall to normal levels (~10%-20%). Any ideas why that might be? Is there a way to dig deeper to find out what udev is actually doing, and what it has to do with a CD being inserted? Amazing- mine did the exact same thing. So did you figure out the cause?  

And to weigh in on the ham-handed issue... I think the most ham-handed solution is to leave the CD in the drive and call it done, which is what I'm tempted to do.  :D

---

### Post by rsavage on 2011-10-15
Well I must say from unpromising beginnings this thread has made me learn a lot.

> **resuser said:**
> and the fact that 11.04 deems it wise to mount my Bootstrap partitions remain.

In the file /lib/udev/rules.d/80-udisks.rules is the rule

```

# Partitions which desktops should not display
#

# Apple Bootstrap partitions
ENV{UDISKS_PARTITION_SCHEME}=="apm", ENV{UDISKS_PARTITION_TYPE}=="Apple_Bootstrap", ENV{UDISKS_PRESENTATION_HIDE}="1"
```

An explanation of what this means is here [http://manpages.ubuntu.com/manpages/natty/man7/udisks.7.html](http://manpages.ubuntu.com/manpages/natty/man7/udisks.7.html)

So if you want to solve this you've got to work out if the boostrap partitions have actually been set to be hidden.  You can use the udisks --show-info command to do this.  Then it is a case of writing a new rule to do it in /etc/udev/rules.d or finding out why xfce/xubuntu is ignoring the attribute.  Hope this helps.

---

### Post by rsavage on 2011-10-16
More about xubuntu drive icons [http://ubuntuforums.org/showthread.php?t=1782823](http://ubuntuforums.org/showthread.php?t=1782823)

---

### Post by Ms. Daisy on 2011-10-16
I got the mounted bootstrap to disappear via the GUI as outlined in the above-linked thread:
> You are right,  they aren't mounted even when their icons show on the desktop. Even in  thunar the buttons show when they are unmounted unlike nautilus, It  certainly is different.

To get rid of all the icons, right click the desktop and in the menus  follow Applications > Settings > Settings Manager, look for the  icons tab. See the attached pics. :smile:

This is if you want to remove the icons altogether, they can be mounted and accessed easily in any thunar window side pane.
                                                                                                              Attached Thumbnails                                           [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=195191&stc=1&thumb=1&d=1308152551[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=195191&d=1308152551")    [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=195192&stc=1&thumb=1&d=1308152551[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=195192&d=1308152551")                        

If I'm understanding correctly, they aren't actually mounted. So hiding the icons solves it. Thanks!

---

### Post by rsavage on 2011-10-18
More on this annoying udev bug [https://bugzilla.redhat.com/show_bug.cgi?id=717249](https://bugzilla.redhat.com/show_bug.cgi?id=717249) .  It would be interesting to know if 11.10 solves this problem?  Not knowing enough about the kernel etc I don't know if the patches have made it into 11.10 or if they apply to the hard drives in old macs?

---

### Post by Ms. Daisy on 2011-10-18
> **resuser said:**
> Also, the bug report is not mine.
How do you know that? Have you tried the patch?

---

### Post by Ms. Daisy on 2011-10-18
> **rsavage said:**
> More on this annoying udev bug [https://bugzilla.redhat.com/show_bug.cgi?id=717249](https://bugzilla.redhat.com/show_bug.cgi?id=717249) . 
That bug report says that "This patch is present in the 2.6.40.3-0 update that [they] just pushed to updates-testing."  They tested it successfully and closed the issue.  So does that mean that if I run an update I will get the patch automatically?  Or is the patch only for redhat/fedora?  Or does this involve complex non-beginner-type stuff on my part? Sorry, they really make the bug reports impossible to read.

---

### Post by rsavage on 2011-10-18
@Ms Daisy I thought you had stopped for the moment?!  I wrote a longish reply to your other thread but accidentally closed the browser tab and lost it all!  Haven't got around to re-typing it!  

That bug report confirms what you've found.  Inhibiting polling through udisks doesn't work.

I still wonder if disabling polling through hal would work like in the other bug reports.  That is the only thing we haven't tried.

sudo apt-get install hal
sudo hal-disable-polling --device /dev/hdc

Reboot, see if it works.  If it doesn't you can remove it with "sudo apt-get remove hal".

I think resuser was answering that the bug report wasn't started by him?

Don't bother investigating applying patches.  V advanced and I don't know how to do it.  I would have thought they would have made it into 11.10 already.  So an update may work.

I thought I understood why this bug was happening, but the bug reports have got me confused too! hal, udev, udisks, kernel polling are all tied up like a snakes wedding.

You're doing a heroic job with your emac!  Ubuntu shouldn't be this hard!

---

### Post by Ms. Daisy on 2011-10-18
> **rsavage said:**
> @Ms Daisy I thought you had stopped for the moment?! I know, I was.  But I'm like a bulldog with a problem.  I just won't let it go even when it's abundantly clear that I should!  I saw that in the bug report they said that an update was created so I became hopeful that there was some easy fix out there.  But you're saying that there's no such fix in 11.04, or if there were I would have gotten it already, right?  Oh well. :(  I'm not sure that I want to upgrade to 11.10, I'm seeing a lot of complaints on the forum. I think you said (and I agree) it would be trading one set of problems for another.  

Well, I suppose I could try one last fix.  If you are willing to explain it, I could try disabling polling through hal.  

And if that fails (or if it's a workaround and not a solution) should I post on the bug report?  Do they want to know or care if other people are affected?

---

### Post by rsavage on 2011-10-18
You posted the same time that I edited the post with hal instructions (plus some other comments)!

I personally wouldn't stick a cd in my drive all the time.  Isn't it noisy?  So I think I would upgrade to 11.10 if it was me.  No major problems have been reported so far.

Don't bother with a bug report at the moment.  See if it works with 11.10 first.

---

### Post by rsavage on 2011-10-18
That's not to say install 11.10 right now.  Take a break from it!

---

### Post by Ms. Daisy on 2011-10-18
Hal had no affect on the machine#-o. > **rsavage said:**
> That's not to say install 11.10 right now.  Take a break from it! Yes, I'll be taking a bit of a break.  I'll try upgrading to 11.10.  Hopefully you won't hear from me until I've successfully got it running!!! And then I hope I'll be ANSWERING a few questions rather than asking.
Thank you SO SO SO SO SO much for your help. You are a gentleman and a scholar.  If you ever need a positive reference, send them my way.

---

### Post by Boris1975 on 2011-10-21
The high-CPU-usage-bug seems to be solved in 11.10.

---

### Post by rsavage on 2011-10-22
It's strange that Natty has been around for 6 months and yet apart from this thread there has only been one other report of this bug on the forum ([http://ubuntuforums.org/showpost.php?p=11254679&postcount=51](http://ubuntuforums.org/showpost.php?p=11254679&postcount=51)).  The only other thread I can remember referring to poor performance was this one [http://ubuntuforums.org/showthread.php?t=1840105](http://ubuntuforums.org/showthread.php?t=1840105), but the final post says xubuntu is running well.

So why is it that on other threads there are suddenly a lot of people referring to high CPU usage in Natty?!?!  Where have you all been?

It's been reported on those other threads that oneiric doesn't have the problem even when using the 'old' natty kernel.  So the patches in the bug reports can't be the fix?  Perhaps the new versions of gvfs, udev or udisks are the fix?  Am I missing something?

I note there were new versions of udisks and gvfs in natty at the start of September.  Were these the cause of people's problems?  That was 6 or 7 weeks ago so again, why haven't there been a deluge of threads on this in that time?

More feedback is needed about this.  It would be interesting to hear too from ppc natty users who don't have this bug.  Perhaps if you install it from cd or usb drive there is a difference or maybe it is just random?!

---

