---
title: "How do I setup a webserver?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by grs on 2007-11-11
I would like to make a basic webserver for the school where I work. I don't want it to connect to the internet but instead allow students to access the websites from within the school network. Is this possable, if so, what programs do I need, where can I get them and how do I set it up?

This is really a trail thing I'm doing. The PC I'm using is an older model which I have loaded Ubuntu onto. What I want is to have somewhere where teachers can leave classnotes, videos, etc that can be access by students. Due to the schools poor internet service and lack of funds I thought it might be easier to keep it local, students have access to the computer rooms after school.

---

### Post by 505 on 2007-11-11
You can install the Ubuntu server edition, or if you already have the desktop edition installed, just install the Apache2 package. This will give you a basic webserver. If you want more advanced stuff, you might also want to consider PHP and MySQL. Check out [one of the best guide](http://www.howtoforge.com/perfect_server_ubuntu7.10) on this topic. You can skip all the details about installing the base system if you have that already, and if you don't need mail, you can skip that one too. Also, you probably don't need  the BIND9 DNS server.

---

### Post by LaRoza on 2007-11-11
You can use the command ```
sudo tasksel
```, select "LAMPP" and place the documents you want to serve in /var/www.

Administrating Apache can be tricky, so there is more to it than that, but that will get it working.

---

### Post by grs on 2007-11-11
Thanks, I'll look into it.
When you go to look up a website on the internet you type in [www.ubuntu.com](www.ubuntu.com) or whatever, if I'm running it so its local only will I need to access it via IP address? I'd need to set a static IP for that, right?

---

### Post by LaRoza on 2007-11-11
> **grs said:**
> Thanks, I'll look into it.
When you go to look up a website on the internet you type in [www.ubuntu.com](www.ubuntu.com) or whatever, if I'm running it so its local only will I need to access it via IP address? I'd need to set a static IP for that, right?

You can use DNS if you want, but I never did that. A static IP is needed.

---

### Post by grs on 2007-11-11
DNS links the www. name and the IP so they both point to the same page? I'm still new to networking at the school I'm just filling in for someones who's on leave.

---

### Post by Dr Small on 2007-11-11
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

### Post by armandh on 2007-11-11
or you could just use network attached storage

---

### Post by grs on 2007-11-14
I've been following the guide for The Perfect Server and have got to step 7, whe I try to type in the new information the keyboard is not responding to key correctly, why?

---

### Post by grs on 2007-11-16
how do I use VIM text editor?

---

### Post by fedex1993 on 2007-11-16
you dont half to use vim. if you want to like edit a file just for simple text and your in a terminal just type ```
Sudo nano then the file where it is located
```

---

