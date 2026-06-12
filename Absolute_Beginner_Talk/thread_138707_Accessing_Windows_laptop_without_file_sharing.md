---
title: "Accessing Windows laptop without file sharing??"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by cy218 on 2006-03-02
I'm struggling!

I have:
1x Compaq Armada 1590DT with Windows 98se and NO DISKS and no CD writer(my old machine)

1x Compaq Armada 110 with Ubuntu Hoary (my new toy!)

I'm trying to move all my files inc. outlook contacts and emails from my old laptop onto my new one. I have access to the office windows network through a  PCcard wireless connection on each machine. Sounds easy?

Complications:
I deleted any of the services on my old laptop that I didn't think I would need (yup -network stuff too). It's only got a 2gig drive and I was playing around with slackware and damn small linux trying to get them to work so I partitioned 1 gig for windows (so I stripped everything out!). Therefore I can't access file sharing (no tabs come up on any of the folders in windows to give me that option).

Am I making any sense?

I'd rather find a network solution than spend half my life transferring with floppies. Besides I thought the challenge may be a learning experience[-( .

Both machines will access the internet through the office router.
I can ping my windows machine with my ubuntu machine within the network.
I can't see my windows machine in 'places' although I can see the other XP machines that are on the network.
I don't want to dump stuff onto any other machine on the network (the boss'd kill me if I spudsed up!)

I think that's it! If anyone can help please bare in mind I'm relatively new to all this. I can use synaptic abd I've played with dpkg a bit BUT I do start to glaze over with things like 'host' and 'client' -some hand holding would be appreciated.

All in all I'm having fun though!

Thanks

Cy

P.S. Reading back over this I suppose what I want to do is use my ubuntu machine to force its way onto my windows machine across the office network without its say so! Sounds dodgy to me. But I thought windows machines were insecure.

P.P.S. When pinging I turned off the firewall on my windows machine (I also allowed the IP address of my ubuntu machine but can't remember if that worked).

---

### Post by aysiu on 2006-03-02
Maybe I'm not understanding your situation, exactly, but if you can ping your Windows machine, can't you use smb?

For example, let's say your Windows machine is 192.168.0.100.

Open up the Nautilus file browser in Ubuntu and type this in the location bar: ```
smb://192.168.0.100/
``` You should be prompted for a password if you're sharing any folders on the Windows side.

---

### Post by carlosqueso on 2006-03-02
I'm not 100% sure, but can't you use samba to create a share on your ubuntu machine that your windows machine can see?  Then you could transfer from your windows to your ubuntu machine instead of the other way around.  Unfortunately, I have no clue how to do this.

---

### Post by cy218 on 2006-03-02
[QUOTE=aysiu]Maybe I'm not understanding your situation, exactly, but if you can ping your Windows machine, can't you use smb?

For example, let's say your Windows machine is 192.168.0.100.

Open up the Nautilus file browser in Ubuntu and type this in the location bar: ```
smb://192.168.0.100/
``` You should be prompted for a password if you're sharing any folders on the Windows side.[/QUOTE]

Thanks for that AYSIU... no joy!

I tried but got this response:

```
"Windows Network: 192.168.1.3" couldn't be found. Perhaps it has recently been deleted.
```

I know this is the correct IP because I got it from the windows "ipconfig".

I don't know if this has any bearing on the problem but when I port scanned the above IP address with network tools, the only one open was 139-netbios-ssn.:-k 

Carlosqueso,

I don't think I can do what you suggest because I have very few services running on my windows laptop -unless anyone has any ideas.

Thanks

---

### Post by cy218 on 2006-03-06
I don't want to seem ungrateful but should I have asked this question in 'networking'?

Is there a way of transferring this post across or cut and pasting it from here and deleting this copy?  I know it's bad show to cross post so I don't want to do that!

Thanks

Cy

---

### Post by LordBug on 2006-03-06
Couple of options here:

1) Windows 98, by default, had admin shares on all the drives.  Unless you've removed this, you should be able to access it.  It's named "C$", assuming your HD is drive C:.  Replace the letter if necessary with the correct drive letter. Try 'sudo mount -t smbfs -o user={admin level user name on the laptop} //192.168.1.3/c$ {mountpoint}' and see what that gets you.

2) FTP.  Setup an FTP server on the new Ubuntu system and use the built-in Windows FTP client (via a command line) to access it.  You might want to read up on FTP commands so you don't mess up files.

3)  Seeing that you're doing this from work, you likely have your own private space on the network.  You could use it for your temporary file share.

---

### Post by cy218 on 2006-03-12
Thanks for that LordBug

I got a bit confused with

```
Try 'sudo mount -t smbfs -o user={admin level user name on the laptop} 

```
What's the user name? My Ubuntu login or something from my windows machine? Would that be the "log out" name on the windows start panel, even though I use no name to start my windows session?

Also:
```
//192.168.1.3/c$ {mountpoint}' and see what that gets you.

```
Where do I get the information for the mountpoint or do I have to create one -how?
Do I need ```
: or \ or / 
```after the c$?

Sorry it's all a bit basic but I'm not particularly up on networking/linux phraseology and never know where to find the stuff the guru's put in brackets.

In the meantime I'm trying to follow the ftp route as well. I've downloaded winscp and putty onto my windows laptop ans I'll see how that goes. Any info on the above would still be appreciated though.

Edit:

Well.... It worked! WinSCP downloaded onto my windows laptop enabled me to drag and drop across to my ubuntu machine once I'd downloaded the SSH server from synaptic. At last!

Mind you, it'd be good to learn how to do it the other way -thanks for the pointers though.



Cy

---

