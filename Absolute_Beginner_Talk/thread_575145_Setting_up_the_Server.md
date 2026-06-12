---
title: "Setting up the Server"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-10-13
Hey guys. I currently have Apache, PHP and MySQL installed on my system, and it is on a local IP address. But anyways, this is my problem. I can view the index of/ thing on my Linux machine (not by typing in localhost, but the ip address 127.0.1.1) but only from there. I tried going to another computer in my network, and it did not show up. I am not sure what I need to do to get it to work on all computers in my network. Do I need to set up some sort of LAN or something? Thanks.

---

### Post by Dr Small on 2007-10-13
*Do* you have LAN (Local Area Network) where eveything runs through a router ? If not, then the other computers can not access it.

If so, then you probably need to enable port 80 on your firewall to allow incoming requests to your webserver.

I don't understand why "localhost" doesn't work, yet "127.0.0.1" does. That sounds like some host problem, but I could be wrong.

Dr Small

---

### Post by milosz.galazka on 2007-10-13
What is your IP address? 

You can find it by using *ifconfig* command...

---

### Post by drndrw on 2007-10-13
Sorry, I knew someone would ask me why the ip works but localhost does not. The localhost does work. As does the IP address. But I don't have any blocked ports on my router. What should I do? And if it helps, I am using a netgear router.

---

### Post by milosz.galazka on 2007-10-13
What messages do you see when executing:
```
sudo /etc/init.d/apache2 restart 
``` 
If you something similar to
```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```
Then add
```
ServerName *:80
```
to */etc/apache2/apache2.conf* file

---

### Post by PilotJLR on 2007-10-13
127.0.0.1 is the same thing as localhost, which is why it doesn't work elsewhere on your LAN. As the other poster said, find your private ip address (probably 192.168.1.XYZ) using ifconfig, then reference that instead.

---

### Post by drndrw on 2007-10-13
Well, I fixed that. As it turns out, my address is 192.168.0.5. But now I have three more questions: 1.) Where did my machine find this address? In resolv.conf, I have it set to 192.168.0.1. 2.) How can I change this address, seeing that it is not from the resolv.conf file? 3.) This is sort of stupid and pointless, but I would like to be able to creat my own domain name extensions for my LAN. I know I need to set up some sort of root server. How can I do this? Oh, and I should add that my router's address is 192.168.0.1, so that might help in answering my first question. Thanks!

---

### Post by milosz.galazka on 2007-10-14
resolv.conf describes where to find DNS servers. It points to your router because it relays DNS queries from your computer to your ISP DNS servers.

Your address is probably assigned dynamically by your router.

---

### Post by drndrw on 2007-10-14
That's what I figured. So then if I chose an address that currently isn't being used (eg. 192.168.0.6) it might use that rather than the one ending in 5? And also, what can I do to set up a root server on my server? And I just noticed that my address changed. Is there a way that I can keep it static?

---

### Post by milosz.galazka on 2007-10-14
For bind configuration you could look [here]("http://langfeldt.net/DNS-HOWTO/BIND-9/") and [here]("http://www.faqs.org/docs/Linux-HOWTO/Chroot-BIND-HOWTO.html").

Then you can assign ip address by MAC at your router and change distributed DNS address to your server.

---

### Post by drndrw on 2007-10-14
Okay, I did that. I hope it doesn't change now. But this is my problem. I tried creating a record in BIND, but it doesn't appear to work now. Why is that? I followed all of the steps I was told to...

---

### Post by milosz.galazka on 2007-10-14
Did you updated resolv.conf to your ip address? How now your bind configuration looks like?

useful tool:
*dig anyhostname *
or
*dig anydomain ANY*

---

### Post by drndrw on 2007-10-14
UH what would I update it? With the new hostname and IP address? And also, I only have one IP address for the mail and nameservers. IS that okay? And after I updated resolv.conf, dig still looks the same. Oh, and I am using the first tutorial (the linux.bogus one) that you gave me.

---

### Post by milosz.galazka on 2007-10-14
hmm... there are other services running so the best way is to setup testing environment like by using qemu on home desktop.

EDIT: Simple example
I just created cut & paste (from tutorial link above [linux.bogus]) config that you can check.
I  installed *bind9* and added to */etc/bind/named.conf*
```
zone "blue" {
        type master;
        notify no;
        file "/etc/bind/db.blue";
};
```

And created file */etc/bind/db.blue*
```

;
; Zone file for blue
;
$TTL 3D
@       IN      SOA     ns.blue. hostmaster.blue. (
                        199802151       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        2H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
;
                NS      ns              ; Inet Address of name server
                MX      10 mail. ; Primary Mail Exchanger
                MX      20 mail2.   ; Secondary Mail Exchanger
;
localhost       A       127.0.0.1
ns              A       192.168.1.101
mail            A       192.168.1.101
mail2           A       192.168.1.101

```

Then I edited */etc/resolv.conf* 
```
nameserver 127.0.0.1
```

Now results:
```
root@bluebird:/etc/bind# dig blue ANY

; <<>> DiG 9.4.1-P1 <<>> blue ANY
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13898
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;blue.                          IN      ANY

;; ANSWER SECTION:
blue.                   259200  IN      SOA     ns.blue. hostmaster.blue. 199802151 28800 7200 2419200 86400
blue.                   259200  IN      NS      ns.blue.
blue.                   259200  IN      MX      20 mail2.
blue.                   259200  IN      MX      10 mail.

;; ADDITIONAL SECTION:
ns.blue.                259200  IN      A       192.168.1.101

;; Query time: 3 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Oct 14 23:26:07 2007
;; MSG SIZE  rcvd: 143
```

```
root@bluebird:/etc/bind# dig ubuntuforums.org

; <<>> DiG 9.4.1-P1 <<>> ubuntuforums.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53926
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;ubuntuforums.org.              IN      A

;; ANSWER SECTION:
ubuntuforums.org.       588     IN      A       91.189.94.186

;; AUTHORITY SECTION:
ubuntuforums.org.       10144   IN      NS      ns2.mythic-beasts.com.
ubuntuforums.org.       10144   IN      NS      ns.ubuntu.com.
ubuntuforums.org.       10144   IN      NS      ns1.mythic-beasts.com.

;; ADDITIONAL SECTION:
ns2.mythic-beasts.com.  172140  IN      A       193.201.200.34
ns.ubuntu.com.          172140  IN      A       91.189.94.173
ns1.mythic-beasts.com.  172140  IN      A       69.56.173.190

;; Query time: 42 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Oct 14 23:27:01 2007
;; MSG SIZE  rcvd: 175


```

```
root@bluebird:/etc/bind# ping -c 1 mail.blue
PING mail.blue (192.168.1.101) 56(84) bytes of data.
64 bytes from bluebird.local (192.168.1.101): icmp_seq=1 ttl=64 time=0.025 ms

--- mail.blue ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.025/0.025/0.025/0.000 ms

```

There is more things to do like reverse dns (needed for example by mail server) and so on ...

---

### Post by drndrw on 2007-10-16
Ah, okay. Thanks! I will try that soon. But I have another problem. My BIND server isn't restarting properly. How can I?

EDIT: It says connection is denied on 127.0.0.1#953

---

