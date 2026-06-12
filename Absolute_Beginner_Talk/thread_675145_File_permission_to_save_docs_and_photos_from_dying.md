---
title: "File permission to save docs and photos from dying system?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by tomole on 2008-01-22
I am using an Ubuntu boot disk to try to save my docs and photos from a system that has stopped booting from the hard drive. I have both win xp and ubuntu on my hard drive. With the boot disk I am able to explore the file systems but I am not able to transfer the files I want to another device because they have a lock icon on them and a message says that I don't have permission.
I am a total noob when it comes to putting terminal commands together and when I search the forums I can't find an answer that is not very cryptic to me.

 Is there an exact command that I can use to get permission to transfer my files while using the Ubuntu boot disk?

---

### Post by kellemes on 2008-01-22
You probably need to get root-permissions..
You can do this from the terminal like so..
```
gksudo nautilus
```
Assuming you're using nautilus (the filemanager) to do this.

---

### Post by philinux on 2008-01-22
Maybe we can fix the booting problem, whats happening, error messages etc.

---

### Post by tomole on 2008-01-22
> **kellemes said:**
> You probably need to get root-permissions..
You can do this from the terminal like so..
```
gksudo nautilus
```
Assuming you're using nautilus (the filemanager) to do this.
I tried it and get this:

T> o run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ gksudo nautilus
Initializing gnome-mount extension

--- Hash table keys for warning below:
--> file:///

--- Hash table keys for warning below:
--> file:///

(nautilus:9710): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:9710): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
ubuntu@ubuntu:~$ 


My files now have a box with an "x" attached with a message when clicked that says I don't have permission to view.

---

### Post by tomole on 2008-01-22
> **philinux said:**
> Maybe we can fix the booting problem, whats happening, error messages etc.
My Ubuntu stopped booting to a GUI and would only boot to a dos-like prompt.

My win xp now reboots the whole system before it finishes booting.

Grub still boots first.

---

