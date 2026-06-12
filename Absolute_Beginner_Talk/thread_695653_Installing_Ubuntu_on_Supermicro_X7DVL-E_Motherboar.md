---
title: "Installing Ubuntu on Supermicro X7DVL-E Motherboard"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by LRT on 2008-02-13
I have a Supermicro X7DVL-E motherboard (specs [here]("http://www.supermicro.com/products/motherboard/Xeon1333/5000V/X7DVL-E.cfm")).

Ubuntu is not listed on their OS Compatibility Chart (found [here]("http://www.supermicro.com/support/resources/OS/5000VCompatibility.cfm")).

Does this mean I won't be able to install Ubuntu on this motherboard?? I looked at their drivers (found [here]("http://www.supermicro.com/support/resources/resource_drivers.cfm")) and they do support Fedora Core and Suse Linux (but the versions listed are a bit outdated), and there is no mention of Ubuntu. This motherboard came inside a Systemax server (very similar to this [one]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2371757&CatId=30")).
It came with Windows 2003 Small Business Server, which I want to get rid of (I think you know why).

What should I do??

---

### Post by Crooksey on 2008-02-13
It should run fine, they cant list every linux distro up there, the fact that it is supported by older Fedora's and Suse's, indicated that it will work fine on newer kernels, there is no linux benchmark test, so I would personally not have a problem buying that motherboard, with the intention of using it to power a linux machine.

---

### Post by LRT on 2008-02-13
Excellent! That is great news. I didn't want to have to tell my boss that we needed to buy a new motherboard! I have one more question, however (and maybe I should start a new thread for this.. please let me know if I should). According to the motherboard specs, there is an on-board Intel ESB2 SATA 3.0Gbps Controller that supports RAID 0, 1, 5, and 10. I am pretty sure this is Software RAID (but please correct me if I'm wrong). The specs say its for "Windows Only". Look under "On-Board Devices" on [this]("http://www.supermicro.com/products/motherboard/Xeon1333/5000V/X7DVL-E.cfm") specs page. 

So my question is, How will this affect my Ubuntu install?? You see the server actually comes with three 250GB SATA Hard Drives inside a drive cage for easy swapping. So do I have to install Ubuntu on RAID??... or do I just use one of the hard drives and ignore the other two??... i'm a bit confused to say the least... and I'm not sure how to install Ubuntu on Software RAID... although I believe the setup here is a Hardware Assisted Software RAID (read [this]("http://www.adaptec.com/en-US/products/raid_tech/_education/hw_raid_vs_sw_raid_wp_link.htm?nc=/en-US/products/raid_tech/_education/hw_raid_vs_sw_raid_wp_link.htm")).

thanks for your help, btw.

---

### Post by dstew on 2008-02-13
[Here]("http://ubuntuforums.org/showthread.php?t=326238") is a thread that discusses this controller. It is a software RAID controller. Ubuntu has software to create and manage software RAID. Installing directly to a RAID is difficult, but can be done using the Live CD. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). In this technique, you install the RAID manager dmraid into the Live CD system and go from there. It is interesting that you can install and run software in the Live CD system, but of course it disappears once you quit. But hopefully by then, you will have Ubuntu installed into your newly made RAID.

I have heard, but have not verified, that the Alternate Install CD can install to a RAID without having to do all the things you do with a Live CD. The Alternate Install CD installs the same Ubuntu system, but with a text-based installer interface rather than the Live CD's graphical interface. You get it by checking the box below the Start Download button on the [Ubuntu download page.]("http://www.ubuntu.com/getubuntu/download")

Finally, you can just install Ubuntu in a regular partition on one of the disks, and use the others as storage as separate disks rather than a RAID. Or, you can install Ubuntu on a partition and create a RAID from the rest of the disks for storage.

EDIT: I think the FakeRaidHowTo assumes your Windows server has already created a RAID. If there is not a RAID at all, you probably have to use the program [mdadm]("http://www.linuxmanpages.com/man8/mdadm.8.php") to create one. You can also install this on the Live CD file system and use it, I believe.

---

### Post by LRT on 2008-02-13
dstew, thank you for your help. I am aware of the text-based installer, but did not know it could install directly onto a RAID array. I will look into this.

> Ubuntu has software to create and manage software RAID.

do you mean software like mdadm??? do you know of any other software??,,, and tutorials??... i am aware of this [tutorial]("http://tldp.org/HOWTO/html_single/Software-RAID-HOWTO/") but its almost 4 years old... 

a few more questions... during the Ubuntu install, I should be able to see the three devices and basically select which device I would like to install on, correct??. Ubuntu would see the three devices as three normal SATA HDs, without any knowledge of them being part of a possible RAID configuration given the fact that I have RAID controller on this motherboard, am i correct??.... if i decide to setup a linux software RAID, this would be done with complete disregard of the RAID controller on my motherboard, correct??? so it would do no harm if i disable RAID on this controller's BIOS, correct??, 

any help is greatly appreciated, thanks!!

**EDIT:** I will look more thoroughly at FakeRaidHowto.. thanks.,

---

### Post by dstew on 2008-02-13
> during the Ubuntu install, I should be able to see the three devices and basically select which device I would like to install on, correct?Yes.

> Ubuntu would see the three devices as three normal SATA HDs, without any knowledge of them being part of a possible RAID configuration given the fact that I have RAID controller on this motherboard, am i correct?Yes.

> if i decide to setup a linux software RAID, this would be done with complete disregard of the RAID controller on my motherboard, correct?Maybe. I don't know if mdadm and dmraid take advantage of any of the controller's special features or not. I think it probably doesn't make a performance difference.

> so it would do no harm if i disable RAID on this controller's BIOS, correct?Again, I am not sure, but I think you are correct. In general, Ubuntu ignores the BIOS, and I think most Ubuntu programs do too.

---

### Post by LRT on 2008-02-13
you were very helpful,,, thanks for your help! 

this is something i can probably easily find out on google, but do you know of any other software and tutorials/howtos????

---

### Post by dstew on 2008-02-13
Well, there is the [Ubuntu Wiki]("https://wiki.ubuntu.com/"). [Here]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=RAID&titlesearch=Titles") is a list of articles that have the work "raid" in the title.

---

