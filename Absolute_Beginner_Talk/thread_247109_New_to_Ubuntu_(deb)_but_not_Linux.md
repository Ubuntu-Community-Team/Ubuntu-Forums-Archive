---
title: "New to Ubuntu (deb) but not Linux"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by 0be1 on 2006-08-30
ok ok, I have become spoiled and soft over the years and have gotten used to a GUI environment (dang I knew I should have stayed with DOS). Anyway, I am new to using a Debian based distro and Ubuntu (which I love the desktop). I will learn more (I promise) and will be using it quite extensively in the near future and en masse, but for now here is my first problem.

I had 6.06 desktop loaded and like past distros used I was going to run test type server apps, mainly LAMP. However, I did not find a way to easily do that with Ubuntu. So I re-installed 6.06 as a LAMP server, done some research (1 page perferibly, not 3000 posts) that explains how to properly and successfully do this. Anyone got the solution for a one time answer and friendly usability? Anyone Bueller, anyone ;)

Thanks for the help, and sorry if the post was (OT)(server, installations issues, etc). And keep up the great work on this product. The best I personally used so far!!!

In case you also need to know, I am loading this on an old Dell Dimension 1100R.

tia...

Shawn

---

### Post by Klaidas on 2006-08-30
So you need to set up LAMP on a desktop install? :)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by 0be1 on 2006-08-30
Klaidas;

I have 6.06 server installed with LAMP. I want my GUI back. It is easier for me to administer a server that way more quickly. Mainly use webmin and have to have a GUI interface.

Other than that, everything is installed to the best of my knowledge.

Shawn

---

### Post by 0be1 on 2006-08-30
Sorry...Maybe here is a better explaination. I would like to have my Gnome GUI back running under 6.06 server.

Thanks...

Shawn

---

### Post by monktbd on 2006-08-30
try
> 
sudo apt-get install ubuntu-desktop


this hopefully resolves all dependencies.
i am not sure whether this is enough or some more repositories need to enabled to make it work.

---

### Post by 0be1 on 2006-08-30
I have already tried (and doing so again) sudo apt-get install ubuntu-desktop. All I get when completed is a # prompt. I have rebooted, etc. Still all I get is either a $ prompt or # prompt when sudo.

It remains a mystery ;) But the truth shall prevail!!

Shawn

---

### Post by Klaidas on 2006-08-30
Hmm.
Try this: [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by 0be1 on 2006-08-30
Klaidas;

ok, after three times of sudo apt-get install ubuntu-desktop it finally took and startx works.

Now how to modify (and which script) to modify the runtime level for x to automatically start.

Thanks for the help, and too bad the instructions from your last post link are not part of a sticky on the server post forum. Lots of great info on there, even though I didn't need it.

Shawn

---

### Post by 0be1 on 2006-08-30
also one more minor thing. I noticed in gdm on the server that I do not have a synaptic icoon under preferences or administration, and I do not have a network (for configuring etho, dns, etc.) under administration. How would I go about installing those as well (sorry for the OT) since this post was already going.

Shawn

---

### Post by bodhi.zazen on 2006-08-30
> **0be1 said:**
> also one more minor thing. I noticed in gdm on the server that I do not have a synaptic icoon under preferences or administration, and I do not have a network (for configuring etho, dns, etc.) under administration. How would I go about installing those as well (sorry for the OT) since this post was already going.

Shawn

Try
```
sudo update-rc.d gdm start 13 2345 . stop 13 16 .
``` to start gdm on boot.

Do not know re: gnome menus.

---

### Post by 0be1 on 2006-08-30
bodhi.zazen;

Is there a typo on your command? I tried this and it comes back with a screen that looks like when you do *command* --help.

and it says (did you forget "." ?)

Thanks...

Shawn

---

### Post by bodhi.zazen on 2006-08-30
> **0be1 said:**
> bodhi.zazen;

Is there a typo on your command? I tried this and it comes back with a screen that looks like when you do *command* --help.

and it says (did you forget "." ?)

Thanks...

Shawn

sorry... ? spaces between numbers
```
sudo update-rc.d gdm start 13 2 3 4 5 . stop 13 0 1 6 .

OR

sudo update-rc.d gdm defaults
```

---

