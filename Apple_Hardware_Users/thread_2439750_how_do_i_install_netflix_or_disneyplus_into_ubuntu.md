---
title: "how do i install netflix or disneyplus into ubuntu?"
date: 2020-03-31
forum: Apple Hardware Users
---

### Post by wandwaving on 2020-03-31
any ideas? i installed google chrome and it doesn't work. google chrome says there's something wrong with the architecture.  please help! thanks.

---

### Post by daniewicz on 2020-03-31
What is the error message exactly?

How did you install Chrome?

Is this a new ubuntu install?

---

### Post by Frogs Hair on 2020-03-31
Hello and Welcome

More information on what is the exact error message an what version of Ubuntu might be helpful. Chrome only runs on 64 bit operating systems , but given the information I don't know if that is the problem.

---

### Post by wandwaving on 2020-04-01
the error message is "Wrong architecture 'amd64'. 
i didn't install chrome. there is that error message. 
it is ubuntu 11.04. the Natty Narwhal.

---

### Post by QIII on 2020-04-01
The first thing you need to do is install a supported release of Ubuntu.  Natty went EOL in October 2012.

There is very little point in trying to solve an issue with an unsupported release that old.

---

### Post by SeijiSensei on 2020-04-01
Also, don't even try going the upgrade route from 11.04.  Install 18.04, or soon 20.04, from scratch.

---

### Post by TheFu on 2020-04-01
> **wandwaving said:**
> it is ubuntu 11.04. the Natty Narwhal.

+1 on installing 18.04, today.

A little knowledge about Ubuntu releases seems to be needed.
There are LTS releases of Ubuntu and then there are all the others.  Seems you should only be using LTS release.  All the others, like 11.04 get 9 months of support, no more.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) explains what LTS means.
10.04, 12.04, 14.04, 16.04, 18.04 where all LTS releases.  16.04 has about 1 yr of support remaining. 18.04 has about 3 yrs of support remaining.  See the pattern?  April, even years are LTS.  **Anything else** is not.

Later this month, 20.04 will be released. It is usually best to wait a few months for any early issues to be resolved.  Mid-June, I'll install 20.04 to see if it is ready for our use.  People who are writing books would load 20.04-beta now and live with any issues. Nobody except a developer should use 20.04 in "production" or on their only system before June.

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle) 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Impavidus on 2020-04-01
I assume you already got the point about using a supported release.

Chrome only works on 64 bit, as google dropped support for 32 bits a few years ago. So you have to install a 64 bit version (amd64 &#8211; yes, that's also for intel processors). Upgrading from 11.04 would be very unlikely to work, but upgrading from 32 bit to 64 bit won't work for sure. So make that a fresh install. I hope your hardware supports 64 bit, but most computers since 2000 do.

---

### Post by deadflowr on 2020-04-01
As far as I know Chrome cannot even install on anything older than 14.04.
That's because no release earlier than that can satisfy the dependency requirements.
They actually dropped support for 12.04 earlier than 12.04 was supported for because of that.
(They dropped support for  Chrome on Ubuntu 12.04 in January 2017 where as Ubuntu 12.04's end of life was after April 2017)

---

### Post by wandwaving on 2020-04-02
How do I install a supported release of Ubuntu such as Ubuntu 18.04? I use a Macbook 2007.  I don't think my computer burn CDs. If I use a USB stick I don't know how to open the file. And which file do I open?

---

### Post by howefield on 2020-04-02
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by gsahli on 2020-04-05
Since you said "which file do I open?" it seems like you don't understand the process.
That's OK, we all have to start somewhere.
First thing - your Macbook may or may not support 64-bit. Which model is it? Is it this: Identifiers: Mid-2007 - MB061LL/A - MacBook2,1 - A1181 - 2139

---

### Post by wandwaving on 2020-04-05
Idk what model it is. I tried to download Ubuntu 18.04. But I get stuck around the login/password area. I put the same login/pass I created. It doesn't work. Please help.

---

### Post by gsahli on 2020-04-05
We're having trouble helping because you don't quite give enough info.
Were you successful installing the 64-bit .amd64.iso from CD or USB stick? That will at least tell us if it's 64-bit capable.
If you were successful, did you do the erase and install option?
Have you tried restarting and immediately holding the Option key to get the Mac's built-in bootloader icons to show?

---

### Post by wandwaving on 2020-04-10
I think I downloaded the Ubuntu 18.04 server instead of the desktop. I tried to download Ubuntu 18.04 Desktop. I could download the file but it took too long to burn the file onto a CD. My laptop doesn't really burn .iso files? So it was taking 3+ hours to burn the disc. I couldn't leave my comp on that long. So I was unsuccessful. What should I do?

---

### Post by gsahli on 2020-04-10
It shouldn't take that long to burn, so I guess it's broken.
How about burning to a USB stick? Or, use another computer to burn the DVD?

---

### Post by CelticWarrior on 2020-04-10
> **wandwaving said:**
> I think I downloaded the Ubuntu 18.04 server instead of the desktop. I tried to download Ubuntu 18.04 Desktop. I could download the file but it took too long to burn the file onto a CD. My laptop doesn't really burn .iso files? So it was taking 3+ hours to burn the disc. I couldn't leave my comp on that long. So I was unsuccessful. What should I do?

I really don't know what you're trying to do...
The ISO is much larger than a CD, it fits only in a DVD. Did you meant a DVD or were you actually trying to burn it to a CD, in which case it would obviously fail?
And why use optical media? If you computer can boot from a USB stick then use that, obviously. The XX century ended some 20 years ago.

---

### Post by wandwaving on 2020-04-10
I tried burning it to a USB but I don't know how to install the Ubuntu 18.04 desktop file after it's on the USB and plugged into the computer.

---

### Post by gsahli on 2020-04-11
Macs have a boot manager which you use by pressing and holding the option/Alt key immediately after hearing the gong sound. After a few seconds (maybe up to a minute?), icons for all the bootable devices appear. You select one (EFI boot) and click on the continue arrow. You'll know if you correctly burned the Ubuntu to the USB stick if it shows up and boots when selected.
[https://laptop.ninja/how-to-install-ubuntu-on-a-macbook-pro/](https://laptop.ninja/how-to-install-ubuntu-on-a-macbook-pro/)

PS - saying "how to install the desktop file" tells us you haven't read much about using linux yet...

---

