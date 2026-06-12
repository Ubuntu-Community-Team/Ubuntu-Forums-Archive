---
title: "What's Samba and why is it trying to connect to my computer?"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by nala on 2006-03-11
Firestarter says that it has blocked 2 serious inbound connections in the past two days. It says something about Samba. Should I be worried?

---

### Post by Pragmatist on 2006-03-11
Give us the exact message.  Also, are you the only one that uses your computer?  I'm guessing you didn't intentionally setup SAMBA if you don't know what it is :)  Do you access windows files from your linux computer?  Try this also:
```
cat /etc/services | grep samba
```

---

### Post by nala on 2006-03-11
Will a screenshot work?

[http://img.photobucket.com/albums/v240/mikuno/screenshot.png](http://img.photobucket.com/albums/v240/mikuno/screenshot.png)

I've never set up Samba and I don't access the files on this machine from other computers.

---

### Post by varunus on 2006-03-11
"Samba" is windows filesharing.  Most windows computers, if the person using them opens up their "Network" area in my computer, it'll probe the network for anyone sharing files.  Firestarter by default considers this a threat, and blocks it.

---

### Post by Swab on 2006-03-11
What is your IP address?  That address looks like it's internal, ie not from the internet.

---

### Post by nala on 2006-03-11
I have no idea. o.o

---

### Post by Swab on 2006-03-11
OK, so open up a terminal and type "ifconfig".... you should see something that says inet addr followed by your IP address.

---

### Post by jamesr on 2006-03-11
Are you on a wireless network? or a wired network?
At home ? or a business?

---

### Post by nala on 2006-03-11
I'm on a wired network at school.

---

### Post by varunus on 2006-03-12
If you're on a wired network at school, then it makes a lot of sense that you'll get SAMBA probes from other people's windows computers looking for shared files.

Like I said above, Firestarter considers this an attempt to get files and calls it critical. (At least, I'm pretty sure that's what this is; opening those ports doesn't cause any problems as long as you're not sharing any files.)

---

