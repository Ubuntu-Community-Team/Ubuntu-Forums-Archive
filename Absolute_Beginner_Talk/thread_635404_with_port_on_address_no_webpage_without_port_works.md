---
title: "with port on address no webpage without port works fine"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jtann on 2007-12-08
i have a virtual server setup with my dir of var/www/siteone.
i can type my lan address and see my webpage. if i type lanip with port 8080 it does not show up. which inturn my wan address doesnt work becaus of the port not working. i have the port forward in my lynksys. im using webmin to setup my server.

---

### Post by jordanmthomas on 2007-12-08
If you can just type a hostname and no port and have it work, then that means your service is listening on port 80, not port 8080.

Does that help you?

Ex:
```
http://somewhere
```
is the same as
```
http://somewhere:80
```

---

### Post by jtann on 2007-12-08
ok that is whats going on do you know in webmin where i would change this.

---

### Post by jordanmthomas on 2007-12-08
I've never used webmin.  I usually just use the configuration files that come with whatever software I am using.

I'm guessing you're using apache?
The line you'd use to change its listening port is in httpd.conf
You're looking for this line:
```
Listen 80
```
Change the 80 to 8080 and apache will listen on port 8080 instead of 80 (after a restart of apache)

Short answer:  not sure how to do it with webmin.

---

### Post by Dr Small on 2007-12-08
If you have installed Apache from the repositories, then most likely you could go into Servers (in Webmin) and go into Apache, and there is probably some configuration in there to change what port it listens on.

If not, just use jordanmthomas' suggestion.

Dr Small

---

### Post by jtann on 2007-12-08
my httpd.conf is blank i did have a ports.conf it had one line in which was listen i change this i see my webpage on 8080 and"80" also now any thoughts

---

### Post by Dr Small on 2007-12-08
> **jtann said:**
> my httpd.conf is blank i did have a ports.conf it had one line in which was listen i change this i see my webpage on 8080 and"80" also now any thoughts
You just confused me....

---

### Post by jordanmthomas on 2007-12-08
So, what exactly is in ports.conf?
I am a little confused as to what you meant was in there.

---

### Post by jtann on 2007-12-08
etc/apache2/httpd.conf has nothing in it. but etc/apache2/ports.conf had one line that was listen 80 so i changed this to listen 8008. now i see it on [http://????:8080](http://????:8080) and 80
on my lan address and my wan address. let me say too that i had to do a removal and reinstall of apache to get this far. so maybe something is wrong with httpd.conf file??
because there is a clear place to put port number in webmin but it was not working.

---

### Post by jordanmthomas on 2007-12-08
Well, if you conf was too messed up, apache wouldn't start.
Odds are, Ubuntu just puts httpd.conf somewhere that you're not looking.

You shouldn't be able to access it on two ports unless it is listening on two ports.  So, something somewhere is telling it to listen on port 80.  

I'm not sure what, because I am not an expert in such things.  Sometimes I think the "added simplicity" Ubuntu tries to offer makes things more complicated.  If things were where they belonged, I could help, but I am not familiar with apache on Ubuntu specifically, so I can't be of any more help I am afraid.

---

### Post by jtann on 2007-12-08
htpd.conf is there there is just nothing in the txt file its 0 bytes

---

### Post by jordanmthomas on 2007-12-08
Try looking in this file:
```
etc/apache2/apache2.conf
```
I believe it's Ubuntu's httpd.conf

(Sorry for the long wait, my computer is being destroyed at the moment as I am installing an OS in a VM)

---

### Post by jtann on 2007-12-08
ok in the end looks like when i type my local lan ip i get webpage nomater what i put in.
with wan ip i have to put in 8080 now. does this seem normal

---

