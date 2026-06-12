---
title: "error 13 - invalid or unsupportable executable format"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by dougoh on 2007-02-27
Hi, 

Can you help me or direct me to someone who can help ?  Below is a posting that I made last Friday, 23 Feb.  I only got 1 reply, listed at the end.  

I am using a friends computer, please send any response to     [email]dougoh@yahoo.com[/email]

Thanks,       Doug

**********

Hi,

I have Win XP and Ubuntu installed on my hard drive in separate partitions. It worked for several months, as I learned Ubuntu. 

About 4 days ago, the date / clock would be way off when I logged into XP. I changed the motherboard battery and the clock seemed to function, but the date did not update from day to day.

About 2 days ago, when I logged into XP, the system would not open any applications. I forget the error message generated. I shut down the computer and restarted it. When I got to the screen the GRUB generates to select the operating system, I could scroll to XP. When I hit return, I immediately get "ERROR 13 - Invalid or unsupported executable format".

I still need to have XP available, as I do not have a dialer that is compatible with Linux.

What have I done and how do I undo whatever happened ?

Thanks, Doug

++++++++

Here is the only reply that I have gotten from my posting on Fri, 23 Feb. - I do not understand the suggestions !

Re: error 13 - invalid or unsupportable executable format

I my opinion u have corropted ur windows installation and i always reinstall it in this case. the reinstalling GRUB is no problem and linux + windows will again there side by side. ur clock problem i could not understand why it is. may be some hardware problem.

---

### Post by rccharles on 2007-02-27
> **dougoh said:**
> 
Re: error 13 - invalid or unsupportable executable format

I my opinion u have corropted ur windows installation and i always reinstall it in this case. the reinstalling GRUB is no problem and linux + windows will again there side by side. ur clock problem i could not understand why it is. may be some hardware problem.

Perhaps your Master Boot Record (MBR) was corrupted.  You can get around a MBR problem by using superGrub.  You should be able to use superGrub. It doesn't use the MBR to boot Windows or any other partition. 

An option would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org...on=screenshots](http://supergrub.forjamari.linex.org...on=screenshots)

You cursor down to the line you want.

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.

I wrote superGrub out to cd and it worked for me. You can boot your partition even without grub on the partition.

This wouldn't be a permanent solution, but it would get you started.


Robert

---

