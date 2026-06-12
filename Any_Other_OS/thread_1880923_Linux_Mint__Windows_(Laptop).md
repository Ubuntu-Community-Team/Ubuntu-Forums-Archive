---
title: "Linux Mint / Windows (Laptop)"
date: 2011-11-14
forum: Any Other OS
---

### Post by tazz4vr on 2011-11-14
Laptop is Dell Inspirion w/Linux Mint, many questions to follow, but for now will start with how do I find out if Windows is still installed?

---

### Post by philinux on 2011-11-14
Moved to Other OS talk.

---

### Post by Megaptera on 2011-11-14
> **tazz4vr said:**
> Laptop is Dell Inspirion w/Linux Mint, many questions to follow, but for now will start with how do I find out if Windows is still installed?

In Mint, use Gparted to see what the partition set up is - that might show an 'ntfs' partition poss Windows.

Or, when you boot it up, does the grub menu show Windows as an option? (A bit obvious but I had to ask! :D )

You could run this boot script and post the results: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tazz4vr on 2011-11-14
Total and complete newbie here, sorry!

How do I get into Mint to use Gparted?  
From 'boot up', does not show anything in reference to Windows.

---

### Post by BillyBoa on 2011-11-14
Find the application Software Manager

From there type Gparted to the search box and install it.

Then go to applications and open it.

---

### Post by tazz4vr on 2011-11-14
Found Software Manager and installed the Gparted.

Could not find 'Applications'.... would that be under Software Manager?

---

### Post by BillyBoa on 2011-11-14
To be honest I have a computer in front of me with LinuxMint 12 installed and I assume you are using the previous version.

Let's see now, go to the left corner on Menu and scroll up. Should be somewhere on _Other_ or _System tools_ folders.

---

### Post by BillyBoa on 2011-11-14
I assume that you opened Gparted. Look now for any partitions with **File System** NTFS.

If any we can continue.

---

### Post by tazz4vr on 2011-11-14
okay, new issue... although I found and clicked on the 'install' for Gparted.  After finding the terminal and entering 'Gparted', the return stated that 'gparted' is not installed.  

Do I need to be online when doing the install?

---

### Post by BillyBoa on 2011-11-14
Yes.

If you cannot be online you can use the CD with which you installed the LinuxMint and boot with it but not installing the system. There is a Gparted on the disk and you can use it.

Try to see if there is a File System NTFS

---

### Post by tazz4vr on 2011-11-14
The laptop already had the Linux Mint installed when I got it.  Per the back of the puter, it shows a sticker for Windows XP.  However when she first boots up, there is nothing showing for Windows.  I am trying to find out if the Windows XP is still on the laptop.

I found a tab for 'Filesystems' under System Information, does not show anything for NTFS.  It shows - Column Titles (Usuage - Device - Mount Point) Is there another location I need to look at?

---

### Post by BillyBoa on 2011-11-14
In Menu and from there Accessories there is an app called, Disk Utility. From there if you go to the left panel and click on the Hard Disk, on the right panel you can see your Hard Disk analysed. So there ask for partitions NTFS (Windows).

---

### Post by tazz4vr on 2011-11-14
Would Disk Utility be the same as Disk Usage Analyzer?  Per menu option, Accessories, there isn't an option labeled Disk Utility.

---

### Post by BillyBoa on 2011-11-14
OK don't worry, let's go to the solution even if we don't now if there is a Windows part.



Push CTRL+ALT+T and open a terminal.

On the terminal write

```
sudo update-grub
```

Insert the password and ENTER


Then restart the computer and see if it appears the screen with the option to select between Windows and LinuxMint.

---

### Post by tazz4vr on 2011-11-14
Did not request password....

response reads-
sudo-update: command not found

---

### Post by BillyBoa on 2011-11-14
> **tazz4vr said:**
> Did not request password....

response reads-
sudo-update: command not found

Just copy and paste the code. You have to be precise. To paste on terminal is SHIFT+CTRL+V
or just mouse right click + paste

---

### Post by tazz4vr on 2011-11-14
give me a few mins... gotta put er online!  Was doing this all offline.

---

### Post by tazz4vr on 2011-11-14
okay, so did the copy/paste and it did request password... now what?

---

### Post by BillyBoa on 2011-11-14
I assume that you don't have the password?

---

### Post by tazz4vr on 2011-11-14
oh no, I have it, entered it in and it did it's thing... just not sure what that thing is but the end result was alot of 'found' and then 'done'

---

### Post by BillyBoa on 2011-11-14
Ok now restart to see if appears a screen with choices.

---

### Post by tazz4vr on 2011-11-14
okay.........8-[

---

### Post by BillyBoa on 2011-11-14
It's working?

---

### Post by tazz4vr on 2011-11-14
Nothing on boot up in reference to Windows, just the Linux Mint.

---

### Post by BillyBoa on 2011-11-14
So I'm really sorry. LinuxMint was installed over Windows. There is no solution.
Have a nice day

---

### Post by tazz4vr on 2011-11-14
Thank you so much for the help... I got my answer and solution not needed, I wanted to learn Linux, the time of procrastination is over!  Thank you!

---

