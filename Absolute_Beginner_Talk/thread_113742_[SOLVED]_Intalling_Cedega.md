---
title: "[SOLVED] Intalling Cedega"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Norwal on 2006-01-07
Hello,

Let me start by saying ubuntu is way cool.  I've been learning Linux on SuSE 10 but a hacker at work told me to try ubuntu. Once you learn a few trick it much nicer that SuSE 10.

But now I'm completly lost!!

I've installed ubuntu, ungraded my video driver, Real Player, mPlayer and all the codecs. I've changed my Kernel to K7.  I was feeling really good for a noob.

Then I down loaded Cedega's 14 day time Demo.  How do I install it???  

Nor

---

### Post by patrick295767 on 2006-01-07
[http://ubuntuforums.org/showthread.php?t=103980&page=2&highlight=cedega](http://ubuntuforums.org/showthread.php?t=103980&page=2&highlight=cedega)
  
I dont know much more, ...I can run age of empire with the version 4.4.3.1
(I dont think you r noob in terms of linux ... )
Welcome to linux ubuntu !
 
Greetz

Pat'

---

### Post by Norwal on 2006-01-07
patrick you're ahead of me.  My question is how to i install Cedega that is how do I get it going on my computer. I have the downloaded installer, now what?

---

### Post by Perfect Storm on 2006-01-07
Hi Norval :)

I'll help you.
Is the file a .sh or .deb file?

If you saved the file to your Desktop open the terminal 

sh:
```

cd Desktop
sudo sh XXXXXXXXXXXX.sh

```
XXXXXXX=the name of thet file


.deb:
```

cd Desktop
sudo dpkg -i XXXXXXX.deb

```
XXXXXXX=the name of the file

Also remember that linux is case sensitive


.:=The AI Dude=:.

---

### Post by Estariel on 2006-01-07
Hi!
If the
```
 sudo dpkg -i cedega-blablabla.deb 
```
yields a dependency error, issue the following:
```
sudo apt-get install -f
```

This fixes all dependency problems dpkg might have had, and installs cedega afterwards (apt knows which files you tried to install by dpkg and will solve their dependencies and install them when you use the "fix" -f option).

i'm posting this, because I had to do this...

---

### Post by Norwal on 2006-01-07
Hello Guys,

Thanks for the help;) 

I tried the Sh comd and it worked.  Cedega is now up and running.  I got MOHAA going and it is faster loading the on my XP box.

I'm having trouble with BF2.  I'm playing with the settings  and seem to get closer and farther away each attempt.  But what the heck it's driving my wife nuts so it worth it! Just kidding.

Ron

---

### Post by Norwal on 2006-01-08
Bad news!!

BF2 will not work in Cedega with an ATI Card.  I have an Asus ATI 9600 XT with VIVO. Great card but poor support I guess.

Cheers and thanks again.

---

