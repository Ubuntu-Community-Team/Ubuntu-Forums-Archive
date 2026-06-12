---
title: "Sudo rights"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by in_orbit on 2006-11-03
Which commands should I issue in the terminal window to give my ordinary user account sudo rights?

/In orbit

---

### Post by bsussman on 2006-11-03
If you mean the account that you set up when you installed, it has sudo rights.

If you mean other accounts that you added,, in a terminal:

```
man sudo
```and study how to alter /etc/sudoers to achieve the effect you want.

If you mean 'How do I use sudo?', in a terminal type

```
sudo <whatevercommandyouneedtosufor>
```and enter your password

---

### Post by Ecthelion on 2006-11-03
... or sudo su
That will make you superuser and every command you issue after that will be executed as if there is "sudo" written before it
Be carefull with it!

You can go out the superuser mode with 
"exit"

This wont close your terminal but set you back as normal user

---

### Post by podunk on 2006-11-03
If you want to be *the* super user and make tons of very dangerous changes to your system and break every thing type

sudo su

in the terminal. It took me about 90 seconds to break everything the last time I tried that. :)

---

### Post by NeoLithium on 2006-11-03
True, for most of the normal use; sudo just at the times it's required is the absolute best option; I really only use sudo su when tinkering when getting a new kernel set up; and even then I'm not too psyched about constantly having superuser with every command I type...

---

### Post by PriceChild on 2006-11-03
I STRONGLY reccomend you read [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) for an explanation of how root works in ubuntu.

You may give Administrator permissions to other users via System>Admin>Users and Groups> **podunk said:**
> in the terminal. It took me about 90 seconds to break everything the last time I tried that. :)I doubt that... unless you were trying it on purpose.

sudo su - is perfectly safe if you know what you're doing. I advise you to stick to sudo for most commands... there's hardly any reason at all to use sudo su -. (one exception i know being eciadsl where it simply won't work with just sudo)

---

