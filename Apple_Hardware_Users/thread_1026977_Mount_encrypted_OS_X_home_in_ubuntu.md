---
title: "Mount encrypted OS X home in ubuntu"
date: 2008-12-31
forum: Apple Hardware Users
---

### Post by JairunCaloth on 2008-12-31
Hey guys, I've got filevault setup on my home directory, and would like to mount it in ubuntu. Any ideas?

---

### Post by JairunCaloth on 2008-12-31
So after some more research and poking into how filevault encrypts I've found that it uses AES encryption, but it does something weird. It's not a flat image, but instead a bunch of "bands".

---

### Post by mkvnmtr on 2009-01-01
MOL or Mac on Linux should let you run your mac system inside Linux but today I mam trying to install and can't seem to get the dependencies to work. I think the have had some trouble keeping the updating distros from breaking their system. You might try downloading from Source Forge or try a virtual enviroment. That would allow you to run your mac just like you were on it.

---

### Post by JairunCaloth on 2009-01-01
I checked out MOL, but it's for PPC only. I tried to build it just to see if it might work, but I couldn't get it to build. :(

---

### Post by mkvnmtr on 2009-01-01
I am sorry we are in the mac forum and you didn't say which you have . Try a virtual install.

---

### Post by cyberdork33 on 2009-01-02
I don't think it will work out, but you can google about mounting encrypted dmg files as it would be similar... Unfortunately, you are using a sparseimage (that is why the "bands") and mounting a sparseimage may not work at all in linux.

---

### Post by JairunCaloth on 2009-01-02
Yeah, from what I can tell it's pretty impossible at this point. I've decided to create an extra partition and encrypt it with truecrypt. I would ditch filevault altogether, but I don't have much choice in the matter.

---

### Post by cyberdork33 on 2009-01-05
> **JairunCaloth said:**
> Yeah, from what I can tell it's pretty impossible at this point. I've decided to create an extra partition and encrypt it with truecrypt. I would ditch filevault altogether, but I don't have much choice in the matter.
Well, what I do is create a seperate encrypted dmg in my home folder to store sensitive information at work. This way, I don't have to encrypt the entire home folder. (Things like music and pictures don't need to be encrypted...)

---

