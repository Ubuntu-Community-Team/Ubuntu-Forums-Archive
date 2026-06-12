---
title: "How to connect two computers"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Bou on 2006-03-07
Hiya guys. For the first time in my life, I'm trying to connect two computers. I already bought the crossed cable and physically connected the two of them, but I don't know how to go past that.

I heard something about avahi, or zeroconf, but I don't really know how to use it or how to be able to access my shared folders any other way. Could anyone please give a hand?

Thanks a lot.

---

### Post by el3ktro on 2006-03-07
If both are Linux machines, then you probably want to look at NFS. NFS allows you to mount a directory from another computer on your local computer, so you can access the remote files as if they where on your local machine.

If you want to connect your Linux computer with a Windows machine, then you need Samba. Samba offers "Windows file sharing" so your Windows machine can access the files on your Linux machine and vice versa.

Which of the both do you need/want?

Tom

---

### Post by Bou on 2006-03-07
[QUOTE=el3kt]Which of the both do you need/want?[/QUOTE]

Both of my computers are running on Dapper, and I think I have NFS installed, since it's demanded the first time you share folders.

I wouldn't mind going over it, though.

Thanks.

---

### Post by el3ktro on 2006-03-07
Well first of all I wouldn't recommend at all for a newbie to run on Dapper - it's not even beta, so it's very likely that something will break sometimes!

Well when you have NFS installed already then it should already be started. To make sure, manually start the NFS daemons:

sudo /etc/init.d/nfs-user-server start

Then you have to edit the file /etc/exports, where you can specifiy which directories you want to export (=share) and which computers should have access to these directories.

The syntax is as follows:

shared_dir     computers_which_have_acces(options)

To share the directory "/home/joe" to all computers with read-write access you had to add the following line to /etc/exports:

/home/joe     *(rw)

Then reload NFS to make the changes effective:

sudo /etc/init.d/nfs-user-server reload

Now you can mount the above directory on another machine like this:

mount -t ntfs other_computer_ip:/home/joe /mnt/somewhere

I hope this helps!

Tom

---

### Post by Bou on 2006-03-07
Thanks Tom, I installed the NFS server as you said. I understand editing the /etc/exports can be done graphically through system/administration/shared folders?

Anyway, the thing is the computers don't seem to really connect. Whenever I try to do it through system/administration/network, I get the following dialog:

[IMG]http://img362.imageshack.us/img362/4444/sinnombre3hi.jpg[/IMG]

which remains for a loong while, then nothing happens. Is there any way to check if both computers are actually connected, regardless of having any shared folders?

Thanks.

---

### Post by LordBug on 2006-03-07
If it's sitting there for a long time, it's likely looking for a DHCP server.  This is something you won't have if you just hooking 2 PCs together with a crossover cable.  You'll need to manually configure IP address information into both computers.

Best way to see if the network is working is to check the output of "ifconfig".  If ETH0 has IP address information, you should be in business.

---

### Post by Bou on 2006-03-07
[QUOTE=LordBug]If it's sitting there for a long time, it's likely looking for a DHCP server.  This is something you won't have if you just hooking 2 PCs together with a crossover cable.  You'll need to manually configure IP address information into both computers.[/QUOTE]

OK I think I get it. I'm feeling like a real newbie by asking this, but... how do I get the IP address information?

You know, I've never had to do that. I always got internet out of the box, so I thought this would just work too.

---

### Post by LordBug on 2006-03-07
Well, you're basically free to set these up however you want honestly.

I would suggest something like this, for several reasons:

IP address, PC 1:  192.168.0.1
IP address, PC 2:  192.168.0.2
DNS, both PCs:  192.168.0.1  (this won't matter since they can't get out to the Internet anyway)
Gateway, both PCs:  192.168.0.1 (this also won't matter, for the same as above)

This will allow the 2 PCs to communicate with each other through the crossover cable, but not access the Internet through these cards.

---

### Post by Brunellus on 2006-03-07
obvious first thought:  are you using a regular ethernet cable, or a crossover cable? 

If you're using a regular cable, then you won't have a connection.  iF your'e directly connecting two hosts, you'll need a crossover cable, or run the connection through a switch.

---

### Post by Bou on 2006-03-07
Hm... I get the following feedback when introducing that data and trying to connect:

[[IMG]http://img51.imageshack.us/img51/5522/16fi1.th.jpg[/IMG]](http://img51.imageshack.us/my.php?image=16fi1.jpg)

[[IMG]http://img114.imageshack.us/img114/2367/22gb.jpg[/IMG]](http://imageshack.us)

I'm starting to think what I've been sold is NOT a crossed cable at all... :(

---

### Post by Brunellus on 2006-03-07
nope.  you were sold a regular cable.  Crossover cables, in practice, are quite rare, since almost everybody just connects to switches anyhow.  You should go and beat your hardware dealer with a stick.

---

### Post by Iowan on 2006-03-07
[http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp]("http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp") Here is a diagram.  With clip down, cable toward you, both connectors generally have white/orange, then orange/white wires.  A crossover will have green wires  on one connector.  You COULD convert one with a nice, sharp knife... but the results are kinda ugly...

---

### Post by dannyl on 2006-03-07
Excuse me for jumping in, but which files do I need to install for NFS? It doesn't appear to be on my system, as the nfs start command listed above returns a command not found error??

Thanks 
Dan

---

### Post by el3ktro on 2006-03-08
[QUOTE=dannyl]Excuse me for jumping in, but which files do I need to install for NFS? It doesn't appear to be on my system, as the nfs start command listed above returns a command not found error??

Thanks 
Dan[/QUOTE]

Quick answer:

sudo apt-get install nfs-user-server


Tom

---

### Post by Bou on 2006-03-08
Yep, they sold me a normal cable. Thanks guys, you saved me a lot of trouble.

I owe you :)

---

### Post by Bou on 2006-03-13
OK, I finally got a crossover cable. I'm getting some problems nevertheless:

NFS server is up & running.

> sudo /etc/init.d/nfs-user-server start
Password:
Starting NFS servers: nfsd mountd.

Both computers seem to be connected allright, ifconfig says so.

> eth0

Link encap:Ethernet  HWaddr 00:40:D0:7E:EA:07
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe7e:ea07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:344274 (336.2 KiB)  TX bytes:351691 (343.4 KiB)
          Interrupt:225

Yet, only folders shared through samba appear at my net servers, not NFS ones. Besides, samba folders are way too slow to browse (though I heard that's a common problem with Dapper) and ask for a password when I try to copy any file to the other computer.

Not having set any password myself, I'd rather this not happening since I don't know what the password is and can't get to copy a thing.

Thanks for your help guys.

---

### Post by patrick295767 on 2006-03-13
Hi, 

1/ First you should be able to ping your computers (both computer should and have to be able to ping each other):

> ifconfig
> ping IPaddress

2/To set up an NFS folder sharing between two linux boxes : 
[https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29)
[https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29)

Greetz

---

### Post by Bou on 2006-03-13
[QUOTE=patrick295767]Hi, 

1/ First you should be able to ping your computers (both computer should and have to be able to ping each other)[/QUOTE]

They are:

> ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=0.561 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=0.103 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=64 time=0.103 ms
64 bytes from 192.168.0.2: icmp_seq=4 ttl=64 time=0.101 ms

2/To set up an NFS folder sharing between two linux boxes : 
[https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29)
[https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29)

Greetz[/QUOTE]

I mess up in this part:

> david@Bou:~$ sudo make -C /var/yp
make: *** /var/yp: No existe el fichero o el directorio.  Alto.

Isn't the GUI upposed to handle this, anyway? or zeroconf? I really appreciate your help, but all this file editing just to share some files is a bit of a turndown... :(

---

