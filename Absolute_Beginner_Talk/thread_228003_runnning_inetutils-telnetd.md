---
title: "runnning inetutils-telnetd"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-08-02
Hi I have installed inetutils-telnetd on machine to be able to access my ubuntu system at home (I have Ubuntu at work) via telnet. But I dont know how to run the application?
Can someone help me?
I assume it is under /usr/sbin because there is a file there like telnetd.
But it does not do anything. Any help will be appreciated. Thanks.

---

### Post by mgor on 2006-08-02
you DON'T want to use telnet, since all information sent to/from the server will be in cleartext. what you want is ssh which will encrypt the traffic,
```
sudo apt-get install openssh-server
```

'openssh-client' have the command 'ssh', which you will use just as the telnet client. a good and free windows client is putty.

---

### Post by saule on 2006-10-11
It took me a lot of time to have telnet server and ftp server working. What worked at the end was :

- Install package xinetd : this a kind of super service that controls ftp and telnet server. This xinetd is the successor of inetd, I knew nothing about those 2 services before and maybe it would have saved me a lot of time to install inetd instead of xinetd ! 
- Install telnetd and ftpd. The problem here is that this install does not update the file xinet.conf

- Modify the file /etc/xinet.conf and put the following lines
(note this is basic configuration, can be better !!)

service telnet
{
        socket_type = stream
        protocol    = tcp
        wait        = no
        user        = root
        server      = /usr/sbin/in.telnetd
}

service ftp
{
        socket_type = stream
        wait        = no
        user        = root
        server      = /usr/sbin/in.ftpd
}

then restart the xinet daemon with 

$ /usr/init.d/xinetd restart

---

### Post by steve.horsley on 2006-10-11
You chose to ignore mgor's advice then? There's a reason telnetd is not part of the standard install, y'know. Really, you should use SSH instead.

---

