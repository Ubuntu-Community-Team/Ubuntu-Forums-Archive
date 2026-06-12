---
title: "Home Network"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2007-08-15
I never set up a network before, and I was wondering if there was a HOWTO set up a home network? I have 4 computers here at home and would like to link them all together.

---

### Post by Malice007 on 2007-08-15
Oh and yes they are all either Kubuntu or Ubuntu.

---

### Post by callan79 on 2007-08-15
> **Malice007 said:**
> I never set up a network before, and I was wondering if there was a HOWTO set up a home network? I have 4 computers here at home and would like to link them all together.

Howdy,

Not sure if there's a single HOWTO as such, but basically you need :

 - 4 computers
 - a network switch (sometimes called a hub, but a switch is faster)

Then you assign each computer an IP Address under system >> administration >> networking. Give each machine 192.168.1.x, where x is 11 for the first machine, 12 for the second, 13 for the third, 14 fir the fourth. Set subnet mask on all computers to 255.255.255.0.

Once done, from TERMINAL on each machine, you should be able to type :

```
ping 192.168.1.x
``` and get a reponse from other machines on your network.

Once the network itself is working, you can then look for HOWTOs for things like Samba (file sharing) etc.

Good luck :)

Cheers
Callan

---

### Post by quinnten83 on 2007-08-15
> **callan79 said:**
> Howdy,

Not sure if there's a single HOWTO as such, but basically you need :

 - 4 computers
 - a network switch (sometimes called a hub, but a switch is faster)

Then you assign each computer an IP Address under system >> administration >> networking. Give each machine 192.168.1.x, where x is 11 for the first machine, 12 for the second, 13 for the third, 14 fir the fourth. Set subnet mask on all computers to 255.255.255.0.

Once done, from TERMINAL on each machine, you should be able to type :

```
ping 192.168.1.x
``` and get a reponse from other machines on your network.

Once the network itself is working, you can then look for HOWTOs for things like Samba (file sharing) etc.

Good luck :)

Cheers
Callan

is automatic ip assignment not an option?
My router just assigns the same IP to a single MAC address.
once you install NFS and or Samba you should be able to see all the other PC's in the homenetwork.

---

### Post by ukripper on 2007-08-15
Use router with inbuilt switch( probably you already have which you use to connect broadband). Nowadays routers supplied by broadband providers are capable of networking having few additonal ports behind them. So if you have straight cables lying around just plug into the router ports and other end to all machines and later configure samba to allow machines talk to each other.

If you have wireless router and machines with wireless card you don't need to worry about getting more cables at all.

---

### Post by callan79 on 2007-08-16
> **quinnten83 said:**
> is automatic ip assignment not an option?
My router just assigns the same IP to a single MAC address.
once you install NFS and or Samba you should be able to see all the other PC's in the homenetwork.

Sure, if your router already handles the IP Addressing etc then great, provided each computer gets the same IP every time, that's kind of important.

When this is done, I guess the next step depends on your definition of 'see' other computers. Sure, you might be able to talk to SAMBA/NFS, but you might find the machines don't just appear in Places >> Network (or in Windows, My Network Places).

Hope this helps, and you might also find some more useful info here :

[http://ubuntuforums.org/showthread.php?t=521173](http://ubuntuforums.org/showthread.php?t=521173)
[http://ubuntuforums.org/showthread.php?t=526896](http://ubuntuforums.org/showthread.php?t=526896)

---

### Post by notwen on 2007-08-16
> **Malice007 said:**
> I never set up a network before, and I was wondering if there was a HOWTO set up a home network? I have 4 computers here at home and would like to link them all together.

Define link them all together, are you wanting basic file sharing over the network?  IS so this is very easily done using NFS, especially since you're running *ubuntu variants only.  Check out this [page]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server").  I would recommend creating a shared folder on each computer and then simply mount each shared folder from the other computers.

Computer1 :mounts Share2, Share3, Share4
Computer 2:mounts Share1, Share3, Share4
Computer 3:mounts Share1, Share2, Share4
Computer 4:mounts Share1, Share2, Share3

You could also have them auto-mounted each time by modifying and adding them into each PC's /etc/fstab.  I use NFS myself for keeping all my files on  File server and I generally save all my file son the server leaving my other PCs and laptops fairly clean.  You can also stream mp3s over the network from Computer 3 on Computer 1 w/o having to copy the music onto each networked Computer. =]  Hope this helps.

---EDIT---

Using this method it would be very wise to have your router assign each PC's mac address a specified ip, since NFS uses ips to specify a machine and it's shared folders. =]

---

### Post by xpod on 2007-08-16
Not sure if there s a proper router involved here but this is what i do without one...

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

EDIT:nfs for file sharing of course:)

---

### Post by Malice007 on 2007-08-17
Thank you for all of your input.

---

