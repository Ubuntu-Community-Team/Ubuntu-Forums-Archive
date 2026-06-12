---
title: "Operative System not found."
date: 2011-06-30
forum: Any Other OS
---

### Post by Mr. ViC on 2011-06-30
So, I'm here in the name of a friend in trouble.

He is using mint, and what he did was this:

He went to Gparted, created a NTFS partition to install Windows XP.

He rebooted with window's CD, ready to install it, but it was not able to do it (I guess I can figure the way to do this later).

He then rebooted again, tried to go through Linux and well, something like "Operative System not found" popped up.

He then went through the live CD, did a:

```
sudo fdisk -l
```

And this came up:

[img]http://uppix.net/3/8/b/5517d337c346a549a24dfa83a5997.png[/img]

Any ideas now?

Thank you very much in advance.

---

### Post by Rubi1200 on 2011-07-01
Hi,
to get a better overview of what is going on, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

You can also use the Mint CD for this of course.

---

