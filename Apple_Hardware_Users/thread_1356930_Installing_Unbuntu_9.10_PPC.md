---
title: "Installing Unbuntu 9.10 PPC"
date: 2009-12-16
forum: Apple Hardware Users
---

### Post by TheOtherWong on 2009-12-16
Hi, quite recently I've been trying to test out Unbuntu on my PPC Mac ever since the programs on the computer have been becoming haywire. Basically, I haven't been able to find any luck in installing the .iso into my computer.

At first I tried to burn the iso into one of my CDs but I didn't have enough space. (My CD's are 650mb and the iso is 700+mb) I've looked up the website and there doesn't seem to have an option to order PPC versions of Unbuntu. (I ordered one 6 weeks ago and I tried installing it with the Live CD, my computer could not read it, even while holding down 'C' key)

During those 6 weeks that I have been waiting, I've been trying to install the PPC Unbuntu with my 2gb flash drive. I'm aware that Toast can do the job, but I'm not willing to pay $100 for the program (Since I might as well buy the new mac cd) I have also used 'UNetbootin' and tried to install the iso program with my laptop that runs on windows (since UNetbootin doesn't have a Mac version), but it couldn't read it as well. (Do I have to press something other than 'C' key?

I've also been searching through many forums to find the answer. The simplest way is use Disk Utility (which is missing from my Mac) so that was also a deadend.

I has also heard about this mounting onto a flashdrive business with Daemon Tools, which I don't think I can prepare on my Windows laptop and use it on my mac.

I guess I have 4 different questions.
1. is there a slimmer version of unbuntu (size-wise) which will be pretty much the same thing and can fit on my 650mb cds?
2. will burning at a very slow speed and allowing overburn fit the OS?
3. is there an option to order PPC CDs from the main site?
4. With 'UNetbootin' Do I have to press something other than 'C' key for my mac to read the virtual cd on my flash drive?

Thank you for your time, and I apologize if the answer is out in the open, I've tried to find it to no avail.

---

### Post by solsonik on 2009-12-17
Do they even have a version of 9.10 for PPC? I recently put Ubuntu on a G3 iMac, and the most recent version I could find with a PPC compatible installer was Edgy Eft (which is what I currently have installed and running).

So, your problem may be that you're trying to use the Intel-based installer, which I found out (the hard way) is absolutely not going to work on a PPC Mac.


[B]EDIT:
[/B]Ok, I found the more recent releases of Ubuntu for PPC. So, I guess my comments probably don't apply if you did get the correct one.

---

### Post by linuxopjemac on 2009-12-17
1. alternate installer ([http://cdimage.ubuntu.com/ports/releases/9.10/release/](http://cdimage.ubuntu.com/ports/releases/9.10/release/))

2. no idea, burn at lower speed anyway

3. why not download

4. don't know

---

### Post by Gen2ly on 2009-12-17
Hmm, TheOtherWong there are other ways of booting the iso possibly, but the easiest way you're going to have about it is to get a 700MB CD.  I've messed with this before and it just isnt' worth the hassle.

I've mentioned before that Ubuntu (that use's Gnome) may be a little heavy for that computer, you might want to consider what I told this guy to do to have a lighter install:

[http://ubuntuforums.org/showthread.php?p=8449767#post8449767](http://ubuntuforums.org/showthread.php?p=8449767#post8449767)

---

### Post by TheOtherWong on 2009-12-17
> **Gen2ly said:**
> Hmm, TheOtherWong there are other ways of booting the iso possibly, but the easiest way you're going to have about it is to get a 700MB CD.  I've messed with this before and it just isnt' worth the hassle.

I've mentioned before that Ubuntu (that use's Gnome) may be a little heavy for that computer, you might want to consider what I told this guy to do to have a lighter install:

[http://ubuntuforums.org/showthread.php?p=8449767#post8449767](http://ubuntuforums.org/showthread.php?p=8449767#post8449767)

I read the suggestion and I'm currently installing Debian 5.03.

Just a quick question.

Mac OS X version 10.4.11
1 GHz PPC G4
768 MB DDR SDRAM

Should I go with Debian, Xubuntu or Ubuntu? (Even if I have to buy a bigger CD) Thanks.

---

### Post by rjcalifornia on 2009-12-17
how about using Kubuntu 7.10?

[http://ubuntuforums.org/showthread.php?t=1265921](http://ubuntuforums.org/showthread.php?t=1265921)

---

### Post by linuxopjemac on 2009-12-18
I have Debian Lenny on a Pismo G3/400, installs easily. You only might need to tweak xorg.conf...

---

### Post by TheOtherWong on 2009-12-18
> **linuxopjemac said:**
> I have Debian Lenny on a Pismo G3/400, installs easily. You only might need to tweak xorg.conf...

Hi, what do you mean by tweaking xorg.conf? I'm new to the linux world so It would be great if you can link me to a step-by-step

---

### Post by linuxopjemac on 2009-12-18
Install Lenny PPC first, if it works out of the box, we don't need to do anything. If you don't get into a graphical (X) environment, you report it here.

---

### Post by oswaldkelso on 2009-12-18
> **TheOtherWong said:**
> I read the suggestion and I'm currently installing Debian 5.03.

Just a quick question.

Mac OS X version 10.4.11
1 GHz PPC G4
768 MB DDR SDRAM

Should I go with Debian, Xubuntu or Ubuntu? (Even if I have to buy a bigger CD) Thanks.

I recommend Debian. I have 2 G4's towers a G4 emac and a G3 imac. Kde4 is very nice but crawls even with all the bling off! It needs better hardware to get a fast desktop. I go with the Xfce/lxde install, and add what else I need. It's vey nice and easy to configure, and fast. Gnome is fine also. Lenny is still on Kde3.5 I think, that's fine but most Debian users, once they've got their feet under the table upgrade to testing for the Desktop.

---

