---
title: "installing beryl 0.2.1"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by unelemented on 2007-11-02
Installing beryl-core-0.2.1 I get this error when running configure in terminal 

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Im using Ubuntu 6.06

---

### Post by Pumalite on 2007-11-02
This might help:

[http://ubuntusoftware.info/beryl.html](http://ubuntusoftware.info/beryl.html)
also:
sudo apt-get install build-essential

---

### Post by unelemented on 2007-11-02
Thanks for your fast response

I couldnt understand that site at all

if i type in that line of code into terminal i get

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
matt@ubuntu:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matt@ubuntu:~$

---

### Post by MrFSL on 2007-11-02
Beryl and Compiz have merged to make Compiz-fusion.

I suggest installing that. Good instructions can be found here:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by unelemented on 2007-11-02
I cant get compiz to work ither

---

### Post by overdrank on 2007-11-02
> **unelemented said:**
> I cant get compiz to work ither

Hi and I hate to be the barrier of bad news but support for beryl and compiz have been dropped in Dapper. I would still be using dapper if that were not the case. :(

---

### Post by unelemented on 2007-11-02
Bugger 
so beryl 0.2.1 wont work then?

---

### Post by overdrank on 2007-11-02
> **unelemented said:**
> Bugger 
so beryl 0.2.1 wont work then?

Not on Dapper but if you upgrade to Edgy 6.10 I think it will. I am not sure it has been a couple of months since I have used edgy. There is always Feisty 7.04 and Gutsy 7.10. 

:popcorn:

---

### Post by unelemented on 2007-11-02
Im going to have to get gutsy then

what about knoppix?

---

### Post by Pumalite on 2007-11-02
Knoppix is great as a Live CD, but I don't think you can compare it to Ubuntu.

---

### Post by unelemented on 2007-11-02
I just had a play on the live cd and buntus way better

Are there any versions of beryl that are floating around that will run  on dapper

---

### Post by unelemented on 2007-11-03
I tryed 2.0 and 1.9999.2 beryl and still got the same message

---

### Post by balagosa on 2008-03-26
> **MrFSL said:**
> Beryl and Compiz have merged to make Compiz-fusion.

I suggest installing that. Good instructions can be found here:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

followed what the CompositeManager site instructed but i halted at running compiz due to the error of:

daniel@daniel-desktop:~$ compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

XGL isnt present. i have been trying to run compiz for the past week and no luck because i cant find an XGL to download.

any help please?

---

