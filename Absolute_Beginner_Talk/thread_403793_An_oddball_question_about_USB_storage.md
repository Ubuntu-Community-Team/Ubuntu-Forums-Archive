---
title: "An oddball question about USB storage"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2007-04-07
Here's one for all you knowledgeable types:

Back in my Windows days, I snatched up a[ Sandisk U3 Cruzer Micro 1GB USB Drive]("http://www.sandisk.com/Products/Catalog%28116-NEW__SanDisk_Cruzer_Micro_USB_Flash_Drive.aspx") with U3 software pre-installed. In case you're unfamiliar with U3, it's a small, read-only, autoplaying CDFS partition added to your thumb drive which points Windows (and windows only) to the U3 software, which is basically like a "start button" for a usb drive. Only apps that are U3-capable will work on this menu/launcher, but nothing in the rules says you can't have a folder full of other apps, too - it *is* USB storage, after all.

I installed a handful of U3 apps like Firefox, T-Bird, Trillian, etc. Since people are always asking me why their computers run slow or don't work right, I created a folder for non-U3 programs I like to have on hand, like CCleaner, RegCleaner, TweakXP, a hex editor, and the like.

Now that I'm running Ubuntu, I rarely use this drive for my own purposes, but I still carry it around in case someone hits me with a Windows tech-support brain teaser. On occasion, though, I do access the drive from Ubuntu and keep certain documents up to date, sync my Firefox bookmarks, and things of that nature. If I happen to run across a handy app while milling around online, I'll download it and move it to the directory on the USB device where I keep all my goodies.

Over the weekend, I was staying with a friend and got the inevitable Windows nightmare story. I busted out my USB drive and started to go to work. The oddest thing happened, though: The U3 software (the autorun Windows desktop launcher) was intact and functioning, and all the U3-compliant apps were working fine as well. I had my browser, e-mail, text editor, IM - everything. I went to dig through my folder of utilities and it was **gone.** Not just empty,* but the entire folder was missing.* I didn't understand why, but didn't give it a whole lot of thought. I downloaded what I needed off the net and got her comp up and running. Yay, me!

But here's the kicker: Now that I'm home, I plug the U3 drive back into my Linux box and my app folder is there again, with everything inside.

I know the storage area of the drive is formatted as a FAT32 partition, so both Windows and Linux should be able to access it without any conflicts. What could have happened that would have disappeared this folder?

Any thoughts?

---

### Post by LaurelLynn on 2007-04-07
Dear detroit/zero,

What first comes to mind is attributes.  Both operating systems let you set attributes on files and folders: hidden, read-only, archived, ...

There could be a Linux attribute set on the folder that is not compatible with Windows. It often hides folders marked hidden or system...

I would try making a brand new folder on the memory stick, in Windows,  then in Linux, copy the files from the original.  Windows should at least see the folder, and probably the files.

Laurel Lynn

---

### Post by detroit/zero on 2007-04-11
Thanks, LaurelLynn. That did work as a temporary fix. I say temporary because having a duplicate 150MB (and growing) folder on my 1GB stick is going to eat up valuable space.

Now I'm just left trying to properly modify the permissions/attributes to allow Windows machines to access the files. I'm not sure where to start on that one, but I imagine I'll dig the answer(s) up somewhere (unless anyone else has ideas...)

Thanks again!

---

### Post by LaurelLynn on 2007-04-11
Glad I could be of help!

I would keep the folder that Windows can read and concider removing the other to save space, if windows can see it, Ubuntu will see it too, and can read and write files. It is probably only the folder itself that is having the problem.

Note:  FAT32 has no permisions, only attributes one of which is read only (in windows you have to clear it before you can delete or change the file, but everyone is allowed to do so),  both operating systems **should** have read/write access.

---

