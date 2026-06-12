---
title: "UnMounting Windows share"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by marmob on 2007-12-03
I just installed Ubuntu and connected to a windows share OK. I now have the share on my desktop, I would like to disconnect and have the share off my desktop but do not know how this is done. I have Ubuntu installed on a Mac I-book

marmob

---

### Post by the.dark.lord on 2007-12-03
Right click on the windows share, select "unmount".

---

### Post by marmob on 2007-12-03
Thanks, It worked

---

### Post by Brian96 on 2007-12-03
When I try to unmount my Windows share (or any other volume for that matter) I get an error that says "Cannot unmount volume: You are not privileged to unmount the volume..."

This happens on my desktop as well as my laptop in Gutsy (Feisty gives me no trouble), each of which triple boot Windows, Gutsy, and a rotating other Linux OS.

Any ideas?

---

### Post by the.dark.lord on 2007-12-04
> **Brian96 said:**
> When I try to unmount my Windows share (or any other volume for that matter) I get an error that says "Cannot unmount volume: You are not privileged to unmount the volume..."

This happens on my desktop as well as my laptop in Gutsy (Feisty gives me no trouble), each of which triple boot Windows, Gutsy, and a rotating other Linux OS.

Any ideas?

Type this command in the terminal 

```
sudo nautilus
```

and try

---

### Post by the.dark.lord on 2007-12-04
> **marmob said:**
> Thanks, It worked

Please mark this thread as "Solved".

---

### Post by Brian96 on 2007-12-04
> **the.dark.lord said:**
> Type this command in the terminal 

```
sudo nautilus
```

and try

I tried that (actually I used gksu nautilus) but nothing happened. That is, in the nautilus window that came up, only the main filesystem showed up as mounted, although the other drives still appeared on the desktop as mounted.

I had another problem with this method the other day, but I can't remember it.

I also tried "sudo gnome-mount --unmount /media/sda5" and it acted like maybe it worked, but when I tried to run fsck on that volume, it told me it was still mounted.

---

