---
title: "Local Network Linux to Linux"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by nyquist on 2007-04-13
Hi,

I have two computers, both running Ubuntu 6.06. They are connected to a router-modem.  Both work OK on the web, e-mail and can see a Windows machine, when it's connected to the router.  

Pinging one machine from the other, using the Ubuntu networking tools also works OK.

However, I can't make files or folders on one linux machine, visible to the other.

The settings I've used are 

Network settings/general /Host .... linux-01
                                        /Domain ....localnet

Network settings/hosts   Added 192.168.1.20 linux-02

The other machine has the names swapped, and the IP address 192.168.1.19

I'm not sure about the Domain setting, or whether it's needed.  I've used the same name on both machines.

Any help would be much appreciated.

Regards

         Clive

---

### Post by Seisen on 2007-04-13
You need to set up NFS to get that to work. Now if you are going to add your Windows box into the mix then you would need Samba. Go to System>Adminisration>Sharing Folders and click on it. Check the first box for NFS and see if that works.

---

### Post by vruum on 2007-04-13
the easiest way to do this would probably be to take advantage of the fact that ubuntu comes with a functional ssh server setup. Open nautilus on one machine press <ctrl> + l an address bar will appear, type : ssh://192.168.1.(19 or 20 depending on which machine your're trying to connect to.) if the username on both machines is the same it will ask for your password an put you in the home folder on the remote machine. if you have differing usernames, you may need to type ssh://$remote_user@192.168.1.19or20 in the address bar, where $remote_user is the name of your user on the machine you're connecting to. when you are in, bookmark it for easy future access.

---

### Post by nyquist on 2007-04-14
> **Seisen said:**
> You need to set up NFS to get that to work. Now if you are going to add your Windows box into the mix then you would need Samba. Go to System>Adminisration>Sharing Folders and click on it. Check the first box for NFS and see if that works.

Thanks Seisen.  NFS appears to be set up.  

I'm not sure what to expect. Should the remote linux computer show up in 'Places', like the Windows computer does?  I've got several books on Linux, they say a lot about networking to Windows, but not much about communication with other Linux machines :o

---

### Post by hyper_ch on 2007-04-14
For SSH one has first to install the server so that this machine listens to ssh requests:

```

sudo aptitude install openssh-server

```

---

### Post by nyquist on 2007-04-14
> **vruum said:**
> the easiest way to do this would probably be to take advantage of the fact that ubuntu comes with a functional ssh server setup. Open nautilus on one machine press <ctrl> + l an address bar will appear, type : ssh://192.168.1.(19 or 20 depending on which machine your're trying to connect to.) if the username on both machines is the same it will ask for your password an put you in the home folder on the remote machine. if you have differing usernames, you may need to type ssh://$remote_user@192.168.1.19or20 in the address bar, where $remote_user is the name of your user on the machine you're connecting to. when you are in, bookmark it for easy future access.

Thanks vruum.  I tried this quickly yesterday, but got 'Permission Denied'.  My book on Beginning Ubuntu by Kier Thomas, says that I need to add the Server component of SSH, so I'll explore SSH in more detail.

Thanks for pointing me in the right direction.

BTW is this the usual way to do Linux to Linux communication?  Should anything appear in 'Places'?

Regards

      Clive

---

### Post by vruum on 2007-04-14
my bad, the reason I suggested ssh was that I thought ubuntu came with an ssh server already configured and started. and you could avoid configuration of samba (samba is, as Seisen said, usefull when dealing with windows networking) Anyway, when you have got the ssh server installed (or if you already have it installed) and you still experience the permission denied message you may need to exchange keys (ssh uses something called public and private keys for security) to do this open up a terminal (gnome-terminal) and type the "ssh://$remote_user@192.168.1.19or20" stuff from before in. it will ask you if you want to add the key (I can't recall the exact question, just answer yes, it will log you in to the remote machine, type exit, and exit again. and then check if nautilus works now. if it does. once you're logged in, make a bookmark, and it should show up in the "places" menu. if it still doesn't work, maybe look into samba instead, as it may be the easier way.

---

### Post by nyquist on 2007-04-16
> **vruum said:**
> my bad, the reason I suggested ssh was that I thought ubuntu came with an ssh server already configured and started. and you could avoid configuration of samba (samba is, as Seisen said, usefull when dealing with windows networking) Anyway, when you have got the ssh server installed (or if you already have it installed) and you still experience the permission denied message you may need to exchange keys (ssh uses something called public and private keys for security) to do this open up a terminal (gnome-terminal) and type the "ssh://$remote_user@192.168.1.19or20" stuff from before in. it will ask you if you want to add the key (I can't recall the exact question, just answer yes, it will log you in to the remote machine, type exit, and exit again. and then check if nautilus works now. if it does. once you're logged in, make a bookmark, and it should show up in the "places" menu. if it still doesn't work, maybe look into samba instead, as it may be the easier way.

Hi,

Sorry for the delay in replying, but I've been having problems navigating my way round this busy group, and trying out things on Ubuntu:o 

I managed to get the servers for SSH installed, and working OK.  It was great to see the directories on the remote computer.  

Once again, many thanks.

               Clive

---

### Post by asforme on 2007-04-16
Maybe it was just my configuration, but sharing files over SSH was painfully slow (on a 1 gig connection).  I ended up going with samba, I cant say how the speeds are on nfs.

---

