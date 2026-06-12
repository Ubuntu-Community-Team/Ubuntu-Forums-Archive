---
title: "chmod +x does not work for me..."
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-07-03
okay, just to try out something, i typed in a terminal:
```
touch example
chmod +x example
```i did check if the file didn't have executable permissions before i did the second command, and it didn't, but then i checked its permissions after i did the second command, and the executable permissions still weren't checked.  how can this be? i thought chmod +x gave a file executable permissions?!!!

---

### Post by Kaidelong on 2006-07-03
This sounds a little weird, you say the permissions are not changing? Could you paste in what you had on the terminal here?

Well, what "chmod +x" does is really "chmod u+x". I think it defaults to that anyway. So only the user that owns the file will have execution permissions to it. Unless you own the file, you're going to need to use sudo to make the change, and if you want to add the executable tag to be accessible to all users on the system you should really be calling "chmod a+x example" (and probably, "sudo chmod a+x example".) 

To see the full permissions for a file, use "ls -l example".

---

### Post by uzi09 on 2006-07-03
here's what looks like a really nice short guide.
i'm sure you already know a thing or two about permissions, but scroll down to the number section.

it's a quite popular and nice method to change permissions around...
[http://www.elated.com/tutorials/management/unix/permissions/](http://www.elated.com/tutorials/management/unix/permissions/)

enjoy
uzi

---

### Post by Kurt` on 2006-07-03
bill@sentinel:~$ touch example
bill@sentinel:~$ chmod +x example
bill@sentinel:~$ ls -AlFh . | grep example
-rwxr-xr-x  1 bill bill     0 2006-07-03 00:46 example*

Works fine here. :neutral:

---

### Post by woedend on 2006-07-03
chmod +x  adds execute for all 3.
u+x is just for user
o+x others
g+x group

you are checking in nautilus, right?  it wont appear until you refresh the directory by clicking out and back in or closing nautilus

---

### Post by user1397 on 2006-07-03
i cant get tomy ubuntu computer right now, but i think it was just what woedend suggested.  i'll try tomorrow.

---

### Post by user1397 on 2006-07-03
ah yes thanks woedend, i just needed to refresh nautilus in order to see the chnages, stupid me...

---

