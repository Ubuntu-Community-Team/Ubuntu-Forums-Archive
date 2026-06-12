---
title: "Windows / Ubuntu networking"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Stewart MacPherson on 2007-02-26
First, I am completely new to Linux.

I have Ubuntu v6.06 installed dual boot on a PC

My network comprises four Win98 PCs, one Win95 PC, two WinXP laptops, all networked using Windows peer-to-peer networking. TCP/IP with static IP addresses.

All the PCs and laptops have their drives partitioned into several logical drives.

The PC running Ubuntu (one of the above) has four logical drives (partitions) under Win98 plus the Ubuntu environment.

I can access all the PCs (and all their partitions) from the Ubuntu OS including all the Win98 partitions on the PC with Ubuntu.

I can print to printers attached to the Ubuntu PC and the Win98 PCs from Ubuntu satisfactorily. (I have three printers, each attached to a Win98 PC with one of these the Ubuntu dual-boot PC)

I cannot see or access the Ubuntu PC (the Ubuntu partitions nor the Win98 partitions) from any of the Windows PCs.

I can ping all the PCs from all the other PCs.

Can anyone tell me (in words of one syllable or less) how I can see the Ubuntu partitions and the Win98 partitions on the machine running Ubuntu from the Windows PCs.

Obviously I can see the Win98 partitions on this PC when I have booted it to Win98.

Thanks

Mac from the Mountains

---

### Post by nereid on 2007-02-26
Did you share a folder from your Ubuntu PC? Sorry, but I can't help you very much here because I haven't played very much with Samba (which is responsible for your problem ;) ).

---

### Post by WakkiTabakki on 2007-02-26
Well, first things first. Having many partition on a single drive doesn't really have anything to do with networking, nor does dual-booting. Meaning, if you have a win98-partition on a Ubuntu-PC it won't show up on the network as a "shared win98-partition" or anything... You could mount it as a vfat-patition and then share it over using smb-protocol, but it would show up on the network just as any other share...
The local hardware/partitioning/dual-booting setup and the network one should really be seen as two different things..

And then a few questions...
1. Since you can see the winPC:s from Ubuntu, I take it you have the samba client installed, yes?
2. Since you can't see the Ubuntu PC from any where, I'm guessing you don't have samba server installed, but if you do, how are you sharing stuff from the Ubuntu PC?


/N

---

### Post by Stewart MacPherson on 2007-02-26
WakkiTabakki, Nereid

Thanks for the response.

I understand your comment about the connection (or lack of) between partitioning, dual-boot and networking.

The information was background to explain what I wanted to get out of the network 
I.e. all files on all machines under all OS to be accessible from all machines. (excluding Ubuntu system files of course)

I do have all the Win98 drives on the Ubuntu PC mounted. They are read/write to all users
I do not know if this constitutes "sharing" in a Ubuntu sense.

I am not sure whether I have the Samba client installed or not.
I just did a basic Ubuntu install from the CD.
How can I check? and if not how do I install?
Also I am not sure about the Samba server either but I suspect not.
Same questions. How check? How install?

I warned you I was new to this.

""how are you sharing stuff from the Ubuntu PC?""

Can you explain this question further please.

This same question goes to you, Nereid, since I don't know the Linux environment I am not sure how to answer.
:confused: 
Mac

---

### Post by nereid on 2007-02-26
Samba should be installed by default. If not a *sudo aptitude install samba* should do the trick (but it seems to be installed, if it was not you couldn't see the Windows systems from Ubuntu).

You share your folders as you do in Windows. If you want other users to access a folder on your Windows PC you share it with them (right click->Properties->Sharing or something like that under Windows). This allows the other users to access it (you can define if the access is read only or read/write). It is the same with Linux (as the Samba program tries to emulate the Windows way). To enabled access over the network to one of your folders you need to share it. I'm not really sure how you do it in Ubuntu but I assume you can also right click on the target folder and get this way to the sharing options for this folder.

---

### Post by rggavubt on 2007-02-26
I have the same question.  I am on my windows pc right now and when I try to access my Ubuntu PC upstairs, it is asking for a userID and password.  I tried my Ubuntu ID and password and that didn't work??

---

### Post by Stewart MacPherson on 2007-02-26
Hi Nereid

Thanks for the info.

I now see what is meant in Ubuntu and how to do it (the mechanical side)

When I try, I get a message saying I need to install Samba (presumably part is not installed) and then get errors when I try to install so I obviously need Internet connection when I try to do the install.
(Normally my  Ubuntu PC is not connected to the Internet)

I will go online and see if I get the install to work and then try the sharing.


  rggavubt,

You are a step ahead of me.  At least you can access the Ubuntu machione from your Win PC even if you can't get past the security.
I don't even see the PC from Win.    :( 



Expect more calls for help on this thread  :) :confused:

Mac from the Mountains

---

### Post by devilhorn on 2007-02-26
I also have the same problem...i'm trying to set up a staging server, (i'm using DREAMWEAVER on a WinXP box connected to an APACHE server box via LAN) ---my XP box can 'see' the UBUNTU server but promts me for username and password when I try to browse to where I want to put the testing files ...(none of my passwords seem to work)

So basically I need to send a copy of my website files to the webserver across my LAN, but I cant seem to PUT the files there....I know the webserver is working because I can view the APACHE page that says "it worked!......etc.."

hopefully this is really stoopid question

dhorn

---

### Post by nereid on 2007-02-27
Samba uses its own rules. It is like I said it emulates the Windows way and it is a little bit more secure doing it ;)

You could start the ssh deamon on your websever and put the files into the apache directory via sftp.

---

### Post by Stewart MacPherson on 2007-02-27
Hi all,

Partial success !     :) 

I installed the Samba software and then set up a share on one of the Win98 partitions on my Ubuntu PC

Lo and behold I can now see the Ubuntu PC in Network Neighbourhood on my Win PCs.

However, when I try to access it I get a message on the Win98 PC asking for a password .

Since I only have one password on the Ubuntu PC I tried that but it says "incorrect password"

Any helpful suggestions please ?

Mac from the Mountains

---

### Post by sunexplodes on 2007-02-27
> **Stewart MacPherson said:**
> Hi all,

Partial success !     :) 

I installed the Samba software and then set up a share on one of the Win98 partitions on my Ubuntu PC

Lo and behold I can now see the Ubuntu PC in Network Neighbourhood on my Win PCs.

However, when I try to access it I get a message on the Win98 PC asking for a password .

Since I only have one password on the Ubuntu PC I tried that but it says "incorrect password"

Any helpful suggestions please ?

Mac from the Mountains



there's 2 answers to this question.

one is easy but less secure, the other is secure but a little tougher.

the easy one is, go to your ubuntu computer, right click and go into the share folder dialog, and uncheck "read only". 

the hard answer, is that samba wants a username and password to access shared folders that are marked read-only, which must be set up in the System>administration>users dialog, then added to the samba config files.

---

### Post by Stewart MacPherson on 2007-02-28
Hi Sunexplodes,

I thought I had done this however I may be missing something.

Where in the PC should I look for what to share, and what folders should I share?

Sorry if this seems trivial but I am completely new to this.

The ( 3 ) Win partitions on my PC show up in filesystem as Data, Utilities, Games.
These are the names in the mount command.
I have set each of these up as shared using SMB with "read-only" cleared and "allow browse" also cleared.

I still get asked for a password when I try to access the Ubuntu PC from the other PCs on the LAN

Mac from the Mountains

---

### Post by WakkiTabakki on 2007-03-03
Have you tried adding yourself as a samba user?
```

> sudo smbpasswd -a <YourUserName>
> sudo smbpasswd -e <YourUserName>

```

You should be asked for a password after the first command. Just enter you own password (twice I guess, once for sudo and once for smbpasswd)

/N

---

### Post by Stewart MacPherson on 2007-03-04
I tried adding myself as a Samba user, as suggested

It needed the password 3 times, once for sudo, once for smbpasswd  -a and once again to confirm the add.

The commands worked fine but I still get the "incorrect password" message when I try to connect from one of tthe Win98 PCs on the LAN.

???

Mac from the Mountains

---

