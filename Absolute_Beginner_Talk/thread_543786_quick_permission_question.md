---
title: "quick permission question"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by gav616 on 2007-09-05
just need someone to tell me how to do this,

i have a drive @ 

/storage

currently i did;


sudo chown -R gav:gav /storage 
then
sudo chmod -R 755 /storage

but what i want is;

Files;
User - Read, Write
Group - Read
Others - Read

Folders;
Users -  Read, Write, Execute
Group - Read, Execute
Others - Read, Execute

Commands please?

would i have to 777 all then go inside every folder to set the files permission not to execute?

---

### Post by Nythain on 2007-09-05
this MIGHT work
sudo chmod -R 644 /storage
sudo chmod -R a+X /storage
im sure there's an easier way, but i dont know how to throw the +X for everyone using the number junk

Edit for the third time (one of these days ill pay attention to what im typing)
it also looks like it can be done similar to this
sudo chmod -R =r,u+w,a+X /storage so you could give that a whirl also i guess

---

### Post by gav616 on 2007-09-05
thank you for the very quick response, that worked

love this community :)

---

