---
title: "Dual Boot does Not Boot - Error in Loading XP"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by drteo66 on 2008-01-01
I'm new to Linux, but have successfully installed Ubuntu 7.10 on the first computer, dual booting with XP.  However, Ive had no luck with the second and similar computer.  I devote one entire hard drive of 120GB to Ubuntu.  C:\ drive is where XP is installed. No problem in installing, Ubuntu on  separate drive except that upon re-booting, neither XP nor Ubuntu would load.  After going through Bios, the display says:
"Error in loading Operating System ..."  Everything stops at that point.

I've tried to use Super Grub, but it boots to the menu and stop freezes.  No movement thereafter. Thus I cannot access windows XP or Ubuntu.  

I have tried this about 7 or 8 times, each time it ends up in the same disaster.

Here are a few things I've done:
1) I've reformatted C:\ where XP is; reinstalled XP fresh.
2) I've several HD, and now have removed all of them except two - one for XP and one for Ubuntu.
3) I've tried other flavor of Linux, and it ends up with the same result - "error in loading Operating System ..."

I've come to live Ubuntu but I cannot get it to work, I'll return to Windows XP exclusively, which I prefer not to do.  I'm a convert to Linux.

I would most grateful to anyone who can help with this problem.


Intel Core 2 Duo E6750
Migabyte GA-P35-DS3L
Crucial Ballistic 1 x 2gb
EVGA P2-N742-LR
Chaintech sound card AV710
etc

---

### Post by HermanAB on 2008-01-01
Well, dual booting is sooo 20th century... ;)

As you have now found, dual booting is at best a pain in the derrier.  Unless you need advanced accellerated graphics in Windoze, it is better to install Linux with a VM system such as Virtualbox or VMware Server and then install WinXP in that.  That way, you can run Windoze in a window, concurrently with your Linux schtuff.  This is far more reliable and convenient than dual booting.

It is more reliable, since the virtual machine is a directory on your Linux file system, thus you can make a backup of the whole WinXP VM, by making a tar ball of the directory and saving it to a DVD.

Once you have a Virtual system installed, you'll find that it is also nice to install a different version of Ubuntu in it, for experimentation.  That way, if you test something out, you have no fear of screwing up your host system and once you have a bunch of VMs on DVDs, you can easily revert back to a fresh VM whenever needed.  I have oodles of VMs, for Redhat, Mandriva, Debian, Ubuntu, Kubuntu, Xubuntu, Centos, WinXP, Win2003 and so on and can easily experiment with any of them or even run more than one at the same time.  It is like having a rack full of machines on my desk.

So, to get back to your problem - I cannot help you, but it looks like you are on the right track with Super Grub.  Some Googling may help.

Cheers,

Herman

---

### Post by drteo66 on 2008-01-01
Herman,
Thank you kindly for your counsel.

Unfortunately, I'm new to Linux.  I like your suggestion.  Is there anyway you can direct to my good tutorials on how to set VM box you described?  Greatly appreciate any help.

---

