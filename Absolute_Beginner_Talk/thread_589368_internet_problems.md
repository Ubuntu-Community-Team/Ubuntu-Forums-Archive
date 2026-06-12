---
title: "internet problems"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by stfury on 2007-10-24
Hi there,

i just install ubuntu gutsy and im having problems with mozilla firefox and thunderbird.
my download and playing of games runs at full speed - perfectly, yet when i browse the internet it is really slow even slower than my 56k (i have DSL)  and also the same for downloading emails?

please will someone help I need this to work.

cheers stfury

---

### Post by Mischa on 2007-10-24
try this as root: (sudo su -)

vi /etc/sysctl.conf

add the following two lines

net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

sysctl -p

see [http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/") for an excellent explanation

---

### Post by stfury on 2007-10-24
hi i did that it did not work i typed in all those commands and then at the end once i have typed them in it doesnt even do anything pls help im so confused i am a linux nuub.

---

### Post by Mischa on 2007-10-24
did you try another browser, like Epiphany Web Browser? to see if it is related to mozilla software?

Applications>Add/Remove>Internet>Epiphany Web Browser

---

### Post by stfury on 2007-10-24
i did this. it is just as slow -----
the problems seems to be this on both browsers.

i got to google.co.za for example and it says loading google.co.za in the bottom bar, when it does this for about 30 secs and then it says transferring... and the webpage is seemingly loaded up in 2 secs, the usual time to go to google.

if i go to a bigger webpage the same 30sec waiting time before it loads the first bit of the webpage seems to happen then it loads normally.

please help

---

### Post by Mischa on 2007-10-24
it seems you have trouble with your dns resolving, what the contents of your /etc/resolve.conf file?

---

### Post by Mischa on 2007-10-24
try one of these dns servers in the /etc/resolve.conf file

[http://www.tech-faq.com/public-dns-servers.shtml](http://www.tech-faq.com/public-dns-servers.shtml)

---

### Post by realvz on 2007-10-24
try this
[www.opendns.com/start](www.opendns.com/start)

---

### Post by stfury on 2007-10-24
how do i get to that file im soz i have no idea how to acces it?

---

### Post by stfury on 2007-10-24
i found it it only has one line in it ------------

nameserver 10.0.0.2


this is the address of my telkom mega 100wr router

---

### Post by realvz on 2007-10-24
try this
[www.opendns.com/start](www.opendns.com/start)

---

### Post by stfury on 2007-10-24
just used those public dns servers it works a treat now thanks a mil guys

---

### Post by Mischa on 2007-10-24
your welcome, have fun with ubuntu and spread the word :)

---

### Post by stfury on 2007-10-24
ok its working now thanks alot guys

---

