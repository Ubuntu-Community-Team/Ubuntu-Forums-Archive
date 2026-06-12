---
title: "ssh question"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-12-09
okay i have my laptop then my second desktop which is like a file server and then my main desktop. Okay is there anyway that i can use ssh with like a username of tom or some radmon name and when i login with that user name can it auto go to a directly and only have permission to write copy and upload to that directory? is there anway that i can set that up for a account name or something

---

### Post by Dr Small on 2007-12-09
You can use usermod to change a user's directory, and then the permissions is up to you.
```
sudo usermod --home **/path/to/new/home** *user*
```

---

### Post by fedex1993 on 2007-12-09
okay ty dr small okay my other question is can the /path to new home can it be /media/something because i have a whole hardrive just partitioned for music and iso files so what permissions would i give the user to all upload to that directory and write and read and download via ssh

---

### Post by Dr Small on 2007-12-09
The path can be anywhere.
As for permissions, just right click on the folder that you wish to set the permissions on (directly meaning, the same directory that you are going to change his home folder too) and then change the group to the user's group, and then just give it 775.

Dr Small

---

### Post by fedex1993 on 2007-12-09
> **Dr Small said:**
> The path can be anywhere.
As for permissions, just right click on the folder that you wish to set the permissions on (directly meaning, the same directory that you are going to change his home folder too) and then change the group to the user's group, and then just give it 775.

Dr Small

okay so if the directly has 3 diffrent other folders inside i would need okay thanks um wthat ftp browser client would you recommend well not ftp but ssh

---

