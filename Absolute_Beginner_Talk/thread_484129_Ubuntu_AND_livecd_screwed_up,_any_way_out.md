---
title: "Ubuntu AND livecd screwed up, any way out?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Freeman163 on 2007-06-25
Well, i originally had a problem where i somehow overfilled my harddrive, and i couldnt log in because "GDM cannot write to the authorization file. this may be because your drive is full, or because it is not installed properly. either way, it is impossible to log in. please contact your systems administrator."

After that, I followed some advice i was given- i booted with the livecd and used the terminal mode to delete a few extra files, thinking it would free up room. instead, the HD doesnt recognize the changes (if they ever actually happened), and the live cd asks for a username and password to startup, which is different from the account on the HD! so, basically i am stuck without the ability to start normally, and i cant reformat and reinstall from the livecd. i acn, however, manage to get to terminal- any ideas?

---

### Post by BobCFC on 2007-06-25
If you select Recovery Mode from the GRUB menu you will get to a command line where you can log in as root an delete some files.    

from command line you type

```
rm file
```

or 
```

rm -rf directory
```

This happens to me because my TV card keeps recording by accident and filling up my home folder.

---

### Post by Freeman163 on 2007-06-25
thank s, ill give it a shot

---

### Post by phr0ze on 2007-06-25
Maybe if you get a script that creates a 20MB file when you login and delete the same file when you log off you can have a way of preventing a total lock out.

---

### Post by BobCFC on 2007-06-25
> **phr0ze said:**
> Maybe if you get a script that creates a 20MB file when you login and delete the same file when you log off you can have a way of preventing a total lock out.

Genius!   It wouldn't even need to be that big... it's just trying to write to some config files.

---

### Post by Freeman163 on 2007-06-25
interesting suggestion, but i could always get a HD bigger than 6gb...

as for the terminal part, I start up recovery successfully, i execute the command properly, but then i ht the retart button, try to log in, and i get the same error. is there some command i need to save the changes or something?

---

### Post by BobCFC on 2007-06-25
Did you free the space in you home folder?

if you type 

```
df -h

```

You'll be able to see the free space on different partitions



In my case it doesn't matter about HD size... i have to delete 5gb+ video files from my stupid tv tuner lol

---

