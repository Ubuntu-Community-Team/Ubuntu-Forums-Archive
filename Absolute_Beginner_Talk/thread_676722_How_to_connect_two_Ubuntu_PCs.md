---
title: "How to connect two Ubuntu PCs?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2008-01-24
Okay, so I've just gotten a new laptop and I want to transfer a heap of data from my old desktop to the new laptop. It's about 80GiB of data, so I'm not very keen on transferring via DVD or flash drive. I really want to do it via a network if that is possible, however I have no idea how to do it.

At the moment, I am connected to our router via wireless (from the laptop) and the desktop I'm trying to transfer the data from is connected to the same router via an Ethernet cable. Is there a simple way of doing this?

The laptop is running Gutsy 64bit and the desktop running Gutsy 32bit.

Thx in advance to anyone who can help.

EDIT: I can easily connect the laptop to the router via an Ethernet cable if that helps.

---

### Post by LaRoza on 2008-01-24
You can use SSH File Transfer Protocol and [http://en.wikipedia.org/wiki/SSH_file_transfer_protocol](http://en.wikipedia.org/wiki/SSH_file_transfer_protocol)

Setting up SSH is pretty easy, [https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

(Filezilla is good for this)

---

### Post by PeterJS on 2008-01-24
The ssh extensions for nautils are good for moving data once you have ssh working. Fire up nautils and in the address bar use:
```

ssh://user@ip

```
and drag and drop to your hearts content.

---

### Post by Rocket2DMn on 2008-01-24
You can also Share the folders you want to transfer, then access them from Places->Network and navigate to the computer with the share, then drag and drop the directories.  I would suggest wiring into the ethernet to massively increase the transfer rate.
To setup a simple share, just right click the folder to share and hit Share and type in your password (since this is an administrative task).  Select a UNIX (NFS) share since you're just using 2 Ubuntu computers.  Samba (SMB) is only needed to share with windows and can be more of a hassle to set up.

You can disable the shares when you're finished.

---

### Post by NovaAesa on 2008-01-24
thx LaRosa! I'll check that out and report back with the results.

---

### Post by LaRoza on 2008-01-24
> **NovaAesa said:**
> thx LaRosa! I'll check that out and report back with the results.

It should work fine. I have done it when I didn't understand what I was doing. 

(LaRoza, I am not Italian :))

---

### Post by LeAstrale on 2008-01-24
im not able to answer anything on networking linux machines.. 
however i know that you would prefer to transfer that amount of Data by CABLE because wireless just is too slow for those big transfers.

/Astral-1

---

### Post by hyper_ch on 2008-01-24
you could use SSHFS to locally mount the remote file system

---

### Post by Cadmus on 2008-01-24
> **astral-1 said:**
> im not able to answer anything on networking linux machines.. 
however i know that you would prefer to transfer that amount of Data by CABLE because wireless just is too slow for those big transfers.

/Astral-1

Agreed, can't beat copper, reliable and higher levels of Ubuntu compatibility than wireless.

---

### Post by LeAstrale on 2008-01-24
> **Cadmus said:**
> Agreed, can't beat copper, reliable and higher levels of Ubuntu compatibility than wireless.

you just gotta love Fiber then <3 even though it isn't very implemented yet.. and asadly enough its converted to cobber for the last link to personal use..

---

### Post by NovaAesa on 2008-01-24
Okay, I tried to access the files from the terminal but that didn't work:
> ps@inspiron:~$ ssh ps@192.168.2.4
ssh: connect to host 192.168.2.4 port 22: Connection timed out
ps@inspiron:~$ 


I also tried to type > ssh://ps@192.168.2.4 but it just said > Nautilus cannot display "ssh://ps@192.168.2.4". Please select another viewer and try again.

I also tried to share the folders I wanted to access, however when I went into Places -> Network, the only thing listed there was "Windows Network" which I assume is there because there are Windows computers also connected to the routher.

Anyone know what I should do?

@LaRoza sorry about the mispelling :)

---

### Post by hyper_ch on 2008-01-24
do you have the ssh server installed on the computer you want to connect to?

```

sudo apt-get install openssh-server

```

---

### Post by kinkyHelenMandarin on 2008-01-24
If u want to use ssh (or any other service (have a look at /etc/services)),
u need to set up a server to handle the connections on the port used by each service,
I think there's no ssh server up by default, but there is a sftp one,
u can use sftp through terminal, but u can also use it through konqueror -which might be quite handy if you want to transfer many files-.

if u have a firewall on, u might need to put it down temporarily (however, what u need is sftp's port -115- to be open)

---

### Post by NovaAesa on 2008-01-24
@hyper_ch: openssh-server is already installed.

@kinkyHelenMandarin: under /etc there was folder called ssh. Is this what you were refering to?

---

### Post by kinkyHelenMandarin on 2008-01-24
> **NovaAesa said:**
> @kinkyHelenMandarin: under /etc there was folder called ssh. Is this what you were refering to?

no, not the ssh folder, but the services file.
now that i think of it again if there is a problem with the server u'll see a "Connection refused" message, not a "Connection timed out" one. did you try to ping one machine from the other.

---

### Post by NovaAesa on 2008-01-24
How do you ping one computer from another (sorry, I'm really a n00b when it comes to networking)?

---

### Post by kinkyHelenMandarin on 2008-01-24
> **NovaAesa said:**
> How do you ping one computer from another (sorry, I'm really a n00b when it comes to networking)?

simply:
$ ping 192.168.2.4

to see the kind of output you should expect try
$ ping localhost
this one will ping yourself

---

### Post by NovaAesa on 2008-01-24
Okay, the pinging worked well. So what should I do with the services file in /etc ?

---

### Post by kinkyHelenMandarin on 2008-01-24
> **NovaAesa said:**
> Okay, the pinging worked well. So what should I do with the services file in /etc ?

nothing, the services file is just an interesting file which u'll find pretty handy if u get more into networking.
Firstly, is the ssh server up on the machine u ssh (i.e. the machine you're trying to have access to)?
This way or another i have never set up an ssh server, have u tried sftp (with the firewall down -if u have any-), u use it kind of the same way u use ssh and it's enough to transfer files -of course-.
try 
$ sftp 'username of the server account'@'the ip of the server'
(u're the host, u want to access the server)

---

### Post by hyper_ch on 2008-01-24
do you have firewall enabled on that other computer that blocks default port?

Did you alter the port of the ssh server on the other computer?

---

### Post by NovaAesa on 2008-01-25
Thanks for the help guys. I decided to just bite the bullet and use a 4GiB USB drive to trasfer the data. It seemed easier that way than to mess around with networking that I  was never going to have to do again. Plus I also kinda had a time limit (I had to give the hard drive in the desktop to someone else).

Thanks all who helped out!

---

### Post by spiderbatdad on 2008-01-25
I haven't tried yet, but I was wondering if I made a crossover cable could I just mount the file system of linux pc1 on linux pc2?

---

### Post by Rocket2DMn on 2008-01-26
A crossover cable should work, but I've never tried it in linux.  It would be much easier if you could wire both PCs into a router.  You can do an SSH mount from your desktop (so it's not mounted in your filesystem, but appears as a network folder on your desktop) - just make sure you have ssh installed and running on the remote computer.  Then go to Places->Connect to Server and put in the IP, select SSH and give a username and pw.  Once mounted, you can drag and drop.

---

### Post by hyper_ch on 2008-01-26
hmmm, on the machine where you want to connect to through ssh you must have the openssh server isntalled... I'd just check that again...

on that machine just do:

```

ssh user@localhost

```

---

### Post by kinkyHelenMandarin on 2008-02-04
> **spiderbatdad said:**
> I haven't tried yet, but I was wondering if I made a crossover cable could I just mount the file system of linux pc1 on linux pc2?

Yeah it works and it's very easy, what you can do is set manually your IP (the one you're using with Ethernet) on both PCs, and use on each PC the IP of the other as your Gateway.
You may have problems with firewalls.

---

