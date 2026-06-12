---
title: "Set up a Server to Monitor Windows computers.."
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by robbie9gallagan on 2007-09-19
I am looking for a way to monitor the kids computers from Ubuntu..

I have cyber sitter installed now, but I was looking for an Ubuntu alternative...

The kids computers run windows, and I want to set up a server to use as a gateway for their internet access... and I want to install some sorta monitoring software on it to keep track of what they are doing on the net...

Such as .. Monitor Myspace... record IMs... ect..


Any Ideas????

---

### Post by 22bsti on 2007-09-22
if you have an old computer with a few nics (like that old amd k6-2 @450 with 256mb just sitting in your closet collecting dust) of ram you could try out pfsense.  It is a firewall\router bsd distribution, it will give you the ability to do l7 packet filteriing (also known as deep packet inspection) this will allow you to see the content of traffic going through and over your network.  It has very detailed and advanced logging capabilities, it is often used on corporate networks, so its solid and probably the best solution for your particular application, best of all it has an optional gui, that is quite user friendly.

it also has the capability to content filtering, meaning you can limit access to certain websites.

---

### Post by Kilz on 2007-09-22
While you cant use it to monitor , Dans Guardian is a parental control to block out adult content. Ubuntu Christian edition has a version with a nice gui. You can install it to any version of Ubuntu, [Go here.]("http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html")

---

