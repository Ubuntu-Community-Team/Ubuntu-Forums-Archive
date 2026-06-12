---
title: "Can anyone help me understand this?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Oneironaut on 2007-05-15
Hello, I´ m a new user to Ubuntu, I just installed Feisty Fawn.

I own a gateway cx210x, a tablet pc which uses  a finepoint digitizer, and I found the following pages regarding how to getting it to work:

[http://www.linuxquestions.org/questions/showthread.php?t=497879]("http://www.linuxquestions.org/questions/showthread.php?t=497879")
[http://ubuntuforums.org/showthread.php?t=387369&highlight=gateway+cx210x]("http://ubuntuforums.org/showthread.php?t=387369&highlight=gateway+cx210x")
[http://ubuntuforums.org/showthread.php?t=146279&page=3&highlight=tablet+gateway]("http://ubuntuforums.org/showthread.php?t=146279&page=3&highlight=tablet+gateway")

My problem is that I can only get as far as step 2 in the linux question thread, I can´t find the serial.conf file,  and I´m really lost can anyone help me understand this instructions?

---

### Post by Oneironaut on 2007-05-15
anyone?

---

### Post by zvacet on 2007-05-15
You can try this

```
whereis serial.conf file
```

---

### Post by Oneironaut on 2007-05-15
it didn´t  find it

---

### Post by freebeer on 2007-05-15
I've no direct experience with it, but a quick peruse of the forums indicates that you might need to install **setserial** from Synaptic Package Manager (it's in the repositories).  It's not installed by default.  Once you install it, presumably you'll get the **serial.conf** file.

BTW, I got the hint from the Step 2 notes that you supplied:

```

Step 2.

You'll need the folllowing in your serial.conf or setserial.conf or **whatever file your distro has to set up it's serial ports...**


```

Since I didn't know what Ubuntu uses, I did a search.  :D

---

### Post by Oneironaut on 2007-05-15
I installed setserial, and everything, and I found a setserial file in bin, does anyone know if that&#347; the right  one??

---

### Post by chamberlain2006 on 2007-05-15
Thats the executable file.  You need a file ending in .conf, probably something like serial.conf in the /etc or /etc/setserial folders.

---

### Post by bcw on 2007-05-21
Hi,

Install the 'setserial' package.  Then create the file '/etc/serial.conf' with the proper values for your system.

You might google for similar machines, and howtos about discovering what the proper values are.  Also, 'man setserial' once you've installed the package can provide advice and examples.

I'm not at my Linux machine right now, but there are some options running 'setserial' at the command prompt.

Cheers,
Bret

---

