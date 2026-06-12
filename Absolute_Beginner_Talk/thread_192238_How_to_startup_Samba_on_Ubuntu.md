---
title: "How to startup Samba on Ubuntu"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2006-06-08
Hello. Every time I reboot my Ubuntu Linux the Samba service stops and I have to start it manually. What is the best/easiest way start up Samba automatically and how do I do this on my Ubuntu Linux ?

---

### Post by chrisdee on 2006-06-08
Any suggestions ?

---

### Post by gogos on 2006-06-08
Make sure the file '/etc/init.d/samba' exists, then try to run the following command:

```
sudo update-rc.d -f samba start 20 3 .
```

(make sure to include the period at the end)

---

### Post by fyassine on 2006-06-14
I have samba running on my system but can't seem to find samba in /etc/init.d/samba in order to be able to start and stop the service as needed.

What would I need to do in order to get samba in the correct location?

---

### Post by gogos on 2006-06-14
Did you install samba with apt-get/synaptic?  The service script in init.d should be set up automatically if you did.

---

### Post by bigken on 2006-06-14
go into a console and type 

sudo apt-get install samba

sudo smbpasswd -e yourname*      add new samba password *

sudo smbpasswd -a yourname                                    

see if that fixs it

---

### Post by Triad773 on 2006-06-14
Also something I saw yesterday when I was trying to do the same thing, try uninstall-reinstall as perhaps the program did not install correctly. I saw that posted somewhere here - when I did, that I saw where there are a few versions of Samba, and I had not specified the one I wanted for my LAN. Installing the one I was looking for made all the difference.

Hope that helps

Cheers

---

