---
title: "&quot;Laptop Lid Closed&quot; message on start-up"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Hammock on 2007-04-07
Hi All, 

I am getting up and running with Kubuntu Edgy on my Dell 700m laptop (in a dual boot set-up with XP-Home).  

I am receiving the message, "Laptop lid closed" after start-up and login, right around the time that the desktop has finished taking shape (at the same time that I receive a message about whether I am running on battery power or AC power).  As you might expect from the fact that I am asking for your help, the laptop lid is actually not closed when I receive this message.

I have recently run (today) apt-get dist-upgrade to get the latest versions of whatever might be causing the problem, but have seen no change.  

As a work-around, I set my power management options so that closing the lid no longer causes the machine to suspend or hibernate.  So, I am able to function.  However, I would still like to correct this problem.

Does anyone have any ideas?

Thank you in advance!

-Andy.

---

### Post by madmax69 on 2007-04-07
I have a Medon MD 95400 that is doing the same thing not sure why any help for us would be apreciated

---

### Post by Hammock on 2007-04-07
Hi all, 

I have been digging for a little more information, and found the following log entry from my most recent start-up:

04/07/2007 06:34:57 PM	mashurubu  kernel  [17179603.516000] ACPI: Lid Switch [LID0]

Does that tell us anything?  

Is ACPI a program which is not getting along with my hardware?  Does the series of numbers give me something to look for? 

Thanks, again!

-Andy.

---

### Post by barbeerian on 2007-04-09
I also have a 700m that is running perfectly except for that exact same problem.

If you need help with anything else, on that system, let me know.

If anyone can shed some light on this lid issue for us, it would be great.

---

### Post by dany_r50 on 2007-04-18
I have the same problem with a Samsung R50 (centrino) laptop. I'm not so worried about it just now but if some day I were able to get my computer suspended or hibernated with Ubuntu Edgy (nowadays it doesn't do it) I would be interested on having this bug solved.

---

### Post by fatmano on 2007-04-18
I am getting the same thing, and have done some digging and on my Compaq x6000 there is a file called state in /proc/acpi/button/lid/LID0 it reads :
state:    closed

I tried to sudo edit it but it wont let me save the file to make the state open.  I tried chmod'ing the file and the directory but was still unable to alter it.  Any thoughts from anyone?

---

### Post by su99 on 2007-05-02
This might help (or not), but doesn't hurt to try:

[http://ubuntuforums.org/showthread.php?t=406250](http://ubuntuforums.org/showthread.php?t=406250)

Basically I had the same issue on dell 710m (not that diff than 700m). The lid state is wrong, so even if I set "close lid to suspend", it doesn't work. However, after close and open the lid once, the lid state is correct and the next lid close will correctly suspend. Then it works every other time and fails every other time.

My solution worked well on my 710m to fix it.

---

