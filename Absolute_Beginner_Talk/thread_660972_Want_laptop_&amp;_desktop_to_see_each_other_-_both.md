---
title: "Want laptop &amp; desktop to see each other - both Ubuntu"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by jnorris235 on 2008-01-07
No good - nothing simple, is there!! And I have tried to read endless threads replete with jargon that have got me nowhere this afternoon.
*****
My wireless network is called CHINA, and the two computers are called TAO and CHI
Both access the internet fine - I just want to drop a file from the laptop to the network!
That's all!!
*****
In Ubuntuguide it says to type:
sudo apt-get install samba smbfs
I do it on both computers

Then type:
sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers

which I did, cut'n'paste like a good 'un.
and insert the line:
system_username="network username"
which I did, as it says - exactly like that, no typos.

I go to Places/Network 
and it lists CHI, TAO, and Windows Network.

Clicking on CHI to access my laptop (it says at the top of the window: CHI on CHI) or even clicking on TAO (again top of window says TAO on TAO - I would have thought it should be TAO on CHINA) gets nothing other than the message below.

Click on Windows Network (why Windows for goodness sake - thought I'd got rid of that) and it says:

MsHome
Click on that (endless clicking...) and I get guess what
CHI and TAO again!
Click on China and I get THE MESSAGE!!

This is the message I get:
The folder contents could not be displayed.
Sorry, couldn't display all the contents of "Windows Network: china".

---

### Post by p_quarles on 2008-01-07
Samba is specifically for configuring network shares that can be seen by Windows machines. Though it will certainly work for what you want to do, it will be simpler to configure something like NFS:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

### Post by billgoldberg on 2008-01-07
I want to do the same as the original poster. 

I haven't been able to do it.

I tried samba dozens of times and it just doens't work.

Can somebody post a drop dead easy how-to for:
sharing files between 2 ubuntu computers, both connected to the router to acces the internet.

---

### Post by PeterJS on 2008-01-07
The absolute easiest way to get files from point A to point B on separate linux machines is SSHFS. Install [sshd]("apt:/openssh-server") on the machine you want to get the files from, and [sshfs]("apt:/sshfs") on the machine you want to move files to.

To use sshfs:
```

sshfs user@machine:/some/folder /some/place/local

```and if you leave the remote directory empty it will default to the home directory for the user you specified.

To unmount it when you are done:
```

fusermount -u /some/place/local

```

---

### Post by stalker145 on 2008-01-07
> **jnorris235 said:**
> No good - nothing simple, is there!! And I have tried to read endless threads replete with jargon that have got me nowhere this afternoon.
*****
My wireless network is called CHINA, and the two computers are called TAO and CHI
Both access the internet fine - I just want to drop a file from the laptop to the network!
That's all!!
*****
In Ubuntuguide it says to type:
sudo apt-get install samba smbfs
I do it on both computers

Then type:
sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers

which I did, cut'n'paste like a good 'un.
and insert the line:
system_username="network username"
which I did, as it says - exactly like that, no typos.

I go to Places/Network 
and it lists CHI, TAO, and Windows Network.

Clicking on CHI to access my laptop (it says at the top of the window: CHI on CHI) or even clicking on TAO (again top of window says TAO on TAO - I would have thought it should be TAO on CHINA) gets nothing other than the message below.

Click on Windows Network (why Windows for goodness sake - thought I'd got rid of that) and it says:

MsHome
Click on that (endless clicking...) and I get guess what
CHI and TAO again!
Click on China and I get THE MESSAGE!!

This is the message I get:
The folder contents could not be displayed.
Sorry, couldn't display all the contents of "Windows Network: china".

Make sure that you enable the SAMBA user if that's the route you end up taking ```
sudo smbpasswd -e system_username
```

---

### Post by jnorris235 on 2008-01-08
Thanks - I'll stick with Samba because many people seem to say its good.
I've no idea what NFS is, but Samba seems to say it will see my Mums laptop (Windows) - and lets face it, I'll never suggest she switches with Windows,. At least Windows just works!!

Having said all that - I did enable the user (why was that not mentioned anywhere - it's all so much fiddling!). On both machines.
But they still wont see each other.

Open Places/Network and CHI (laptop) and TAO (Desktop I'm typing on) both listed.
The folder contents could not be displayed. is all it says if I click on them.
Also listed is Windows Network and click on that I get CHI and TAO again - same result.
Please - save a suicide - why wont it work?
Is it down to these permissions?

---

### Post by stalker145 on 2008-01-08
> **jnorris235 said:**
> Thanks - I'll stick with Samba because many people seem to say its good.
I've no idea what NFS is, but Samba seems to say it will see my Mums laptop (Windows) - and lets face it, I'll never suggest she switches with Windows,. At least Windows just works!!

Having said all that - I did enable the user (why was that not mentioned anywhere - it's all so much fiddling!). On both machines.
But they still wont see each other.

Open Places/Network and CHI (laptop) and TAO (Desktop I'm typing on) both listed.
The folder contents could not be displayed. is all it says if I click on them.
Also listed is Windows Network and click on that I get CHI and TAO again - same result.
Please - save a suicide - why wont it work?
Is it down to these permissions?

It sounds like it may be...

If I remember correctly, I think I went so far as to give full R/W permission on the shared folders to everyone and their dog to get my SAMBA working... but don't quote me because it's been a *looong* time.

---

### Post by backflip on 2008-01-08
I have the exact same set-up and after much searching I was able to share folders using the info I found in this post [http://ubuntuforums.org/showthread.php?t=574171&highlight=install+nfs&page=2](http://ubuntuforums.org/showthread.php?t=574171&highlight=install+nfs&page=2)

---

