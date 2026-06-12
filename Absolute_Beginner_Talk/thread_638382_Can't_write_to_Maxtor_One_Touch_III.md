---
title: "Can't write to Maxtor One Touch III"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by dabode on 2007-12-12
So I have a Maxtor One Touch III 60GB external USB hard drive that I've been using for my Vista laptop, and I have some files on my Linux box that I want to transfer to my laptop via the external drive, but For some reason I'm not allowed to write to it. The Linux box recognizes the drive, and I can open it, and view the files on it, and even copy them to the Linux machine, but I am not allowed to write to it. I don't even have the option to create a new folder on the drive. It is also not password protected when I use it on my Windows computer, so I don't think that's an issue here. I've seen other threads here regarding the drives not mounting, but I'm assuming that it IS mounted because it's recognized, and I can pull files from it. Anyone have any insight on this?

---

### Post by dabode on 2007-12-12
Also, when I right-click the drive and got to properties, on the permissions tab it says "You are not the owner, so you can't change these permissions". Owner is "root" and group is "root" and access for everything is set to read-only.

---

### Post by dabode on 2007-12-12
I could really use some help on this. I'm sure it's a simple fix. I just need to know how to changes permissions.

---

### Post by skrribble on 2007-12-12
im assuming that the hard drive is formated to ntfs???

if it is, have you downloaded and installed "ntfs configuration tool"???

after doing this from add/remove, open the program and enable read/write on ntfs drives.... then everything should magically work

---

### Post by dabode on 2007-12-12
I'll give that a try. Thanks

---

### Post by dabode on 2007-12-12
I solved the problem but I feel pretty stupid. It was all because I didn't "safely remove" the hard drive last time I disconnected it from my Windows machine. After plugging it back into the the Windows PC, and safely removing, I'm now able to write to the drive when plugging it into the Linux box.

---

