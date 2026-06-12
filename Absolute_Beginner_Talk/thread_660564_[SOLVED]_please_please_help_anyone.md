---
title: "[SOLVED] please please help anyone"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by magicman5421 on 2008-01-06
For anyone not familiar with the program Truecrypt, it creates a volume inside a file and encrypts it. To decrypt, you enter the password for the volume and it mounts it to a specific directory.

I just mounted a volume to my home directory and it overwrote everything! There's nothing in the recycle bin, nothing anywhere in my home directory! I can't even open the terminal because it seems there are some files necessary for it to open in my home directory. Is there something like a global "undo" button or some way of reversing what i did?

---

### Post by PurposeOfReason on 2008-01-06
I really don't want to be the bearer of bad news, but if you wiped your ~/home, there isn't really anything left that I have ever heard about. That is why it's smart to back it up every now and then.

---

### Post by magicman5421 on 2008-01-06
i didn't wipe home/*, i wiped home/myfolder. Still hopeless?

---

### Post by PurposeOfReason on 2008-01-06
Okay, so it was like /home/pictures and the pictures got erased but it's not in the trash? If it's not in the trash, that's like shift+delete AKA, it's gone forever.

---

### Post by Rhubarb on 2008-01-06
You could run a program called testdisk, it's in the ubuntu repositories.
It allows you to undelete files it finds in a partition.
I recommend you read some online guides about testdisk to see how you can get it to recover any important files you need.

Obviously, it's always good practice to backup your system at regular intervals.

---

### Post by magicman5421 on 2008-01-06
@purposeofreason: no the directory is /home/myfolder and i deleted everything in myfolder, that is documents pictures, all of everything. I'm probably running on borrowed time because I'm typing this from the computer being discussed and firefox is starting to glitch. Oh well, if it's gone forever, I was looking for an excuse to install ubuntu studio anyway. Here it is.
@Rhubarb: synaptic no longer works, none of my programs do...I'm wondering why firefox is still working...
EDIT: uh oh...firefox is starting to glitch...oh well...

---

### Post by ivancamilov on 2008-01-06
Hi... first of all, when you shift+delete your things aren't gone forever. Actually, it is pretty hard to completely erase a file from your disk (which is great for a typical user, but terrible for security).

I've never used 'testdisk' myself, but it seems to be just the solution for your problem.

---

