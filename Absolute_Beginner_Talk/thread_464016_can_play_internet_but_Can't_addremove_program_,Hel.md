---
title: "can play internet but Can't add/remove program ,Help please"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by witoat on 2007-06-04
Hello ,there 

I have just finished installing Ubuntu ,I read that almost the software has to be update by using add/remove. I do it but It could't load anything and poped up a message like failed to download .I can play Internet but I cant add or download program from internet by using add/remove or synapticofin terminal . I have searched in google but I cant see anything that help me . Help me please , I really want to listen to songs .

---

### Post by viciouslime on 2007-06-04
> **witoat said:**
> Hello ,there 

I have just finished installing Ubuntu ,I read that almost the software has to be update by using add/remove. I do it but It count't load anything and poped up a message like failed to download .I can play Internet but I cant add or download program from internet by using add/remove or synapticofin terminal . I have searched in google but I cant see anything that help me . Help me please , I really want to listen to songs .

What is the exact error that comes up?

---

### Post by witoat on 2007-06-04
The error is like this .

---

### Post by rich.bradshaw on 2007-06-04
what happens if you type

sudo apt-get update

in a terminal?

---

### Post by witoat on 2007-06-04
Here it is :


E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


What does it means ? and what should I do?

---

### Post by witoat on 2007-06-04
and I am finding my way to prove it .I have changed the mirror and find suitable download server but It appears like this :

---

### Post by witoat on 2007-06-04
please help me , i really want to use ubuntu well.

---

### Post by fastpakr on 2007-06-04
Do you have add/remove and package manager open at the same time?

---

### Post by witoat on 2007-06-04
no,i dont know what package manager is

---

### Post by witoat on 2007-06-04
> **fastpakr said:**
> Do you have add/remove and package manager open at the same time?

I think I havent opened them at the same time.

---

### Post by Ink-Jet on 2007-06-04
Can you even open them at the same time?

---

### Post by witoat on 2007-06-05
> **fastpakr said:**
> Do you have add/remove and package manager open at the same time?

I 'm sorry,I dont know where package manager is ,please help me?

:(

---

### Post by Feba on 2007-06-05
it looks like it's a problem with one (or more) of your repos, not with synaptic. Have you tried using sudo apt-get install program, and seeing what the results are?

---

### Post by witoat on 2007-06-05
> **Feba said:**
> it looks like it's a problem with one (or more) of your repos, not with synaptic. Have you tried using sudo apt-get install program, and seeing what the results are?

the results are: 

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


what does it mean ? Help me please.

---

### Post by seshomaru samma on 2007-06-05
it means that another application is open at the same time (maybe synaptic or add/remove programmes)
try to reboot and run:
```
sudo apt-get update
```

---

### Post by witoat on 2007-06-05
> **seshomaru samma said:**
> it means that another application is open at the same time (maybe synaptic or add/remove programmes)
try to reboot and run:
```
sudo apt-get update
```

After I enter  sudo apt-get update in terminal ,Here is the result :

```
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Err http://mirror.nttu.edu.tw feisty Release.gpg                               .
  Could not connect to mirror.nttu.edu.tw:80 (210.240.172.138), connection timed out
28% [Connecting to mirror.nttu.edu.tw (210.240.172.138)] [Connecting to archive.ubuntu.com (91.189.89.6)]

```

what would I do ?

---

### Post by Rui Pais on 2007-06-05
hi,
do you mind to post the output of the following:
```
ping -c2 mirror.nttu.edu.tw
```
and 
```
ping -c2 210.240.172.138
```
please.

---

### Post by witoat on 2007-06-05
> **Rui Pais said:**
> hi,
do you mind to post the output of the following:
```
ping -c2 mirror.nttu.edu.tw
```
and 
```
ping -c2 210.240.172.138
```
please.

This is what I got from :```
ping -c2 mirror.nttu.edu.tw
```

PING mirror.nttu.edu.tw (210.240.172.138) 56(84) bytes of data.
64 bytes from mirror.nttu.edu.tw (210.240.172.138): icmp_seq=1 ttl=46 time=165 ms
64 bytes from mirror.nttu.edu.tw (210.240.172.138): icmp_seq=2 ttl=46 time=181 ms

--- mirror.nttu.edu.tw ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 165.498/173.431/181.365/7.944 ms



and this is what I got from ```
ping -c2 210.240.172.138
```

PING 210.240.172.138 (210.240.172.138) 56(84) bytes of data.
64 bytes from 210.240.172.138: icmp_seq=1 ttl=46 time=155 ms
64 bytes from 210.240.172.138: icmp_seq=2 ttl=46 time=172 ms

--- 210.240.172.138 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 155.557/164.154/172.751/8.597 ms


what should I do?

---

### Post by Rui Pais on 2007-06-05
uhmm... so you can ping the mirror.nttu.edu.tw and your network seems to be resolving ips correctly.
Thats strange that update fail. Server is up, i browse to it and didn't seems slow at all. 
And i'm in Portugal on the other side of the world, for you should even be faster...

btw can you navigate through [http://mirror.nttu.edu.tw](http://mirror.nttu.edu.tw) with your browser?

Try to launch synaptic and on main menu choose Configurations-> Repositories
and tray to choose other servers close to you (on a neighbor country) 
Then redo the update.

If it fail, post you /etc/apt/sources.list so we can check if something is wrong with it.

good luck.

---

### Post by witoat on 2007-06-13
Thanks for your advices ,I really want to use Ubuntu.I realized that I installed Ubuntu in my acer aspire 5580 ,it is not work for it(In my opinion). About my download , I use the internet through my university internet service which have a proxy .I dont know but what can I do?

---

### Post by Rui Pais on 2007-06-13
Hi,
don't know much about proxys, maybe that could make the problem...

Most cases of mysterious slowdowns while internet seems functional with a browser, boils down to 2 things, ipv6 and dns issues (i suspect more of the 1st).

For ipv6, edit /etc/modprobe.d/blacklist and add at end of file:
```
blacklist ipv6
```
you need to reboot your computer to test it's effects.
Check by doing:
```
lsmod |grep ipv6
```
should return an empty line. If so try to update again.

If that fails try use DNS from openDNS:
[here an how-to]("http://www.opendns.com/start/ubuntu.php").

good luck

---

### Post by batwings on 2007-12-19
hi all, 

i'm having the same issues,  i can get to the net thru a proxy server at my workplace, but can't do the add/remove thingy. 

it keeps saying "you need a working internet connection"

---

