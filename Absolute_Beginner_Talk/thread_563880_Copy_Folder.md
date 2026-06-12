---
title: "Copy Folder"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by ThRixXx on 2007-09-30
I cant copy my files to my external hard drive.. It says "You don't have permissions to write to this folder".  I have to make backups, is their a way i can make it work? Using terminal? 

Fanx in advance...

---

### Post by dr.silly on 2007-09-30
sudo nautilus --no-desktop

should do it

or

sudo mv file1 file2

---

### Post by petersjm on 2007-09-30
not sure what that "--no-desktop" does above (anyone care to explain?) but, yeah, if you gksu nautilus from the terminal (or kdesu konqueror in Kubuntu) it will open your file manager with privileges.

---

### Post by ThRixXx on 2007-09-30
nautilus doesnt work, any other help ? It says only "root" has permisions on external hard drive

---

### Post by dr.silly on 2007-09-30
when i look at the command for opening a folder it says nautilus --no-desktop folder, so i assumed it necessary

---

### Post by dr.silly on 2007-09-30
try the sudo mv

---

### Post by ThRixXx on 2007-09-30
I dont know exactly how the "sudo mv" works...

---

### Post by n3tfury on 2007-09-30
sudo gives you root access

see here for the mv command:  [http://www.unet.univie.ac.at/aix/cmds/aixcmds3/mv.htm](http://www.unet.univie.ac.at/aix/cmds/aixcmds3/mv.htm)

---

### Post by vanadium on 2007-09-30
Is this what we need to learn to beginning users? Just load nautilus with root privileges and go ahead? I believe it would make more sense to learn how to grant permissions to the user in the first place.

Anyway, an external drive is normally mounted with full permissions for the user. That he cannot write to the drive might be caused by the drive being in Windows ntfs format.

@ThRixXx: post the output here of the command

mount

This way, we know the name and format of the drive for which you want to gain write access.

---

