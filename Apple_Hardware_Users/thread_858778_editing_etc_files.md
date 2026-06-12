---
title: "editing etc files"
date: 2008-07-13
forum: Apple Hardware Users
---

### Post by apaukalypse on 2008-07-13
Hello all.  I am new to ubuntu and the Linux community and while I was installing various things people kept having instructions saying I had to change info in etc files.  Every time I try to save the changes the computer tells me I am not allowed.  I have searched everywhere for a way to change the permissions of these files but have had no luck.  What am I missing?

-apauk

---

### Post by AnLGP on 2008-07-13
you have to sudo edit them

example

sudo leafpad /boot/grub/menu.lst

sudo stands for Super User DO.  It's basically giving yourself permission to edit essential system files.  They put it there for good reason, trust me :D

Do that (sudo) with whatever editor you have and /path/to/file and your terminal will ask for your password.  put it in and you should be able to save it.

[http://www.gratisoft.us/sudo/man/sudo.html](http://www.gratisoft.us/sudo/man/sudo.html)

---

### Post by apaukalypse on 2008-07-13
cool, thanks man!

---

### Post by blunt.dualboot on 2008-07-14
Hi,

Just to add to what AnLGP said.

leafpad is the editor application. If you do not have that install it might not work.

I usually use gedit.

eg

> sudo gedit /boot/grub/menu.lst

would edit menu.lst file using gedit file. 

I do have problem with Linux command as well. :D. But I have to say it's fun to learn those stuff. :)

Good Luck,

Blunt

---

### Post by Vivaldi Gloria on 2008-07-14
Press Alt+F2 and start

```
gksudo gedit /file/to/edit
```

to edit in gedit. 

In terminal use also "gksudo gedit" rather than "sudo gedit". In general, use gksudo for graphical apps. Read this for more info:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by fishish on 2008-07-14
I am trying to edit my sources.list using gksudo, to add medibuntu repositories, but not succeeding. (Xubuntu 8.04)

When I enter; gksudo gedit /etc/apt/sources.list

all that returns is the $ prompt. The file doesn't open. I am not even asked for the password.

Possibly more clues:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

gives, 

--11:34:28--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.

Or possibly unrelated?

---

### Post by Vivaldi Gloria on 2008-07-14
> **fishish said:**
> I am trying to edit my sources.list using gksudo, to add medibuntu repositories, but not succeeding. (Xubuntu 8.04)

When I enter; gksudo gedit /etc/apt/sources.list

all that returns is the $ prompt. The file doesn't open. I am not even asked for the password.

Possibly more clues:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

gives, 

--11:34:28--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.

Or possibly unrelated?

Medibuntu is down for the moment.

---

### Post by fishish on 2008-07-14
Thanks. 

Any idea why the gksudo part of my post isn't working?

---

### Post by Vivaldi Gloria on 2008-07-14
> **fishish said:**
> Any idea why the gksudo part of my post isn't working?

I don't like hijacking other people's threads. So I suggest you start a new thread. Consider also these points before you do that:

1) If you have gedit in another desktop maybe it's opening there.
2) You're typing correctly, right?
3) Can you open any document with "gksudo gedit document" at all?
4) Can you start anything with gksudo at all? Say "gksudo nautilus".
5) Can you do anything in the terminal with sudo? Try "sudo blkid" for example.
6) What happens when you press ALT+F2 and start 
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Elfy on 2008-07-14
xubuntu doesn't have gedit unless you install it - replace gedit with mousepad or learn to use nano instead - a lot simpler.

---

### Post by Vivaldi Gloria on 2008-07-14
> **forestpixie said:**
> xubuntu doesn't have gedit unless you install it 

Simple facts of life. Always good to know. ;)

---

### Post by Elfy on 2008-07-14
It tokk me nearly an hour to realise when I was playing with xubuntu the first time - that's when I stopped using gedit and started using nano instead :D

---

### Post by fishish on 2008-07-14
Thanks forestpixie. It worked with mousepad. 

I tried the same command before with nano, which is installed, but also just gave me another $ prompt. I'm guessing that's why you suggest "learn to use nano." I assumed nano should also work with gksudo, but I see now that it is a command line editor.

Vivaldi Gloria, sorry for not posting in a new thread, it just seemed relevant to the thread topic.

---

### Post by Vivaldi Gloria on 2008-07-14
> **fishish said:**
> Vivaldi Gloria, sorry for not posting in a new thread, it just seemed relevant to the thread topic.

No big deal man. Have fun. ;)

---

