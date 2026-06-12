---
title: "How can I change the computer name"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by ubuntu27 on 2007-04-09
Hello there Ubunteros!

I've just upgrade to Feisty with a Fresh Install using the Alternate CD.


I have a question.
I didn't choose a name for my computer when I was installing, meaning I left it untouched with my IP as the computer name.

How can I change it? DO I have to re-install to change it?


With the computer name I mean the same name that appears when you open the terminal

MY-USER-NAME@COMPUTER.: ~$


Thank you for your time!!

---

### Post by Bachstelze on 2007-04-09
We're going to assume you want to set the hostname as "alice", of course change it since you'll probably want to set somethig else ;)

```

sudo -i
hostname alice
echo "alice" > /etc/hostname
nano /etc/hosts
```

and add your new hostname on the correct line (127.0.0.1 if you don't know where to put it), you're there :)

---

### Post by sushii. on 2007-04-09
@ubuntu27: Ubunturos? That's what we're called? Very creative username, btw.

---

### Post by bran on 2007-04-09
> **ubuntu27 said:**
> Hello there Ubunteros!

ntouched with my IP as the computer name.

How can I change it? DO I have to re-install to change it?


With the computer name I mean the same name that appears when you open the terminal

MY-USER-NAME@COMPUTER.: ~$

!

system>administration>network> on the general tab change the host.

if I understand rightly what you want to do.

---

### Post by ubuntu27 on 2007-04-09
THank you guys! That's exactly what I wanted.

> **sushii. said:**
> @ubuntu27: Ubunturos? That's what we're called? Very creative username, btw.


Ubunteros. It's Ubuntu Users in Spanish. I also saw that the same word are used in other languages as well. (PS it's a slang)

---

