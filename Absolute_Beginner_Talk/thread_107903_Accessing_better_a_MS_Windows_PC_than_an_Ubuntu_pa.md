---
title: "Accessing better a MS Windows PC than an Ubuntu pal in my home network"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by qgil on 2005-12-24
I have a laptop still with Hoary connected via wireless to an access point and a desktop with Breezy connected via LAN cable. Each one have Internet access, no problem.

I want to access from one machine to the other, at least to some folders.  Via Places -> Networks I don't quite get there, sometimes I see the folders, can't access them altough they are marked as shareable. Still dont understand why should I go through a "MSHOME" workgroup to find the PCs.

If I try to find informaton in the Internet I get swapped in complex SAMBA related stuff that explain me how to deal with local networks involving MS Windows PCs. But, why do I need this to connect from one Ubuntu to another Ubuntu in a 100% GNU/Linux local network?

On the other hand, my partner has a laptop with MS Windows, she created a folder shareable and... I can access it without a problem!!!!!! I can move to her folder files, which I can't do between my Ubuntu machines. 

Is it more easy to connect to a MS Windows computer than to connect to a Ubuntu pal in my home network? Weird, isn't it? What I'm doing wrong?

---

### Post by gnu2tux on 2005-12-24
Hi,

 The reason you are having problems is because you are trying to use Windows Networking on a Linux computer (It's called samba). It's perfectly OK to do it that way, but if you simply want Linux to Linux connections, then SSH is far better.

Ensure you have installed openssh-server on both boxes for this to work (use synaptic package manager) and then follow these easy steps:

In Ubuntu 5.10 click on Places menu,
then click Connect to Server.
Change the Service type to SSH
Type the name of the server you want to connect to in the server text box.
Leave the port box empty
Enter a specific folder on the remote machine if you want it to start from there (otherwise leave it blank).
Finally enter your username for the remote machine and give the connection a name, eg: 'mp3s on linuxbox1'.

Hope this helps, for more information on installing software and general help visit my website: 

[http://www.linuxnewbieguide.org]("http://www.linuxnewbieguide.org")

---

### Post by qgil on 2005-12-24
Thanks for the tip. There is an arguably problem of usability since it's normal that I'd like to find my other computers under "network" but let's follow the path your recommend.

After doing all the steps, I get this error message:

--------

Cannot display location 'sftp://[user]@[server]/[directory]'

---------

(with my own user, server and directory, all of them correct and I've tried many combinations)

Any hint?


EDITED: with the destinaton user, server and directory, of course

---

### Post by gnu2tux on 2005-12-25
What happens if you leave the directory out? oh - and are you sure that you installed openssh-server (and that no firewall is blocking port 22)? 
Regards, ali 

[QUOTE=qgil]Thanks for the tip. There is an arguably problem of usability since it's normal that I'd like to find my other computers under "network" but let's follow the path your recommend. After doing all the steps, I get this error message: -------- Cannot display location 'sftp://[user]@[server]/[directory]' --------- (with my own user, server and directory, all of them correct and I've tried many combinations) Any hint? EDITED: with the destinaton user, server and directory, of course[/QUOTE]

---

### Post by qgil on 2005-12-25
ali, thanks for all thank you for your patience and will to help.

I have done all the combinatons, leaving empty and filling fields. Same error message.

About proxies... I haven't set any. If I go to System > Preferences > Proxies I see in Advanced Configuration there are to hosts ignored:

localhost
127.0.0.0/8

No idea what does it mean. :confused: 

(Anecdote: in the meantime due to Christmas time yesterday I had to record a CD full of, ahem, private copies of shared Xmas songs. Lucky me my father@law came with his laptop with CD recorder and... Windows XP. He only had to create a shareable folder. I could detect that folder in 2 secs and transfer 100Mb in few minutes, without any configuration. Withouth XP yesterday I wouldn't have Xmas songs in the family dinner and my partner would have possibly asked for a divorce!!!)  [-o<

---

### Post by The Warlock on 2005-12-25
To set up a Samba share (which is certainly the easiest, although not the most efficient, secure, etc, system for sharing files, even in Linux), go to System->Administration->Shared Folders and just add folders to share. Make sure you check "allow browsing folder". You might want to check "read only" as well.

Click on the General Windows Sharing Settings button (it's in the Add dialog) to change your host description, domain/workggroup, etc. You don't *have* to be MSHOME, if you don't want to.

---

### Post by steve.horsley on 2005-12-25
I suspect that you need to confirm to SSH that the othe host is known properly first. Try to connect a terminal session between the two machines first. This will get known hosts updated, and hopefully, give you an indication of what's wrong if you can't connect.

Open a command prompt and do the command:
```
$ ssh username@hostname
```
replacing the user and host name appropriately, of course. e.g.
```
steve@StevesPC:~$ ssh steve@192.168.8.101
```
You may well get a messagelike this:
```
The authenticity of host '192.168.8.101 (192.168.8.101)' can't be established.
RSA key fingerprint is <long hex number here>.
Are you sure you want to continue connecting (yes/no)? 
```

In which case you can answer yes (assuming you are sure you connected to the right machine). Once you have answered this question once, you will not be asked it again - the identity is remembered. I suspect that this may be the reason that Nautilus cannot map drives to your other machine.

---

