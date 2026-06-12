---
title: "Checkgmail preferences?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by shawn.mnb on 2008-01-06
Hey all...

I downloaded checkgmail today and was having the problem with the invalid username, but apparently following some advice from the forum I got it working. However, now I cant access checkgmail's preferences. I just dont know how to get to them. The icon is on the panel at the top but when I right click on it none of the options give me 'preferences'. What can I do?

---

### Post by shawn.mnb on 2008-01-06
Possible update? I think the problem may be old 'checkgmail' files in my usr/bin folder which I cant delete because access is denied. How can I delete them? Id like to install the newer version there instead.

---

### Post by kyphi on 2008-01-06
To uninstall checkgmail go to System ->Administration -> Synaptic Package Manager.  Scroll to the entry checkgmail and mark it for complete removal.

Alternatively you can also mark it for reinstallation.

It seems that something did not install correctly with your previous installation if Preferences cannot be accessed.

---

### Post by shawn.mnb on 2008-01-06
hey, i uninstalled checkgmail in synaptics then reinstalled it and also applied the fix:

wget [http://checkgmail.svn.sourceforge.ne...ail/checkgmail](http://checkgmail.svn.sourceforge.ne...ail/checkgmail)
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

I still cant see preferences though unfortunately.
any other information I can give?

---

### Post by shawn.mnb on 2008-01-06
I tried a different workaround with:

sudo aptitude install checkgmail
wget [http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail](http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail)
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

but it tells me:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any thoughts?

---

### Post by shawn.mnb on 2008-01-07
bump

---

### Post by kyphi on 2008-01-07
The version I downloaded and installed from sourceforge is "checkgmail_1.12-1_all.deb".

If that is not the version you have installed, uninstall your installed version and start again.  Several bugs, such as the incomplete login have now been fixed.

---

### Post by shawn.mnb on 2008-01-08
Im really new to ubuntu (about a week now) and Im still confused as to how to go about installing that specific deb file
I tried:

sudo apt-get checkgmail_1.12-1_all.deb
[sudo] password for *****:
E: Invalid operation checkgmail_1.12-1_all.deb
*****@*****-laptop:~$ sudo dpkg -i checkgmail_1.12-2_all.debdpkg: status database area is locked by another process
*****@*****-laptop:~$ sudo apt-get install checkgmail_1.12-2_all.deb
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 

I have the .deb file sitting on my desktop but I dont know how to install it properly. how would I download and install directly from the website to make sure that I also get all of the dependencies?

Hope you can help

---

### Post by Seisen on 2008-01-08
If you double click on the file Gdebi will install the .deb file and pull the dependicies if they are available or you can use dpkg in the terminal

```
sudo dpkg -i checkgmail_1.12-1_all.deb
``` and this error

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
```

is caused if you have synaptic, add/remove or try to apt/aptitude and you already have one of the others running at the same time.

---

