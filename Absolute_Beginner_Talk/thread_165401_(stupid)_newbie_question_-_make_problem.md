---
title: "(stupid) newbie question - make problem"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by david@mc on 2006-04-24
Hi folks

I've installed ubuntu to try out as a dual boot alongside Windows 2000P, and it looks great!  To my surprise disk partitioning was really straightforward, resizing my Windows partition and I'm amazed it all worked so smoothly.  

As my first task I thought I'd try installing a program - abiword.  Previously my Linux experince has been limited to a Puppy Live CD which runs well and I really like abiword. 

My Windows / ubuntu PC is not connected to the internet (I'm using my iMac for this) so I tried to install from a CD following the instructions on another thread. I ran the tar xvzf, cd package, and ./confiure commands fine but when I ran "make" it complained "command not found".  Is there something simple I'm missing? 

David

---

### Post by kh4nh on 2006-04-24
[QUOTE=david@mc]Hi folks

My Windows / ubuntu PC is not connected to the internet (I'm using my iMac for this) so I tried to install from a CD following the instructions on another thread. I ran the tar xvzf, cd package, and ./confiure commands fine but when I ran "make" it complained "command not found".  Is there something simple I'm missing? 

David[/QUOTE]

You might wanna install build-essential first. Can you also post the message after doing ./configure

---

### Post by ncappel1 on 2006-04-24
I hope this isn't too basic, but here is a great refresher which sounds like exactly what you need:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

and [http://www.psychocats.net/linux/installingsoftware](http://www.psychocats.net/linux/installingsoftware)

let us if this helps!

---

### Post by joshrobinson on 2006-04-24
```
sudo apt-get install build-essential
```

need it to use make

---

### Post by david@mc on 2006-04-25
Thanks very much guys!

The build-essential app was what I was lacking.

David

---

