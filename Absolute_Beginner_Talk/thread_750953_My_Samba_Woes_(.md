---
title: "My Samba Woes :("
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by General Mayhem on 2008-04-10
Howdy all, hope I can get some help on installing Samba?

I'm tasked with setting up a Linux File Server that XP's can access, hence Samba. The problems I am having are extremely frustrating.

I d/l Ubuntu as it's the new beaut thing, I google for how-to install samba on ubuntu guides and seems fairly simple. The guides say do this and do that, I attempt to and straight out of the block I am hit with a hurdle. Ubuntu doesn't come pre-packaged with Samba??? wth! all the guides say it does, I look in synaptic package thing and sure enough there are several samba references there saying samba is installed, all but 1 file. The actual Samba package itself isn't there.

I have tried with v7 and v8 Ubuntu, same thing.

All the guides say to start things off, click on administration/folder share. So I do and a box pops up saying I need to install NFS and Samba. WTH! Why isn't Samba part of the Ubuntu cd package? It tries to connect to the internet to download samba. My problem here is at work they have a proxy, I enter my proxy details into firefox and I can surf the net, but this flippin package installer just sits there refusing to connect to the net to d/l samba. As far as the linux box is concerned it doesn't think there is an internet connection :(

On 1 version of Ubuntu I tried I got an error message box come up saying it couldn't connect to net and put up a list of 6 files it couldn't get, I being quick witted :) thought, I'll copy/paste into google as firefox works and d/l samba package manually. I do that and when I go into synaptic package thing it gives an error saying the version of samba isn't compatible with some samba lib files etc etc. But this is the very same samba that the folder share wizard was trying to d/l ?????

I was so frustrated I used Suse 10 that someone gave me and again Samba doesn't come with it either, when I followed the guides for Suse it tries to connect to net to d/l Samba and again I am back at square 1, I enter work proxy details in firefox and can surf net but flippin linux cant access the net to d/l the packages. So I d/l them manually in firefox but now I get RPM incompatibility errors with libraries. So I gave up on Suse as well.... 

I took the Ubuntu cd's home and in VMware managed with difficulty to get Samba working with Ubuntu.

How can I get Samba working at work? How do I set up Linux system itself to have internet access. XP is sooooo much easier, all I do is enter proxy details into IE and the XP system itself uses those setting if it needs to access the net to updates etc. Linux apparently doesn't work so simple. How can I over come these hurdles please.....

Frustrated at why everything in Linux has to be so unnecessarily complex to do very simple tasks :(

---

### Post by Trail on 2008-04-10
System -> Preferences -> Network Proxy.

Instead, for terminal use (aptitude or apt-get) use:
```

export http_proxy='http://123.456.789.123:80"

```

---

### Post by paydaydaddy on 2008-04-10
Here is a thread that will help you get started with samba.
[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)

---

### Post by General Mayhem on 2008-04-10
oops

---

### Post by General Mayhem on 2008-04-10
Still not working :(

I am at work now and typing this message in Firefox using my work proxy so I have inet access. But when I enter my proxy details into network proxy and include my login details, linux is still unable to connect to net to either update itself or download samba package :(

Damn Linux...

mel@mel-desktop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate

I completely deleted samba-common from Synaptic Package and now I get this;

mel@mel-desktop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package samba

So I'm guessing Linux is still unable to connect to inet even though I clearly have inet access via Firefox :(

Can anyone tell me what I need to do to d/l the damn samba package manually within firefox?

EDIT: Went here [http://us1.samba.org/samba/ftp/Binary_Packages/Debian/samba/3/](http://us1.samba.org/samba/ftp/Binary_Packages/Debian/samba/3/)  to update manually, got most packages installed all for 1, you guessed it, the samba package. When I try to install that I get all kinds of missing libcupsys2-gnuts10 errors. when I tried to install libcupsys2-gnunls10 I got an gnutls11 missing dependency error. When I tried to install gnutls11 I get can't install that because I'm missing some other lib dependency. This crap never freaking ends...

---

### Post by cdenley on 2008-04-11
Assuming you configured your proxy...
```

sudo apt-get update
sudo apt-get install samba

```

Having any server installed by default would be a bad idea. Since it's not installed by default, it probably isn't on the installer cd. Since apt didn't have an internet connection before, it has probably never downloaded the package index files. It wouldn't know about the samba package until it does.

---

