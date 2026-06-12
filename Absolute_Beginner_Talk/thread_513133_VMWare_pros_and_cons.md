---
title: "VMWare pros and cons"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-07-30
Although a happy Ubuntu user for the past twelve months, I still have reasons to use a  Windows programs on times but find dual booting a slight inconveniece. Because of this, I'm considering VMware and wonder what the Pros and Cons there may be with its use. 

The two programs I wish to use in Windows are Frontpage and Web CEO would anyone be able to say if these programs would work using VMware within Ubuntu?

Having no experience of  VMware  can I ask if there are  any security issues I should be aware of.

Assuming it will do what I require without me having to dual boot, I'd like to ask which is the easiest way of obtaining and installing the software please?

---

### Post by aitorcalero on 2007-07-30
I am using vmware server to launch windows xp, and it works perfectly. Performance mainly depends on how many memory is assigned to virtual machine.
Security issues will be those corresponding to windows :( no more no less, since any viruses, trojans or whatever will be only in vmware virtual disk. 
If you only want to use those two programs vmware server, or virtual box, is your the right choose. They will run perfectly, but you need at least 1 Gb RAM, to set a VM with 512Mb RAM
The best way to download vmware software is via Automatix or Synaptic, but you need to register in vmware site to request a valid license key for your sever.
PS.: check out other virtualization soft: qemu or virtual box.

---

### Post by a.v.l on 2007-07-30
After opening VMware in Automatix, I was told there was an update available and shown a link to the officail website. From there I registered with my name and email address and downloaded version 2 with an .rpm extension. This wouldn't open so I removed it.  

I then downloaded a .tar.gz version to the desktop and opened (I think) as I can now see VMware player in Applications> system tools. When I select VMware player a  window opens called "Open vitual machine" at which point I have to admit to being lost as I cannot proceed past this point. Can someone offer help please?

---

### Post by asmoore82 on 2007-07-30
I just got VirtualBox OSE up and running Friday and it works great.
BUT, you have to compile it from source code; I couldn't find it in apt.

i think I'm going to post a VBox Howto soon.

---

### Post by a.v.l on 2007-07-30
> **asmoore82 said:**
> I just got VirtualBox OSE up and running Friday and it works great.
BUT, you have to compile it from source code; I couldn't find it in apt.

i think I'm going to post a VBox Howto soon.

Thanks for the tip. Just found Virtualbox in Automatix and it installed perfectly, first time. Infact  I'm  writing this reply from within it now.  Not being to sure of the security risks, I've installed a free anti virus and firewall program.  This looks like it will be an improvement on having to dual boot each time I want to use Frontpage and Web COE.

---

### Post by a.v.l on 2007-07-31
> **a.v.l said:**
> Thanks for the tip. Just found Virtualbox in Automatix and it installed perfectly, first time. Infact  I'm  writing this reply from within it now.  Not being to sure of the security risks, I've installed a free anti virus and firewall program.  This looks like it will be an improvement on having to dual boot each time I want to use Frontpage and Web COE.

Would someone know how to swop between Virtualbox (XP) and Ubuntu. I believe there is a default key combination to do this which I'm unable to find  presently.

---

### Post by anewguy on 2007-07-31
Well, first be sure to install the vm tools to the virtual machine, as that will help.  I believe there is a key combination to give the mouse focus "back" to Ubuntu.  Check under "Help" on the virtualbox main screen, as it contains a TON of information if you look for it!  It's probably something like ctrl-f or something along those lines, but I only used virtualbox for a short time before I decided to use VMWare-Server instead.:)

---

