---
title: "can't write to usr.  How to?"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by op3studios on 2005-05-30
This must be dumb but I can't write to my usr directory which is where I left most of my free space formatted ext3.
Says I don't have write permissions.

I am logged in as my username.  So I guess I need to give my username extended write permissions or??

I mounted a Fat32 partition to share data between windows and ubuntu.
I see the contents of the fat but can't drag them into usr.  Nor can I make a new folder in usr.

Says I don't have write permissions.

I can write to my username folder in the home folder, but that is only 250mb
Should I resize this and if so how?

 I would like to have read write permissions to everything as I need it.

I've searched and the results didn't do it.
thanks

---

### Post by bored2k on 2005-05-30
[QUOTE=op3studios]This must be dumb but I can't write to my usr directory which is where I left most of my free space formatted ext3.
Says I don't have write permissions.

I am logged in as my username.  So I guess I need to give my username extended write permissions or??

I mounted a Fat32 partition to share data between windows and ubuntu.
I see the contents of the fat but can't drag them into usr.  Nor can I make a new folder in usr.

Says I don't have write permissions.

I can write to my username folder in the home folder, but that is only 250mb
Should I resize this and if so how?

 I would like to have read write permissions to everything as I need it.

I've searched and the results didn't do it.
thanks[/QUOTE]
 /usr is a space saved for the superuser. It's the house of important system files you don't want to tinker with. You need to resize. Everything you do goes to /home.

---

### Post by sethmahoney on 2005-05-30
Are you trying to move files to /usr ?  If so, your user space is on /home/yourusername where you replace yourusername with whatever your user name is.  Hope that makes sense.

EDIT: nevermind.  Yeah, use the /home directory, not /usr, and you should probably resize /home

---

### Post by op3studios on 2005-05-30
more info=
                    size            used    unused         flags
 hda1 ext3   1,012         938           74               boot
     a2 ext3   50,300       5,000        45,000
     a3 fat32 21,000        14,500        6,000
     a4 swap  2,055

thanks x2

---

### Post by op3studios on 2005-05-30
now I have to cross the desert to learn how to resize home.
though I must admit I'm having fun! and learning stuff.
thanks for your reply.  I've got usr rights, and can r/w to fat32 part.
Notes=


[http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions](http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions)

changing ownership of non owned files.

I think this is right:
sudo chown system_username /location_of_files_or_folders
(sudo chown yourusername /file path)

---

### Post by digby on 2005-05-31
As a point of interest (that I just learned myself) /usr stands for Unix System Resources.  I'd always just assumed that it was user and thus for use by users as well.  From what I've read, most everything you use should be in your home directory as was mentioned above.  If you want to install other programs for more than just yourself, that is what /opt is reserved for.

---

