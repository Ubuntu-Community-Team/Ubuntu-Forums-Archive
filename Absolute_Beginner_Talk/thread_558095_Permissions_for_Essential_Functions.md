---
title: "Permissions for Essential Functions"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by bill45 on 2007-09-23
This seems a good absolute beginner subject.  I have 7.04 installed, happily adding applications, twiddling with games, etc and this morning inspired to actually start using the system.  That ended abruptly with a door slammed in my face.  

My main purpose using PCs is editing photos, I-net and e-mail, audio streams, collect, record WEBcasts, generally w/MP3 but happy to convert to OGG if necessary.  My first attempt to cut paste from a USB device ended with no permissions in the target directory.  

I created three subdir for this purpose;
/home/audio
/home/photo
/home/documents

*mini rant*
I expect a dialog to pop-up asking for password or to be able to change permissions in properties but none of these obvious choices are available.  Properties permissions page is blanked out because I don't "own" the folder.  If I were designing an OS with the object of recruiting users away from the competition, I would have to make a conscious decision to obfuscate a simple essential procedure by merely stopping the process and not offering any dialog or alternative.  In other words the natural thing to do when observing testing these things would be to generate an error and an alternative work around.  The more intuitive solution for a balked copy-paste is to offer a remedy to complete the process.  I don't mind repeatedly typing passwords based on maintaining security.  I do mind being offered a total blank with no way forward.  Does the Ubu development process include "clean room" testing by non-adepts?   Where is "clippy" when we need him? 
*rant over*

OK, Ive Googled, scanned and searched Ubu forums on permissions-cut-paste, etc.  Ubu tells me I don't own the folders in question so I can't write to them.  I've searched the index in my rickford Grant book and pawed through the file management sections and maybe I missed it.  I've queued up Linux Reality #13  for a review listen.  I've removed the folders and I'm willing to start again to get this right.


Thanks, I know the solution is very fundamental and obvious to all of you "instructors" out there.

Bill
Indiana

---

### Post by tomasp on 2007-09-23
Maybe you created the folders using sudo (making those folders owned by the superuser) and are trying to copy as a "regular" user, is that the case?

If it is, you just need to change the folders permissions, go into terminal and type:
sudo chmod 777 *folder1* *folder2* ...
this will give read, write and execute permissions to everyone on those folders

hope it helps

---

### Post by qamelian on 2007-09-23
The folders you created should not have been created in /home. You should have created them in /home/your_username.

---

### Post by Nikitas350 on 2007-09-23
open the terminal (application ----> accesories--->terminal) and run then following command: sudo chmod -R 770 /home
enter the password
and it is done :)

---

### Post by cmnorton on 2007-09-23
If you are the only one using this system, I'd suggest creating these folders under /home/<yourname>. Usually, /home/<whatever> is a user's login directory.

sudo chown -R fred:fred /home/photos and the other two directories.
sudo chmod -R 700 /home/photos and the other two directories.
Thiese two commands set ownership and permissions respectively. 

/home/<username>

is usually, but not always, reserved for a login name.

---

### Post by Lord Illidan on 2007-09-23
> **Nikitas350 said:**
> open the terminal (application ----> accesories--->terminal) and run then following command: sudo chmod -R 770 /home
enter the password
and it is done :)

No. Don't do that.

Your home directory is **not **/home, it is **/home/username**. You should have made your folders under that directory.

---

### Post by bill45 on 2007-09-24
OK , delay for a day, back to this problem;

I do not have permission to mkdir or copy-move files in my home, or my home/username
I cannot create directory or file manage anywhere on the system.  the Nautilus GUI directory options are grayed out.

How can such a condition be possible?
I have not changed any default settings, I have a very simple login. The system is so "secure" it is essentially useless beyond I-net browsing and playing a few games. 

I am just about ready to login as root and use this as a DOS system. This is too absurd. I want transparent access and permissions in /home and everything below that level, I don't care how "insecure" it is. If necessary I'll encrypt my data files.

Bill

---

