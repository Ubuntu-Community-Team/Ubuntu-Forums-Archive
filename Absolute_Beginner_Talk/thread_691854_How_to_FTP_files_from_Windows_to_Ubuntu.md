---
title: "How to FTP files from Windows to Ubuntu"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by drarncruz on 2008-02-09
I am trying to figure out how to upload my website files from my PC (windows) to my testing server laptop (Ubuntu and XAMPP).  I have filezilla on the PC and proFTPd server on the laptop which came with XAMPP.  Both computers use the same IP address and are currently networked through router.  If I use filezilla, you must input username, password, and URL address.  Is it possible to do this with two computers with the same IP address?  If so How?

Thanks

---

### Post by L1nchp1N on 2008-02-09
Have you tried to network the two computers??  I'm not sure how it would be done with a windows and linux clients, but you should be able to make the laptop see the desktop so that you can just copy the files from the Windows machine.

If they're connecting through a router, it should be as simple as allowing access through any firewalls from the LAN ip address.

Not sure how techy you are, however I did find this ... [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba).  Seems a bit complex just to be able to access another machine, however I is a noob as well.

---

### Post by TheWizzard on 2008-02-09
you need to enable port forewarding on your router for port 21 to your ftp-server.
and check if your firewall isn't blocking port 21

---

### Post by drarncruz on 2008-02-09
I guess the main reason for transfering the files from my windows computer to my test server on my laptop is so that I can set the permissions (chmod 777).  I know that you can do this from filezilla when you upload a website.  Is there a way to set the permissions for certain files directly on ubuntu?  I'm trying to run free php scripts that I download off the internet and they require you to set the permissions for certain files in the scripts to 777.  If there is a way to do this directly on ubuntu please let me know.

---

### Post by TheWizzard on 2008-02-10
you can change permissions with chmod
```
chmod 777 filename
```

please be very careful with stuff you download from the internet! especially if the script requires you to change permissions of certain files. NEVER run a downloaded script as root (unless you know what every detail does).

---

### Post by drarncruz on 2008-02-10
thanks for the input guys!

---

