---
title: "Shared Swap Partition"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by menawollas on 2005-10-13
I recently installed hoary to play around with, with the intention of blowing it away and starting again when breezy was out.

One thing I had done was install KDE on Ubuntu, which works fine with the option of choosing how you want to start, but it did leave some odds and ends, in particular whited out icons, on the menus. 

What I now intend to do is to set up my PC so I have the option of booting to Windows, Ubuntu or Kubuntu via Grub, rather then choose the desktop once having started Ubuntu.

If I do this, can Ubuntu and Kubuntu share the same swap partition, or would they need to each have a seperate one ??

Thanks

---

### Post by Wolki on 2005-10-13
[QUOTE=menawollas]If I do this, can Ubuntu and Kubuntu share the same swap partition, or would they need to each have a seperate one ??
[/QUOTE]

Usually yes. In general the swap space isn't used to store any data, and having another linux access tha same partition (if you don't do it at the same time :)) will have no negative effects.
The problem is when you hibernate. Then the contents of your RAM are stored on your swap partition, and if another linux uses that for normal swap, it will overwrite your hibernated session.

---

