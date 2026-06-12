---
title: "Bootable USB stick on MacOS"
date: 2020-12-23
forum: Apple Hardware Users
---

### Post by llama99 on 2020-12-23
I'm following the instructions on Ubuntu Tutorials for creating a bootable Ubuntu USB stick.  For step #2 ("Requirements"), one is supposed to download an Ubuntu ISO file.  A link is provided called "Get Ubuntu" to give one download links.  

Upon clicking on "Get Ubuntu," there are a number of links but none that mention USB sticks.  Which link on this page should be used for downloading an ISO file for a USB stick? 

I'm new to Ubuntu--I have a second thread dealing with my attempt to create a bootable USB stick for use on a PC.  

I'd appreciate any assistance with this matter.  Thanks.

---

### Post by #&amp;thj^% on 2020-12-23
Better method IMO: [https://ubuntuforums.org/showthread.php?t=1958073](https://ubuntuforums.org/showthread.php?t=1958073)

---

### Post by howefield on 2020-12-23
Moved to the "*Apple Hardware Users*" forum.

---

### Post by llama99 on 2020-12-23
Thanks for the reply.  That method may be better, but it's too complicated for a simple boy like me.  The Ubuntu Tutorial doesn't look too bad for a non-tech person, it just doesn't provide any information about creating a Ubuntu ISO file for a USB.

---

### Post by #&amp;thj^% on 2020-12-23
It really isn't that hard, just overwhelmed by all the text there.
That is after all, a part of the linux journey. (learning)

---

### Post by TheFu on 2020-12-23
Download the ISO file that matches the CPU architecture for the system. Almost nobody creates ther own ISO. I haven't since some time in the 1990s.  google "ubuntu download" to find a mirror download website. 

There are slightly different flavors and releases for ubuntu. New people today should get a 20.04.x LTS release.  The choice of GUI depends on the specific hardware i will be run using. The default Ubuntu is heavy and should be avoided if using a flash drive. Pick xubuntu or lubuntu instead. These work well on lower-end GPUs and use less CPU.  You can always always change to GUI in about 3-5 minutes.

I only use USB linux for installing or to troubleshoot full installs. Running off usb will always be slow, except for speecfic releases lke tinycore deigned to load everything into ram before running.

---

### Post by coffeecat on 2020-12-23
@1fallen, the OP is trying to follow the official Ubuntu tutorial which is beautifully presented and which is far easier for a newcomer.

@llama99, I assume you are following this tutorial: [https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview) . If you want help with a tutorial you have found, please in future provide a link. That way, members helping you don't have to waste time googling to identify it.

To answer your questions. Any ISO is suitable for writing to a USB device. In step 2 of that tutorial, in the Get Ubuntu link, choose Ubuntu Desktop. Then choose 20.04.1 LTS. That's the long term support version, supported for 5 years. 20.10 is an interim release supported only for 9 months and not really suitable for a newcomer.

[quote=llama99]The Ubuntu Tutorial doesn't look too bad for a non-tech person, it just doesn't provide any information about creating a Ubuntu ISO file for a USB.[/quote]

Oh, yes it does. Steps 3, 4, 5, and 6 tells you exactly how to prepare a USB on a Mac.

If you get stuck, do post back. Good luck.

---

### Post by deadflowr on 2020-12-23
> Upon clicking on "Get Ubuntu," there are a number of links but none that mention USB sticks. Which link on this page should be used for downloading an ISO file for a USB stick? 
No such thing.
All ISO can be ported to a usb stick or dvd or other media.
None are specifically created for any one media type.

Edit: Ninja'd
coffeecat's explanation is better, imo.

---

### Post by #&amp;thj^% on 2020-12-23
> **coffeecat said:**
> @1fallen, the OP is trying to follow the official Ubuntu tutorial which is beautifully presented and which is far easier for a newcomer.


Agreed it is better written and easier for new users to follow.
Hard/Complicated/Technical to me is viewed differently is all.:D
BTW: Good to see your presence. Been a minuet or two.

**EDIT:** Must say I'm a bit embarrassed, the poster had two post's of similar nature.
one for the Mac Book and one for HP laptop, needless to say I posted in the wrong thread. :shock:
Sorry for any confusion on my part.

---

### Post by llama99 on 2020-12-23
Thanks everyone.  I returned to the Ubuntu tutorials and downloaded "Ubuntu 20.04.1" to the Mac.  This corresponds to step 2 as shown in this link:

[https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#2-requirements](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#2-requirements)

Then I dragged what I downloaded onto the USB stick, which I assume is the correct procedure.  When I click on what I downloaded, I get a box with this message:  "The following disk images couldn't be opened. . .No mountable file systems."  Below is a screenshot, hopefully readable.

[ATTACH=CONFIG]287611[/ATTACH]

I did the same download again and got the same result.  Any tips on downloading Ubuntu 20.04.1?

---

### Post by coffeecat on 2020-12-23
> **llama99 said:**
> 
Then I dragged what I downloaded onto the USB stick, which I assume is the correct procedure.

No, it isn't. *Read the tutorial* **steps 3, 4, 5, 6 and 7**.

---

### Post by llama99 on 2020-12-23
I want to get the order of operations straight.  I read through steps 3-7 of this link:  [https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview)

In Step 6, it says, "After entering your password, Etcher will start writing the ISO file to your USB device."

Going back to Step 2, after clicking on "Get Ubuntu" and "Ubuntu Desktop," I'm lead to this page:  [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop).  This is where I'm downloading Ubuntu 20.04.1 LTS in order to get the Ubuntu ISO file.

How does the installation of Etcher relate to downloading Ubuntu 20.04.1 LTS?  If I'm starting at Step 3, at what point do I return to downloading Ubuntu 20.04.1 LTS?  After step 6?

---

### Post by llama99 on 2020-12-24
Ignore last post, I figured out the steps.  I completed step 5 of the tutorial ([https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#5-etcher-configuration](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#5-etcher-configuration)), getting a successful "Flash" which indicates that Etcher is configured on the USB drive.  Then I got this error message:  "The disc you inserted was not readable by this computer."

After some Startpaging, I came upon this webpage:  [https://www.easeus.com/mac-file-recovery/the-disk-you-inserted-was-not-readable-by-this-computer-mac.html#4](https://www.easeus.com/mac-file-recovery/the-disk-you-inserted-was-not-readable-by-this-computer-mac.html#4).  I went to Step 4, performed the steps for initializing the USB drive.  I couldn't repair the disc, got a message stating, "Disc Utility can't repair this disc."  So I erased the USB drive.  According to the webpage, [SIZE=2]"After this your Mac should now recognize the disc correctly.  You will no longer receive such an unreadable disc error."[/SIZE][SIZE=1]
[/SIZE]
Then I did Step 5 of the Ubuntu Mac tutorial over again, successfully "Flashed," and got the same error message:  "The disc you inserted was not readable by this computer."  So I haven't been able to get Etcher to write the ISO file to the USB.

Any tips on how to proceed?

---

### Post by CelticWarrior on 2020-12-25
The resulting drive may not be supposed to be read from the installed OS, but it should be a bootable one.
Have you actually tried to boot from it?

---

### Post by llama99 on 2021-01-03
Well I backtracked to this link:  [https://www.pendrivelinux.com/univer...easy-as-1-2-3/]("https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/").  I managed to install the Ubuntu on a USB via an HP Stream laptop.

I popped the USB into a Mac, pressed "Alt Option" while restarting, and the USB did show up as "EFI Boot" as it's supposed to.  I clicked on EFI Boot and the system checked for errors, there were none.

Then I landed on a page which offered these options:  "Try Ubuntu" and "Install Ubuntu."  I tried to opt for the former since Ubuntu is already on the USB, but my mouse was non-functional.  I couldn't select anything.  

I manually shut off the computer, started it up, and found that the mouse works fine on the regular Mac operating system.  I restarted while pressing "Alt Option" and again selected "EFI Boot."  After the error check, I was brought to the same page containing "Try Ubuntu" and "Install Ubuntu," and my mouse was again non-functional.  In fact, my keyboard doesn't appear to work either on this page, as I tried hitting using the arrows to select a different language ("English" was highlighted by default) and nothing moved.

Any idea on why the mouse doesn't work when trying to use Ubuntu?  Thanks.

---

### Post by sudodus on 2021-01-03
A that early stage of booting, in the grub menu, the mouse is not yet activated. You can navigate with the arrow keys ('arrow down' and 'arrow up') and activate the selected item with then 'Enter' key.

---

### Post by llama99 on 2021-01-05
The keyboard doesn't work either at this stage.  The up and down keys and the "Enter" key don't work.  Any tips on how to proceed?

---

### Post by sudodus on 2021-01-05
If *you* know how run Ubuntu on a Mac computer in general and to make the keyboard work during boot, please chip in :-P

---

### Post by gary1008 on 2021-03-06
It is trickier if you have a 2019 or later MacBook Pro. The problem is to make the stick bootable. Just having the install file on it is not enough.
This link: [https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733](https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733)
suggest using UNetbootin to download a Ubuntu installation and make the stick bootable. The whole link is confusing and technical but the part about downloading and installing UNetbootin isn't too bad if you just find it.
Basically you don't install it - you download it and copy to the Applications folder.
There are a couple of spots to fill in when you run it. But first you have to format the stick into FAT using Disk Utility.
Good luck!

---

