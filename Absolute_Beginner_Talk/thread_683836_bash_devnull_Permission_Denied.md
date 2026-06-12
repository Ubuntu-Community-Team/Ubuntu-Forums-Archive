---
title: "bash: /dev/null: Permission Denied"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by kitcecil on 2008-01-31
Hello, I'm a brand-new Linux User. I just installed Ubuntu 7.10, and I used the alternate installer. The installation went without a hitch, but as I got to my login screen I recieved an error:

```
bash: /dev/null: Permission Denied
```

I have already searched the forum to see if anyone had the same problem and I thought I had some luck, but the only fixes I found broke as soon as I restarted; such as the "chmod 666 /dev/null" fix.

I apologize in advance, I probably won't understand technical commands so you may have to spoon-feed it to me, haha.

Thank you.

---

### Post by jan quark on 2008-01-31
what is the result of the following command
```
ls -l /dev/null
```

---

### Post by kitcecil on 2008-01-31
It shows the line:

```
crw------- 1 root root 1, 3 
```

---

### Post by jan quark on 2008-01-31
```
brw-[COLOR="Lime"]rw[/COLOR]---- 1 root disk 3, 0 2008-01-31 07:55 /dev/hda

```

thats the result of my booting drive
it is seems it is a permission problem

bit I still search for the solution

---

### Post by jan quark on 2008-01-31
ok now I have somthing
bit I dont know perhaps its a little risky so dont shout at me pls

remove the dv/null

```
sudo rm /dev/null
```

and recreate it 
```
sudo mknod -m 0666 /dev/null c 1 3
```

hello you geeks out there can this work??

if you are brave enough try it :)

---

### Post by emarkd on 2008-01-31
I've never done this either.  Would it be saver to try and create a /dev/null2 and see if it works before removing /dev/null?

Just a thought.

---

### Post by emarkd on 2008-01-31
I tried it on my system and it seems to work.  I'd still create a /dev/null2 first, then if it works remove /dev/null and mv /dev/null2 /dev/null

---

### Post by jan quark on 2008-01-31
well the creation code works it creates what I want namely a hda with read and write root permissions
and the remove code works as well

---

### Post by kitcecil on 2008-01-31
I've tried recreating the /dev/null from recovery mode, but after I reboot, I'm still encountering the same problem. I must be missing something.

---

### Post by jan quark on 2008-01-31
so you removed the original and recreate it as posted above and no change occur ?

---

### Post by kitcecil on 2008-01-31
I input the commands as you told me, and when I rebooted, I got the same error. I went back and checked my /dev/null and the permissions had changed back to the original.

---

### Post by Beggar on 2008-01-31
In theory a simple
```
sudo chmod 666 /dev/null
```

should work. If it doesn't, this code properly worked for me (same as previous post, but now with backup goodness, always backup)

```

sudo mv /dev/null /dev/null2
sudo mknod -m 0666 /dev/null c 1 3

```

should you have more problems use

```

sudo mv /dev/null2 /dev/null

```

---

### Post by kitcecil on 2008-01-31
Whenever I make a change to /dev/null, it doesn't appear to save it. What could be wrong?

---

### Post by kitcecil on 2008-01-31
bump.

---

