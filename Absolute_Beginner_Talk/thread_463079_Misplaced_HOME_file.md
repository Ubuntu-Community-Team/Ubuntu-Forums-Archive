---
title: "Misplaced HOME file"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by pbhill on 2007-06-03
After trying to set up file sharing  with another computer, (Winxp) I somehow moved my HOME folder to the /root  directory. I now get this caution upon startup: 

"User's $HOME/dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions, User's $HOME directory must be owned by user and not writable by others."

How can I undo this? And what does it mean by 644 permissions?
Thanks for any help.

---

### Post by chili555 on 2007-06-03
When you open Nautilus or Konqueror, and navigate to the highest level /  do you see /home or is it just gone? If it is just gone, open a terminal and:```
cd /
mkdir home
cd home
mkdir user
```Substitute your actual user name here. Now you have the directories restored, ready for all the files, etc.```
sudo mv /root/home/user/* /home/user
cd /home/user
ls -al
```See all your files, etc.? Good! Does *user* own them or *root?* If user does not own them, you can:```
sudo chown -R user /home/user/*
```> And what does it mean by 644 permissions?From man chmod:>  A  numeric  mode  is  from  one  to four octal digits (0-7), derived by adding up the bits with values 4, 2, and 1.   Any  omitted  digits  are assumed  to  be leading zeros.  The first digit selects the set user ID(4) and set group ID (2) and sticky (1) attributes.  The  second  digit selects  permissions  for  the  user who owns the file: read (4), write(2), and execute (1); the third selects permissions for other users  in the  file’s group, with the same values; and the fourth for other users not in the file’s group, with the same values.Your session thinks it cannot open *dmrc* because the permissions are wrong; actually, it can't open the file because it has moved and left no forwarding address!

---

### Post by pbhill on 2007-06-04
Thanks for the reply!
Well that didn't seem to work... Now I can't start Ubuntu. After entering my password I get about 10 seconds before it tells me to use the failsafe terminal.  So I'm thinking before i dig this hole too deep, I'll just do a quick reinstall from the live CD. However, No matter WHAT i do, it keeps booting from the hard disk. I hit F12 and select CD but no dice.  Now  I'm really stumped... Where to go from here? (Fortunately I have my other box running, even if it is winxp.)

---

