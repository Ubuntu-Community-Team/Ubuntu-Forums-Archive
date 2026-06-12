---
title: "Ubuntu permission problems when mounting an apple drive"
date: 2010-07-16
forum: Apple Hardware Users
---

### Post by billybobby2010 on 2010-07-16
I cannot access the hard drive of my Macbook through a normal lauch (the computer shuts down), so I try to copy some files with Ubuntu Live CD 10.04. First time user. Looks great but a bit complicated for me. So far I did: 

sudo su
mkdir /media/apple
mount /dev/sda2 /media/apple -o umask=000

Then, I have access to my hard drive but there are small 'x' on the icons. Thus I did:

gksudo nautilus

Bingo! The 'x' are no more there anymore and I can open the files, for instance with OpenOffice. Yet, I cannot modify or copy the files: 'you do not have the permission necessary...'. Nor can I 'save as': error saving the document xxxxx: xxxx/xxxx/xxx/xxx does not exist. 

I just want to save some files on my external hard drive. Don't know much how to play with the permissions. Please help me. Thanks.

---

