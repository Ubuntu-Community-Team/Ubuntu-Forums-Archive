---
title: "How do I mount a samba share?"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by bcasanov on 2008-04-15
Hi, 

I am a beginner at home networking, and recently installed samba on one of my computers having Kubuntu and configured it to share the home folder.  I have another computer with Ubuntu Hardy with which I want to access files on the other computer.  I go to Places>>Network, and then see my server in Nautilus, and then click on it to browse the shares. Once I click on the share folder labeled Home, I get a message saying: "Unable to mount location--unable to mount Windows share."  What do I do about this?

---

### Post by bodhi.zazen on 2008-04-15
Install smbfs and re-try mounting the share.

```
sudo apt-get install smbfs
```

Then mount as root :

```
sudo mkdir /media/samba
sudo mount -t cifs //server_ip/share /media/samba -o user
```

If that works, configure sudo to allow users to mount the samba share.

---

### Post by bcasanov on 2008-04-15
Thanks for your response!  This might be a dumb question, but do I put the share name in the spot where it says share and do I put the username of the computer from which I am accessing the share or the username of the computer hosting the share?

In other words, should the command look something like this? 
> sudo mount -t cifs //192.168.0.106/Home /media/samba -o user-name-of-computer-accessing-share

...or like this?
> sudo mount -t cifs //192.168.0.106/Home /media/samba -o user-name-of-computer-hosting-share

Regards,

bcasanov

---

### Post by spiderbatdad on 2008-04-15
Not sure, but thinking there should already be the hosts username in the path to the share, and user accessing share comes last...like:
```
sudo mount -t cifs //192.168.0.106/Home/username/media/samba -o user-name-of-computer-accessing-share 
```

---

### Post by HermanAB on 2008-04-15
You shuold visit the Samba project web site and read the official howto as well as the guide specific to Ubuntu.

Cheers,

Herman

---

### Post by bcasanov on 2008-04-15
Do you have a link you could give me?  Searching through Google gave me many links that were pretty outdated.

---

### Post by spiderbatdad on 2008-04-15
This link is good for all Ubuntu releases:[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

This is also an excellent how-to [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by mgmiller on 2008-04-15
another package you may want to install that will give you a nice GUI that makes configuring your samba easier is:

```
sudo apt-get install system-config-samba
```

After it's in, look in System > Adminstration > Samba

It lets you easily change work group names and set up just about everything.

---

### Post by bcasanov on 2008-05-05
Thanks guys for everything!  I got my Samba shares mounted by setting up a guest account.

---

