---
title: "[SOLVED] Can't install Ubuntu"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by putanitsa on 2008-01-10
Hi everyone,

I'm a complete newbie, so please excuse any stupidity on my part. I've never used Linux, but I'm in love with its philosophy, so I'm trying to try it out. So far, it's been difficult.

I'm trying to install Ubuntu 7.10 on my computer (as a dual boot with XP), but it won't install. I have checked my cd with Md5Sum and it's ok, I've burned a few copies to make sure it wasn't the cd.

Everytime I boot from the cd, once I select "check CD for defects" or "start or install Ubuntu", I get a screen saying
BusyBox v.1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
(initramfs)
What is this?

I've tried to find info online, but I don't understand what is going on and what I'm supposed to do. Some people have suggested to press F6 when I get to the menu and type "all_generic_ide" in place of the quiet splash, but all that does is I see a long long list of words I don't understand and then the screen goes black.

Anyone want to help me out?

Thanks,
-putanitsa.

---

### Post by zabien1970 on 2008-01-10
Which program did you use to burn the cd

---

### Post by putanitsa on 2008-01-10
Roxio. Why, does that matter? I chose "burn image" if it matters.

---

### Post by buccaneere on 2008-01-10
> **putanitsa said:**
> Hi everyone,

I'm a complete newbie, so please excuse any stupidity on my part. I've never used Linux, but I'm in love with its philosophy, so I'm trying to try it out. So far, it's been difficult.

I'm trying to install Ubuntu 7.10 on my computer (as a dual boot with XP), but it won't install. I have checked my cd with Md5Sum and it's ok, I've burned a few copies to make sure it wasn't the cd.

Everytime I boot from the cd, once I select "check CD for defects" or "start or install Ubuntu", I get a screen saying
BusyBox v.1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
(initramfs)
What is this?

I've tried to find info online, but I don't understand what is going on and what I'm supposed to do. Some people have suggested to press F6 when I get to the menu and type "all_generic_ide" in place of the quiet splash, but all that does is I see a long long list of words I don't understand and then the screen goes black.

Anyone want to help me out?

Thanks,
-putanitsa.

The code string [HTML]all_generic_ide[/HTML] goes at the end of the strange code string that comes up when you enter f6 at bootup.

Then proceed with boot...

---

### Post by theRightNee on 2008-01-10
i cannot say what your problem is, but have you tried running in safe graphics mode? i find that this often helps, especially on slower computers. 
BTW, you may also want to redownload the file. It may not be the CD, but the file itself thats corrupted.

hope this helps =]

---

### Post by putanitsa on 2008-01-10
> **buccaneere said:**
> The code string [HTML]all_generic_ide[/HTML] goes at the end of the strange code string that comes up when you enter f6 at bootup.

Then proceed with boot...

So I'm not supposed to erase "quiet splash--"?
Also, what do you mean by "proceed with boot"?

---

### Post by zabien1970 on 2008-01-10
> **putanitsa said:**
> Roxio. Why, does that matter? I chose "burn image" if it matters.

I've seen alot of people not burn the image right and then not be able to figure out whats wrong

---

### Post by putanitsa on 2008-01-10
**theRightNee:** I just tried running it in Safe Graphic mode and I get the same thing. I'm downloading the file again, I'll see if that helps. But shouldn't checking the file with Md5Sum make sure the file is ok?

**buccaneere:** this is a picture of what I get when I do that:
[IMG]http://farm3.static.flickr.com/2059/2184850646_25bf5288a4.jpg[/IMG]
It just goes on and on and then eventually the screen goes black and nothing happens.

**zabien1970:** does it sound like I did something wrong in the burning process?

By the way, thanks everyone for the quick answers. I'm starting to think I might be too dumb for Linux, but hopefully it's not the case and I'll figure this out!

---

### Post by EXCiD3 on 2008-01-10
Here's something that should have been asked from the very beginning: What are your system specs?

I think you are going to need to add a boot parameter in able to get it to boot. Nothing should be wrong with your disk, as it appears to have burned fine...but that is a possibility.

---

### Post by putanitsa on 2008-01-11
[B]EXCiD3:
[/B]
AMD Athlon
1.25 GHz
1.12 GB of Ram

Does that answer the question?

---

### Post by EXCiD3 on 2008-01-11
How about your video card and wireless/wired ethernet? Sometimes these are the reasons for not being able to boot from CD. Also do you have IDE or SATA hard drives?

---

### Post by zabien1970 on 2008-01-11
lol, yeah system specs would be nice to know.

I've never used Roxio but Infraview is recomended, although I've heard some other programs work just as well, also burning to fast can corrupt the image.
While in windows if you view the content of the cd there should be multiple files, if there's just one you didn't burn correctly as an image, although th burn could still be corrupt

but letting us know the specs will help, some computers don't like the live cd and need the alternate cd instead

---

### Post by putanitsa on 2008-01-11
**EXCiD3:**
Video card: ATI Radeon 9250
My internet is the wired kind. What kind of information do you want me to give about that?
How do I figure out if I have IDE or SATA hard drives?

I'm using Everest to figure out this information, so if you can tell me where to go to find it, please do! I'm clueless when it comes to that kind of info.

---

### Post by erginemr on 2008-01-11
> **putanitsa said:**
> **theRightNee:**
By the way, thanks everyone for the quick answers. I'm starting to think I might be too dumb for Linux, but hopefully it's not the case and I'll figure this out!

Definitely no! You are as eligible as everyone else in this forum to use Linux. The Ubuntu Live CD has started nasty with a problem with your hardware config, that's all. Linux as a desktop has come a long way and is not inside the geeks' territory any more. And I am sure you will find a way to overcome it and move on, soon.

If worse comes to worst and none of the later suggestions in this thread work, then I would recommend you to download first Linux Mint, and then PC Linux OS Live CD's (both of which provide a more out-of-the-box experience than Ubuntu, in terms of mp3 and DVD movie playback and other closed-source stuff), so that maybe you won't have this problem during thier boot.

---

### Post by EXCiD3 on 2008-01-11
Something must be causing Ubuntu to crash to busybox. What is the text that appears right before the Busybox prompt. Typically the errors encountered are displayed right before it displays the Busybox prompt.

Open terminal and post your output of "lspci" and "lsusb". This will show a list of hardware connected to the pci slots and usb ports of your computer.

---

### Post by ryanVickers on 2008-01-11
> **putanitsa said:**
> 
BusyBox v.1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash) # comm 1
(initramfs) # comm 2
What is this?

comm 1: this is the kernel version I believe, or some script used to start it
comm 2: this is creating a temporary partition in your ram to use as disk space and whatever else it needs while running, hence "ini RAM FS (file system)" if you break it down ;)

---

### Post by putanitsa on 2008-01-11
Ok, so here are the specs
CPU: AMD Athlon XP 1.25 GHz
1.12 GB of RAM
Video card: ATI Radeon 9250
Network Adapter: Realtek RTL8029(AS) PCI Ethernet Adapter / VIA Compatable Fast Ethernet Adapter
My hard drives are ATA, based on this info: MAXTOR 6L040L2  (40 GB, 7200 RPM, Ultra-ATA/133) / QUANTUM FIREBALLP AS30.0  (29 GB, 7200 RPM, Ultra-ATA/100)

**zabien1970:** I've looked at the cd from windows, and I do see many files, it looks like the image was burnt properly. As I said, when I boot from the cd, I do get the first screen asking if I want to start/install/check cd for defects...

**erginemr:** Thanks for the words of encouragement! I tried to install Linux Mint just for the heck of it, and I get exactly the same problem...

**EXCiD3:** There is no text before it goes to busybox. I select start/install, and I can see the ubuntu logo and progress bar (moving) and then I get the busybox screen without any error message beforehand.

**ryanVickers:** Thanks for the info! It could've been masonic plans and I wouldn't have known :p

---

### Post by stevescripts on 2008-01-11
Have you tried a different cd burning program?

I would suggest that you might try isorecorder -
[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

Also, make sure you a using a CD-R, as a R-W wont hold
the entire image.

Dont know anything about Roxio, FWIW.

isorecorder "works for me"

Hope this helps.

Steve

---

### Post by MattTait on 2008-01-11
Note to all who think this is a burning error: It is not.

Ubuntu is defaulting to the internal kernel shell and setting up a temporary filesystem in RAM (RAMFS).

It might be possible that you are attempting to install a 32 bit ubuntu on an AMD 64 bit processor machine. This is a known problem.

During the boot screen, press F6 to get to the command parameters, and delete them all. Put in their place the text:

irqpoll pci=noacpi noapic nolapic acpi=off

---

### Post by bighomer on 2008-01-11
Don't know if this'll help but...
I've had many unsuccessful attempts trying to install, and it was indeed the media. The sony cdrw just wouldn't install. Used a plain maxell cdr, it worked fine.

---

### Post by putanitsa on 2008-01-11
**MattTait:** How would I know if I have an AMD 64 bit machine?
I followed your instructions, and this is what I got:
[IMG]http://farm3.static.flickr.com/2026/2185452037_defdc2e59e.jpg[/IMG]

**bighomer:** I'm using a plain maxell cdr...

---

### Post by putanitsa on 2008-01-14
*bump*

---

### Post by timbounceback on 2008-01-14
OK, so to clarify:
What is happening is that the kernel is looking for a "root=" option at the kernel. You can do this by by hitting F6 and appending the root option there. I know I'm not being specific, but I really don't know that much about this kind of stuff. What do you get when you hit F6 before booting (when at the "start of install Ubuntu" screen)?

---

### Post by dstew on 2008-01-14
I think you should try the Alternate Install CD. It installs the same Ubuntu system using a text-based installer that avoids a lot of the LiveCD-hardware incompatibility issues you are dealing with. Get the Alternate Install CD on the same [Ubuntu Download]("http://www.ubuntu.com/getubuntu/download") page. Just click the box below the Start Download button.

---

### Post by timbounceback on 2008-01-14
> **dstew said:**
> I think you should try the Alternate Install CD. It installs the same Ubuntu system using a text-based installer that avoids a lot of the LiveCD-hardware incompatibility issues you are dealing with. Get the Alternate Install CD on the same [Ubuntu Download]("http://www.ubuntu.com/getubuntu/download") page. Just click the box below the Start Download button.
Agreed.

---

### Post by putanitsa on 2008-01-14
I used the alternate cd and it worked without a problem! Thank you! :) I'm looking forward to using Linux.

---

