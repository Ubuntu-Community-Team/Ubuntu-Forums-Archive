---
title: "fstab trouble!"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Slimboyfat on 2008-01-17
Hello to everybody – this is my virgin post

I posted this in Networking, but I suspect I should have put it here!

I’m a complete newbie to all of this and am finding the hands on approach to Linux great, but very challenging (haven’t had to think like this since I tried writing adventure games on a Dragon32 and that was 30 years ago – whatever happened to Scott Adams?)

I’m running Ubuntu 7.10 on an Asus Eee and have been trying to mount a NAS drive (Iomega home network)

I found various helpful threads on the subject here and got as far as creating a folder in media called nasdrive and using the following:

sudo mount -t smbfs //192.168.1.7/PUBLIC /media/nasdrive

This worked fine and I was feeling very pleased with myself

However, I then went on to try and auto-mount on startup and used the following:

sudo vim /etc/fstab
add the following line:
//192.168.0.3/your_path /media/netdrive smbfs

Trouble is, I don’t know what I’m doing really, just copying and pasting sudo commands – pretty stupid of me, I should have quit while I was ahead.

I appear to have created a swap file and buggered things up a bit – the system feels very slow and the internet connection has slowed up for some reason. The mount to the NAS drops in and out too. If I run sudo vim /etc/fstab I get the following:

E325: ATTENTION
Found a swap file by the name "/etc/.fstab.swp"
owned by: root dated: Wed Jan 16 16:09:32 2008
file name: /etc/fstab
modified: YES
user name: root host name: ubuntu
process ID: 5584
While opening file "/etc/fstab"
dated: Wed Jan 9 10:30:48 2008

(1) Another program may be editing the same file.
If this is the case, be careful not to end up with two
different instances of the same file when making changes.
Quit, or continue with caution.

(2) An edit session for this file crashed.
If this is the case, use ":recover" or "vim -r /etc/fstab"
to recover the changes (see ":help recovery").
If you did this already, delete the swap file "/etc/.fstab.swp"
to avoid this message.
"/etc/fstab" 7L, 333C

So, my questions:

1. What does ‘your_path’ mean in this context
2. How do I and should delete the swap file – step by step
3. How do I add a line to fstab and what should it be – step by step
4. Have I caused any other problems elsewhere?

I would be really grateful for any help you can give me

regards

Slimboy...

---

### Post by Nano Geek on 2008-01-17
Perhaps this would help you mount it.
[Mount Windows Shares Permanently ]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28samba%29%7C%28mount%29#head-d14db9e44eb9655a6a09e2c8e936727115340a87")

And as for your questions:
1. It was saying that you should enter the path to the folder you want to mount. You shouldn't actually use the phrase "your_path" unless that's what the folder's called.
2.**sudo rm /etc/.fstab.swp** should remove the file, but I don't know what that file is for. It might be important, so be careful. You might want to try rebooting first to see if that gets rid of the slowness. 
3.The Link I gave should answer this question.
4.I don't think so. Everything should work fine after you get the share mounted.

---

### Post by Slimboyfat on 2008-01-17
many thanks

I didn't actually type your_path - I assumed that it meant the share name on the NAS drive (PUBLIC)??

---

### Post by Slimboyfat on 2008-01-17
I've looked at the link and it makes sense to me, but I don't know how to actually do what it says!
precicely how do I edit my fstab?  (bearing in mind that trying to do this and not knowing what i was doing caused the problems in the first place!)

---

### Post by Slimboyfat on 2008-01-17
sorry - stream of semi comatoseness (long day)

the time and date against the swap file are precicely when I was trying to enter the permanent mount - 
[I]
Found a swap file by the name "/etc/.fstab.swp"
owned by: root dated: Wed Jan 16 16:09:32 2008
[/I]
presumable this does indicate that i could delete it?

---

### Post by Iowan on 2008-01-17
> **Slimboyfat said:**
> sorry - stream of semi comatoseness (long day)
...presumable this does indicate that i could delete it?
or rename it... then delete if nothing really bad happens.

> precicely how do I edit my fstab?
What you did *should*  have worked... or try **gksudo gedit /etc/fstab**.

---

### Post by Slimboyfat on 2008-01-18
thanks - what I mean is, do I just start typing, or click to a certain part of sftab or what?

---

### Post by Nano Geek on 2008-01-18
Usually you just put it on its own line at the bottom of the fstab file.

---

### Post by Slimboyfat on 2008-01-21
I'm pretty convinced that I ought to delete the swap file
If I vim edit it, I just get a whole lot of corrupt junk in terminal (a billion@symbols)
Bearing in mind that it was created precisely at the time I was trying to insert the permanent mount into fstab, and that fstab looks to be OK, doesn't that indicate that the swap file was as per 2?:

(2) An edit session for this file crashed.
If this is the case, use ":recover" or "vim -r /etc/fstab"
to recover the changes (see ":help recovery").
If you did this already, delete the swap file "/etc/.fstab.swp"
to avoid this message.
"/etc/fstab" 7L, 333C

I had already run "recover"

answers on a postcard please

regards
Slimboy

---

### Post by Nano Geek on 2008-01-21
To delete files from using the command line, you use the **rm** command. 
So to remove that file all you need to do is run:```
sudo rm */etc/.fstab.swp*
```

---

### Post by Slimboyfat on 2008-01-21
IMHO - this is what I did

[I]If you make a mistake when saving a file, such as pressing Ctrl-ZZ or closing Vi before saving the file, you'll end up with a swap file (akin to a DOS/Windows temp file) in addition to the original file. Usually the swap file will have the .swp extension. The original file will not contain the recent changes you made; attempting to reopen it will result in an error message. 

The swap file is not readable but can be recovered by typing a command like this at the $ prompt and pressing Enter: 

vi -r {your file name} 

In some extreme cases, recovery is not possible. But in most cases, such as closing Vi before saving, a system crash, or a power failure, recovery works very well. After you recover, you must manually delete the swap file using a command like this at the $ prompt: 

rm .{your file name}.swp [/I]

so I'm going to go ahead and delete it

---

