---
title: "File and Folder Permissons and being able to edit my files"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-11-09
I have a drive that is split in to 4 partitions:

Win xp OS >>>  / H O M E  >>> Ubuntu OS >>> swap

All my Files for both windows and ubuntu are in the /home partition.

when i was on my regular user account on ubuntu i was trying to copy some images over to the home directory and found that i did not have permission to copy or create files in that directory. so i did a GUI log in as root (I Knows, but i dont no how to do it from the terminal) and went to /home/james/documents and made that entire "documents" folder, including all the folders inside able to have folders created and deleted from it.

However all the files inside such as music files and picture files and text files are still locked and i cannot edit them, i can view or listen to them, but i cannot make changed then save.

i don't want to have to go to every file while logged on as root and change the permission. is there any quicker way to do this?

thanks

---

### Post by taurus on 2006-11-09
Are you trying to copy stuff from XP to your $HOME account?

---

### Post by Jamesbowden on 2006-11-09
no im working in ubuntu

---

### Post by taurus on 2006-11-09
I know you are working in Ubuntu but are you trying to copy files from your XP partition to your $HOME?

---

### Post by Jamesbowden on 2006-11-09
No, I was trying to copy from my ubuntu desktop, anyway its not the copy im haveing a problem with, i sorted that out by doing a GUI log in as root and letting people create/delete files in my /home/james/documents directory.

the problem i'm having is the pictures, images, text files, music files, videos ect. are allset so that no other user apart from root can edit them, only view them. and i dont want to have to do another GUI log in as root and edit the permissions one by one.

sorry if i didn't make myself clear, im rely dyslexic and find it hard to word things.

---

### Post by taurus on 2006-11-09
Okay, let's try this again.  You mount your Windows XP partition in your $HOME directory and you have problems moving or copying stuff in there!

---

### Post by Jamesbowden on 2006-11-09
lol, ok forget windows xp for now, i only mentioned it because i thought it might be affecting things.

ok.

first i was trying to copy an image from my desktop in ubuntu to the directory "/home/james/documents". I got a message telling me that i did not have permission to create files in this directory.

so then i logged on as root in ubuntu, and right clicked on "/home/james/documents" and went to permissions, and then changed the drop down menu under "others" to "create and delete files" and then applyed changed to all sub-directorys as well as the folder its self.

after doing that i logged back on as my user "james" and went to edit some pictures and text files in the "/home/james/documents" directory and found that i could not edit them, only view them. and i also found that it was the same for all other files such as. music, video, scripts ect.

is their anyway to change the permission for all these files at once so that i can edit them from my user "james"

hope that made it clearer

---

### Post by taurus on 2006-11-09
Okay, paste the output of these two commands from a terminal, Applications -> Accessories -> Terminal, then.

```
ls -la /home/james
ls -la /home/james/documents
```

p.s.  Don't include files/directories that you don't want others to see...

---

### Post by Jamesbowden on 2006-11-09
It didn't work man.

heres the out put of the terminal.
i still cant edit my image, text, music or video files.

```
james@James-laptop:~$ ls -la /home/james
total 672
drwxr-xr-x 29 james james   4096 2006-11-09 18:23 .
drwxr-xr-x  6 root  root    4096 2006-11-09 17:46 ..
drwxr-xrwx  2 james root    4096 2006-11-07 21:15 .automatix
-rw-------  1 james james    520 2006-11-09 18:48 .bash_history
-rw-r--r--  1 james james    220 2006-11-06 21:59 .bash_logout
-rw-r--r--  1 james james    414 2006-11-06 21:59 .bash_profile
-rw-r--r--  1 james james   2227 2006-11-06 21:59 .bashrc
drwxr-xrwx  3 james james   4096 2006-11-07 21:26 .config
drwxr-xrwx  2 james james   4096 2006-11-09 17:46 Desktop
-rw-------  1 james james     26 2006-11-07 19:19 .dmrc
drwxr-xrwx 13 root  root    4096 2006-11-08 16:28 Documents
-rw-------  1 james james     16 2006-11-07 19:19 .esd_auth
lrwxrwxrwx  1 james james     26 2006-11-06 21:59 Examples -> /usr/share/example-content
-rw-r--r--  1 james james 483359 2006-11-07 21:14 .fonts.cache-1
drwxr-xrwx  4 james james   4096 2006-11-09 18:00 .gconf
drwxr-xrwx  2 james james   4096 2006-11-09 18:49 .gconfd
drwxr-xrwx 21 james james   4096 2006-11-09 17:22 .gimp-2.2
-rw-r-----  1 james james      0 2006-11-09 17:50 .gksu.lock
drwxr-xrwx  3 james james   4096 2006-11-07 19:19 .gnome
drwxr-xrwx 10 james james   4096 2006-11-09 17:56 .gnome2
drwx------  2 james james   4096 2006-11-07 19:19 .gnome2_private
drwxr-xrwx  2 james james   4096 2006-11-07 21:02 .gnupg
drwxr-xrwx  2 james james   4096 2006-11-07 21:16 .gstreamer-0.10
drwxr-xrwx  2 james james   4096 2006-11-07 21:18 .gtkpod
-rw-r--r--  1 james james     87 2006-11-09 18:15 .gtkrc-1.2-gnome2
-rw-------  1 james james    513 2006-11-09 18:00 .ICEauthority
drwxr-xr-x  2 james james   4096 2006-11-09 18:14 .icons
drwxr-xrwx  3 james james   4096 2006-11-07 21:20 .macromedia
drwxr-xrwx  3 james james   4096 2006-11-07 19:19 .metacity
drwxr-xrwx  3 james james   4096 2006-11-07 20:44 .mozilla
drwxr-xrwx  3 james james   4096 2006-11-09 17:56 .nautilus
drwxr-xrwx  3 james james   4096 2006-11-09 16:55 .openoffice.org2
drwxr-xrwx  9 james james   4096 2006-11-07 21:26 .opera
drwxr-xrwx  2 james james   4096 2006-11-07 21:25 .qt
-rw-------  1 james james   1327 2006-11-09 18:17 .recently-used
-rw-r--r--  1 james james   6551 2006-11-09 18:17 .recently-used.xbel
-rw-r--r--  1 james james      0 2006-11-07 20:47 .sudo_as_admin_successful
drwxr-xr-x  2 james james   4096 2006-11-09 18:14 .themes
drwxr-xrwx  4 james james   4096 2006-11-07 21:36 .thumbnails
drwxr-xrwx  2 james james   4096 2006-11-09 17:55 .Trash
drwxr-xrwx  2 james james   4096 2006-11-07 21:03 .update-manager
drwxr-xrwx  2 james james   4096 2006-11-07 19:19 .update-notifier
-rw-------  1 james james    123 2006-11-09 18:00 .Xauthority
drwxr-xrwx  2 james james   4096 2006-11-07 21:36 .xine
-rw-r--r--  1 james james  28480 2006-11-09 18:23 .xsession-errors
james@James-laptop:~$ ls -la /home/james/Documents
total 52
drwxr-xrwx 13 root  root  4096 2006-11-08 16:28 .
drwxr-xr-x 29 james james 4096 2006-11-09 18:23 ..
drwxr-xrwx  9 root  root  4096 2006-11-08 08:04 Applications
drwxr-xrwx  3 root  root  4096 2006-11-06 22:53 Back ups and Records
drwxr-xrwx 15 root  root  4096 2006-11-06 22:53 E-Books
drwxr-xrwx  4 root  root  4096 2006-11-06 22:55 Games
drwxr-xrwx 12 root  root  4096 2006-11-09 17:34 Pictures
drwxr-xrwx  4 root  root  4096 2006-11-06 22:56 PSP Tools
drwxr-xrwx  5 root  root  4096 2006-11-06 22:51 Rich Media
drwxr-xrwx  7 root  root  4096 2006-11-08 08:00 Scripts
drwxr-xrwx  6 root  root  4096 2006-11-08 16:31 Updater
drwxr-xrwx  4 root  root  4096 2006-11-08 18:03 Web Sites
drwxr-xrwx  6 root  root  4096 2006-11-06 22:10 Work
james@James-laptop:~$ 


```

---

### Post by taurus on 2006-11-09
Okay, /home/james/documents is not the same as /home/james/Documents since Linux/Unix is case sensitive.  At the prompt, change the permissions of /home/james/Documanets again with

```
sudo chown -R james:james /home/james/Documents
```
Now, you should own /home/james/Documents and you can do whatever you want with it without becoming root...

---

### Post by Jamesbowden on 2006-11-09
Thanks man, that worked.

Sorry i am so bad at explaining things.

thanks for being so patient.

---

### Post by taurus on 2006-11-09
> **Jamesbowden said:**
> Thanks man, that worked.

So you are the owner of those files/directories again, eh!

> Sorry i am so bad at explaining things.
thanks for being so patient.
No sweat at all.  That's why I asked those questions to make sure I knew what the problem was first before I gave you a solution.  Slowly but we got it done.  ;)

---

