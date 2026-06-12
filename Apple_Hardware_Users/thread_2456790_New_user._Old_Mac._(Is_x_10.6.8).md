---
title: "New user. Old Mac. (Is x 10.6.8)"
date: 2021-01-19
forum: Apple Hardware Users
---

### Post by simonsaysit on 2021-01-19
Hello everyone. Linux seems like a lovely use of my 
MacBook Pro 1,2 intel core duo, 2.16ghz, (2 cores, 1 processor) 1gb x2 but I guess I could upgrade that! 667Mhz, 160gn hard drive running OS X 10.6.8 and that seems to be the real issue. 
I can’t get onto any sites to download “because Safari can’t establish a secure connection to the server...” and I guess that’s the main reason I want to ditch the Mac OS. 
I’ve got access to another Mac if that would work to download but I really need advice to know how and if that’s possible. Thanks everyone. Take care, Simon.

---

### Post by grahammechanical on 2021-01-19
Instructions on how to burn the Ubuntu ISO image to DVD on a Mac

[https://ubuntu.com/tutorials/burn-a-dvd-on-macos#1-overview](https://ubuntu.com/tutorials/burn-a-dvd-on-macos#1-overview)

Instructions on how to burn the Ubuntu ISO to USB stick

[https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview)

Installation guide for Ubuntu desktop

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Try before you install guide

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

Regards

---

### Post by QIII on 2021-01-19
Moved to Apple Hardware Users.

---

### Post by 2blue on 2021-02-08
How are you doing? Can you download another browser? I use firefox on my mac and it behaves well on any distro download I have tried. With 1GB ram you should be fine, but with minimal specs you might benefit from light running versions like lubuntu or xubuntu. You do get the same options for any software. As long as you can get on another machine and burn the iso you should be fine, USB flash memory is good, and DVD still works fine if you have one. My mac burns DVDs fine, but for USB flash drives I use Etcher.  I assume you have a 64 bit machine, but if you mac is older it might be 32 bit, and you may have to aim towards Debian who still supports 32bit. If it`s less than 10 years old it`s as far as I know 64 bit, older hardware than that is not common I guess.

---

### Post by 8chuck8 on 2021-02-23
Hi there.
I am trying to revive a similar piece of hardware, MacBook Pro, probably 6 years old.
Currently it runs on Mac OS Catalina and is very slow (I should not have done the Catalina upgrade I guess :-()

I would like to install a dual boot system.
I went through the numerous guidelines on the web, got my USB boot stick, set up partitioning, etc.

I can dual boot and Ubuntu runs from the stick with no problem.

However when I want to install Ubuntu it hangs after the third screen: I tried all options: minimal install, normal install and the respective third party sw download options.
when I kill the install window I get the message, "Installer not responsive".

who knows a solution to the problem?

---

### Post by CelticWarrior on 2021-02-24
First you say > [COLOR=#000000]set up partitioning[/COLOR] then > [COLOR=#000000]tried all options: minimal install, normal install and the respective third party sw download options[/COLOR] ???

Those aren't all the options. If you partitioned in advance you need to choose "something else" and then select all the required partitions including the ESP (EFI System Partition).

---

### Post by 8chuck8 on 2021-02-24
Thanks for your comments.
I first added two new partitions under Mac OS: Ubuntu (330GB) and SWAP (10GB).
then I rebooted pressing the option key, I can chose between OSX and two USB drive symbols EFI (not sure why there are two EFI symbols). I chose either EFI and it boots from the USB stick.

Below see the three screens that follow until it hangs.
I don't see the "Something else" option?

[IMG]https://photos.google.com/photo/AF1QipNwuvsQpACKsdPur4JZS8L-oEy2d6X8ro1TsH-a[/IMG]

hmmm not sure how I attach pictures??? I uploaded from my google album?

---

### Post by 8chuck8 on 2021-02-24
<Image link snipped>

---

### Post by CelticWarrior on 2021-02-24
Please add pictures as attachments, not as pictures.

Now, you don't need and probably shouldn't create partitions for Ubuntu but instead have unallocated space. No swap partition needed either (you can have it but for years Ubuntu have been using a swapfile instead). Only one partition / (root)  - besides the EFI partition that's already there - is currently needed. That partition, if created prior to the installation, must be of a compatible file system (EXT4 is recommended), Ubuntu will NOT install in Mac partitions.

---

### Post by 8chuck8 on 2021-02-24
Thanks, looks like this is going into the right direction, however I still don't know how  to do it?

Objective is a dual boot Macbook.

It looks like that I have to go back to the MacOS disk utility tool and change the partitioning. 
What partitioning do I need to set up?

I think you call it "unallocated space" how do I do that?

---

### Post by 8chuck8 on 2021-02-24
Looks like creating unallocated disk space is not straightforward in Catalina.
I found an older version:
[https://www.youtube.com/watch?v=R5CUm3AvF8k](https://www.youtube.com/watch?v=R5CUm3AvF8k)
however the resizevolume command does not work any morei n Catalina.

looks like something more hardcore is needed:
[https://superuser.com/questions/1270251/resizing-windows-10-bootcamp-partition-manually](https://superuser.com/questions/1270251/resizing-windows-10-bootcamp-partition-manually)
i.e. getting into MacOS recovery mode....
Is there an easier way?

---

### Post by CelticWarrior on 2021-02-24
> [COLOR=#000000]What partitioning do I need to set up?[/COLOR]

[COLOR=#000000]I think you call it "unallocated space" how do I do that?[/COLOR]

Unallocated space means no partition. You simply delete the two partitions you said you created for Ubuntu thus leaving that space unallocated.
And no, you don't need to use MacOS for that. You can open Gparted or Disks in the Ubuntu live session and do everything from there before starting the installation.

---

### Post by 8chuck8 on 2021-02-25
....sorry, I did not see the second page :-)
thanks, that will make life much easier, rather then going around all the MacOS hurdles.

Are there any instructions how to use Gparted? otherwise I should be able to find them myself somewhere.

---

### Post by CelticWarrior on 2021-02-26
Gparted is as easy as the OSX Disk Utility, the tool that you probably used to create the (unneeded and unusable) partitions in the first place. The same way you created them you can also delete, resize, etc. just make sure you aren't deleting the system partition(s).

I said you can do the same with GParted and you can, right-clicking any partition gives you all the possible actions, but I never said you should. Partitions are always better managed from the original already installed OS using said OS native tools. And all you should have done was to shrink one or more partitions there to make room for Ubuntu.

Now my honest and necessarily harsh opinion: You don't know enough yet for the task you want to perform. A solid knowledge of the basics of partitioning is needed and the sequence of questions show that you don't know what you're doing so the risk of ending up with an unbootable system is very high. Please obtain an OSX recovery/installation media before going any further. And, of course, make sure you have good backups of all those personal files you can't afford to loose.

---

### Post by 8chuck8 on 2021-02-26
Harsh words? "... you are clueless" haha.
You are hurting my pride. But yes, I am skating on thin ice here. But that's ok. I am trying to resurrect an old MacBook that would otherwise been thrown away.

I re-partitioned under MacOS and created unallocated space (like 320 GB), however Ubuntu stalled exactly at the same spot. I also reconfirmed that it is unallocated space, when I discovered that Gparted isl already in the Ubuntu utilities. hmm, what now?

I found Fossapub and tried that, the advantage being that you can install it in RAM (ok, just for the session).
I probably try to install it to the hard drive. But now I have to create formatted partitions (a main partition plus a Swap partition. I still have to check some details regarding formatting etc. According to your point I should the partitioning under MacOS (if the correct formatting can be selected). Otherwise I use Gparted under Fossapup.

Anyways, the ice is thin, I hear some occasional cracks, but I am still skating away :-)

---

### Post by 8chuck8 on 2021-02-28
lost a battle, won the war.
In case someone is reading this and wants to know the outcome.

I lost MacOS (oh, well, I forgot that expanding a partition also kills the content :-)).
I installed MX Linux with no problem and did a clean install on the hard drive.
It is working as expected and I achieved my goal to resurrect my old Macbook.

Ok, sour grapes, I would have liked to keep my MacOS and data that I never looked at in 5 years.

My conclusion: there is quite a variety of cases combining Linux version and MacOS, even if you are only a few months off, instructions you find might be wrong.
So make sure to look for something that represents exactly your situation.

---

