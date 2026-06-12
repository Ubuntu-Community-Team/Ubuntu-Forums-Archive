---
title: "[SOLVED] Desktop icons for smb shares actiing funny - copying files"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by MountainX on 2008-03-19
I created smb shares (by editing fstab) and KDE put icons on my desktop after I mounted the shares. However, all the icons have the same text: "Remote Share (//1..." 

I opened the properties of one and in the general tab I changed the text in the first box from "Remote Share (//192.168.99.10/MyShare)" to "MyShare". When I clicked OK, I got a dialog that said it was copying thousands of files! I don't know where it copied them to or why, but I canceled quickly.

How do I rename these icons so I can see where they point?

How do I find the copied files? 

Thanks

---

### Post by MountainX on 2008-03-20
bump

---

### Post by spiderbatdad on 2008-03-20
You should be able to change the launcher name by right clicking it and selecting rename. When you opened the properties, I believe what you saw was the file indexing to display the total size...not actually copyinf the files anywhere. Now the location must remain the same or the launcher will not point to the share, but the name should be able to change, no problem.

---

### Post by MountainX on 2008-03-20
When I right click there is no option to rename. I'm in Kubuntu Gutsy. My options are:
Open
Copy
Open with Dolphin
Open WIth...
Email File
Unmount
Properties

In Properties, under General, there is a text box that looks like the name. This is what I changed. When I exited by clicking OK (after editing the name in the text box), I got a new progress dialog showing thousands of files to be copied. It is definitely not the size calculation in the properties that I was seeing.

I appreciate any additional info.

UPDATE 1:
The problem happened when I changed the text in the first box from "Remote Share (//192.168.99.10/MyShare)" to "MyShare". I just tried another test. This time I changed the text in the first box from "Remote Share (//192.168.99.10/MyShare)" to "ShareName- Remote Share (//192.168.99.10/MyShare)" and it did not try to copy any files when I closed the properties dialog.

My basic problem is solved now, but I am not going to mark the thread solved until I figure out why I can't freely edit the text in this textbox and where the copied files went. Thanks.

UPDATE 2: I'm giving up. I think this was a freak thing. I'll mark the thread solved now.

---

