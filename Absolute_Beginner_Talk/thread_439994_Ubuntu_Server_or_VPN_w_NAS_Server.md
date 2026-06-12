---
title: "Ubuntu Server or VPN w/ NAS Server?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by csleech on 2007-05-11
Hello all!

I am rather new to linux and can honestly say I haven't done any more than install a couple different distros and play with them for a couple days before I have become frustrated with not knowing what to do. I am very profficent in Windows (I am an Application Engineer for a software reseller) and want to take the next step in trying to learn linux. So PLEASE bear with me.

With that out of the way :), I would like some opinions or advice from some of you out there that know this software.

At home I currently have three computers and a laptop. My one computer houses 5 hard drives and contains about 800MB of information. I would like to be able to share that accross my house (eventually) to any machine that is connected to my network; now I know I can do this with Windows, but follow along. I have a machine that I am dedicating to host files and currently I have NASLite running on that machine; there are some downfalls to NASLite (I have CDD verion) such as it cannot set user permissions and you cannot block access to a certain drive to a certain user. My ultimate goal is to share this information with friends and family and also allow them to have a drive to place information to share with me. I want to be able to control access to the discs based upon a user login. 

I have several options in doing this. One of them is to purchase a VPN router that controls the access for me. There is one that I have been looking at that is a ZyWall SSL 10 that allows for remote CLIENTLESS VPN connections (clientless is a MUST for me, my family is computer illiterate). However, this solution is $350. Another solution is to purchase a Linksys and do the DD-WRT flash and utilize the VPN capabilities of that modified router. The issue with this is that I do not know if you can control disc access with this firmware (I am in the process of trying to find out).

LAST option that I see is to keep the router that I have, enable VPN passthrough and setup a VPN type server. I do not know anything about what the linux community has to offer as a solution for my VPN desires, but I figured no better place to ask then here. :). So with that said, what is a must for my situation is as follows:

1. Clientless access (HTTP or HTTPS)
2. Controlled Access to certain discs (or files on discs)
3. Security, this is a must, some of the files are sensitive information.
4. MUST work with Windows (currently NASLite uses SMB to do this)
5. Scalability, I need the ability to keep adding hard drives using PCI expansion cards.

Can anyone from the community give me a linux (Ubuntu) prospective on this :confused: 

THANKS IN ADVANCE EVERYONE!!! :)

---

### Post by freebeer on 2007-05-11
Hi!

I'm interested in following this thread, alas, I don't have a solution for you as you've described it.  I'm wondering if just setting up a web server with Apache isn't an easy solution for you.  Then control access to the files through file permissions (you'd probably want them on a Linux ext3 or similar formatted drive/partition?  I'm sure there's a tighter, more elegant way to do this, but that's just off the top of my head.  You could then tweak it later as you learned more.

You might also want to post this up on the Servers & Security forum area... I suspect you'll get a better reply. :D

---

### Post by csleech on 2007-05-11
[http://ubuntuforums.org/showthread.php?p=2634700#post2634700](http://ubuntuforums.org/showthread.php?p=2634700#post2634700)

Posted there as recommended. Thank you!

---

