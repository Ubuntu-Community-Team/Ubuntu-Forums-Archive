---
title: "Error Networking Panther to Ubuntu"
date: 2007-06-04
forum: Apple PPC Users
---

### Post by bridesign on 2007-06-04
I'm trying to network a Ubuntu box (Edgy) to my OS X Panther G5. I've read through many forums and while they say it is simple I still haven't succeeded in this endeavor. Admittedly I'm a Linux noobie. I have manged to connect FROM Ubuntu to the mac but not from the G5 to Ubuntu. 

As far as I can tell both machines are on the same workgroup. Sharing is setup, a folder is set to be shared on both machines, privileges set, along with passwords. I found a beautiful screenshot of the Go to Server screen on Ubuntu that helped me configure that correctly and finally connect to the G5. On the G5, however, I select Connect to Server, enter smb://<machine IP>/ and I see the correct shared folder window prompt. I enter in my username and password but instead of connecting I get an error "Could not connect to server because the username or password is not correct."

This seems to tell me I've missed something on the Ubuntu configuration since Ubuntu can connect to the mac. Does that makes sense or am I crazy? Anyone have any ideas for a fix?

---

### Post by stmiller on 2007-06-04
In the Mac system prefs under sharing, click to allow 'windows sharing'

or in other words, samba. :)

---

### Post by TH3_D0ct0R on 2007-06-05
yea well i fiddled around with my mac downstairs and when it asks for a password and user name dotn put one in...i can see the files but i cant write to them...ill prolly figure that out later...but see if the no name and password thing works.



Respectfully

Th3_D0ct0R

---

### Post by bridesign on 2007-06-06
> **stmiller said:**
> In the Mac system prefs under sharing, click to allow 'windows sharing'

or in other words, samba. :)

On the G5 Windows Sharing and Personal Sharing were both on already. Still the password and username error persists. Anyone else have an idea?

---

### Post by bridesign on 2007-06-06
> **TH3_D0ct0R said:**
> yea well i fiddled around with my mac downstairs and when it asks for a password and user name dotn put one in...i can see the files but i cant write to them...ill prolly figure that out later...but see if the no name and password thing works.



Respectfully

Th3_D0ct0R

Thanks D0ct0R, I tried your suggestion. Without the username, password or Domain listed I can log in but like you I did not have permission to transfer files. That seems to imply to me that there is something going wrong with the username or password setup on the Ubuntu machine. Have you had any success with a work around?

---

### Post by TH3_D0ct0R on 2007-06-07
yea..idk i think that an operating system like mac OX which is unix based i believe should be able to use unix networking....and there is a unix network thing on the ubuntu shared folder app....but about the username and password on the ubuntu machine....idk if its wrong i just think that its not set up in windose way..i spose you havent tried to network your mac with a windose machine?

---

### Post by stmiller on 2007-06-07
Samba requires that you have a registered samba username and password, on your local machine. If the OS X user/pass is different from your Ubuntu one, try adding the OS X user/pass as a samba user on your Ubuntu box. This page has some info:

[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/)

---

