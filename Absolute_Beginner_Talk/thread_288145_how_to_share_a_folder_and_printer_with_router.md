---
title: "how to share a folder and printer with router"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2006-10-29
Hello!

I just installed a 4 mb DSL line with a router, exactly Thombson 530 v6 router. It is a 2 ports router, 1 USB and 1 ethernet.

I installed it in 2 PCS.
The first PC is using Windows XP. It is connected through USB to the router.
The other PC is using Xubuntu Dapper Drake. It is connected to the router through Ethernet cable.

(How easy was to install the router to Xubuntu, just pluged  the ethernet cable to the PC and that was all !! Xubuntu autodetected the modem !!)

I read somewhere that as I use a router, and I connect with each PC to internet and don't need to have the other PC turned on, my two PCs are in diferent phisical lans, so I cannot share printer nor a folder.

Is this true?

The Xubuntu PC is going to work as web server in some near future.
What you recommend me to do?
I read somewhere that I can install a switch with the router to be able to share resources? Is this safe? Is there a better option? What option is compatible to use Xubuntu PC as web server?

Maybe there is another option, like having a folder somewhere in internet, send there the files to pass to XP, and download them through internet and an FTP program? It may be  a momentary solution... ?

Or how can I visit my Xubuntu PC through my XP PC and go to a folder for example through FTP?

Any ideas?


Thanks.

Jordi

---

### Post by Denn1s on 2006-10-29
If both computers are conected to the same router then you have a lan, you should take a look at [samba]("http://us2.samba.org/samba/what_is_samba.html") and check if that is wath you are lookin for.

---

### Post by jordi_rc on 2006-10-29
Thanks.

I looked at a guide that I found:

[http://www.guia-ubuntu.org/breezy/servidor/samba](http://www.guia-ubuntu.org/breezy/servidor/samba)

And this guide: 

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

And installed samba.

But I think I must do something in XP or maybe I am mising something because I don't see the other PC.

Do I have to do something in XP to see my other PC?

Jordi

---

### Post by Denn1s on 2006-10-29
Everything is harder in Xp, but you should at least be able to watch it, remember to have them in the same work group, also remember to have at least one share folder, make it here: System > Administrator > Shared Folders.

Once you are able to see your computer you are most likely to need an account to access it from Xp, do it this way:

```
sudo smbpasswd -a username

```

---

### Post by jordi_rc on 2006-10-30
I did that but it didn't worked.

I use a router, each pc is connected directly to internet, and they don't see each other.

Is there a way to send files through internet?

Thanks again.

Jordi

---

### Post by ditikos on 2006-11-11
Use secure copy (scp/ssh).

sudo apt-get install ssh

and go to the putty page and get scp for windows.
use the following to send from your pc to linux box:

**scp <file> <username>@<linuxbox>:<filesystem path>**

and backwards:

**scp <username>@<linuxbox>:<filesystem path+file> <localfile>**

---

### Post by jordi_rc on 2006-11-12
Thanks Dikitos.

I have a program called Putty installed in my XP. Is that program the appropiate for this in XP?

In ubuntu, I usually use synaptic for installing packages.

Should I look for ssh in the list of packages?

I suppose I can make a shell script in my server to send the backup files to the XP PC. Can I ?

Thanks again dikito.


Jordi

---

