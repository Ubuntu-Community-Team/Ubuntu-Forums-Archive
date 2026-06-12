---
title: "problem installing rEFInd"
date: 2017-01-10
forum: Apple Hardware Users
---

### Post by joannacw on 2017-01-10
I'm trying to install rEFInd to my Mac prior to installing Xubuntu on a partition. I was trying to follow the steps given at [http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)  I ran into a problem at "Drag and drop the install.sh file from the downloaded zip file into the terminal window and press Enter to run it." I didn't see an install.sh file. I tried, instead, dragging ang dropping refind-install, and got the following message:

```
Mac-Intoshs-MacBook:~ macintosh$ /Users/macintosh/Downloads/refind-bin-0.10.4/refind-install 
Not running as root; attempting to elevate privileges via sudo....

WARNING: Improper use of the sudo command could lead to data loss
or the deletion of important system files. Please double-check your
typing when using sudo. Type "man sudo" for more information.

To proceed, enter your password, or type Ctrl-C to abort.
```

I aborted.  Should I have gone ahead? Did I pick the wrong file? (I didn't see anything else in the zip file which said 'install" at all.) Or is the problem that my several-year-old comupter is too old for the latest version of rEFInd? I tried googling but didn't find a listing of system requirements for rEFInd's different versions. Is there a better way than rEFInd to install Xubuntu on a partition?

Sorry I have been posting co many questions lately. I hope to stop doing this soon. The more I ask and try, the more I realize how little I understand.

---

### Post by slickymaster on 2017-01-10
*Thread moved to **Apple Hardware Users**.*

---

### Post by &amp;KyT$0P# on 2017-01-10
According to [this instructions]("http://www.rodsbooks.com/refind/installing.html#installsh") from the author of rEFInd, you're running the right script.

So yes, go ahead and enter your password.

---

### Post by joannacw on 2017-01-11
Thanks, halogen2! I was delayed for a while by the fact that I didn't seem to have a password for my used Mac, but now I've gotten around that and installed rEFInd succesfully, as I thought. At any rate it allowed me a choice between booting from my minimal CD to install Xubuntu and booting in OS X.  

I completed the install from the CD, putting Xubuntu in a partition on the HD, and then rebooted in OS X, ejected the CD and rebooted again.  This time OS X was the only choice I got in the rEFInd boot screen.
I did get a warning during the install process saying that I hadn't created a reserved BIOS boot area. I tried creating a third partition labeled "Reserved BIOS boot area" but that plainly didn't help;I left 10 GB of free space outside the OS X and Xubuntu partitions and hoped that would suffice--but plainly it did not. Can I go back in, either from Mac OS X (where the disk utility does show the partitions I created as being in place) or via the minimum install CD, and do whatever needs to be done to create a boot area?  Where would I find out what needs to be done to create a boot area? Sorry for the constant questions.

---

### Post by &amp;KyT$0P# on 2017-01-12
> **joannacw said:**
> I did get a warning during the install process saying that I hadn't created a reserved BIOS boot area. 
:confused:
Er, what type of Mac do you have?

If you don't know, you should be able to access it in Mac OS system information.  See where it says "MacBookPro9,1" in my signature?  Look for something similar to that.

Also can you please open Gparted on the live CD, select to display your Mac's disk, and post a screenshot of what it shows?

---

### Post by joannacw on 2017-01-12
Sorry! I forgot that I'd put my Mac system information at the top of my other open question thread, not this one.
[COLOR=#000000]I have a MacBook Pro with a 2.16 GHz Intel Core Duo processor and 2GB 667 MHz DDR2 SDRAM  [/COLOR] running Mac OS X 10.6.8
My  CD is a minimal install CD not a full-featured one--can I still open Gparted from that? Or take screenshots from it?

---

### Post by &amp;KyT$0P# on 2017-01-12
> **joannacw said:**
> [COLOR=#000000]I have a MacBook Pro with a 2.16 GHz Intel Core Duo processor and 2GB 667 MHz DDR2 SDRAM  [/COLOR] running Mac OS X 10.6.8
What is the model identifier?

> My CD is a minimal install CD not a full-featured one--can I still open Gparted from that? Or take screenshots from it? 
You can if its live environment has a GUI.  If you have just a console type interface, don't bother reading the rest of this post.


Do you see Gparted in the menu, under "System" or something like that?  If not, run this -
```
sudo apt-get install gparted
```

Let's get a screenshot program too -
```
sudo apt-get install scrot
```

Now open Gparted and open a Terminal.  In Gparted, select to display your Mac's internal disk.  Then, in the Terminal, run -
```
scrot -s -d 2
```
Click the Gparted window to select it for a screenshot, then quickly (within the 2 seconds) click it again to bring it above the Terminal.  Once the Terminal command exits, you should have a screenshot in the live CD user's home folder.

---

### Post by joannacw on 2017-01-12
No GUI on the CD. I was going to have to pick that up myself after the basic installation.

Perhaps then I need to just buy a DVD, download the full version of Xubuntu, and overwrite the minimal install?

Also one very ignorant question: where would I find the model identifier for my MacBook Pro? I bought it used so don't have original manual or packaging...

---

### Post by &amp;KyT$0P# on 2017-01-12
> **joannacw said:**
> No GUI on the CD. I was going to have to pick that up myself after the basic installation.

Perhaps then I need to just buy a DVD, download the full version of Xubuntu, and overwrite the minimal install?
Yes I would recommend that if possible.  You need to redo the installation anyway (more on this after I look up a few things about your Mac model identifier).

> Also one very ignorant question: where would I find the model identifier for my MacBook Pro?
Can't remember exactly where to get this on Mac OS.  From memory... maybe Applications > Utilities > System Information.app?  Or Apple menu > About This Mac?

---

### Post by joannacw on 2017-01-13
Thank you again! System Profiler says this is a MacBook Pro 1,2  with one Intel Core Duo processor (speed 2.16 GHz,), two cores, a 2 MB L2 cache, 2 GB of memory, and a bus speed of 667 MHz.  Am I correct in thinking that with this system I should be picking up the 32-bit, not the 64-bit, version of Xubuntu? 
Thanks again.

---

### Post by &amp;KyT$0P# on 2017-01-13
You're welcome!

> **joannacw said:**
> System Profiler says this is a MacBook Pro 1,2
Which is a 32-bit EFI machine.  Looks like Ubuntu doesn't really support 32-bit EFI, so you'll need to try installing in BIOS mode.

**Before installing**, you'll need to create a [BIOS boot partition]("https://en.wikipedia.org/wiki/BIOS_boot_partition").  This is a 1-2 MB unformatted partition, with the "bios_grub" flag set.  You can do all this within Gparted.

I am not sure whether there are requirements of the location on disk of the BIOS boot partition.

> Am I correct in thinking that with this system I should be picking up the 32-bit, not the 64-bit, version of Xubuntu? 
Yes.

---

