---
title: "How to enable ATI Graphics card in Gnome 3 (Mint 12)"
date: 2012-01-22
forum: Any Other OS
---

### Post by azertyfred on 2012-01-22
Hi

I have a ATI Mobility Radeon HD 5650 switchable graphics card in my HP laptop. At this moment, the 'weaker' Intel graphic card (it is switchable..) is activated and I try to find a way to activate the 'better' graphic card (ATI Radeon)? How can I do this? 

You can see that the IGD (integrated card, which is the Intel card) is activated and powered on (+), the DIS (discrete graphics, more powerfull) is turned off:

fred@fred-HP-Pavilion-dv6-Notebook-PC ~ $ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
[sudo] password for fred: 
0: IGD: + : Pwr:0000:00:02.0
1: DIS: : Pwr:0000:01:00.0

Thx in advance

Fred

---

### Post by Perfect Storm on 2012-01-23
Moved to Other OS/Distro Talk.

---

### Post by azertyfred on 2012-01-24
anyone? thx in advance.

---

### Post by rojaasensei on 2012-01-24
I'm in the same perplexing situation on Ubuntu 11.10 with the Lenovo G770

---

### Post by mips on 2012-01-24
vgaswitcheroo?

[http://forums.mydigitallife.info/threads/24483-Switchable-Graphics-Ubuntu-10.10](http://forums.mydigitallife.info/threads/24483-Switchable-Graphics-Ubuntu-10.10)
[http://forumubuntusoftware.info/viewtopic.php?f=69&t=5785&sid=9659a0581fd0d8d5c410b50b4edd2024](http://forumubuntusoftware.info/viewtopic.php?f=69&t=5785&sid=9659a0581fd0d8d5c410b50b4edd2024)

You would probably find similar info on the ubuntu forums if you searched.

---

### Post by rojaasensei on 2012-01-24
[http://forums.mydigitallife.info/threads/24483-Switchable-Graphics-Ubuntu-10.10](http://forums.mydigitallife.info/threads/24483-Switchable-Graphics-Ubuntu-10.10) has been read before.  Step one fails when I enter 
sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switchhttp://

It produces the message "bash: /sys/kernel/debug/vgaswitcheroo/switch: Permission denied"

---

### Post by mips on 2012-01-24
Try: echo OFF | sudo tee /sys/kernel/debug/vgaswitcheroo/switch

---

### Post by rojaasensei on 2012-01-24
> **mips said:**
> Try: echo OFF | sudo tee /sys/kernel/debug/vgaswitcheroo/switch

no response from terminal. Terminal will not accept any further input from keyboard

---

### Post by azertyfred on 2012-01-25
I also read about the vgaswitcheroo on other forums, but it doesn't seem to be the solution for this problem.

---

### Post by azertyfred on 2012-01-26
I was wondering if this is a problem only related to Gnome 3 (Mint 12). Because if this problem can be solved by installing another distro, that would be a fine solution. Is there another option?

---

### Post by hhh on 2012-01-26
Have you tried this?...
[http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-problems-with-ati.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-problems-with-ati.html)

---

### Post by azertyfred on 2012-02-11
Sorry for the late response, I've been searching for a solution for this problem but not too much progress so far..
I've installed PinguyOS instead of Mint 12 and the graphics are ok, but still the intel card is in use instead of the ATI. The HDMI cable don't work and I have a kill screen now and then.
I'm not sure the fix in the link mentioned above is about switchable graphics.

---

### Post by azertyfred on 2012-11-06
Hi there, I finally got the solution for this problem. It is vgaswitcheroo that you need for fixing this problem. I also had permission denied error messages when entering the ECHO or the DDIS command. Also when I started with the command:

grep -i switcheroo /boot/config-2.6.*

I got an error message. You should start with the command:

grep -i switcheroo /boot/config-`uname -r`

which should return 'CONFIG_VGA_SWITCHEROO=y'. All instructions are very well explained in this thread:

[http://doc.ubuntu-fr.org/vga_switcheroo](http://doc.ubuntu-fr.org/vga_switcheroo)

It's a french forum thread, so you should translate the page if you don't understad French.

Also very important: before proceeding to any commands in terminal enter first:

sudo -s

which gives root access to all commands that follow afterwards. If you don't do this, you will get root access message errors.

If it's not clear, please contact me for further details. I'm very happy I got it to work, it's been more than a year that I'm searching for this solution..

Also, when I activate the more powerfull graphic card I get my HDMI cable to work. Before this fix I couldn't use HDMI because it needs the ATI card and not the integrated (Intel) one.

Good luck!

---

