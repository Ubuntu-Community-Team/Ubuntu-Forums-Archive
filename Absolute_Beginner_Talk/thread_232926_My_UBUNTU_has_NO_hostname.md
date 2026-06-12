---
title: "My UBUNTU has NO hostname"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by chopper81 on 2006-08-09
Thank you for the help that I received earlier today. Could any one out there please tell me how to get the hostname back on my system. From the terminal all I get is <user>@:~ .There is no hostname therefore I can not do anything with that laptop. I can not open up the Connection properties to change the hostname back. As soon as I click on configure, it just goes away.
Chopper81

---

### Post by kb3hkg on 2006-08-09
Try running the following command in a command line

hostname <desired name>

---

### Post by chopper81 on 2006-08-09
I put in hostname <...> (only with the real hostname) and got back <you must be root to change the host name>. So I out sudo in front of it and tried again. This time I got back <unable to lookup via gethostbyname().

---

### Post by chopper81 on 2006-08-09
I tried to boot up in Recovery mode and I got an error that said <Temporary Failure in name resolution>. Does that help out or make things worse?
chopper81

---

### Post by steve.horsley on 2006-08-09
I was going to suggest using recovery mode. If that doesn't work, you need to get a live CD, and mount your hard disk so you can edit files from there. 

You need to put a single line containing the hostname in the file /etc/hostname and you need to put the exact same hostname in the file /etc/hosts on the line that starts with "127.0.0.1 localhost". My hostname is StevesPC, so that's what's in /etc/hostname, and my /etc/hosts file containd this line:
127.0.0.1 localhost StevesPC


Assuming you root partition is /dev/hda5 (change as appropriate), the commands on the live CD you need are:
> sudo mkdir /media/hda5
sudo mount -t ext3 /dev/hda5 /media/hda5
sudo gedit /media/hda5/etc/hostname /media/hda5/etc/hosts

---

### Post by chopper81 on 2006-08-09
Could you please suggest a way to get this live CD?
Chopper81

---

### Post by Spinelli on 2006-08-09
Try this link.
[http://www.ubuntu.com/download]("http://www.ubuntu.com/download")

---

