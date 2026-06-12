---
title: "chmod...uh...i don't get it"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-11-08
i'm trying to change permission on the userChrome-example.css file so that i can change it to userChrome.css. everything i've tried has resulted in a **permission denied** response. i was reading about this 'chmod' command in the o'reilly linux pocket guide and i just don't get it. would i just enter *sudo chmod rwx 'the file name'*?

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxdeer.jpg[/IMG]

---

### Post by souki on 2005-11-08
sudo chmod +rw filename

---

### Post by Ali_Baba on 2005-11-08
Hi,in chmod command you must first write to who you are giving access and then the type of access.like sudo chmod a+rwx is for all users chmod u+rwx is for owner and chmod g+rwx is for group and so on.read man chmod for more help :D

---

### Post by Kyral on 2005-11-08
....Time for another redition of my "For Beginners" series? Permissions? :D

---

### Post by wishyjr on 2005-11-08
yes, that would be helpful Kyral, thanks :)

also, when you run the chmod command is the change of permissions permenant? or do the permissions 'reset' after a reboot or something?. ta.

---

### Post by rmjokers on 2005-11-08
The permissions you set are permanent unless you set them for a temporary file such as a device in the /dev directory.

---

### Post by HJThis on 2005-11-08
Hello,Kyral

Man i would love for you to get somthing like
this going after the great Thread on Terminal
howto.

so please when & if you find the time

Best of luck

---

### Post by teddy69 on 2005-11-08
[QUOTE=Kyral]....Time for another redition of my "For Beginners" series? Permissions? :D[/QUOTE]

that'd be great :)

---

### Post by wishyjr on 2005-11-09
ok, i'm trying to let myself (username is 'paul') write data to a directroy called /data on my filesystem. Ive entered the command: **sudo chmod a+rwx /data**. The command ran through but i stil cant write stuff to it -what am i missing?

btw, im the only user of the system and the /data directory is owned by root.

thanks

BUMP! anyone?

---

