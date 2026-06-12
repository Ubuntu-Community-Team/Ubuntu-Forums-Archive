---
title: "Live CD &amp; x server problem"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by szarley on 2007-06-03
hi...
well, first of all I don't really use ubuntu... I always put installation for some other time ;)
but... I do play sometimes with live cd...
I had 6.10, now I have 7.04 and everything was ok, the system was starting, everything was working fine.
yesterday I wanted to play with ubuntu again, and all of the sudden I have this weird message "failed to start the x server" and a lot of other stuff I don't understand ;)
so basically my question is not "how to solve the problem" (the answer would be nice thou)...
the question is WHY?
I didn't change anything in my laptop, so why now?
Why everything was ok for a long time, I was starting my laptop many times with live cd (this and older version), and now I can't...
If someone can enlighten me I will be very grateful :)
thank you

---

### Post by zvacet on 2007-06-03
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by szarley on 2007-06-03
thx...
unfortunately this didn't really help...
I still can not run Gnome...
I was trying to reconfigure the xorg, but it just doesn't work...
I have a feeling that my live cd just doesn't like me anymore... it just decided "no" ;) :(

---

### Post by zvacet on 2007-06-04
Try to type in terminal

```
sudo /etc/init.d/gdm start
```

Maybe is your graphic card so try

```
sudo dpkg-reconfigure xserver-xorg
```

and select** vesa** driver to see if you can get graphic

---

### Post by szarley on 2007-06-04
I did that already...
try couple of times... setting vesa, setting smth different, starting, stopping Gnome...
I always end up with the same message "Failed to start x server"...
and still I am very surprised since I didn't have this problem before...

---

### Post by szarley on 2007-06-06
ok... 
I know that in the first thread I did not actually asked for "solving problem" help...
Never the less **zvacet** tried to help me, thank you for that :)
Still the problem is not solved and I can not use the live cd, since I am stuck...
So I would like to rephrase my humble request ;)

Can you please help to solve my problem...
I tried the solutions mentioned above and failed
Any other suggestions?

And of course I still will not mind if someone will add the "WHY?" part ;)
thx

---

### Post by Crafty Kisses on 2007-06-06
> **szarley said:**
> I did that already...
try couple of times... setting vesa, setting smth different, starting, stopping Gnome...
I always end up with the same message "Failed to start x server"...
and still I am very surprised since I didn't have this problem before...

This is saying that on the LiveCD?

---

### Post by zvacet on 2007-06-06
When you boot up Cd press F1(it is help)and there you will find solutions for graphic.

---

### Post by szarley on 2007-06-06
> **Codename said:**
> This is saying that on the LiveCD?

yes it is on live cd...
I don't have the courage to install when it looks like a challenge to see anything apart the prompt...

**zvacet,** I think I tried all the possible solutions presented under F1... nothing works... I have managed to run visuals under vga, but I was not able to do anything else since the cursor itself was the size of 1/20 of the screen...

I am totally frustrated...

---

### Post by szarley on 2007-06-07
ok... I have found a solution (well, sort off) here:

[http://ubuntuforums.org/showthread.php?t=466355](http://ubuntuforums.org/showthread.php?t=466355)

so basically it works, but I am not sure if all works as it should... anyway thx to all who cared to help me :)

---

