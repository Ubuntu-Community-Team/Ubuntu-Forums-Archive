---
title: "Questions about using Ubuntu as a file server."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-10-15
Hi all,

I am contemplating re-structuring my home network and have a few questions about using Ubuntu as a file server.   I am currently using NasLite-2.06 a *nix based file server. While this option works it is limited on features.  Like the drives are SMART as is the controller, but no SMART under Naslite-2 for RAID, No security, etc.

1. RAID -  My current setup is a Dell Dimension 4550 2.84GHz pentium4 with 768 MB RAM, 4- 250GB Seagate Barracuda SATA-150 HDDs in RAID 5 via a LSI MegaRAID 150-6 Hardware RAID controller.  This controller is supported under the latest Kernel so I imaging it should work in Ubuntu? Would Ubuntu be loaded onto the RAID drive or should I install another drive for the OS.

2. I have 3 Ubuntu pc and 1 windoze laptop, so I would need to be able to share to windoze. Is this possible? I imagine it is.

3. I want to run headless, so remote admin is a must.

4. GUI is preferred is this possible? I am no CL guru though I could learn.:lolflag:

additional info:
currently have a wired network for Ubuntu, wireless for the doze laptop all through a Netgear ProSafe 802.11g VPN Firewall Router. Printer is a networked Brother 2070n. Need more info let me know and I'll post away!

Edit - one more thing - Power options -  Can you configure auto shutdown and autoboot at certain times?

Thanks

---

### Post by [S|G] on 2007-10-15
Hello,

I can't really help you with the hardware support questions, so let's head on to the others :)

2 - Yes, you can share to windows machines as well as other linux machines. You'll just need to create the share using samba. Since you prefer to use a GUI you have 2 choices:

A) Install Ubuntu as a normal desktop, open the nautilus file manage (gnome's default file manager), right click the directory you wish to share, choose "sharing" (or something like that) from the menu and choose "Windows Networks".

B) Install swat, which is a web configuration interface to samba. That way you can manage it using your webbrowser.

3 - You can use SSH and VNC if you wish to remote administer the server

4 - Look at question 2 answers ;)

5 - Yes, you can configure auto shutdown and autoreboot. You'll need to create a cron schedule. Take a look here for more info: [http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

EDIT: To turn on your computer automatically, you'll have to check your BIOS options. Usually it's called "RTC Alarm".

---

### Post by mramsey on 2007-10-16
> **'[S|G] said:**
> Hello,

I can't really help you with the hardware support questions, so let's head on to the others :)

2 - Yes, you can share to windows machines as well as other linux machines. You'll just need to create the share using samba. Since you prefer to use a GUI you have 2 choices:

A) Install Ubuntu as a normal desktop, open the nautilus file manage (gnome's default file manager), right click the directory you wish to share, choose "sharing" (or something like that) from the menu and choose "Windows Networks".

B) Install swat, which is a web configuration interface to samba. That way you can manage it using your webbrowser.

3 - You can use SSH and VNC if you wish to remote administer the server

4 - Look at question 2 answers ;)

5 - Yes, you can configure auto shutdown and autoreboot. You'll need to create a cron schedule. Take a look here for more info: [http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

EDIT: To turn on your computer automatically, you'll have to check your BIOS options. Usually it's called "RTC Alarm".

Sounds like what i'm after. Do you know where I can find out about the raid controller? I went to the lsi site and found drivers for suse and redhat .

---

### Post by hyper_ch on 2007-10-16
is it just you accessing it or also other people?

---

### Post by mramsey on 2007-10-16
> **hyper_ch said:**
> is it just you accessing it or also other people?

4 users in total. Not requiring access via the www. if that's what you mean.

---

### Post by hyper_ch on 2007-10-16
do you want the shared drive be permantently mounted on each computer? (e.g. in windows have always access to it as q: drive or so?)

---

### Post by mramsey on 2007-10-16
> **hyper_ch said:**
> do you want the shared drive be permantently mounted on each computer? (e.g. in windows have always access to it as q: drive or so?)

Yes, you've got the idea.

---

### Post by hyper_ch on 2007-10-16
too bad... otherwise the simplest solution would have been to install openssh-server ;)

You need samba in that case.

---

### Post by mramsey on 2007-10-16
> **hyper_ch said:**
> too bad... otherwise the simplest solution would have been to install openssh-server ;)

You need samba in that case.


Oh well nothings perfect:)...Do you know where I can reference the hardware issue? That seems to be my biggest question, if its not supported then I will leave it the way it is.

---

### Post by hyper_ch on 2007-10-16
no clue.. never used raid... probably never will use it ;)

---

### Post by mramsey on 2007-10-16
Update: OK so I did more research and forun this info at [[COLOR="yellowgreen"]Linuxmafia[/COLOR]]("http://linuxmafia.com/faq/Hardware/sata.html#sis-965l").  According to this my SATA Raid controller is supported in ubuntu.:)

> Ubuntu (or Kubuntu) Linux 5.04 "hoary hedgehog" and later's

The controller is supported in the linux kernel 2.4.x and later...

> (link) LSI Logic MegaRAID SATA 150-4 (four ports) and 150-6 (six ports) Serial ATA RAID Host Adapters — real hardware RAID. Work with 2.4.x kernel's megaraid2 driver (same one as for SCSI). Cards use an Intel GC80302 dedicated I/O processor. This chipset, under its former AMI brand name, has had a long and excellent history with SCSI gear.

I really want to stick with Ubuntu here! :) I did stumble across [[COLOR="YellowGreen"]openfiler[/COLOR]]("http://www.openfiler.com/") if anyone else is looking for NAS, based on CentOS.

I only have about 30GB currently stored on the server now so I can move it to my local HD for now. I think I may configure it a bit differently this time around though. Maybe do a couple of Raid-1's or something.
I am open to suggestions at this point I have 4 250GB drives for storage.

---

### Post by mramsey on 2007-10-16
> **'[S|G] said:**
> 
5 - Yes, you can configure auto shutdown and autoreboot. You'll need to create a cron schedule. Take a look here for more info: [http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

EDIT: To turn on your computer automatically, you'll have to check your BIOS options. Usually it's called "RTC Alarm".

I guess I really would not have to power down as much as spin down the disks. Like I mentioned previously I currently have no power options and only really need it to run 10hrs per day.

---

