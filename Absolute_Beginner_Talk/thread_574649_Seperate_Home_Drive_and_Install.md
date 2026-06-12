---
title: "Seperate Home Drive and Install"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2007-10-13
I have a separate home partition, Now I want to install "Gutsy" side by side with my stable "Feisty", my question is can I share my /home partition between the two versions or are there chances of mix up. I'am worried esp about Xorg files.

---

### Post by forestpixie on 2007-10-13
I've read, but have no first hand experience, that it's not a very good idea to share /home partitions.

xorg files should be in /etc/X11 as far as I know.

I had gutsy on a separate partition for a while - didn't get a mix up, except with grub, but I think that was my fault for not telling the install to put it on the right drive/partition

hope that helps some

---

### Post by shearn89 on 2007-10-13
If I were you, i'd wait 5 days and just upgrade to the Gutsy RC. It should all be stable, and you won't have to worry about it. If you upgrade now, you can still boot to your old kernel (which should let everything work if you have probs with the new gutsy one) through grub.

I wouldn't try sharing a home partition - i haven't heard good things.

---

