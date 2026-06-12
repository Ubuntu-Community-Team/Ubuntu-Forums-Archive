---
title: "lost internet"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by leedsdevil on 2007-09-01
ok ive tried searching the forums to try to fix my lost internet no luck. ok i have a wired net work seems like every thing is working and says that it connected but cant open firefox . the wife is mad so i like to fix it fast please help

---

### Post by Kosimo on 2007-09-01
If you can give more information we can may help you. 
What do you mean about it can't open Fireofx?  Firefox doesn't appear at all? Webpages are not  showing?  Did you configure your IP manually? Do you have a DHCP server ?

---

### Post by leedsdevil on 2007-09-01
ok it said it cant find server so no pages are showing up did i try to do anything no i m not sure what happened

---

### Post by Kosimo on 2007-09-01
Is a fresh install?
Do you have some switch connected on that computer?
How many network cards do you have installed on that computer?
How are you connecting to internet?

---

### Post by Lucifiel on 2007-09-01
What network card(NIC) do you use?

Do you use a router?

And also, do you use a static ip? If you disable the static ip, does the internet work?

Also, can you check if the wires are connected properly? It might be that the wire is out. :p

---

### Post by leedsdevil on 2007-09-01
no its not a fresh install yes i have it hooked up to my switch provided by ips (mi424wr) and just the one nick card

---

### Post by leedsdevil on 2007-09-01
i just checked the connection its still in and how do i change to static ip address?

---

### Post by leedsdevil on 2007-09-01
ok after diggin around i find i do not have an Ip address some how i lost it now how would i get this back easy please im not good at this yes i have now checked all the cables and card i know that somehow i lost my ip address thx

---

### Post by Lucifiel on 2007-09-01
Do you know how to access your router page?

Usually, the address for your router page is something like: 192.168.254.xxx 
And you will need to check your port forwarding page to see that for which IP the ports are being opened. 

Sorry for my English: I just woke up.

---

### Post by leedsdevil on 2007-09-01
no i dont know how to find my converter i checked connection information and it has all 0s on itlol its makes me want to cry

---

### Post by Lucifiel on 2007-09-01
> **leedsdevil said:**
> no i dont know how to find my converter i checked connection information and it has all 0s on itlol its makes me want to cry

Okay, I'm looking at the manual for your router now. The address to access your router page should be: 192.168.1.1

Try these instructions, though from the manual. Perhaps you can try and skip Step One. Edit: These instructions are for setting a dynamic IP. If you're not sharing internet with another computer, then you will not need a static ip. 

Linux
1. Login into the system as a super-user, by entering &#8220;su&#8221; at the prompt.
2. Type &#8220;ifconfig&#8221; to display the network devices and allocated IPs.
3. Type &#8220;pump -i <dev>,&#8221; where <dev> is the network device name.
4. Type &#8220;ifconfig&#8221; again to view the newly allocated IP address.
5. Make sure no firewall is active on device <dev>.



You really should download the manual from here so that you can refer to it:
[http://www.askios.net/article-37.html](http://www.askios.net/article-37.html)

---

### Post by leedsdevil on 2007-09-01
Okay, I'm looking at the manual for your router now. The address to access your router page should be: 192.168.1.1
 that is correct i found it some where else  ok but when you say promt where or what prop are you refferning to?
thanks alot for your help

---

### Post by Lucifiel on 2007-09-01
> **leedsdevil said:**
> Okay, I'm looking at the manual for your router now. The address to access your router page should be: 192.168.1.1
 that is correct i found it some where else  ok but when you say promt where or what prop are you refferning to?
thanks alot for your help

Oh, I'm sorry. "Prompt" refers to Terminal.

You should be able to find it by going to "Accessories" and then "Terminal".

---

### Post by southernman on 2007-09-01
Just to add to lucifiel suggestion. Unless you changed the username and password on the router it will be "admin" for both.

After you get this fixed, you should change the password at the least... and don't forget it or else you'll have to reset the router and start all over. *fun* ;)

good luck... we don't want you getting a lumpy head! :o

---

### Post by leedsdevil on 2007-09-01
ok i got to pump i not sure what you had meant can you give me a better way or explain?

---

### Post by Lucifiel on 2007-09-01
> **leedsdevil said:**
> ok i got to pump i not sure what you had meant can you give me a better way or explain?

Oh, okay... the <dev> part should be something like: > pump -i eth0. It really depends on what you get after typing > ifconfig

For me, my ifconfig output is something like this:
> XXX@XXXXXXX:~$ ifconfig
eth0      
Link encap:Ethernet  HWaddr 00:19:DB:AA:BD:7B  
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:717049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:958364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:234179263 (223.3 MiB)  TX bytes:520225726 (496.1 MiB)
          Interrupt:17 Base address:0x6000 

lo       
 Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15556 (15.1 KiB)  TX bytes:15556 (15.1 KiB)


---

### Post by leedsdevil on 2007-09-01
ok i have something different that what you have linked i also have it reads like this eth1:avah . i also tried to  sign is as a super user will not let me and for the pump command its not found this really bites

---

### Post by Lucifiel on 2007-09-01
> **leedsdevil said:**
> ok i have something different that what you have linked i also have it reads like this eth1:avah . i also tried to  sign is as a super user will not let me and for the pump command its not found this really bites

Because:

Super user aka Admin is disabled by default on Ubuntu, I think. 

Also, try using > dhclient and see if that command works in place of "pump". 

Like > dhcpd -i eth1

---

### Post by leedsdevil on 2007-09-01
oh yeah that worked now where to?

---

### Post by Lucifiel on 2007-09-01
> **leedsdevil said:**
> oh yeah that worked now where to?

Now try typing this again: :P  
Hopefully, you now have a new dynamic IP. :) 

> ifconfig

---

### Post by leedsdevil on 2007-09-01
ACK no good not working
maybe ill reinstall Ubuntu and set it up different

---

### Post by Lucifiel on 2007-09-01
> **leedsdevil said:**
> ACK no good not working
maybe ill reinstall Ubuntu and set it up different

Huh?

Why'd you need to reinstall everything? Hmm... have you tried reinstalling Firefox?

---

### Post by leedsdevil on 2007-09-01
no i havent tried to reinstall firefox how would i be able to do that?
this is one of my first Ubuntu pcs and i didnt set a swap file or partion the drive let every one said to  i know i hate that ideal  Thank you for contuining help

---

### Post by Lucifiel on 2007-09-01
> **leedsdevil said:**
> no i havent tried to reinstall firefox how would i be able to do that?
this is one of my first Ubuntu pcs and i didnt set a swap file or partion the drive let every one said to  i know i hate that ideal  Thank you for contuining help

Huh? You need to have a swap partition in order for things to work... it might be why Linux isn't functioning properly. It should be 1x to 2x the size of your system memory. 

Anyways, open up Terminal ("Accessories---> Terminal).

And then, in Terminal, type this:

> sudo aptitude reinstall firefox

---

### Post by leedsdevil on 2007-09-01
ok im reinstalling firefox . maybe you are rite ive been having a small issue of linux locking up now could i do that (repartion) on this hard drive that already has every thing on it by using gpartioner?

---

### Post by leedsdevil on 2007-09-01
and that reinstall didnt do the trick

---

### Post by Lucifiel on 2007-09-01
> **leedsdevil said:**
> ok im reinstalling firefox . maybe you are rite ive been having a small issue of linux locking up now could i do that (repartion) on this hard drive that already has every thing on it by using gpartioner?

Uhhh... you mean, Ubuntu is all on big partition? Holy crud... and there isn't a separate "home" partition? Errr... ^^;;

I think I'd reinstall Ubuntu then. But before that, did you burn the Ubuntu cd properly? It should be burnt at the lowest speed your cdwriter supports so that the installation works properly.

Btw, you should have 3 partitions:
> 
"linux-swap" = 1x to 2x the size of your system memory.
"/" = "root" partition. This is something like the System/System32/Windows directory. 
Should be around 5gb to 8gb huge. 
"/home": Should be around 10gb huge. This is where all your personal data is stored like your Firefox profiles, what you download, etc. It's something like "Document and Settings" in Windows. 

If you only have 1 partition, I suggest that you backup all the folders and files in your "/home" directory. Just use Nautilus(the default file manager) and browse to "/home" and burn the folders. That way, you'll get to keep your Firefox bookmarks, your cd burner settings.

---

### Post by leedsdevil on 2007-09-01
Ok thanks for the help and suggestions . im still the newbie on this Ubuntu.And i had read the forums alot and have learned alo by my post and you just confirmed all that ive learned on this site. As far as my cd it is a good one. I just cant belive that Ubuntu was working well on this machine till i lost my internet ACk well time to learn how to repartion in linuxand gpartioner OK all thanks for all the effort    Leeds

---

### Post by Lucifiel on 2007-09-01
> **leedsdevil said:**
> Ok thanks for the help and suggestions . im still the newbie on this Ubuntu.And i had read the forums alot and have learned alo by my post and you just confirmed all that ive learned on this site. As far as my cd it is a good one. I just cant belive that Ubuntu was working well on this machine till i lost my internet ACk well time to learn how to repartion in linuxand gpartioner OK all thanks for all the effort    Leeds

Oh and I forgot to mention this: 

> your Swap partition should be of "linux-swap" format. Your "/" and "/home" partitions should be ext3 format.

No problem. :) May you get Linux working. :)

---

### Post by frrobert on 2007-09-01
Did you check your DNS setting? I use a static ip address and for some reason Ubuntu 7.04 loses the DNS setting about every other boot.  Go to administration and networking and make sure the DNS entry is correct.

---

### Post by leedsdevil on 2007-09-01
i have look at the DNS but yet i dont know what to put in and where

---

