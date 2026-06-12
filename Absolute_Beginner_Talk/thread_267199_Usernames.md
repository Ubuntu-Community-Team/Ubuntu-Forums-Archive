---
title: "Usernames"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Jimmytzin on 2006-09-28
Hey can anyone tell me how to get all the usernames back on the list.. well GDM is the one I need to get back on the list because somehow it got erased.. or someone erased it PLEASE HELP ME!!!! ooh yeah I'm a noob so..

---

### Post by Bachstelze on 2006-09-28
```
gksudo gdmsetup
```

Should be somewhere in there.

---

### Post by Jimmytzin on 2006-09-28
What's that or how and where do I type that...

---

### Post by Bachstelze on 2006-09-28
Oh, my bad. I didn't notice it was your first time here...

Well, welcome to Ubuntu then :)

Whenever someone will ask you to type things like this, it goes in the **terminal** (also sometimes called **console**), you can access it from Applications > Accessories > Terminal (Alt+F2 > gnome-terminal also works).

But in your case, you can access GDM setup from System > Administration > Login Screen Setup.

(All of it might not be 100% accurate as I haven't use GNOME for ages but it should be close enough)


**EDIT :** actually, I'm not sure I understood your problem very well, could you please try to explain it more precisely ?

---

### Post by Jimmytzin on 2006-09-28
Well the other night we had a really bad electric storm and everything shut off.. and then when I booted my comp back on.. on the startup windows when it starts booting all the programs it said failed on a bunch of them and it won't logg in to the normal screen.. it starts up on the terminal and it says that the user GDM doesn't exist.. and well it doesn't let me use any internet based programs

---

### Post by Bachstelze on 2006-09-28
All right so now is the time to use the terminal ;) Open up a terminal window and type (or copy/paste) this, then press enter and tell me if it gives you a line of text or not :

```
cat /etc/passwd | grep gdm
```

it should output a line like this :

```
gdm:x:42:42::/var/gdm:/sbin/nologin
```

---

### Post by Jimmytzin on 2006-09-28
Thats gonna be a problem cuz I partitioned the hard disk and I have both op's running.. not at the same time but.. well I'm using XP right now that's how I got acces to the internet.. if you have a few mins.. sure I'll try it

---

### Post by Jimmytzin on 2006-09-28
Hey what's that vertical line that yopu typed before grep?

---

### Post by Bachstelze on 2006-09-28
On my French keyboard it's done with AltGr + 6 but I don't know about yours... Anyway, it's not that important, just type cat /etc/passwd, it will output a few lines of text, see if there's one with 'gdm' in it (that's what grep does automagically).

---

### Post by blackened on 2006-09-28
On an english keyboard it is usually shift+backslash somewhere near (usually above) the enter key. It's also known as a vertical pipe, or just a pipe.

---

### Post by Jimmytzin on 2006-09-28
Well after trying all sorts of ways I got this 
root:x:0:0root:/root:/bin/bash

---

### Post by Bachstelze on 2006-09-28
Is that the **only** line you get ?

---

### Post by furiousV on 2006-09-28
> **Jimmytzin said:**
> Hey what's that vertical line that yopu typed before grep?

Or on a UK keyboard it is between Shift and Z.

It is called the pipe character.

---

### Post by blackened on 2006-09-28
I must apologize to ye citizens of the UK. To put it correctly: on an American English keyboard the pipe is shift+backslash.

---

### Post by Jimmytzin on 2006-09-28
cat /etc/passwd grep gdm didn't do anything as soon as I pressed enter it just went down to another line.. but empty

---

