---
title: "Dialer"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by rboik on 2006-07-13
](*,) Hi: I just installed Ubuntu on my machine, but can't find the dialer to set up, I have a dialup conection. Any ideas? Thanks rboik

---

### Post by lordlollo on 2006-07-13
Go to 

System -> Administration -> Networking

then enter your root password. Isn't 'Modem connection' listed? If it is, you can simply configure your connection with data provided by your isp.

Hope this help.

---

### Post by rboik on 2006-07-13
Yes it does I just there was more to it for some reason. It dials but doesn't hook up I must have the settings wrong. I will have to get ahold of my ISP. thanks rboik

---

### Post by rboik on 2006-07-13
](*,) I am still confused on this. I got ahold of my ISP and they said all I needed to do was put DHCP in, but couldn't tell me where. In my network it doesn't have an add button where it shows the modem like it does in the documentation. I am able to dial in but not connect. rboik](*,)

---

### Post by editrix on 2006-07-13
> **rboik said:**
> ](*,) I am still confused on this. I got ahold of my ISP and they said all I needed to do was put DHCP in, but couldn't tell me where. In my network it doesn't have an add button where it shows the modem like it does in the documentation. I am able to dial in but not connect. rboik](*,)

Sorry to ask, but is the person you spoke to knowledgable in Linux? There's a bug in Dapper that causes hangups and it's a real easy fix, and that may be your problem. Try this:

In /etc/ppp/options comment out the line 
auth
that requires remote host to authenticate itself.

I'm sure I copied this from a post here in the forums, but the search engine isn't turning up anything, so sorry, can't give you the full URL.

---

### Post by rboik on 2006-07-14
No the ISP doesn't support Linux so they don't know much about it. I also used the search engine at first to no avail. Thanks for your help. rboik

---

