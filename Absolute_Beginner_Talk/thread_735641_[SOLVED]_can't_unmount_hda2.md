---
title: "[SOLVED] can't unmount hda2?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Calindae on 2008-03-25
I can't unmount hda2 says it is busy is there anyway to force it?

---

### Post by c-ron on 2008-03-26
Rebooting unmounts your drives... ;-)
But seriously, something is accessing that drive and should probably not be forced to unmount.
Close any file manager windows you might have open, close terminals, check all virtual consoles to make sure none are in a directory on that driver  (Ctrl+Alt+F1 for example.. ps. get back to Xserver with Ctrl+Alt+F7)

You might have a zombie or hanged process running that was accessing the drive. List them with ps -aux | less from the terminal and look for any programs that you've already closed. Kill them with sudo kill (pid) where (pid) is the process ID listed from ps.

---

### Post by Khalis7 on 2008-03-26
> **Calindae said:**
> I can't unmount hda2 says it is busy is there anyway to force it?

What you could try is to type this command in terminal:

```
sudo umount -f /media/drive
```

where you substitute "drive" with the name of your drive that you want to unmount. 

More about unmounting drive by typing code below in terminal:

```
man umount 
```

---

