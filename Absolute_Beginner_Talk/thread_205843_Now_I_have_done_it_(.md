---
title: "Now I have done it :("
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by bbales on 2006-06-29
Ooooo. I did something bad.

Since I am the only one that uses my linux computer, I was trying to make it so I could use sudo without supplying a password. I found on the net that you could use visudo and add the line 'username ALL = NOPASSWD: ALL'.

Well, it didn't work, so I thought maybe the other lines needed to be remarked out, so thats what I did. there were two, one sorta like root = ALL:ALL (or something) and another like %admin..Anyway, long story short sudo does not work now, and I have to have sudo to run visudo to change it all back #-o 

Gah, I am stumped!

---

### Post by scxtt on 2006-06-29
boot into recovery mode ...

---

### Post by bbales on 2006-06-29
It appears that is going to reinstall Ubuntu, is that correct? If so, am I going to loose everything I have done up to now, such as my teamspeak server, Apache2 etc (they took me forever)?

---

### Post by bbales on 2006-06-29
Eh, actually I still had the Ubuntu CD in my drive, so it booted into that #-o 

Booting into recovery did the trick! Thanks a bunch.

---

### Post by th3james on 2006-06-29
Can i just ask why your trying 2 make sudo passwordless? This sound like a very unsafe thing to do to me, you might as well just run as root all the time (almost like windows)

---

### Post by bbales on 2006-06-29
I am the only person that uses the computer, and it is in my own home, so I see no reason not do it that way. Also you still have to be logged in as a valid user.

As to it being like it root at all times, that seems to me incorrect since you still need to use sudo to perform root tasks.

Now, being new, I could be completely wrong on all points. I just seems logical.

---

### Post by nocturn on 2006-06-29
[QUOTE=bbales]
As to it being like it root at all times, that seems to me incorrect since you still need to use sudo to perform root tasks.

Now, being new, I could be completely wrong on all points. I just seems logical.[/QUOTE]

Nope, it is pretty much as bas as logging in as root all the time.
A trojan could quite easy exploit this.

It's your computer though, but I wouldn't have it on any of mine.

---

### Post by aysiu on 2006-06-29
There are basically five different kinds of security when it comes to computers:

1. Security from malware infection
2. Security from a cracker
[b]3. Security from yourself (accidentally screwing up your system)
4. Security from other users on the same system[/b]
5. Physical security (actually putting a padlock on the computer)

and it appears you're concerned with only two of those types.

---

