---
title: "Which FTP server?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-01-13
I am looking for the right FTP sever to run on my LAMP server. I want to transfer folders from 1 lan machine to the Lamp server to Apache. 

I want to publish a website from a lan to apache with is running.

Hamm

---

### Post by taurus on 2007-01-13
There are a few of them but I use vsftpd on three machines at work.

---

### Post by stijn_pol on 2007-01-13
I use proftpd. Works fine to me, easy to install.
Search the forum for 'howto proftpd'.

---

### Post by Hamm on 2007-01-13
> **stijn_pol said:**
> I use proftpd. Works fine to me, easy to install.
Search the forum for 'howto proftpd'.

I might be missing it but, I an a noob and I need a GUI to do this. I am not comfortable with command line input yet...... working on it...](*,)

---

### Post by taurus on 2007-01-13
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gproftpd
```

---

### Post by Hamm on 2007-01-13
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gproftpd
```

Another noob thing again...... how do I start gproftpd after I installed it. Sorry for being such a newbie...:???:

---

### Post by stijn_pol on 2007-01-13
Probably by checking your application's menu, somewhere under internet programs for example. You can also open gproftpd by typing gproftpd in commandline.

(Newbie too)

---

### Post by Hamm on 2007-01-13
I found it....... time to crash my server:rolleyes:

---

### Post by Hamm on 2007-01-13
It is now telling me that I need to run gproftpd as root to and users????? what am I missing?/?   :confused:

---

### Post by taurus on 2007-01-13
Applications -> Accessories -> Terminal
```
gksudo gproftpd
```

---

### Post by Hamm on 2007-01-13
here is my latest......](*,)

[IMG]http://www.furnbach.com/image/gproftpd.jpg[/IMG]

---

### Post by Hamm on 2007-01-13
I don't know if this makes a difference but, I installed it as a "stand alone" not a "inetd".

:confused:

---

### Post by Hamm on 2007-01-13
Well....I removed and then reinstalled using apt-get and started gproftpd with the gksudo command. It worked the first time. I used Webmin to start the FTP server (I didn't know the console command) and was able send over a website for testing.....:)

---

