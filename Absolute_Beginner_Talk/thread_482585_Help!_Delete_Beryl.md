---
title: "Help! Delete Beryl??"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-23
Hello, I'm having a serious problem. I was on my desktop, and I modified a Beryl setting (I checked something like "Force XLA" or something. Now, my desktop is frozen, and I can't boot up because Beryl starts at bootup. Now, I booted up in a terminal. How do I disable/remove Beryl (plus settings)?

---

### Post by Vodkayum on 2007-06-23
Sorry I can't technically help but I got your moral support lol. 
I did same thing but it didn't freeze me out just made a mess of things. I was able to remove from the add/ remove prgrams list.

---

### Post by zerobinary on 2007-06-23
try this command
sudo dpkg -r --force-all beryl or beryl-core or something like that
sudo kill1(1-19) the process number of beryl in the task manager

---

### Post by xpod on 2007-06-23
```
 sudo gedit /home/yourusername/.beryl-managerrc
```

Change the "platform" to 0 should do it i think

---

### Post by alecwh on 2007-06-23
The whole interface is frozen, I can't open gedit..
I can only access the terminal (by doing control alt f1)

---

### Post by PhatStreet on 2007-06-23
> **alecwh said:**
> The whole interface is frozen, I can't open gedit..
I can only access the terminal (by doing control alt f1)

It's been a while since I've used Ubuntu, but I believe you should have the command-line text editor *nano*.

---

### Post by alecwh on 2007-06-23
> **xpod said:**
> ```
 sudo gedit /home/yourusername/.beryl-managerrc
```

Change the "platform" to 0 should do it i think

You are a miracle worker! Thanks a bunch! :D

By THE WAY, if anybody in the future has the same problem, when you launch, click "Control Alt f2", put in "sudo apt-get remove beryl"

Then, boot back up

Do what the quote above me says

and launch beryl. :D

---

### Post by xpod on 2007-06-24
Sorry,I did`nt realise you were actually frozen out last night.
It was 1.30am so thats my excuse,glad you got it sorted anyway.:p

---

