---
title: "Cannot access web server outsite LAN"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-09-10
I set up my Apache2 web server on Ubuntu Desktop 7.04 . (horrid, I know)
The server works fine inside my LAN.
I can go to my IP and it will load etc.

I set up port forwarding on my router to port 80 to my ubuntu server 198.168.1.5 etc.

I did this last year and everthing was fine. I could access my site from anywhere.

But this time I can't seem to load the website outside my LAN.

Any ideas?

If file permissions on folder/file contents is not correct can this pose a problem?

---

### Post by zipperback on 2007-09-10
> **Xarok said:**
> I set up my Apache2 web server on Ubuntu Desktop 7.04 . (horrid, I know)

Running a small web server on your desktop system is fine for personal use and such, just make sure you do it with a decent amount of memory and such in your system.

I wouldn't try to run a commercial business or something with it though.

> **Xarok said:**
> 
The server works fine inside my LAN.
I can go to my IP and it will load etc.

I set up port forwarding on my router to port 80 to my ubuntu server 198.168.1.5 etc.

I did this last year and everthing was fine. I could access my site from anywhere.

But this time I can't seem to load the website outside my LAN.

Any ideas?


Yes. Go here -> [http://www.hidebehind.net](http://www.hidebehind.net)

Enter the url for your webserver  and see if it displays.

It's an anonymous proxy and it will try to pull the web page up and proxy serve it back to you.

Also try: [http://192.168,x,x](http://192.168,x,x)  (or whatever your web server ip address is)  directly from your browser.

[> **Xarok said:**
> If file permissions on folder/file contents is not correct can this pose a problem? 

File permissions are important. But I suspect the problem is a simple configuration issue. Unless of course, your isp has port 80 blocked for incoming traffic requests. If that is the case, then you will need to change the port for your web server.

- zipperback

---

### Post by rich.bradshaw on 2007-09-10
I agree, prob your ISP blocks port 80... change it to something else, and load your IP using

xxx.xxx.xxx.xxx:port

to load it in Firefox.

---

### Post by ShagzModo on 2007-09-10
Are you 100 percent sure of your router config?

---

