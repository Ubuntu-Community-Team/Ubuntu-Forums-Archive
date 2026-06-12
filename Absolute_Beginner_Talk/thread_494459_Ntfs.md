---
title: "Ntfs"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by blithen on 2007-07-06
I have tried a range of things, and I it is just not working. 
I am not dual booting.
But I do have 2 HDDs one is my main(has linux on it)
And my other is just a random collection of music, and other files. But I made that harddrive back when I had windows. 
So then I download the NTFS config tool that comes with linux, and it doesn't work. I check the box, and I click okay and it doesn't work.
the drive is still read only, any ideas?

---

### Post by Inxsible on 2007-07-06
> **blithen said:**
> I have tried a range of things, and I it is just not working. 
I am not dual booting.
But I do have 2 HDDs one is my main(has linux on it)
And my other is just a random collection of music, and other files. But I made that harddrive back when I had windows. 
So then I download the NTFS config tool that comes with linux, and it doesn't work. I check the box, and I click okay and it doesn't work.
the drive is still read only, any ideas?

It could be a ownership issue. you can change ownership on the mount point to be able to write to it.

```
sudo chown -R <your username>:<your group> <path to mount point>
```

---

### Post by kagashe on 2007-07-06
Any NTFS partition mounted in Linux is owned by root. When you install NTFS config tool the user "root" gets Read/Write permission, unless you have granted the permission to other users while installing it.

Try sudo to write to the partition.

kagashe

---

### Post by blithen on 2007-07-06
what is <your group> exactly?

---

### Post by blithen on 2007-07-07
-Bump-

---

### Post by Inxsible on 2007-07-07
usually your group is the same as your username unless you have specifically changed it.

---

