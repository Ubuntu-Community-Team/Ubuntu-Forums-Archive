---
title: "DNS NOOB question"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by teqsun on 2008-03-25
ok so I have installed LAMP, got my perl, php, mysql, phpmyadmin, apache, ftp, and samba (hopefully) working the way I want them to.  I have a pretty fair understanding of how all of these work (except samba but I can get to that later)

I keep hearing about DNS this DNS that... I understand that it is a Domain Name Server (service?)  I also understand that through magic it tells the whole world that mydomain.com should point to my IP.

That is basically all I know about this.

I have a few domains registered,  teqsun.com lboc.net mylboc.net and I would like to use at least one of them for my home machine.  I am currently using a DYNDNS service provided by no-ip.

The whole reason behind this is for my apache server, I want to have the ability to use subdomains.  I know I need to use DNS to do this but when I do a google about DNS all I get is stuff that is way too simple or way too complex for my current understanding.

Can someone please shed some light or point me in the direction of some help?

---

### Post by Dithers on 2008-03-25
Do you have a static or dynamic IP?
The Dynamic DNS will be your only option without a satic IP

...or redirecting to your dynamic from a webhost

---

### Post by teqsun on 2008-03-25
I have a static ip, so long as the cable modem is not reset.

---

### Post by chilinski on 2008-03-25
I'm not sure I understand, so let me present something.

You have an Apache server on your network at home. You want it to serve web pages for one of your domains (let's say the teqsun.com domain). And maybe you want to also serve web pages for mydogiswonderful.com and theworldsmyoyster.com and several others.

On your Apache server, you tell it that you will host the virtual domains mydogiswonderful.com and theworldismyoyster.com in the httpd.conf (or related file depending on Apache version) file.

Then you go to wherever you have your domains registered and set up the DNS A Records for teqsun.com, mydogiswonderful.com and theworldismyoyster.com to all point to the same ip address. I know there's a way now to handle dynamic addresses if you have that on your home network connection, but I haven't done that yet. I've always had static ips. 

Does that help? Or did I completely miss the point?

---

### Post by teqsun on 2008-03-25
that helps alot thanks!

---

