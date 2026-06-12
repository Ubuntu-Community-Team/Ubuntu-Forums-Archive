---
title: "[SOLVED] Transfer lots of files from Vista to Ubuntu?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by mgbridges on 2008-03-20
I'm setting up my Ubuntu PC as a small home fileserver and steadily transferring most of the data files from my Vista laptop. I've now come to the point where I want to transfer all of my music files (about 50GB) from the Vista machine to the Ubuntu machine and it's proving a bit trickier than I thought.

I set up Samba and got each machine to see the other over my wireless network. I tried pushing the files across from Vista using Windows Explorer but I keep losing the Samba connection part way through the transfer.

Is there a safe way to initiate this from the Ubuntu end? I tried using cp but couldn't work out the syntax for the source, given that it's a different machine on the network.

Would rsync be a better bet? If so, any tips on how to do it?

Thanks,

Martin

---

### Post by jordanmthomas on 2008-03-20
If you're wanting to use cp, you'll want to mount your Vista SMB share
look up smbmount (I hear using cifs is faster, but for me it's all good)
```

mkdir vista
smbmount //vista/sharename vista
```
(assuming you're not using a password) Then you can 
```
cp vista/file ~/whatever
```


Also, when you say it's a fileserver I assume you have no X installed?
If you do, both nautilus and konqueror can browse SMB shares.

press ctrl - L in them and then type
smb://vistabox/sharename

and you can copy / paste that way.

(edit)
If you do end up using nautilus, beware that on my computer at least it always takes up 100% of my CPU any time I do any significant copies and (rarely) crashes during it.
It's always done this, and I don't really know why, so I use other solutions.

---

### Post by redbullmonsta on 2008-03-20
I had the same issue, and it stems from the poor ability for vista to transfer a large amount of files, explorer seems to die.... there are numerous post on the web regarding this

The way i got round it was to map the samba share as a network drive in windows then go to the dos promp and do the copy from there.... you could also download 'guildftp daemon' for windows and ftp the files out but i would recommend the first option :)

Don't know about rsync im afraid

Good luck

---

### Post by Tomatz on 2008-03-20
If you are trying to do this wirelessly.  Maby you should consider connecting your laptop (or both) to your router via ethernet. :)

---

### Post by mgbridges on 2008-03-20
> **Tomatz said:**
> If you are trying to do this wirelessly.  Maby you should consider connecting your laptop (or both) to your router via ethernet. :)

Not really practical I'm afraid, given where the router and the PCs are located.

Martin

---

### Post by Tomatz on 2008-03-20
Bummer :(

---

### Post by mgbridges on 2008-03-20
> **jordanmthomas said:**
> If you're wanting to use cp, you'll want to mount your Vista SMB share
look up smbmount (I hear using cifs is faster, but for me it's all good)
```

mkdir vista
smbmount //vista/sharename vista
```
(assuming you're not using a password) Then you can 
```
cp vista/file ~/whatever
```

How do I find out the sharename on the Vista box? I haven't explicitly set one up in Samba as far as I know, but I can browse the files from the Ubuntu box using Nautilus.

> **jordanmthomas said:**
> Also, when you say it's a fileserver I assume you have no X installed?
If you do, both nautilus and konqueror can browse SMB shares.

press ctrl - L in them and then type
smb://vistabox/sharename

and you can copy / paste that way.

I have X installed and as mentioned can use Nautilus to see the files on the Vista laptop. However, if I try doing a simple Copy and Paste of the files it craps out with SMB timeouts partway through.

Any other ideas?

Martin

---

### Post by hyper_ch on 2008-03-20
I would use SFTP/SCP for that....

(1) Install openssh-server on your linux machine
```

sudo apt-get install openssh-server

```

(2) Download and install WinSCP from [http://www.winscp.com](http://www.winscp.com) (free)

(3) Start WinSCP and connect to your Linux machine with the account's username and password... you then can simply drag and drop the files there... works great :)

---

### Post by mgbridges on 2008-03-20
> **hyper_ch said:**
> I would use SFTP/SCP for that....


Is this likely to get round the Samba timeout-type issue I've been having?

Martin

---

### Post by hyper_ch on 2008-03-20
That will not use the SMB protocoll but SSH

---

### Post by Ardrias on 2008-03-20
Another vote for using SCP here. It's usually the easiest and best way of going about things.

---

### Post by hyper_ch on 2008-03-20
well, in a LAN unencrypted transfer might be faster - but openssh-server and winscp have been a combo that always worked without much hassle..

---

### Post by mgbridges on 2008-03-20
I installed OpenSSH and WinSCP and it did seem to be working better for me. However, now I'm getting different errors - gethostbyname failed from the WinSCP side, as if my desktop had dropped off the network (although it is definitely still there).

I think I will try breaking the copy down into smaller chunks and see if that helps.

Martin

---

### Post by jimv on 2008-03-20
Ok, so I have Vista machine with a 500gb hd in it, and an ubuntu server with a 40 gb hd in it.  I set up my ubuntu machine to stream music located on the Vista machine over the web.  Also, I used the ubuntu server the other week to compile a geocoding database out of 3000 zip files located on the Vista box.  The task ran for 16 hours, and the network didn't time out once.

How did this happen with Vista in the equation?

Well, I've been running the SP1 beta and it seemed to fix all the connectivity issues I was having with Vista.  So my advice?  Go grab SP1 for Vista...it's out now.

If you're subscribed to MS Technet, you can download it here:
[http://technet.microsoft.com/en-us/windowsvista/bb738089.aspx](http://technet.microsoft.com/en-us/windowsvista/bb738089.aspx)

Or else use Windows Update to get it.

Tons of bug fixes in it...you like very much.

---

### Post by mgbridges on 2008-03-23
Breaking the copy down into smaller chunks and using SCP did the job - thanks for the suggestions.

Martin

---

