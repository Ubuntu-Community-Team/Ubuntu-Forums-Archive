---
title: "How can I remove rEFInd"
date: 2013-01-30
forum: Apple Hardware Users
---

### Post by Von Kuser on 2013-01-30
I have a **Macbook Pro 8,2** and I managed to install ***Windows 8*** and ***Ubuntu 12.10*** along with ***Mac OS X Mountain Lion***.

To make my life ‘easier’ I decided to install ***rEFIt***, which did not work correctly and did not display all my operative systems, so I uninstalled it by erasing the folder “***/efi/refit***” using ***OS X***.

Then I stumbled upon ***rEFInd***, which seemed to be a better option as it had been updated as compared to ***rEFIt*** which development seem to have stopped in 2010.

**WHAT HAPPENED:**
Now, rEFInd ‘worked’ in the following manner:

It’s menu showed the following:
[IMG]http://i.imgur.com/pkD2kfq.png[/IMG]

From left to right.:
Option 1.- Mac OS X
Option 2.- vmlinuz-3.5.0-22-generic
Option 3.- initrd.img-3.5.0-22-generic
Option 4.- vmlinuz-3.5.0-17-generic
Option 5.- initrd.img-3.5.0-17-generic
Option 6.- Linux (Ubuntu)
Option 7.- Windows 8

Options 2 – 5: took me to some kind of ‘Terminal’
Options 6 & 7: took me to Ubuntu’s booting menu. (Where I could choose from Ubuntu and Windows 8)

Now, this made having ***rEFInd*** useless for my purposes. So I tried the following to remove it.

_Attempt #1 - Followed ‘Uninstalling rEFInd’ ([http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html))_

I followed the procedure for OS X, which consisted of opening the terminal and doing:

**$ sudo rm -r /EFI/refind** – *Result*: No such directory was found.

I later tried on Ubuntu’s Terminal: 
**# rm -r /boot/efi/EFI/refind** – *Result*: No such directory was found.

_Attempt #2 – Tried Following THIS: [https://bbs.archlinux.org/viewtopic.php?id=152832](https://bbs.archlinux.org/viewtopic.php?id=152832)_

\
Upon trying to do ‘**# efibootmgr -v**’ I got the following message:

[FONT="Courier New"]Fatal:  Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.[/FONT]

Then ran '**modprobe efivars**' in the terminal, but it made no difference.

_Attempt #3 – Ubuntu’s Boot-Repair_

Installed and used the automated ‘***Recommended Repair***’option.

Result: 
Added an 8th option on ***rEFInd***,* option 1 is the only one that boots*, booting ***OS X***, the rest of the options are un-operational/don’t boot an OS.
NOTE: Boot-Repair created this report: [http://paste.ubuntu.com/1589208/](http://paste.ubuntu.com/1589208/)


**CURRENT SITUATION:**

Partition Inspector on Mac OSX shows the following: [http://pastebin.com/sXg6wjxE](http://pastebin.com/sXg6wjxE)

***rEFInd*** initiates upon booting, *only Option 1 (**OS X**) works. *

I need some guidance/help on: 
-Fixing my booting options.
-Removing rEFInd.

If I can’t solve it then I would like to know how to reset my Macbook 8,2 to manufacturing settings. (The recovery option does not appear when I press ‘Alt’ upon turning my laptop on)
Any help would be GREATLY appreciated.

Thank you,
Von Kuser

---

### Post by Garlandg on 2013-01-30
To remove rEFInd, all you have to do is mount the parition it's installed on and remove those files.  Did you run the install script on your mac?  If so, it's probably in your /EFI/ folder.  there will be a folder named "refind" in there.  Remove that, and refind will be uninstalled.  

If you installed using the script with the --esp option, you'll need to mount your EFI partition.  run
```
diskutil list
```in the terminal to see the list of partitions, find the EFI partition, and mount with with 
```
diskutil mount /dev/disk<diskID> 
```Then go to that disk and remove the refind folder from there.

---

### Post by Von Kuser on 2013-01-30
> **Garlandg said:**
> To remove rEFInd, all you have to do is mount the parition it's installed on and remove those files.  Did you run the install script on your mac?  If so, it's probably in your /EFI/ folder.  there will be a folder named "refind" in there.  Remove that, and refind will be uninstalled.  

If you installed using the script with the --esp option, you'll need to mount your EFI partition.  run
```
diskutil list
```in the terminal to see the list of partitions, find the EFI partition, and mount with with 
```
diskutil mount /dev/disk<diskID> 
```Then go to that disk and remove the refind folder from there.

Ok, I ran '[FONT="Courier New"]diskutil list[/FONT]' on my OS X terminal. I got this: [http://pastebin.com/66CtA5qr](http://pastebin.com/66CtA5qr).

Then ran '[FONT="Courier New"]diskutil mount /dev/disk0s1[/FONT]'

But I got the following message:
```
'Volume on disk0s1 failed to mount.'
```

Anything else I could do?

---

### Post by Garlandg on 2013-01-30
I forgot that this partition needs a couple more arguments.
```

mkdir /Volumes/EFI
sudo mount -t msdos /dev/disk0s1 /Volumes/EFI
```That should mount it.

Remember:
Make sure that you don't remove the APPLE folder inside the EFI partition.

if rEFInd is installed in the EFI partition, it will be placed in the root of the partition next to the APPLE folder.

---

