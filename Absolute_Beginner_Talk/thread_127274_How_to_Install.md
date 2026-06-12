---
title: "How to Install"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-02-08
I just wondering how to install programs you download. I just got a game called et-linux-2.60.x86.run it says it is a SH if that helps at all.  I got it from here [http://www.splashdamage.com/modules.php?op=modload&name=Downloads&file=index&req=viewsdownload&sid=2](http://www.splashdamage.com/modules.php?op=modload&name=Downloads&file=index&req=viewsdownload&sid=2) 
it is down the page ET 2.60 Full (Linux)  

Also how about a newer version of Firefox how would I do that?

---

### Post by TrendyDark on 2006-02-08
For Firefox, try this thread for a program called Automatix:

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

For ET, you're going to have to install the video drivers for your video card first. I just installed mine to get ET working as well.

To install ET though, just run this command (you need the drivers for it to work):

```
sudo sh ./et-linux-2.60.x86.run
```

(assuming you downloaded it to your /home directory, if not, just move it there.

---

### Post by CookieOrc on 2006-02-08
Thanks I installed it now I need to post a new one for my drivers lol... Thank you

---

### Post by TrendyDark on 2006-02-08
What video card are you running, I could point you in the right direction if need be.

---

### Post by CookieOrc on 2006-02-08
Nvidia 6200

I have a Athlon X2 3800
I am sure I am running in 64 bit

---

### Post by TrendyDark on 2006-02-08
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

There's the thread/HowTO for installing the lastest Nvidia drivers. 

Are you using the 64-bit version of Ubuntu? If so, uninstall it and run the other way fast, lol. I have a AMD64 2800+ and heard there was a performance gain when using the 64-bit Ubuntu, but it was just a world of hurt/problems.

---

### Post by David Corrales on 2006-02-08
Don't forget to set the execution bit on for the file you want to execute.
**chmod +x *filename*** will do the trick.

---

### Post by CookieOrc on 2006-02-08
I have noticed that. All 64bit versions really do suck. This really isnt my first distro and I am not really a beginner. I just never leanred some of the basics and dont feel like crashing my computer again. I might go back to 32bit but I wanna stick out a bit longer. THanks a ton though.

---

### Post by TrendyDark on 2006-02-08
[QUOTE=David Corrales]Don't forget to set the execution bit on for the file you want to execute.
**chmod +x *filename*** will do the trick.[/QUOTE]

Ah, yes, I forgot that part. If you run into permission errors with anything in the future, it can sometimes be fixed by this:

```
chmod 777 path/to/file
```

& No problem. I'm no expert at Linux, but I feel that if I help people with what I know and ask enough questions, I'll get better and better at this whole deal.

---

### Post by CookieOrc on 2006-02-08
Lol i cannot even use Automatix. Does not support AMD64... This is going to be a long day...

---

### Post by David Corrales on 2006-02-08
I'll add some info about permissions to the thread because, even though TrendyDark's tip will probably fix any problems you have, it's very possible to break something (permission-wise) if you keep using 777 all the time.
Those numbers you see represent the bit mask applied to the file by the OS before it is accessed. Actually, there's some other bits more like SUID that come into play, but for this quick explaination, I'll just refer to our usual 3 digits.

777 would translate to (**r = read, w = write, x = execute**):
(You can get this kind of info by using **ls -l** from the command line)

```

Owner   Group    Others
rwx      rwx      rwx               attribute
421      421      421               binary value of the bit
---------------------
111      111      111               bit on/off
 7        7        7                sum of the binary values

```
Using this information you can now deduct that a permission number:

644 means: rw, r, r
```

Owner   Group    Others
rwx      rwx      rwx               attribute
421      421      421               binary value of the bit
---------------------
110      100      100               bit on/off
 6        4        4                sum of the binary values

```

700 means: rwx, -, -```

Owner   Group    Others
rwx      rwx      rwx               attribute
421      421      421               binary value of the bit
---------------------
111      000      000               bit on/off
 7        0        0                sum of the binary values

```
and so on...

So, by using 777 you're in fact allowing **anyone** to do as they want to the files you mark with those permissions. As you can see, doing that to a file can either be:
Harmless (in a single user environment, maybe a personal text file)
Compromise a file you didn't want to be readable by everyone (personal document on a multi-user environment)
Halt a process (sshd won't boot up if some of the files it depends on are without the correct permissions).
Of course there's a lot more of situations that can arrise by having incorrect permissions on files, but those are just typical cases.

P.D. The directories need the "execute" bit on if you want to be able to browse them, so make sure you don't do a recursive run of **chmod** disabling the execute bit or you're in for an afternoon of manually enabling permissions to directories. Not fun.

---

