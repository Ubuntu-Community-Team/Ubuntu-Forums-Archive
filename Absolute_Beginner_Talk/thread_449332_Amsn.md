---
title: "Amsn"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-05-20
I recently upgraded/updated my version of amsn.
Now when i start the new version I get a message saying:
AMSN not uses MSNP9, which requires the use of a secure connection
using ssl. In order to use SSL, aMSN needs to install a module called TLS,
which is missing from your system. This wizard will help you to download and
install TLS. Please choose your system tupe so we can automatically download
the required TLS files.

I selected Linux-x86, press ok and then get the following error message:
Error installing TLS module::Couldn't get http"//switch.dl.sourceforge.net/sourceforgee/amsn/tls-1,5,0-linux-x86.tar.gz

So I downloaded the files myself and have them standing neatly on my dekstop. I even extracted them, but there isn't any file in there that looks like something that can be installed. 

Obviously i don't know how to proceed. If anybody can give a hand with this, it would be appreciated.

---

### Post by Waappu on 2007-05-20
Hi

See if this helps
[http://ubuntuforums.org/showthread.php?t=368813&highlight=amsn](http://ubuntuforums.org/showthread.php?t=368813&highlight=amsn)

---

### Post by quinnten83 on 2007-05-20
I tried with the apt-get instruction, as i only understand like one third of what those guys are saying. apt-get got me this as a result:
darrell@darrell-laptop1:~$ sudo apt-get install tcltls
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tcltls is already the newest version.
tcltls set to manual installed.
The following packages were automatically installed and are no longer required:
  docker sox tk8.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So appearantly it is allready installed, but amsn does not recognize it
I figured out where i need to specify the library in amsn, and have done so, but it keeps telling me that tls is not installed. i even tried with the commands given in the other thread..

Anybody got any suggestions?

---

### Post by seshomaru samma on 2007-05-20
> So I downloaded the files myself and have them standing neatly on my dekstop. I even extracted them, but there isn't any file in there that looks like something that can be installed.

first look for a README file
also check[**_ this_**]("http://monkeyblog.org/ubuntu/installing/") out

---

### Post by quinnten83 on 2007-05-21
> **seshomaru samma said:**
> first look for a README file
also check[**_ this_**]("http://monkeyblog.org/ubuntu/installing/") out

I figured out what I was doing wrong. I couldn't edit the page, because in the terminal i had given it the wrong name. In nautilus (that's the " explorer" in Linux, right?) the filename was 

/usr/lib/tls1.50/pkgindex.tcl but when i tried looking in the terminal i noticed that the name was
/usr/lib/tls1.50/pkgIndex.tcl, with an uppercase I.
I appended the 0, removed the .amsn in home, since there wasn't much in that folder anyhow and let amsn create a new one and now it works.

---

### Post by quinnten83 on 2007-05-21
Oh, tnx for the replies btw, your help was most appreciated.
added info on this problem can be found on the amsn forum (this one was even made sticky).

---

