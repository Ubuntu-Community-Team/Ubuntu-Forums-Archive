---
title: "Firewall-Antispyware?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by especlipse290 on 2007-08-16
Is there need for any of it.

If so can someone tell me what to get

---

### Post by bodhi.zazen on 2007-08-16
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Steveway on 2007-08-16
There is an inbuilt firewall called iptables.
And you don't need things like antispyware or antivirus.
Welcome to the free and secure world.

---

### Post by Seisen on 2007-08-16
No, read these they will explain everything

[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

[http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security")

---

### Post by oilchangeguy on 2007-08-16
> **especlipse290 said:**
> Is there need for any of it.

If so can someone tell me what to get

ubuntu has a built in firewall, called iptables. 
and no need for any anti-spyware.

also there's probably hundred's of threads on this subject. before you post, go to the search box at the upper right of the page, and see if you can find what you are looking for. because if you have a problem/question, more than likely it's already been addressed.

---

### Post by heimo on 2007-08-16
> **especlipse290 said:**
> Is there need for any of it.

If so can someone tell me what to get

See this:
[http://www.psychocats.net/ubuntu/security#firewallantivirus](http://www.psychocats.net/ubuntu/security#firewallantivirus)

---

### Post by tashmooclam on 2007-08-16
I copied the below from the thread "Ubuntu testimonials and experiences" The sticky FAQ criticism post.
I actually think that this should be renamed and just called "Ubuntu FAQs" because I think it's very informative. 

*There is no antivirus/antispyware/defragmenter/registrycleaner!*

They simply are not needed.

While Viruses for Linux do exist, they are almost never seen in the wild, and are not nearly as destructive as their Windows counterparts. Linux inherits UNIX's user/privilege model which makes it very difficult for a given program to gain the kind of system-wide access that allows Windows viruses to propagate and damage the system. The worst that could happen, under most circumstances, is that a user's home directory might be compromised or deleted-- a concern, to be sure, but not nearly as big as catastrophic system failure. Likewise Spyware is literally unheard-of in Linux (we are not aware of any Linux spyware "in the wild" at this time).

Linux also does not employ anything like Windows' " Registry " to store configuration settings. Linux configuration files are usually user-readable and editable text files. Also, Linux filesystems are not prone to filesystem fragmentation in the same way that Windows filesystems (FAT32 and NTFS) are, so defragmentation is not an issue.

Just enjoy your system, Linux will take care of the rest.

*There is no firewall!*

The firewall (iptables) is built into the kernel, and if you need to run services that require a firewall you can install a program like Firestarter to simplify the firewall configuration. By default, however, an Ubuntu install does not listen for incoming network connections unless a user specifically configures it to. Out of the box, it is already more locked-down than a Windows box with a commercial Firewall.

---

### Post by bodhi.zazen on 2007-08-16
> **tashmooclam said:**
> 

*There is no firewall!*

The firewall (iptables) is built into the kernel, and if you need to run services that require a firewall you can install a program like Firestarter to simplify the firewall configuration. By default, however, an Ubuntu install does not listen for incoming network connections unless a user specifically configures it to. Out of the box, it is already more locked-down than a Windows box with a commercial Firewall.

Actually, out of the box IPTables are very permissive. This is OK because there are no open ports.

If you install server software you should configure iptables, check out the security thread that has been posted here and firestarter/guarddog

---

### Post by misfitpierce on 2007-08-16
Indeed firestarter for Ubuntu and Guarddog for Kubuntu is the way to go on editing the built in IPtables...

sudo apt-get install firestarter and so forth wiith the one you want.

---

### Post by Seisen on 2007-08-16
> If you install server software you should configure iptables, check out the security thread that has been posted here and firestarter/guarddog 

Firestarter and Guarddog are Gui based so it won't work for the server install.

---

### Post by floke on 2007-08-16
This whole 'any viruses would just wreck your home directory' attitude very strange. I can reinstall my system in 20 mins; but my /home ??? Now that would be a disaster.

---

### Post by oilchangeguy on 2007-08-16
given the low installed base of linux, verses windows. and the fact that each distro of linux is slightly different. someone would have to go thru alot of trouble to target one, or several distro's of linux. while there are different flavors of windows (xp) home, pro, media center. under the skin, it's still windows xp. and since 90+ percent of the worlds computers run a microsoft operating system. what's the biggest virus target?  i'm not saying it can't happen. but chances are veeeeeeeeeeeeeerrrrrrrrrrrry low that it will.

---

