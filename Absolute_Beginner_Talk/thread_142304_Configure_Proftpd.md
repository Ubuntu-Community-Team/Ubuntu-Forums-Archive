---
title: "Configure Proftpd"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Ignite_nz on 2006-03-10
I just installed proftpd, and I have no idea what so ever how to configure the users etc, can someone give me a brief description of what I do to manage users and their directories etc?

Also is there a packag I can get that lets me have a mail server on my Ubuntu system:confused: 

Thanks!

---

### Post by frodon on 2006-03-10
For proftpd, have a look to my guide, it may help you : [http://www.ubuntuforums.org/showthread.php?t=79588](http://www.ubuntuforums.org/showthread.php?t=79588)

---

### Post by Ignite_nz on 2006-03-10
OK I installed that GUI thing, but im still not having any luck.

I added a user and whenever I try to connect the connection just gets refused. I typed ps -e and nothing came up with proftpd in the list...

---

### Post by frodon on 2006-03-10
Sorry but i can't help you with so few informations.

Give me the log of connections error you get, tell me what is your configuration : do you have a router, firewall, are you trying to connect with the same computer which run the server and ... with what : web browser, FTP client.

If you type : ```
sudo /etc/init.d/proftpd start
```Do you get errors ?

So make all the tests that could provide informations and give the maximum details.

---

### Post by Ignite_nz on 2006-03-10
```
 /etc/init.d/proftpd start 
```
Generates the following error:
```
root@server:/etc# /etc/init.d/proftpd start
Starting ProFTPD ftp daemon:  - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
.

```

---

### Post by frodon on 2006-03-10
I guess you use the GUI, there a lot of options in that GUI so there surely something wrong in the config you generated, anyway you could put for the group the name of the user you use for the ftp server if you don't find the way to disable this error.
I already met people here who get this error, i tested the GUI and never got it so i think it's just a wrong configuration.

---

### Post by Ignite_nz on 2006-03-10
Okay I'm getting nowhere, I have no idea what information to give you, how do I remove proftpd and gproftpd so that I can start it all over again, and try from there?

---

### Post by Ignite_nz on 2006-03-10
Okay I've tried EVERYTHING. The server starts but when my FTP client tries to onnect to it, the connection just drops right away.
```
[R] Connecting to 10.0.0.6 -> IP=10.0.0.6 PORT=21 (attempt # 1)
[R] Connected to 10.0.0.6
[R] Connection failed (Connection lost)

```

---

### Post by frodon on 2006-03-10
You can use synaptic to remove gproftpd and proftpd.
Do have a firewall or a router ?
I advice you the partB of the guide if you're not scared to use a FTP server without a GUI to configure it, I can't provide you a lot of support for the GUI because it's not my script and therefore i don't know how it has been designed.
Also many people have used the partB successfully and therefore me and other people here can provide you more support using this way.

---

### Post by taurus on 2006-03-10
I have both proftpd and vsftpd running (on different machine, of course) and I find that vsftpd is a little easier to config than proftpd although proftpd is always my first choice.  So, if you still can't get proftpd to work, remove it and try vsftpd with apt-get then.

---

### Post by Ignite_nz on 2006-03-10
OK, this is getting beyond a joke. I've tried absolutly everything, even vsftpd, and I just have NO idea how to configure. Would someone be interested in SSH'ing to my server in order to setup proftpd for me? Because I just don't know what I'm doing wrong, and it's driving me absoluty crazy!

Your help would be greatly appreciated.

---

