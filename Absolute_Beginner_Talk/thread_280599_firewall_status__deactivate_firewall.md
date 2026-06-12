---
title: "firewall status ???? deactivate firewall ???"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-10-19
How to I check if my firewall is activated or deactivated? If it is activated how do I deactivate it??

The reason I want to do this is because I started nfs-kernel-server but on my client when I type in the mount command like this:

```
mount -t nfs 146.230.193.109:/nfsshare /mnt/nfs
```

I get the following error
mount: RPC: timed out

please note 146.230.193.109 is the ip address of my host and please note that my client is not a computer it is a biometric board that is used to detect a fingerprint that runs under linux OS 2.4.19 rmk7. Im using my computer at campus that is connected to out campus server however when I use the fingerprint board I disconnect the ethernet lan cable and replace it with my board's ethernet cable. The board is also connected to the PC via a RS232(serial) cable.

Also I cannot seem to find the following file:

```
bulletproof@Bulletproof:~$ cd /var/run
bulletproof@Bulletproof:/var/run$ ls -l portmap.state
ls: portmap.state: No such file or directory
bulletproof@Bulletproof:/var/run$ cd /
```

But I can 

```
bulletproof@Bulletproof:/$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    923  status
    100024    1   tcp    926  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32796  nlockmgr
    100021    3   udp  32796  nlockmgr
    100021    4   udp  32796  nlockmgr
    100021    1   tcp  33891  nlockmgr
    100021    3   tcp  33891  nlockmgr
    100021    4   tcp  33891  nlockmgr
    100005    1   udp    806  mountd
    100005    1   tcp    809  mountd
    100005    2   udp    806  mountd
    100005    2   tcp    809  mountd
    100005    3   udp    806  mountd
    100005    3   tcp    809  mountd



```

---

### Post by pay on 2006-10-19
In Ubuntu the ports that aren't used aren't open (to my understanding) but if you want a firewall there is firestarter and guarddog.

---

### Post by cinderella on 2006-10-19
> **pay said:**
> In Ubuntu the ports that aren't used aren't open (to my understanding) but if you want a firewall there is firestarter and guarddog.

Are u implying that my firewall is deactivated?????

i just would like to check if my firewall is activated or not because usually this becomes a problem when mounting on the client

pls let me know how to disable it if it is activated

---

### Post by ewl1217 on 2006-10-19
You posted this command:
```
mount -t nfs 146.230.193.109:/nfsshare /mnt/nfs
```I'm no expert on NFS, but it doesn't seem like the colon (":") should be there. Try this instead:
```
mount -t nfs 146.230.193.109/nfsshare /mnt/nfs
```

---

### Post by cinderella on 2006-10-19
> **ewl1217 said:**
> You posted this command:
```
mount -t nfs 146.230.193.109:/nfsshare /mnt/nfs
```I'm no expert on NFS, but it doesn't seem like the colon (":") should be there. Try this instead:
```
mount -t nfs 146.230.193.109/nfsshare /mnt/nfs
```

Nope that is the format of the mount command on the client. any other suggestions????

Does anyone have a step by step way of explaining how to check the status of firewall and if activated how do i go about activating it ????

](*,) :confused: :mad:

---

### Post by fordy on 2006-10-19
I am a nube myself (caution!) but on my Ubuntu I have to start the firewall explicitly (that is it is NOT started by default - unless you have set it to do that).  When the firewall is running, I get an icon in the notification area (top right).  So, its a fair bet that if you haven't started it, and there's no icon, then you have no firewall running.

However, if as a previous poster suggested, Ubuntu has ports closed by default then this could be your problem.  Also, when you have a colon in the IP adress it is usually followed by a port number and this could also be your problem (no port is specified).

Anything else you need to speak to someone who knows what they are talking about.  Yours, Prince C.

---

### Post by podunk on 2006-10-19
For the firewall:

Applications>System>Firestarter>deactivate button

---

### Post by randomi on 2006-10-19
Ubuntu comes standard with IPTables installed. Meaning that Ubuntu comes standard with a firewall. The easiest way to talk to IPTables is to install firestarter (there is another option but I can't remember the name of it). You can use the repos in install it for you.

Open a terminal and type in

```
sudo aptitude install firestarter
```

Once it's installed you can access it from Applications -> Internet -> Firestarter. From there you can disable the firewall or configure it to work with your needs.

---

