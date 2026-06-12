---
title: "(man-in-the-middle attack)!"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-10-31
dod@UBUNTU704:~$ ssh mark@192.168.1.199
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
62:92:a0:62:c5:67:7d:ce:6a:9e:59:c0:e5:9b:d7:58.
Please contact your system administrator.
Add correct host key in /home/mark/.ssh/known_hosts to get rid of this message.
Offending key in /home/mark/.ssh/known_hosts:2
RSA host key for 192.168.1.199 has changed and you have requested strict checking.
Host key verification failed.
dod@UBUNTU704:~$ 


how can i find that man(IP) who is in middle ?

---

### Post by thelocust on 2007-10-31
If the computer you are trying to connect to is a trusted computer (like one on your own network) It is likley that it's host key change because of a recent upgrade or something like that. go in to your /home/username/.ssh folder and delete the text file the next time you connect it will remake that text file with the new host key

---

### Post by macogw on 2007-10-31
Um...this isn't much of a "beginner" question.  It's network security.  I've seen that, though, when I wasn't authenticated to the VPN and tried to ssh then got caught at the VPN's gateway and so the response was coming from a different server than what I was trying to access.

---

### Post by MrFSL on 2007-10-31
> Um...this isn't much of a "beginner" question.

It could be a beginner question depending.

If this is happening on your internal network and you use DHCP it might be the case that your IP addresses are changing and IP's aren't matching up with the certs as described by thelocust above.

---

### Post by macogw on 2007-10-31
> **MrFSL said:**
> It could be a beginner question depending.

If this is happening on your internal network and you use DHCP it might be the case that your IP addresses are changing and IP's aren't matching up with the certs as described by thelocust above.

oo hey its a 192.168 didnt notice that... i notice that there's a lot of things that get asked in absolute beginners that seem like they should go in one of the specific forums but get put here because the person is a beginner, rather than because the question is of a beginner nature, and a security question seemed like it would be in the former category.

---

### Post by mokkai on 2007-10-31
> **thelocust said:**
> If the computer you are trying to connect to is a trusted computer (like one on your own network) It is likley that it's host key change because of a recent upgrade or something like that. go in to your /home/username/.ssh folder and delete the text file the next time you connect it will remake that text file with the new host key


after i delete /home/mark/.ssh/known_hosts  ,everything is fine
thank you

---

### Post by MrFSL on 2007-10-31
> i notice that there's a lot of things that get asked in absolute beginners that seem like they should go in one of the specific forums


I agree... but perhaps the name should be changed. People that believe that they themselves are "absolute beginners" post their questions in the "absolute beginners" section.  So it has become more of a category defining the user instead of the subject.

---

### Post by academiphiliac on 2007-11-22
Had this problem today. (Happy Thanksgiving, everyone!) Typically, this is not something to worry about, it seems from these posts. Should I actually find a genuine breech, though, does anyone know what I should *do*?

---

### Post by bodhi.zazen on 2007-11-22
> **academiphiliac said:**
> Had this problem today. (Happy Thanksgiving, everyone!) Typically, this is not something to worry about, it seems from these posts. Should I actually find a genuine breech, though, does anyone know what I should *do*?

Well, the first thing is to determine the cause of the message.

If you do not know the cause, then the advice to delete ~/.ssh/known_hosts is **BAD**.

This error message is saying that something has changed with the server you are ssh into. If the server is on dhcp for example and the ip changed, new network card, you changed keys, etc.

If you *know* you changed these things, OK, then delete, or better edit, ~/.ssh/known_hosts.

Otherwise, you need to contact the server administrator for advice.

If you delete ~/.ssh/known_hosts without doing your homework you have no idea where you are connecting [-X

---

### Post by academiphiliac on 2007-11-22
It's the home LAN, so in this case I am the administrator. It looks like it was just a DHCP issue, not an attack. Just wanted to know if, in event of a real attack, all you had to do was restart everything or something.

As per the suggestions I was getting in the chatrooms, I think I just need to get my lazy butt over to the MAC settings and make sure only the home computers can access the wifi.

---

