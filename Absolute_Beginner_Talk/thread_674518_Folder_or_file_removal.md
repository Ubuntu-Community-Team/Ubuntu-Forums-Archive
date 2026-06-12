---
title: "Folder or file removal"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by palika on 2008-01-21
I'm new to Linux, new to Ubuntu, so forgive me if I talk kindergarten-like.
I have Ubuntu 7.10 installed and it's working great, except this, to which I can't seem to be able to find a solution anywhere (I tried).
I downloaded a 1 GB sized file of a game, called X-Plane flight simulator (ported to Linux), which doesn't install as a package, instead it creates a folder and deposits different sub folders there. 
Now I changed my mind and want to get rid of it (need the space), but when I try to remove the folder (and its contents) I get the message that I have to be the 'owner' to touch that folder (I cannot change the permissions).
So I try to log in as root (or sudo) then cd to the folder, but then it's giving me the 'no such file or directory' message.
I also tried the recursive removal method, same result.
That folder is untouchable.
Help????

---

### Post by jleaker01z on 2008-01-21
Click Applications>Accessories>Terminal

Type "gksudo nautilus"

This will open a file manager with 'root' priviliges.  BE CAREFUL.  You can really mess up your system if you delete the wrong things.  Make SURE you are only deleting what you need to, then close that file manager.  DO NOT USE IT for routine tasks.

Dont forget, this root priviliged file manager will start in 'roots' home directory.  Your home directory will be located at /home/username.

---

### Post by Dopski on 2008-01-21
Thank you very much jleaker01z, this likewise solved my problem on deleting files I previously can't delete. 

Maraming Salamat! ( This is Tagalog words for "Thank You Very Much")

---

### Post by jleaker01z on 2008-01-21
You're welcome :)

---

### Post by palika on 2008-01-22
Great advice, thank you very much.

---

