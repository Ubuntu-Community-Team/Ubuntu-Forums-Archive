---
title: "Howto ?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by hianddry on 2007-11-15
I should be grateful for ultra basic advice.
A friend of a friend recently installed a new hard disc on my ancient P3M 450/288MB laptop; reinstalled Win 98se and then, I thought Xbuntu .[in order that I could try it before possible transition]
Switching on, I got a boot sequence for  v8.10 Kernel, recovery, 86 ?, other OS and 98se.
Selecting the former takes 60-75 minutes to boot up - into a blank screen xbuntu !!.
There are no icons and both the bottom left buttons dont work.The only way I have found to escape is switch off. !!
Any venture into X/Ubuntu results in a complete re-installation of 98se, but neither of us knows how to remove/rectify the buntu installation.
I am told it was all installed from a/the CD - which I have
Any help would be appreciated

---

### Post by alienexplorers on 2007-11-15
Try booting into recovery mode.  Login and hopefully you will get a prompt simular to a dos prompt.  At that prompt type in:
> sudo dpkg-reconfigure xserver-xorg
select the basic options given and then when you are done reboot.
Hopefully It will load xubuntu for you.

---

### Post by hianddry on 2007-11-16
> **alienexplorers said:**
> Try booting into recovery mode.  Login and hopefully you will get a prompt simular to a dos prompt.  At that prompt type in:

select the basic options given and then when you are done reboot.
Hopefully It will load xubuntu for you.

Thank you very much, before I start yet another precautionary backup etc can you give me guidance on the following

The current 1 hour+  boot time fo "buntu"
 [a review of the "big" distros stated a P2 400/128Mb system was adequate for each - so my ancient laptop should,on that basis, be able to cope with either X/Ubuntu]

completion afterwards 
what is/are the commands to be entered afterwards, in order to  leave recovery and reboot.

The future
As I have been left alone to resolve the above problems; and to future understand buntu s elementarty workings I have  been searching for a  relevant book. 
Can find nothing on Xbuntu - will Ubuntu books, of which there are several, cover cover the generalities of using/operating X or are they completely disimilar ?? 

Sorry to show my utter ignorance but I am currently in it up to my neck !!
Thanks foryour time

---

### Post by mali2297 on 2007-11-16
> **hianddry said:**
> 
The current 1 hour+  boot time fo "buntu"

When boot up starts, press CTRL-ALT-F1. You should then be able to view messages as the boot up process proceeds. Can you determine at which stages the process seems to get stuck?

> 
completion afterwards 
what is/are the commands to be entered afterwards, in order to  leave recovery and reboot.

This should be enough in recovery mode:
```

reboot

```
Otherwise,
```

sudo reboot

```

> 
The future
As I have been left alone to resolve the above problems; and to future understand buntu s elementarty workings I have  been searching for a  relevant book. 
Can find nothing on Xbuntu - will Ubuntu books, of which there are several, cover cover the generalities of using/operating X or are they completely disimilar ?? 

Some of the GUI tools differ, otherwise they are similar.

---

### Post by meindian523 on 2007-11-16
please use an appropriate title for the thread.....

---

### Post by hianddry on 2007-11-16
Sorry do not understand your message
The OS was previously stated; I have had another OS installed - that on face value is not what I expected and neither of which I currently know the slightest thing about; It refuses to load and corrupts win 98se each time I attempt to boot into it; I dont know how to either rectify or remove it  and finally have been left to find my own solution.
Under these circumstances the thread title seemed the most
appropriate                        
Regards

---

### Post by hianddry on 2007-11-16
Thank You Alienexplorer and Mali for your help

Using both your info I now have the recovery failure message

"mount special device/dev/disk/by-uuid/4CBO-A9BD does not exist" 

whatever that means, it still wont work
Regards

---

