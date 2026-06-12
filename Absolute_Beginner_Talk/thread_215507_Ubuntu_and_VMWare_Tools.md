---
title: "Ubuntu and VMWare Tools"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by mcdrake on 2006-07-14
Hi guys!

I guess this really is an absolute beginner question. But anyhow ... I have successfully installed Ubuntu on a VMWare Server. Now that I also need these VWWare Tools I am kinda stuck here. 

I click "Install VMWare Tools" on my VMWare Console and what I get is a folder being displayed with the Ubuntu VMWare Tools directly in Ubuntu. It must be some kind of virtual mapped CD-ROM. 
(VMWare is supporting Ubuntu Linux distributions) 

How do I exactly get these packages installed now? I looked up the manual and stuff but still can't get these tools up an running. 

Any help is greatly aprechiated. 

Cheers, 
McDrake

---

### Post by adam.tropics on 2006-07-14
[This page]("http://www.vmware.com/support/gsx25/doc/tools_install_lin_gsx.html#1032727") at the vmware site explains how to do this. In particular look at point number 3 where they explain where to find them.

---

### Post by matthendrix on 2006-10-24
This worked for me after unsuccessfully trying other methods..

   1.  Get a root shell: sudo bash
   2. Update your list package list: apt-get update
   3. Upgrade your components: apt-get upgrade

      Note: Repeat the previous step as many times as you need to get all the available updates installed.
   4. If necessary, do a dist-upgrade: apt-get dist-upgrade
   5. Once you have have done all the core updates you can, edit the /etc/apt/sources.list file and uncomment all the application repositories you want to include in your updates. I usually uncomment them all, but that is your call.
   6. Repeat steps 2 and 3 until all patches have been applied. Once this is done, you are ready to install the packages VMWare will need.
   7. Install build tools: apt-get install build-essential
   8. Get version of your kernel: uname -r. You will use the output from this step in the next step.
   9. Install the linux headers for your kernel. Issue: apt-get install linux-headers-{output of prev step here}. This will install the linux headers VMWare needs to compile their tools.

That is it. Once you have done all that, you should have all the pieces you need to install the VMWare tools without a hitch.

Thanks to [http://www.abbeyworkshop.com/2006/06/04/ubuntu-vmware-install.html]("http://www.abbeyworkshop.com/2006/06/04/ubuntu-vmware-install.html") for the tip.

---

