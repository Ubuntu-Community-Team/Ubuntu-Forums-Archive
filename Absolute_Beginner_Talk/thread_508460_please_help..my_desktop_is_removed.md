---
title: "please help..my desktop is removed"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by waterspider on 2007-07-24
i was on the process of upgrading my edgy, after it finished i restarted the system then nuthing appear on the screen except a terminal window...please any..i want to get my desktop back..what do i do?:(

---

### Post by Foxmike on 2007-07-24
Is there an error message telling you that the X server couldn't load ore something like that?

---

### Post by Carlos Santiago on 2007-07-24
try:
```
sudo apt-get install gnome-desktop
```

---

### Post by waterspider on 2007-07-24
Hi, there is no any error message.:confused:

---

### Post by Carlos Santiago on 2007-07-24
then try:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by waterspider on 2007-07-24
sudo apt-get install desktop, i tried it but not it is not working....any help

---

### Post by Tiekyl on 2007-07-24
What does it do when you try to install ubuntu-desktop?

---

### Post by Rocket2DMn on 2007-07-24
What happens when you login at that terminal and type "startx"

---

### Post by waterspider on 2007-07-24
when i typed startx,it will says that: xauthor:creating new authority file /home/iceman/.serverauth.4461
                                                          x:user not authorised to run the x server, aborting.
                                                            could not get a file descriptor referring to the console 

hplease help me

---

### Post by Rocket2DMn on 2007-07-24
Try
```
sudo dpkg-reconfigure xserver-common
```
found at: [http://www.mail-archive.com/slug@slug.org.au/msg10537.html](http://www.mail-archive.com/slug@slug.org.au/msg10537.html)
They use debian, but Ubuntu is built on debian.

---

### Post by waterspider on 2007-07-24
it still saying that package 'x server-common is not installed and no info available....thnx for all the support

---

### Post by kostkon on 2007-07-24
> **Rocket2DMn said:**
> Try
```
sudo dpkg-reconfigure xserver-common
```
found at: [http://www.mail-archive.com/slug@slug.org.au/msg10537.html](http://www.mail-archive.com/slug@slug.org.au/msg10537.html)
They use debian, but Ubuntu is built on debian.

For ubuntu it's:

```
sudo dpkg-reconfigure xserver-xorg
```

Thus, do the above and then just reboot with

```
sudo shutdown -r now
```

or do this:

```
sudo /etc/init.d/gdm start
```

I hope I helped you somehow.

---

### Post by Rocket2DMn on 2007-07-24
Ah, didn't want him to have to reconfigure the xorg since I'm not sure it relates to the rights to start the X server.  It seems like the problem is different to me.

---

