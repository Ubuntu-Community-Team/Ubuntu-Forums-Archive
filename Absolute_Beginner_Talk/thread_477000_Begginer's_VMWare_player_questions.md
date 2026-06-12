---
title: "Begginer's VMWare player questions"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-17
:)I downloaded and installed VMWare player and used the following web page to set it up so I could run my existing Windows partition from inside of Ubuntu:

[http://www.advicesource.org/ubuntu/R...re_player.html](http://www.advicesource.org/ubuntu/R...re_player.html)

I have 2 problems I haven't been able to find a solution to both on the web and from the player documentation.

(1)  How do I get my Synaptics touchpad/mouse to work with the guest operating system?  It works when VM player first starts, but the minute it goes into the boot thing for Windows I can no longer use the touchpad/mouse.

(2) How do I setup my wired network (eth1) so it is accessable from the guest operating system?

Thanks in advance for any help, as these really have me stumped.;)

---

### Post by Clay_Banger on 2007-06-17
you may need to install VMWare Server instead of VMWare Player. As Player is, as it says, a player, you may not be able to add and remove devices, ie your touch pad. VMWare server is the repos.

---

### Post by Seisen on 2007-06-17
You can also try VirtualBox if you want.

---

### Post by gcos7 on 2007-06-18
Thanks for the replies.  Here are the results so far:

- downloaded and attempted to install the VMware server.  The installation failed, resulting in VMware server showing as an option in applications/system but it doesn't work.  The VMWare player option has disappeared, so now I can't start either.

- downloaded and installed the virtualbox.  In configuring the virtualbox, it appears it only accepts disk images that have been created by virtualbox.  Since my laptop did not come with an actual Windows XP cd, but rather I had to build some restore cd's, I don't see how I can load a guest operating system into a new image.  What I want to do is use my existing Windows XP partition as the disk the virtualbox uses.

---

### Post by Clay_Banger on 2007-06-18
> **gcos7 said:**
> - downloaded and attempted to install the VMware server.  The installation failed, resulting in VMware server showing as an option in applications/system but it doesn't work.  The VMWare player option has disappeared, so now I can't start either.
The installation of vmware server requires that you agree to sum terms and conditions and enter a serial number while it is installing. did you do any of that?

---

### Post by gcos7 on 2007-06-18
I got a serial number, but it never asked me for it during the installation.

Also - for virtualbox - it will run my recovery cd, boot windows, but windows aborts when it tries to run windows setup.  Tried save mode but it wanted to run windows setup first.

---

### Post by bodhi.zazen on 2007-06-18
I do not have all the answers for you, but this may give guidance : 

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

---

### Post by gcos7 on 2007-06-18
It appears that VMware server does not install in 7.04.  I looked at their website and it all appears to be for Ubuntu (or Debian) less than 7.04.

---

### Post by rangans on 2007-06-18
You need to setup vmware tools inside the guest. If you are not able to get the vmware server running atleast extract the tar file and inside lib folder there should be vmware tools installer for the various platforms extract that and then install it into windows. This should get you better networking. To get any networking at all you need to setup the ethernet0 type and present properties inside the .vmx configuration file. I suggest that you go to vmware's market place download a pre-built vmx that can install a generic OS from an ISO and proceed from there. You can also use this excellent website [www.easyvmx.com](www.easyvmx.com)  to create a vmx and vmdk file all by yourself and there are several levels of complexity to which you can go with this one. Hope that helps.

---

### Post by bodhi.zazen on 2007-06-18
> **gcos7 said:**
> It appears that VMware server does not install in 7.04.  I looked at their website and it all appears to be for Ubuntu (or Debian) less than 7.04.

Both VMWare server and player work in both 7.04 and 7.10 (as does VirtualBox).

---

### Post by Clay_Banger on 2007-06-18
> **bodhi.zazen said:**
> Both VMWare server and player work in both 7.04 and 7.10 (as does VirtualBox).
I second that, its in the repos, so there is no reason for it not to work.

---

