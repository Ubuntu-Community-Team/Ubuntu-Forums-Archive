---
title: "FTP Server"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by zombietls on 2006-10-20
I was wondering that if i could install ubuntu server and have it strictly be an ftp server instead of the full website hosting server, if possible how would it be done and instructions or links is appreciated thank you

---

### Post by thornomad on 2006-10-20
Yes, surely, you can.  

I have some [instructions for doing the LAMP (Linux, Apache, Mysql, PHP) install]("http://www.damontimm.com/blog/how-to-install-a-lamp-server-linux-apache-mysql-php-on-older-laptop-with-ubuntu/") ... but you could choose the "normal" server installation instead of LAMP if you wanted.  

There is more than one FTP option, but I run vsftpd.  You can do a [sudo aptitude install vsftpd]("http://www.damontimm.com/blog/how-to-install-configure-ftp-server-vsftpd-on-ubuntu-linux/") and you will be good to go.

---

### Post by zombietls on 2006-10-20
i can get the lamp server installed but how would i be able to make it so that people can join the ftp not on my local network and im gusing the ftp tools come preinstalled after i run ```
 sudo aptitude install vsftpd
```

---

### Post by thornomad on 2006-10-20
The people outside of your local network would need to know your public IP address and your router would have to be configured to forward all requests for port 21 (ftp port) to your linux server system.  Then, they could login using the public ip address with their ftp software.

---

### Post by zombietls on 2006-10-20
is ftp port 21 udp or tcp ?? and how do i found out my public ip adress. and do i open ports 21 on the public adress or my local ip (168.192.0.3 or public "no idea")

---

### Post by thornomad on 2006-10-20
What kind of router do you have ?  

Go to [http://www.whatismyip.com](http://www.whatismyip.com) to find your ip address.

You want to forward Port 21 on your router to your private IP's port 21.  Open router admin at 192.168.1.1 (or whatever it is) and set it there.  And it is TCP.

---

### Post by zombietls on 2006-10-20
ok ty i am getting cable internet either today or monday so im sure i can get it dont then, so i will have to open port 21 tcp to my local ip 192.168.0.3 then find my local ip and then in order for someone to connect it will be something like [ftp://0.0.0.0](ftp://0.0.0.0) <--- my public ip i am amsumming correct

---

### Post by thornomad on 2006-10-20
Well, the person would need an FTP program ... but, yes, basically:  They will enter the public IP address, which will point to your cable modem, which will trigger the router ... because it is an FTP request it is on port 21 ... your router, seeing it is on port 21, will forward the request on to 192.168.0.3 (your server).

And that should be it.

---

### Post by Streetwalker32 on 2006-10-20
> **thornomad said:**
> The people outside of your local network would need to know your public IP address a

I can now connect from remote computer (smartftp) as anonymous user. How do I set up useraccounts on the server ?

---

### Post by seijuro on 2006-10-20
footnote if you're cable isn't a business line some services such as http,ftp,ssh,etc. may be blocked by your isp check with them to see what their policies are.

---

### Post by thornomad on 2006-10-20
> **Streetwalker32 said:**
> I can now connect from remote computer (smartftp) as anonymous user. How do I set up useraccounts on the server ?

[http://www.informit.com/articles/article.asp?p=378136&seqNum=10&rl=1](http://www.informit.com/articles/article.asp?p=378136&seqNum=10&rl=1)

There are some tips there; maybe try that tutorial.

---

### Post by zombietls on 2006-10-20
> **seijuro said:**
> footnote if you're cable isn't a business line some services such as http,ftp,ssh,etc. may be blocked by your isp check with them to see what their policies are.


doesnt every isp provide you services to http, but anyways my cable is just your regular basic high speed conection, and yes it allows all those.

---

### Post by thornomad on 2006-10-20
> **zombietls said:**
> doesnt every isp provide you services to http, but anyways my cable is just your regular basic high speed conection, and yes it allows all those.

Some ISP do not intend for you to use their bandwidth to HOST a server ... the intend for you to use it to access other people's servers.  And, if you start hosting, sometimes they don't like it or won't allow it.  Not all.  Mine has no problems.

---

