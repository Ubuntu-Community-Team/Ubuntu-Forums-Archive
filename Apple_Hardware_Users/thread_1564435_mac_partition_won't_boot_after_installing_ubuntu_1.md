---
title: "mac partition won't boot after installing ubuntu 10.4"
date: 2010-08-30
forum: Apple Hardware Users
---

### Post by cbbplanet on 2010-08-30
So I repartitioned my mac hard drive using the disk utility in my mac os. Shrink the mac HD and created a new partition for ubuntu. I installed Ubuntu and everything works fine and it was be able to boot back into mac yesterday. However, this morning, when I was holding down the ALT key at startup trying to go into my mac, no boot options come up, it automatically goes into the ubuntu boot option (grub 2) and i tried to go into the mac osx on sda2 from grub2 but it'll take a very long time and nothing boots up. It just says 'waiting for root devices'. Do I need to insert the mac cd and try to repair the system? All my files and partition are still there so I think its not completely gone. 

ps. I have the newest macbook version (6.1?)

---

### Post by dngfng on 2010-08-31
Newest MBP is 6,2 currently - still if I where you I would go ahead and install rEFIt under OS X that will give you a better boot menu at start up.

If you want to find out witch version your mbp is use the following command in the linux terminal:

sudo dmidecode -s system-product-name

Also once you know what MBP version you have got you should have a look at this:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
and look at the instructions to install the proper packages and perform the correct settings
so that ubuntu can run properly on you MBP.

There are known to be heat/Fan issues so you may want to have a look at the macfanctl listed in my Signature.

---

### Post by cbbplanet on 2010-09-01
Hi sorry, I actually have a MacBook, not MBP. So I believe its 6.1 (the newest generation one) How do I install rEFIt? Is it from the original recovery CD it came with?

---

### Post by dngfng on 2010-09-02
> **cbbplanet said:**
> Hi sorry, I actually have a MacBook, not MBP. So I believe its 6.1 (the newest generation one) How do I install rEFIt? Is it from the original recovery CD it came with?

rEFIt is an opensource OS Selector for Mac's. You can download it from here:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
Just install it in OS X. 

You are best of following the instructions listed in this guide (even if you are only aiming to dual boot and not triple boot.
[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

Also you can find instructions for your MacBook 6,1 here in the Ubuntu Community documentation:
[https://help.ubuntu.com/community/MacBook6-1/Lucid](https://help.ubuntu.com/community/MacBook6-1/Lucid)

Let me know if you have any more issues.

---

### Post by cbbplanet on 2010-09-04
hmm, i guess i should have followed the instruction on that guide before i installed ubunut. However, the problem is that I can't even go into my mac os and therefore, can't even install the rEFIt

---

### Post by vgrisham on 2010-09-04
Maverick is not booting for me (Macbook Pro 5,3; rEFIt). I get the same message as [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393") that affected Macbooks in the Spring when Lucid was in Beta. 

After installing Maverick, I went back to Lucid Lynx which works great. I believe I will wait until 10.10-1 to try again.

EDIT: Sorry, I posted this to the wrong thread. 10.04 boots fine for me with rEFIt.

---

### Post by cbbplanet on 2010-09-04
^ thing is i'm not even on 10.10. I was using the 10.04 netbook edition which is Lucid I believe. I guess I will try to see if I can boot off of my mac osx cd and see if I can repair the os.

---

### Post by vgrisham on 2010-09-04
> **cbbplanet said:**
> Hi sorry, I actually have a MacBook, not MBP. So I believe its 6.1 (the newest generation one) How do I install rEFIt? Is it from the original recovery CD it came with?

You should follow a multi-boot guide such as [this]("http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required") one. It explains everything. Print it out ahead of time as well as the Ubuntu guides cited; they're specific to your model.

---

### Post by cbbplanet on 2010-09-06
> **vgrisham said:**
> You should follow a multi-boot guide such as [this]("http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required") one. It explains everything. Print it out ahead of time as well as the Ubuntu guides cited; they're specific to your model.

yes, i know. I regret not following that thread and installing the rEFIt ahead of time when my mac was working. However, kind of too late now since my mac won't boot and i'm stuck on linux only. I'm trying to find a way to install rEFIt in linux so i can go back to put into mac again.

---

### Post by dngfng on 2010-09-07
Have you tried fixing OS X with the OS X DVD's. Once repaired it should only boot into OS X from where you can install rEFIt.

There is a chance that it may destroy your Linux installation but that is unlikely.

---

### Post by cbbplanet on 2010-09-08
thanks! My mac partition suddenly magically boots up one day so I went into it and install the rEFIt and now everything is fine! 

however, now i'm trying to find out how I can eliminate grub so i don't go through two time for the boot menu. from what i researched, it seems like you can't replace grub with rEFIT?

---

### Post by dngfng on 2010-09-09
> **cbbplanet said:**
> 
however, now i'm trying to find out how I can eliminate grub so i don't go through two time for the boot menu. from what i researched, it seems like you can't replace grub with rEFIT?

Since rEFIt is not a bootloader but simply a "bootloader selector" you still need grub - the next best thing you can do is just reduce the timeout of grub to 0/1 sec depending on wether you want to be able to switch into recovery mode or not if you ever hit a problem.

---

### Post by xiq on 2011-12-11
> **cbbplanet said:**
> hmm, i guess i should have followed the instruction on that guide before i installed ubunut. However, the problem is that I can't even go into my mac os and therefore, can't even install the rEFIt
Hi,

Just a note (I'm still in the process of working my issue out), but I already had rEFIt installed on my macmini4,1 and was happily dualbooting OS X and 11.4. When I did a "remove 11.4 and install 11.10" from the Ubuntu installer, it seemed to knock out my rEFIt, and my macmini now boots straight in to grub, and the OS X boot options from grub get me straight to a darwin kernel panic.

I'm going to try re-installing rEFIt from the rEFIt boot cd... I'll update here if I discover anything revelatory.

EDIT: *facepalm* after burning the rEFIt boot CD to disk, I was just checking up on the boot hotkey for booting from CD and noticed that by holding down "Option" you can get a kind of built in boot selector. I tried this and it gave me the option to boot the inactivated rEFIt which happily booted a working OS X, I re-ran /efi/refit/enable-always.sh and everything is back to normal.

pix

---

