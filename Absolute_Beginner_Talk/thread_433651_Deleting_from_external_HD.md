---
title: "Deleting from external HD"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by twofished on 2007-05-05
My office has an external harddrive and everyone shares it for back up. When I try to delete my folders there, I get a prompt saying it cannot be deleted because it's on a read-only disk. I also cannot change the permissions in properties because I am not the owner (the owner is root). What can I do? I am new to Ubuntu so please tell me in easy language! Thank you

---

### Post by starcraft.man on 2007-05-05
> **twofished said:**
> My office has an external harddrive and everyone shares it for back up. When I try to delete my folders there, I get a prompt saying it cannot be deleted because it's on a read-only disk. I also cannot change the permissions in properties because I am not the owner (the owner is root). What can I do? I am new to Ubuntu so please tell me in easy language! Thank you

Whats the filesystem of the disk? Is it a native supported one like Reiser or Ext? Or is it maybe NTFS?
If its NTFS you need to use ntfs-3g drivers to read write to it normally.

---

### Post by meborc on 2007-05-05
> **twofished said:**
> My office has an external harddrive and everyone shares it for back up. When I try to delete my folders there, I get a prompt saying it cannot be deleted because it's on a read-only disk. I also cannot change the permissions in properties because I am not the owner (the owner is root). What can I do? I am new to Ubuntu so please tell me in easy language! Thank you

if you need to change the permissions start the nautilus via "sudo nautilus" from terminal... now you have the root permissions... be careful though... because while being root, you have the power to do anything :)

---

### Post by starcraft.man on 2007-05-05
> **meborc said:**
> if you need to change the permissions start the nautilus via "sudo nautilus" from terminal... now you have the root permissions... be careful though... because while being root, you have the power to do anything :)

*dun Dun DUNNNNN* :p

Hope we both helped, if not post back and we will try to think harder :)

---

### Post by Mr.Beast on 2007-05-05
Glad you posted this as this was one of my minor bugbears I had encountered, It just wasn't high on my list of things to hassle people with or search for yet ;-)
My disk is NTFS and I have my music collection on it that I take to work.
I'm going to try the nautilus options first, and then perhaps install NFTS-3g.

---

### Post by twofished on 2007-05-05
Hey thanks a lot for your help. It is NTFS. How do I find/install and use the ntfs-3g driver?

---

### Post by twofished on 2007-05-05
I tried running sudo-nautilus but I don't know the password. I tried my admin password but it didn't work.

---

### Post by starcraft.man on 2007-05-05
> **twofished said:**
> Hey thanks a lot for your help. It is NTFS. How do I find/install and use the ntfs-3g driver?

[This]("http://ubuntuforums.org/showthread.php?t=217009") should help explain.

I don't know why your sudo command doesn't work, unless you manually change the password its the same as the one you log in with >.>

---

### Post by twofished on 2007-05-05
Hey,

Sudo Nautilus worked but 'desktop' is an empty file. How do I locate the external disk file after launching Sudo Nautilus? Thanks for your patience!

---

### Post by drowner on 2007-05-05
> **twofished said:**
> Hey,

Sudo Nautilus worked but 'desktop' is an empty file. How do I locate the external disk file after launching Sudo Nautilus? Thanks for your patience!

I'm going to guess (and im so new, so dont take my word for it) that the problem is you are looking at root's desktop (STOP LOOKING AT ROOT'S DESKTOP! ;) )

go to the very top (filesystem) then into /media and you should see the external drive in there.

Let me know (like i said, im new!)

---

