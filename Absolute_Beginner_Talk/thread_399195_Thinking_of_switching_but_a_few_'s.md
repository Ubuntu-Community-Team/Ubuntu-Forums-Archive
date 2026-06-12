---
title: "Thinking of switching but a few ?'s"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Psychotron on 2007-04-02
Hi all I just wanna say I have been test driving Ubuntu Server 6.06 LTS danner on a vmware in XP and I am loving it.  I have used gentoo stuff for servers for years now and emerge is getting on my nerves.  Here is what I want to do.  I have a win2k3 server setup at home to host apache2, mail, and files for my network.  I want to dump win2k3 and go to Ubuntu on it.  It has 2 HD's in it.  1st is split into 2 partitions, 1 about 8gig for windows, apache, mail, and the other for files.  The 2nd hd is just one partition for files.  My object is to put all the files from 1st hd/2nd partition on hd 2 and then install ubuntu onto the 1st hd.  Now on to the questions:

1.  Will I be able to mount the 2nd hd in ubuntu, copy the files to the 1st hd and then format the 2nd hd from ntfs to native linux and be good to go?  I could use samba then in ubuntu to access files from my main XP pc same as before. (I want to get rid of the ntfs in the linux box for simplicity sake)

2.  Will I have to worry about a major update every 6 months when a new server release comes out?

3.  Can I remote desktop into ubuntu from my XP machine?  I can ssh to it no prob and be fine but just curious. (Ah just saw I could use VNC)

4.  Should I wait until Ubuntu matures more before I think about switching or is it stable enough now?  I will eventually switch my gentoo servers to Ubuntu also since apt-get is sooooo much nicer than emerge imo. (I just did a total system update on one of my gentoo servers and it was a nightmare, spent 2 days fixing stuff it broke.)

5.  Am I just being stupid for asking all these questions?  :lolflag: 

Thanks go to the Ubuntu Community for such a nice OS.  \\:D/

---

### Post by ardchoille42 on 2007-04-02
> **Psychotron said:**
> Hi all I just wanna say I have been test driving Ubuntu Server 6.06.1 TLS danner on a vmware in XP and I am loving it.  I have used gentoo stuff for servers for years now and emerge is getting on my nerves.  Here is what I want to do.  I have a win2k3 server setup at home to host apache2, mail, and files for my network.  I want to dump win2k3 and go to Ubuntu on it.  It has 2 HD's in it.  1st is split into 2 partitions, 1 about 8gig for windows, apache, mail, and the other for files.  The 2nd hd is just one partition for files.  My object is to put all the files from 1st hd/2nd partition on hd 2 and then install ubuntu onto the 1st hd.  Now on to the questions:

1.  Will I be able to mount the 2nd hd in ubuntu, copy the files to the 1st hd and then format the 2nd hd from ntfs to native linux and be good to go?  I could use samba then in ubuntu to access files from my main XP pc same as before.

2.  Will I have to worry about a major update every 6 months when a new server release comes out?

3.  Can I remote desktop into ubuntu from my XP machine?  I can ssh to it no prob and be fine but just curious.

4.  Should I wait until Ubuntu matures more before I think about switching or is it stable enough now?  I will eventually switch my gentoo servers to Ubuntu also since apt-get is sooooo much nicer than emerge imo. (I just did a total system update on one of my gentoo servers and it was a nightmare, spent 2 days fixing stuff it broke.)

5.  Am I just being stupid for asking all these questions?  :lolflag: 

Thanks go to the Ubuntu Community for such a nice OS.  \\:D/

2. Dapper, which is what you have, is supported for 3 years on the desktop and 5 years on the server.. so you only have to install a new Ubuntu if you feel like it during that time. I run Dapper on 11 machines and won't upgrade until Feisty is released, though I would be perfectly happy using Dapper for 3 years due to it being a solid and problem-free release.

3. I have a friend who uses ssh to maintain her Ubuntu machine from Windows and she has had no problems doing so.

4. I have an 8 year old niece who uses Ubuntu 6.06.1 LTS on a daily basis. She can install it and maintain it all be herself. She stopped using Windows about 6 months ago and loves Ubuntu. She has to ask some questions when compiling software but I think that would be normal for an 8 year old girl. other than that, she runs it entirely on her own. If that's not user-friendly and easy for newbies, I don't know what is.

5. It's never stupid to ask questions, that's how we learn things. And these forums are the best in the Linux community, IMHO.

---

### Post by Psychotron on 2007-04-02
Thanks for the comments.  I use ssh to manage my gentoo servers so I am used to it also.  I am still wondering if question #1 makes sense and is very doable.  I am guessing so.

---

### Post by mrreality13 on 2007-04-02
Ubuntu 6.06 LTS - Supported to 2011 for server edition

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by rabid9797 on 2007-04-02
for question #1:

you should have no problem copying files into ubuntu on the first hd(after install) straight off a clean install with no tweaking at all, as long as you don't need to write to a nfts disk, just read(to copy files)
formatting hd 2 after everything is copied is relativley easy, no harder than it would be to do in windows, and then from their its just a simple matter of copying the files back over to hd 2(ext3, which is the native format for ubuntu, is very stable and has no problems with copying large amount of files/files that are large sizes)

---

### Post by Psychotron on 2007-04-02
yeh I understand it is supported for 5 years and thats is what I am test driving.  I want to now if I will go wacky trying to upgrade it every 6 months when a new version rolls out or is it a simple Update Manager/Aptitude run?

Thanks rabid9797 thats what I needed to know.  I assumed it was possible just wanted to make sure.  I knew about the "don't write to ntfs drive" thing is why I want to change it.  I see you like House.  One of the best shows out there imo.

---

### Post by ardchoille42 on 2007-04-02
> **Psychotron said:**
> yeh I understand it is supported for 5 years and thats is what I am test driving.  I want to now if I will go wacky trying to upgrade it every 6 months when a new version rolls out or is it a simple Update Manager run?

Thanks rabid9797 thats what I needed to know.  I assumed it was possible just wanted to make sure.  I knew about the "don't write to ntfs drive" thing is why I want to change it.  I see you like House.  One of the best shows out there imo.

The server is supported for 5 years. Just curious, why would you upgrade a server in that time? All you really need is bugfixes and security updates and those are easily installed with a single command:

```

sudo apt-get upgrade

```

If you're talking about upgrading to the newest version of Ubuntu every 6 months, that's not really needed on a server.. and probably discouraged.

---

### Post by rabid9797 on 2007-04-02
<3 house :) 

depending on what you do with ubuntu will determine how easy of an upgrade you have .

if you do alot of custom programs, stuff not in the repos, or alot of tweaking, than you could run into trouble when upgrading from one version to another. but, if you stay within the repos(samba is in the repos, of course) and stay to light configuration, you really should have no problem upgrading from server to server.
i'd just make sure you wait till the final release of a new version comes out, and not jump on the beta, just to be on the safe side. in fact, it might be better to wait a week or two, let the final final bugs and updates get into a new verison, and then do an upgrade.

the actual proccess of upgrading is incredibley easy btw. its just a matter of editing your source list(im just including this info if in some case you dont' know) and replace the old repos with the new repos and do a simple 
sudo apt-get dist-upgrade

and that's it. apt-get downloads, replaces, and configures everything for you(including updating programs in the repos to be compatible with the new version) automatically.
its usually a 30 min- 1 hour and 30 min proccess, including downloading and installing, but it's pretty easy

---

### Post by Psychotron on 2007-04-02
Gotcha, thats the main reason I hadn't updated my gentoo kernel or system until now.  I was fixing an email problem I had and had to install a new dependency which would not work on the kernel, gcc, glibc versions I had.  had to do a major update on the box.  Thats why I was asking.  I like to be able to get it working and forget it.  :)

---

### Post by ardchoille42 on 2007-04-02
Well, rabid9797 does have a good point, upgrading is really easy if you decide to upgrade every 6 months.

---

### Post by justin whitaker on 2007-04-02
> **Psychotron said:**
> yeh I understand it is supported for 5 years and thats is what I am test driving.  I want to now if I will go wacky trying to upgrade it every 6 months when a new version rolls out or is it a simple Update Manager/Aptitude run?

You do not have to upgrade. At some point, the bleeding edge releases like Edgy get replaced with the next Generation....but you can keep on using the LTS version without bothering. 

Edgy, Fiesty, and any other non-LTS release are just for folks that want to use them, and do not mind dealing with some bugs and quirks along the way. 

BTW, you can dist upgrade or use aptitude to upgrade....pretty simple, but it may break things, so do not do that on a production server. :)

---

### Post by rabid9797 on 2007-04-02
> **ardchoille42 said:**
> Well, rabid9797 does have a good point, upgrading is really easy if you decide to upgrade every 6 months.

but you have a good point too. a server distro is supposed to be just that, just a server. if you were using it as a desktop, you'd just do a desktop install plus LAMP, and then it would be useful to do an upgrade everytime a new version came out(since its used much more)

but a server is just supposed to run, be stable, be safe, and work correctly. not really point in updating a stable,working, server every 6 months if your just using it for file trafficking on your network.

---

