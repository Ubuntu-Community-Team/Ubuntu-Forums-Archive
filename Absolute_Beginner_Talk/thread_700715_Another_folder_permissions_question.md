---
title: "Another folder permissions question"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by 3pinner on 2008-02-18
hello,
 If I log on as administrator, how can I copy files to users home folders?
 Every time I try, I get the message that I do not have permission to copy to that folder. 

this is for Ubuntu 7.10 desktop.

Thanks

---

### Post by ruy_lopez on 2008-02-18
```
sudo cp -r folder /home/<user>/
sudo chown user:user /home/<user>/folder

```

sudo gives you temporary root permissions. If you copy folders using sudo, it changes the ownership/group to root. So change it to the user/group that the home folder belongs to, using chown.

EDIT: if the folder you copy has subfolders and files, use "sudo chown -R user:user /home/<user>/folder" to change the ownership of the subfolders/file.

---

### Post by 3pinner on 2008-02-18
thank you!
I should have stated my question a bit more clearly.

I am moving files, and programs,  from a Windows HD to my Ubuntu drive. I need to move those files to my user account, so I'm not logged on as root every time I need to access them. In windows, I had the priveleges as admin to move files whereever I wanted them, but cannot do that in Ubuntu. 
So I'm looking for a simple way logged on as administrator to move the files to my user account and be able to open/use them in that user account.

---

### Post by ruy_lopez on 2008-02-18
(See below)

---

### Post by imT on 2008-02-18
try ```
gksudo nautilus
```
be careful how you use it...

---

### Post by Vadi on 2008-02-18
Alt+F2, and do "gksudo nautilus" - that'll run Nautilus as an administrator, so you'll be able to copy/move files within it however you want.

---

### Post by kaiju on 2008-02-18
i think you should be able to access files on windows partitions with your regular account, too.
that aside, if you use 'gksudo nautilus' to move your files, do remember to change their ownership to your user afterwards, so you'll be able to access them from your account.

---

### Post by 3pinner on 2008-02-18
thanks!
Problem solved...............
I am still in GUI mindset - left over from years with windows, so now I'd like to know what the command line sequence would be if I used terminal to solve the problem the way I did, instead of the GUI
Here's how I did it:
I logged on as user, went to my home folder, properties, permissions, and under the GROUPS listed admn as the group, and gave it CREATE AND DELETE FILES as folder access. 
stupidly simple (kinda embarrassed to post this........)
Now I figure whenever I log on as admin, I can at least copy stuff to my user account.

1) will there be any security issues to doing it this way?

2) what would the command line sequence be to do what I did in GUI?
(this will help me learn the Linux command line a bit better)
Thanks!

---

### Post by ruy_lopez on 2008-02-18
> **3pinner said:**
> what would the command line sequence be to do what I did in GUI?
(this will help me learn the Linux command line a bit better)
Thanks!

If the WindowsHD is mounted, look for it inside /media or /mnt

Once you know the path to the WindowsHD (lets assume it is /media/windowsHD)

if you want to copy a folder called 'blah'
```
sudo cp -r /media/windowsHD/blah /home/yourname/
```

Then to change the ownership and group, so you can read the contents:

```
sudo chown -R yourname:yourname /home/yourname/blah
```

---

### Post by kaiju on 2008-02-18
to find out more about any linux command, read its man page, by typing e.g. "man chown" into a terminal window. you can search through the man page with "/", and "n" will bring you to the next match (useful for quickly finding out e.g. what "-R" in "sudo chown -R ..." is for).

---

### Post by ajgreeny on 2008-02-18
If you just want to copy files from /media/windowsXP to your /home/username folder you don't need to use sudo, but can do it as a user, and therefore do not need the extra step of the chown command.  Don't forget ntfs and fat32/16 format does not support permissions, and therefore if you copy files a user, not root, the permissions and ownership of the copied files will not be a problem, they will already be yours.

---

### Post by kaiju on 2008-02-18
from what i've heard, full ntfs write support should be solved by now (please someone correct me if i'm wrong here). so you should be able to copy or move files from any windows partition the regular way.
that said, we're back to the question: why do you need to use your root account to access files?

---

### Post by ruy_lopez on 2008-02-18
> **ajgreeny said:**
> If you just want to copy files from /media/windowsXP to your /home/username folder you don't need to use sudo, but can do it as a user, and therefore do not need the extra step of the chown command.

I assumed you were copying to different users' homes. Hence the need for logging in as administrator.

---

### Post by 3pinner on 2008-02-18
thanks for the help.
Some clarifications:
1)  I have no problems accessing, reading, or moving junk from  my Windows install to my desktop in UBUNTU either as admin or a user. ubuntu 7.10 reads my NTFS file system fine.

2) My issue was: When logged in as admin on ubuntu, I want to be able to move files at will from  my admin desktop (where most of my windows junk was copied to) to my home/username folder.(not my home/admin folder)

I did this by adding the admin group to the home/username folder so I (logged on as admin) could copy (write) stuff to that home folder.

thanks for the syntax on how to do it in terminal. I'm the curious type. and since I'm dumping windows, I wanna run ubuntu like a pro! :guitar:

---

