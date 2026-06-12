---
title: "Ubuntu Server"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by kjhud on 2007-12-22
I am wanting to be able to access my desktop from my laptop and use it to save files. I put in 7.1 last night and I was told to install Webmin and Samba. I have both D/L'ed, is this the correct procedure?

---

### Post by cmnorton on 2007-12-22
D/L (Downloaded?)

Does this mean you installed these or just downloaded them? Why do you need anything other than SAMBA? How would you access your desktop other than mount a samba drive?

---

### Post by blueridgedog on 2007-12-22
To use your Ubuntu box as a file server, samba is the correct tool.  

However, you stated that you wanted to access your desktop from your laptop.  Do you mean "desktop" as in a PC or "desktop" as in a computing environment.  samba will let you get to a server or desktop linux box from another system and access files.

Did you install ubuntu server or desktop? (perhaps that is the reason for the use of the word desktop before).

With samba installed there are tons of howtos on the web for getting it setup and the file /etc/samb/smb.conf (which you will edit to create your "shares" is pretty well documented.

---

### Post by kjhud on 2007-12-23
I have both apps installed, Webmin and Samba. I have Ubuntu desktop installed as the OS on my dell desktop. I want to be able to use my dell laptop and access files through my network buy I am having issues and i am not sure if it is because of compatibility issues between Vista and Ubuntu or I just haven't configured my network right.

---

