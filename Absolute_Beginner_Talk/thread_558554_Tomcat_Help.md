---
title: "Tomcat Help"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Dave85 on 2007-09-24
Hi,

Im having a rather hard time with Tomcat. It used to work fine, but now, it doesn't.
I reinstalled it to my /usr/bin/ folder.
Now the werid thing is, I have followed the instrustions for installing tomcat, but when i try and enter into my browser *[http://(computername):8080](http://(computername):8080)*, it doesn't work and times out.
Now, the funny thing is, if i put in *[http://local-host:8080](http://local-host:8080)*, that will work.
The browser works fine as i can search the internet, i can ping the linux computer from any of my 3 computers and it pings fine.
Any idea why this is happening?

Many Thanks

Dave

---

### Post by jnorthr on 2007-09-24
can you ping [www.google.co.uk](www.google.co.uk) ? If not, it may be an issue with your DNS, otherwise i would wonder if there is a sym link that is still pointing to your previous tomcat install. Any chance of that ?

---

### Post by Dave85 on 2007-09-24
Hi jnorthr,

I can ping [www.google.co.uk](www.google.co.uk) without a problem.

I can't see any reason for a sym link pointing in another previous. As when you startup tomcat from the bin folder, doesnt it look for all the file info from that tomcat dir (above /bin). I may be wrong though.

Now, i have run a port scan on the machine and it doesnt seem like port 8080 is working, but then, when i try and change the port in the config.xml file to another port, it still doesnt work. But then again, i can access tomcat using that port through the local-host, but not through the computer name.

Any ideas?

---

