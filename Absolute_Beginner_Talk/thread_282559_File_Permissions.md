---
title: "File Permissions"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Frankenchrist on 2006-10-22
I have this problem that I first thought was related to Samba.  When I set up my Samba share I could see folders but not files, and sometimes files and then sometimes not....Anyway, I realized that because I kept copying all of the data from a USB harddrive that had received the data from windows, the file permissions were all screwy...Now I've been monkeying with chmod to no avail -I have a large collection of folders containing mp3's with subfolders etc that I cannot change permissions on in one quick click or command it seems, so I need to just change all of the permissions on the drive itself and then copy them in if possible to avoid having to do it on all the individual files and subfolders.  Is this possible? What commands for mounting the usb hd do I need in order to be able to wipe all of the old permissions?

---

### Post by aysiu on 2006-10-22
I've moved your thread to Absolute Beginner, where I think it's more appropriate to be than Desktop Environments.

I'm not sure if it's Samba related. What filesystem is the USB hard drive--NTFS? FAT32?

By the way, if you want to change ownership recursively, you can do so with this command (hint: won't work with NTFS/FAT32--only after you've copied to Ubuntu's Ext3): ```
sudo chown -R username:username /home/username/foldername
```

---

### Post by Frankenchrist on 2006-10-22
Thanks, my drive is fat 32 but at least you've given me the hope that I can now change the permissions because they are already on the comp... I didn't know how to add an additional user to the command.  I was using a comma in between the usernames and it wasn't allowing it.  I'll go try it now.
Update- it didn't allow multiple usernames- i.e. it didn't allow bob:linda:smith- and if smith is the group, I need linda to get access... That is my problem.  It will only allow bob:smith.  I need everybody to be one happy family because even trying just smith- for some reason linda doesn't have access. I really appreciate the help.

---

### Post by aysiu on 2006-10-23
username:username means owner:group

---

### Post by Frankenchrist on 2006-10-23
I know now- and besides I just gksudo nautilus'ed and was able to right click on all the files and BINGO my noobness hit my in the head like a 12 hour weekend samba setup hammer.... It's working now. Now I have to see if it's secure.  Thanks for helping these forums are great.  (and to make you feel better I only posted twice in that twelve hours) ](*,)  and now :D

---

