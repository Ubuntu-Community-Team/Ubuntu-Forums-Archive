---
title: "lost file"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by neas18 on 2007-08-12
Hey I recently downloaded a file and tried moving it to my desktop and lost it.

I opened command termial and type 'sudo mv filename ~/Desktop' and it's vanished

is there any way i can get this file back

Thanks

---

### Post by felicity on 2007-08-12
You can try to locate it. First update your database.
```
sudo updatedb
```

Then type:
```
locate filename
```

---

### Post by neas18 on 2007-08-12
Nope didn't bring up any results

---

### Post by felicity on 2007-08-12
The filename is case sensitive. So Filename is different from filename. If that doesn't work, perhaps it's been deleted? I'm not sure how to recover deleted files. Perhaps someone else can help.

---

### Post by steve.horsley on 2007-08-12
It should have been moved to your desktop. Odd.

You could try these two commands:
[B]sudo updatedb
locate <filename>[/B]
updatedb takes a while - it is listing every file on disk to the locate database.

EDIT:
Dammit - I type way too slow!

---

### Post by neas18 on 2007-08-12
ok I tried the updatedb and locate 'file' again and no results. Also not sure if this would

make a difference or not but before I did any of this I type 'su' to login as root

before i moved the file

---

### Post by felicity on 2007-08-12
Ubuntu doesn't have a root account accessible with su by default, that I know of. Did you make your own? It's possible the file was moved to the /root/Desktop folder then.

---

### Post by neas18 on 2007-08-12
root@Ubuntu:/home/sean# cd ~/Desktop
bash: cd: /root/Desktop: Not a directory


And no I didn't create one, that I know of? anyway I'm guessing that's a problem

---

### Post by felicity on 2007-08-12
The file may be named Desktop now, in your Root folder. Try browsing there in Nautilus (File System > Root).. if there is a file named Desktop there, you may try renaming it to the file and extension you originally had and see if it will open.

---

### Post by neas18 on 2007-08-12
alright awesome, I found it. Now how do I get it to my desktop and change the permissions 

so I can rename it?

---

### Post by felicity on 2007-08-12
Well since you were using a root account for everything else, you can use it to move and rename the file. The folder you want to move it to is /home/yourusername/Desktop (because ~/Desktop under root is a different folder than ~/Desktop under your user account)

---

### Post by MenZa on 2007-08-12
You might have the change the owner of your file once you've moved it, to be able to use it as your regular user:

```
sudo chown sean:sean <filename>
```

Assuming your regular username is sean.

---

