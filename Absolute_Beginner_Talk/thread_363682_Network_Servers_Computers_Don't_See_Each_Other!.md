---
title: "Network Servers: Computers Don't See Each Other!"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by sirmrmatt on 2007-02-17
I have two Ubunty Edgy computers on the same router. When I go to "Network Servers" (which I assume is the same as "Network Neighborhood," I get nothing. Some little Samba things, but they never connect.

The computers don't see each other!

This is not like a Windows-Linux connetion. Linux-Linux ought to work out of the box, no?


- Matt

---

### Post by meng on 2007-02-17
Have you tried connecting by IP address?

---

### Post by paydaydaddy on 2007-02-17
That poses a good question for us noobs. How do you find the IP address on the linux machines? Using Dapper Drake.

---

### Post by meng on 2007-02-17
Easiest way:
drop to terminal and type
ifconfig

and look for the network interface in question (e.g. eth0, eth1, wlan0, ath0) and the entry 'inet addr'

---

### Post by sirmrmatt on 2007-02-17
> **meng said:**
> Have you tried connecting by IP address?

I have not tried, I will try to  connect via IP (which I assume means smb:///192.168.1.xxx , correct?)

However...the $63,000 question...why on EARTH don't these computers see each other out of the box?

This is a simple, expected function of home computers. I adopted Ubuntu on both of my comptuers, I love it, but why, oh why, is there no working, easy "Network Neighborhood" in edgy...BOTH installs?

I just do not understand this. 

I had a hard drive issue with one computer (drive was failing and needed to get data off quick), but I could not do this via a network transfer due to this issue. The drive has since been replaced and all is well, and the no-networking still stands.

I just want to be able to, for example, add a printer hooked to another computer in the house to the other one using a simple network printer utility. Ubuntu has that utility, it IS simple and nice looking, but the only problem is that it can't SEE it's bro on the network.

I don't get why this would be.

- Matt

---

### Post by rudlavibizon on 2007-02-19
I tried samba and had no success just like you and then i followed[ this ]("https://help.ubuntu.com/community/SettingUpNFSHowTo")how to. I just blindly copy pasted mostly without knowing actually what I was doing, but succeded in the end. This is a serious problem and ubuntu developers should look into it to see if they can make things easier for users while not compromising security. It really seems weird that i can see windows shared folders without typing any commands in the terminal and cannot do the same with ubuntu. I actually enjoy doing this stuff because i always learn something while doing it and it makes me feel smart ;) , but if someone is in a hurry and just wants to copy files from one computer to another, this can really put him off ubuntu and linux in general. 
I would also like to ask if someone can point me to a how-to or tutorial or even a book were all this networking stuff for linux is explained simply enough for a newbie to **understand** and not just to copy/paste to get things done.

PS. there is also another [how-to in this forum]("http://ubuntuforums.org/showthread.php?t=249889") you should check out

---

### Post by sirmrmatt on 2007-02-19
I remotely ran the procedure (through SSH) and now only have to get home later to turn on the other computer and test. I assume this procedure will be necessary for both computers.

However, this still BEGS the question: why is this so damned hard?

Simple home network file sharing is a huge deal for most people. My Dad does it on his little home Windows system, for transferring digicam pictures for backup, etc., this is not some pedantic, obscure function, and yet the procedure to get it (as in link above) is.

:confused: 

- Matt

---

### Post by dannyboy79 on 2007-02-19
> **sirmrmatt said:**
> I have not tried, I will try to  connect via IP (which I assume means smb:///192.168.1.xxx , correct?)

However...the $63,000 question...why on EARTH don't these computers see each other out of the box?

This is a simple, expected function of home computers. I adopted Ubuntu on both of my comptuers, I love it, but why, oh why, is there no working, easy "Network Neighborhood" in edgy...BOTH installs?

I just do not understand this. 

I had a hard drive issue with one computer (drive was failing and needed to get data off quick), but I could not do this via a network transfer due to this issue. The drive has since been replaced and all is well, and the no-networking still stands.

I just want to be able to, for example, add a printer hooked to another computer in the house to the other one using a simple network printer utility. Ubuntu has that utility, it IS simple and nice looking, but the only problem is that it can't SEE it's bro on the network.

I don't get why this would be.

- Matt


they don't see each other out of the box because for security reasons ubuntu never comes with ANY services enabled by default. Dapper is NOT a server out of the box which is what you need for them to comminicate. One has to be a server (listen for connections) and the other a client. (sends requests for connection) So needless to say you either need to setup NFS or SAMBA. NFS is best for linux to linux connections which you can follow this guide here: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html)

or if you want more complicated setup, you can try samba, the easiest guide is here, for linux to linux setup. [http://www.linuxjournal.com/article/1262](http://www.linuxjournal.com/article/1262)

the trick is that you only want to set 1 of the computers to be the server, so these settings here: 
domain master = yes
    os level=33
you want 1 machine to have "NO" and just delete the os level option. so it would be this for the other box:
domain master = no
#   os level=33

in mosty config files, a # means it's not used or even looked at by the service cause it's commented out. good luck, post back if you ened help. I have 2 ubuntu boxs talking to each other as well as a xbox, and a win xp pro box all within a samba network.

---

### Post by dannyboy79 on 2007-02-19
> **rudlavibizon said:**
> I tried samba and had no success just like you and then i followed[ this ]("https://help.ubuntu.com/community/SettingUpNFSHowTo")how to. I just blindly copy pasted mostly without knowing actually what I was doing, but succeded in the end. This is a serious problem and ubuntu developers should look into it to see if they can make things easier for users while not compromising security. It really seems weird that i can see windows shared folders without typing any commands in the terminal and cannot do the same with ubuntu. I actually enjoy doing this stuff because i always learn something while doing it and it makes me feel smart ;) , but if someone is in a hurry and just wants to copy files from one computer to another, this can really put him off ubuntu and linux in general. 
I would also like to ask if someone can point me to a how-to or tutorial or even a book were all this networking stuff for linux is explained simply enough for a newbie to **understand** and not just to copy/paste to get things done.

PS. there is also another [how-to in this forum]("http://ubuntuforums.org/showthread.php?t=249889") you should check out

well networking ISN'T just for linux. that's the beauty of it, networking can involve any and all os's. here is a book, networking for dummies, since you requested it that way. [http://www.amazon.co.uk/gp/reader/0764542605/ref=sib_fs_top/026-8514855-0746826?ie=UTF8&p=S00Y&checkSum=mAtnTU0pWLaGB0kBAhjvouJaoFhaM3eg1fi%2Fd%2FyuAkQ%3D#reader-link](http://www.amazon.co.uk/gp/reader/0764542605/ref=sib_fs_top/026-8514855-0746826?ie=UTF8&p=S00Y&checkSum=mAtnTU0pWLaGB0kBAhjvouJaoFhaM3eg1fi%2Fd%2FyuAkQ%3D#reader-link).

other wise, if you want a little more of a technical read and it's free, read the linux man pages. they come free with most all distro's. just do "man" and whatever command you're not sure about so in this case, you can do ```
man smb.conf 
``` or ```
man samba 
``` and read and learn all you want. also, samba wasn't designed for making linux communicate with linux, it was designed for linux to communicate with Windows Networks. NFS is the preferred method of networking for linux to linux although samba does work just fine.

---

### Post by meng on 2007-02-19
> **sirmrmatt said:**
> However, this still BEGS the question: why is this so damned hard?
It's a good question, and one could ask the same of Windows. Why has it always been so damned difficult for me to do home networking between Windows boxes? And as for my Windows box being able to see my Linux box, hell, I had to drop to the command line to set that up. Neither Linux nor Windows shines at out-of-the-box network setup.

(By the way, I found Linux-Linux home networking with samba to be very easy, in fact much easier than my Windows-Windows experience. I understand experiences vary from user to user.)

---

### Post by dvarsam on 2007-02-19
> **sirmrmatt said:**
> I have two Ubunty Edgy computers on the same router. When I go to "Network Servers" (which I assume is the same as "Network Neighborhood," I get nothing. Some little Samba things, but they never connect.

The computers don't see each other!

This is not like a Windows-Linux connetion. Linux-Linux ought to work out of the box, no?


The easiest thing is to connect Ubuntu <-> Ubuntu & Windows <-> Windows

For the 1rst case, you would first have to Set both of your PCs to use Static IPs.
Then install "openssh-server" package on both of your Ubuntu PCs.
You can connect using "Places\Connect to Server..." from your Menu.
Alternatively, you could use "Applications\Internet\Terminal Server Client" to do that.

For the 2nd case, you would again have to Set both of your PCs to use Static IPs.
Then launch "Start\All Programs\Accessories\Communications\Remote Desktop Connection".
You could also see [http://www.ubuntuforums.org/showthread.php?t=365246](http://www.ubuntuforums.org/showthread.php?t=365246)
Scroll down & it will help you to setup your Windows PCs.

Good Luck!

---

