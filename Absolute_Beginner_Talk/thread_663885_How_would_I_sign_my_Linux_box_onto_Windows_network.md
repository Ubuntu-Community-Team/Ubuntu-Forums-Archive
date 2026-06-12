---
title: "How would I sign my Linux box onto Windows networks?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2008-01-10
Well, this is probably a really dumb question, but I'm going to ask anyway.

My school is networked together through Windows. All the OS's are Vista, specifically.

I have a project coming up and I need to show Debian off on the network - this means I'll have to sign in with my username and password.

I've tried Samba before, but it is confusing. Maybe I'm just stupid?

Each student is given four numbers, then are allowed to make the password of their choice. The logon is then sometimes followed by an at (@) sign and location of a certain network - the middle school has their own network, the high school has their own network, etc.

Something like this: ####@hs.school.edu

It's not against the rules or anything (if you are thinking along those lines) because I'll still be behind the schools filter.

I just need to show off the project and it needs to get onto the net for some resources... Can someone help me?

---

### Post by Pevichaey5 on 2008-01-10
i think you are after on how to join a domain controller

if so

System>>Administration>>Network

click on the general tab and specify the domain name there

---

### Post by kestrel1 on 2008-01-10
You may be better off asking the network technicians to set this up for you. If they are worth anything they should know how to get you connected with Ubuntu.
Have you tried going to Places & Connect to server? You get the option to connect to a Windows share. If you need to get on to the Internet, you may need to set your connection up to go through the schools proxy server (if they have one). You would have to know the servers IP address & the port number to use.

---

