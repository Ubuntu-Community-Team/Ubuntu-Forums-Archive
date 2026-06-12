---
title: "Local Server With /home/&lt;username&gt;/www/ As Root"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-05
Hi I'm a webdesigner coming from windows where I ran a local webserver called WosX which is a portable local webserver. It was setup so that I just had to run the exe file and the server and mysql database was running. The \www\ directory was inside the serve and was running from the usb folder.

I have been trying to install a local server on Ubuntu and the one I have tried is LAMP, and I have tried to follow, among others, [this tutorial]("http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu") on setting it up with phpmyadmin. The problem is that it places the /www/ folder in the /var/ directory But whatg I would really like, was for the www folder to be somewhere inside my /home/<username>/ folder.

Is there anyway to accomplish that?

---

### Post by Pragmatist on 2007-06-05
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Check out the section titled "Using Apache"

---

### Post by goatflyer on 2007-06-05
How about this idea, that keeps apache happy without changing it and maybe is good enough for you too.

```

cd ~
ln -s /var/www www

```


Only thing to check is if you have permissions to work on files.

---

### Post by kasperbs on 2007-06-06
Thanks for your replies, very usable. goatflyer can you explain my what that command does. O think I get the idea, but I'm not entirely sure what it means, something like a shortcut or? The permissions need to be given for the /var/www folder right?

EDIT: Also is there any method available so that I can actually put the /www folder inside my /home folder so that apache reads from it in that position. The server will only run locally so I'm not so worried about security

---

### Post by indytim on 2007-06-06
Alternative Suggestion : change the permissions on /var/www and give your self ownership of /www .


That's what I'm doing on my local LAMP.

Good Luck,

IndyTim

---

