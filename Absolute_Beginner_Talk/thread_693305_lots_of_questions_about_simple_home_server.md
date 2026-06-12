---
title: "lots of questions about simple home server"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Mykle87 on 2008-02-10
I am going to be living off campus with a few guys next fall and I am planning on setting up a simple server. I am thinking I should go with ftp instead of samba because it is simple and cross-platform and I can set up all the computers (Mac, XP, Vista, Linux) with Filezilla. We are going to have a router. Here are my questions:

1. Is ftp too insecure? Should I go with SFTP? I don't want this server accessible from the internet. I only want it to be used behind the router.

2. Does this server need to have a static IP address? What about the other computers on the network?

3. How do you even set up a ftp server? I'm disappointed Filezilla doesn't have a linux server. I am very new to linux. I am planning on using 7.10 desktop edition.

I guess that is it for now. I'm sure I will have more questions as people reply to my post. I'm pretty sure this would be a whole lot easier with windows xp but I really want to give ubuntu a shot. I feel like this is a good opportunity to use it. Also, I'm thinking I'll install uShare to send movies to our xbox 360. Any feedback is appreciated. Thanks.

---

### Post by JoshuaRL on 2008-02-10
First off, Linux is THE OS for servers.  People have been running Linux in a server environment for decades without problems.  So as far as being easier in XP, I'm sorry but no.  That's why Microsoft has their own server version (Windows Server).

1).  FTP should be fine if you only want to use it behind the router.  Just make sure you have a firewall on the router and that you have a good strong password for it.  Most come with either "admin" or "password" as the default and any tunnelling worms check that first.

2).  Only if you want to serve files over the net to others.  If it's only going to be in-house, then no.  All the computers connected to the router will have their own IP sub-address.

3).  I can't speak with authority, but I believe this will help:  [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

You might also check out MythTV if you have a TV card, it is a program that has PVR and a Windows Media Center-esk interface (although they beat Microsoft to it by a couple years).

---

### Post by Mykle87 on 2008-02-10
That forum post is from 2005 and seems rather complicated. Is there anything a little more current? I have done some research and it seems proftpd is the way to go. I have heard of MythTV and that could definitely be a future project after I get this set up :) Also, I only said XP would be easier because I am familiar with Filezilla and it would be so easy to share media with the 360. I still definitely want Ubuntu Linux :)

---

### Post by JoshuaRL on 2008-02-10
I think that Filezilla works with Linux:

[http://filezilla-project.org/download.php?type=client](http://filezilla-project.org/download.php?type=client)

Is that needed to serve stuff to a 360?

---

### Post by x1a4 on 2008-02-10
Instead of FTP you might want to look at SSH.  Not only is it easy to use and a lot more secure than FTP, it's available for all major operating systems.  See [OpenSSH.org]("http://openssh.org/").  You can setup the OpenSSH server on Ubuntu, and use the clients to connect.

---

### Post by Dr Small on 2008-02-10
1.) FTP is insecure as it tunnels it's passwords through plain text.
2.) If you want people to be able to connect to you. then yes. It needs to be a static IP Address.
3.) Setting up a FTP server is simple, just run this command:
```
sudo apt-get proftpd gproftpd
```

Then just launch gProFTPd to configure it ;)

Dr Small

---

### Post by rkd on 2008-02-10
From your description, it isn't clear to me whether you want to access the server only from the house you will be living in, that is, only from the local LAN, or do you want to access the server from outside the house, too?

If you only want to access the server from inside the house, then if your router has a firewall built-in, as many of them do, that usually is enough protection from the outside world, and you would not have to be very concerned about security (unless you need security to protect the guys living there from each other).

If that is the situation, I think you would find it easier for people to use the server if you used Samba, because that will allow people to see the server on the network by name (they won't have to type in an IP address), and you could use DHCP to assign addresses to all the computers, including the server. Macs and Linux systems can access Samba shares, so it is cross-platform just as much as ftp is.

There might be some reason not to use Samba when you are only accessing the server from within the house, so I'm not saying that it is the only way to go, but perhaps you have dismissed it too quickly.

If you want to access the server from outside the house, then ftp, or one of its variants, probably is a better choice. Setting up for secure access from outside the house is a bit of effort, but once it is set up, it should work okay and be secure.

---

### Post by JoshuaRL on 2008-02-10
Guys, what about the Xbox 360?  He said he wants to serve videos to it.  I'm not sure, but I think that's why he wants to use FileZilla.  Any thoughts?

---

### Post by nalmeth on 2008-02-10
Is there any reason you don't want to use SAMBA?

It is also cross-platform, and will probably be easier to use for your roommates.
FTP will require them downloading all the files they're interested in, whereas with SAMBA they just browse to Network Places and they can browse the folder you have shared.

Anyway, with ftp you won't need a static IP, but its not a bad idea if people play around with the router. If you install OpenSSH, it will setup sftp, which is just ftp with some encryption AFAIK. For your purposes, if you have a firewall setup, and your router is not forwarding port 21 + 22 to the outside world, unencrypted ftp would probably be fine.

> Guys, what about the Xbox 360? He said he wants to serve videos to it. I'm not sure, but I think that's why he wants to use FileZilla. Any thoughts?He seems to have an idea in place for sharing with 360. Unfortunately I don't have any ideas of my own

---

### Post by rkd on 2008-02-11
I think the matter of using uShare to provide files to the Xbox 360 is completely independent of the file server. 

A very quick scan of the uShare web pages indicates that it is its own server, using uPNP to advertise itself on the network. My impression is that it can be installed alongside other kinds of server software on a box without interference, but I don't actually know anything about it, so I might be getting the wrong impression.

---

### Post by hyper_ch on 2008-02-11
what exactely do you want to achieve with the server?

---

### Post by kryth on 2008-02-11
I agree with Dr. Small. Proftpd is very easy to setup and use. Especially with Gproftpd.

---

### Post by Mykle87 on 2008-02-11
Well, what I have read about SAMBA says that it doesn't work with Vista and I assumed it didn't work with Mac. This is why I decided to go with FTP. I only want to use this file server on the network which from what I hear I don't have to do a lot of router set up which is great. Ok here is a little more info on how I am going to use this server.

I am going to set up a box with Ubuntu and take all our movies and rip them (using K9copy) to the hard drive for everyone to access them. Also, I hope to use uShare to allow the movies to show up on xbox 360. Oh and this server will be a backup server for my vista box so I will want to set up 2 user ftp groups. 1 for my housemates and 1 for me. Thanks for all the responses.

---

### Post by rkd on 2008-02-11
There is a very simple configuration setting change in Vista that will let it communicate with Samba, so that should not be a barrier to using Samba, if Samba otherwise would be a better choice for you than ftp. And Macs on recent versions of OS X can easily connect to Samba shares.

There is no doubt you could make either ftp or Samba work for what you want to do, and we can help you get either set up. I think your roommates would find it easier to use the server if it were Samba, but that depends a bit on how familiar they are with computers and networking -- if they are comfortable with ftp and IP addresses, then it might not be important that Samba would be a little easier for people with less experience.

You get to decide. I just don't want you to be jumping to a conclusion based on a misunderstanding about Samba.

---

### Post by Mykle87 on 2008-02-11
Thanks for the info rkd. I'm pretty sure I am going to have to set all the computers up so I will go with whatever one is easier. Can you set up different user groups with samba? Like have 1 samba share for my house mates and a separate one for me?

---

### Post by rkd on 2008-02-11
Yes, you can set up any number of user groups on Samba, each protected by passwords.

Do you know what router you will be using between your LAN and the internet? I think it is important that it have a decent built-in firewall, for your protection. If you know the make and model, I should be able to look up its capabilities on the web. If you haven't got the router yet, I could tell you some features you should make sure whatever you buy has.

---

### Post by Mykle87 on 2008-02-11
We are going to get fios so we will be using the router provided by verizon.

---

### Post by rkd on 2008-02-11
I found a few pages that say a little about the router that Verizon supplies with the FIOS service. Apparently the router they were using when they first started rolling out the FIOS service wasn't so hot, but the current one is pretty good. It sounds like it has a good firewall in it, which is what I was concerned about.

If, for some reason, it turns out that the router they include does not have an adequate firewall, that isn't a big problem. It is no trick to put another, more capable router between their router and your LAN. At least that is true for the wired ethernet LAN. I imagine it is possible to turn off the wireless part of their router so that any wireless connections also go through your router (so they are protected by the firewall in your router). Anyway, it probably won't be necessary to augment their router with one of your own, since it sounds like their router has all the security you need in its firewall. So I think you'll be fine with Verizon's router.

---

### Post by Mykle87 on 2008-02-11
Ok that's good to know. I'm sure it has some good settings like any router to lock down the wireless part and make it more secure.

---

### Post by Mykle87 on 2008-02-12
I wish I could start a poll in this thread for samba vs ftp. I like that GUI for proftpd. It looks really easy to set up. But samba seems really easy to set up and use also.

---

### Post by rkd on 2008-02-12
I don't think a poll in this thread would be very useful. What matters is what seems best to you and your roommates who have to use it. 

You'll be able to set up either Samba or ftp easily, so it is a toss-up there. 

The deciding question is which form of interface would you and your roommates prefer using when accessing the files day-to-day. Only you and your roommates can decide that.

---

### Post by Mykle87 on 2008-02-12
Yeah that makes sense rkd. I will have to ask them. I know I'll be setting the thing up. Question: If the IP of the ftp server js DHCP assigned on the network and it changes, will I have to repoint all the clients to it? Same question for Samba.

---

### Post by rkd on 2008-02-12
For Samba, the computers on the network don't need to be configured with the IP address of the server -- there is a broadcast protocol by which the address is made known to all the clients. That is one of the knocks against the Windows protocol in large networks with hundreds of computers, but it works very well in small networks.

I don't know of any similar way for ftp clients to avoid being affected by a new IP address for the server (though there might be one -- I'm no expert on ftp).  It isn't hard, though, to set up a static address for the server, even while using DHCP for all the other computers on the network.  You just have to make sure you pick an address for the server outside the range of the addresses that the DHCP server will hand out.

---

### Post by Mykle87 on 2008-02-13
Yeah I'm pretty sure I would be able to set up a static IP address for the server. I definitely want to make sure that it is simple for everyone since we are representing different operating systems. Luckily I have a lot of time to think about this. Thank you for all the advice.

---

### Post by rkd on 2008-02-13
Yes, it is good to have lots of time to plan.  Do you have a computer on which you could practice setting up Samba and ftp and get a feel for how it would be to access them from other computers? You wouldn't have to care much about how fast it is. Just something to experiment with the software setup.

---

### Post by Mykle87 on 2008-02-13
Not yet but hopefully soon. I'm definitely going to experiment. Also, I keep coming up with all these other ideas such as VNC as possibly SFTP and SSH over the internet. If I did all of that, it would require several different user groups. And also, it would serve as my main daily backup place.

---

### Post by rkd on 2008-02-13
Adding access to the server from outside your house into the picture immediately makes security a more difficult matter. Remember one of my first questions was whether you were thinking only of access from within the house? There was a reason I asked that.

It certainly is possible to do it, but not as easy. Just letting you know -- you are the one who will be doing the work, so it doesn't matter much to me whether it is easy or hard.

---

### Post by Mykle87 on 2008-02-13
Yeah accessing the server from the internet is just a thought. I'm not sure if it would be useful for me. Also, if it affects the security of the data being moved around within the network, then I will definitely not access it from the internet. To make it simple (since I still want other opinions), I will not access this server from the internet.

---

### Post by Mykle87 on 2008-03-07
I just thought of something. Does samba care what file format the share is? Like if I share an ext3 drive, would windows and mac be able to natively read and write the drive?

---

### Post by rkd on 2008-03-08
No worries there.  Samba can serve up files on any kind of filesystem.  The client computers see them all the same.

---

### Post by Mykle87 on 2008-03-09
I am very glad to hear that. I hate that fat32 is the only filesystem that is read/write natively on any OS.

---

### Post by Ecclesia on 2008-03-10
Mykle87, it occurs to me that what you're looking for may already be available in a really simple preconfigured format.  I'd check out freeNAS and see what you think: [www.freenas.org](www.freenas.org)

I tried it out a while back and it was very easy to configure.  Most of the work is already done for you, and it has mediatomb built in, which might work for your xbox (not positive about that, however).  You can set up ftp or samba quite easily through a web gui.  It's a little like configuring a router - quite slick.

I ended up going with debian however, (ubuntu would not work on the old machine I had kicking around) and making it accessible by VNC so that I could use it as a remote control jukebox for the stereo.  I would have installed mythtv, but I don't have a tv card kicking around and I'm skeptical about how well the old machine would work with it anyway.

If you'd like to do something like that, I've posted my solutions to setting VNC here:
[http://ubuntuforums.org/showthread.php?t=720403&highlight=vnc](http://ubuntuforums.org/showthread.php?t=720403&highlight=vnc)

---

### Post by Mykle87 on 2008-03-10
> **Ecclesia said:**
> Mykle87, it occurs to me that what you're looking for may already be available in a really simple preconfigured format.  I'd check out freeNAS and see what you think: [www.freenas.org](www.freenas.org)

I tried it out a while back and it was very easy to configure.  Most of the work is already done for you, and it has mediatomb built in, which might work for your xbox (not positive about that, however).  You can set up ftp or samba quite easily through a web gui.  It's a little like configuring a router - quite slick.

I ended up going with debian however, (ubuntu would not work on the old machine I had kicking around) and making it accessible by VNC so that I could use it as a remote control jukebox for the stereo.  I would have installed mythtv, but I don't have a tv card kicking around and I'm skeptical about how well the old machine would work with it anyway.

If you'd like to do something like that, I've posted my solutions to setting VNC here:
[http://ubuntuforums.org/showthread.php?t=720403&highlight=vnc](http://ubuntuforums.org/showthread.php?t=720403&highlight=vnc)

Thanks Ecclesia for the recommendation. I have looked into freenas and it looks great. However, I have been wanting to take the plunge into linux for a while now and I think Ubuntu may be the best option for me. I like the idea of having a full os to keep me off of my gaming rig.

---

### Post by Ecclesia on 2008-03-10
Gotcha,  figured that might be the case given your mention of copying movies directly to the box rather than transferring them from another machine.

Also, for what it's worth, I'd add myself to the list of people recommending Samba.

---

### Post by Mykle87 on 2008-03-10
Alright. Samba seems to be the overwhelming majority. I'm sure it will suite my needs just fine along with Ubuntu :)

---

