---
title: "you do not have the permissions necassary to view the contents of &quot;recup_dir*"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by moosky13 on 2008-01-06
I'm trying to follow the directions from another post but I can't seem to get the directory correct.  This "sudo chown -R loginname: recup_dir*" is not working.  I'm replacing the loginname with my login name but my recup files are located in my Documents folder.  How should I type the sudo command.  I'm trying to "restore" the files I've recovered.  I wiped my hard drive the other day.  Hopefully I can read these files.  thanks in advance for anyones help.

---

### Post by PinkFloyd102489 on 2008-01-06
"sudo chown -hR user:group dir"

---

### Post by moosky13 on 2008-01-06
I tried typing what you said.  I get this error: chown: `user:group': invalid user

---

### Post by nowshining on 2008-01-06
changed user to ur username and group to what group u were in or that user is/was in, and remove the quotes -

---

### Post by moosky13 on 2008-01-07
I'm sorry.  I'm not sure what you mean.  My username is "yermom" and I'm confused when you say group.  The files I'm trying to recover is in my documents folder.  Should it look like this:  sudo chown -hR yermom:documents

Thanks

---

### Post by nowshining on 2008-01-08
group is the group ur in, 

is this in ur /home folder

if so and u can't get in

try this instead

open up a terminal

type

sudo nautilus

enter ur pw, ur pw will not show up as u type and this is normal for a security reason, just type it out as usual and press enter when done, u should now get a nautilus window and it being root.

navigate to

filesystem - /home/urusername/

find the folder - and right - click properties - permissions tab

make sure owner is u at least, file files and folders where owner is and change to allow read and write to that folder & the same for files, click apply and if not apply button, press close. Now u should have what u need.

Close out the root nautilus and the terminal

---

