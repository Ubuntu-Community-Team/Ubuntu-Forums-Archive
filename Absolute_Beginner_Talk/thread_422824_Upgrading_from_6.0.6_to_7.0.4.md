---
title: "Upgrading from 6.0.6 to 7.0.4"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-04-25
Hello:

I currently have Ubuntu 6.0.6 installed on my computer, but am right now downloading 7.0.4. My question is how do I update from one version of Ubuntu to another without losing all my applications, and files?

---

### Post by Seisen on 2007-04-25
You can upgrade to edgy from dapper than upgrade from edgy to feisty. It really helps if you have a fast connection. That way you don't have to worry about losing all your files. Otherwise you need to back them up.

---

### Post by Amenemhet on 2007-04-25
OK, not sure but maybe the new version will have an upgrade option, otherwise try this >
Edit your /etc/apt/sources.list file and change all 'dapper' to 'edgy'
Now go to terminal
>apt-get update
>apt-get dist-upgrade
>apt-get upgrade
>reboot

---

### Post by orwellus on 2007-04-25
Thanks for the replies. I guess what I'm mainly worried about is it messing up the partitions. I have one for my old windows, and then one for Ubuntu. I am trying this upgrade, because I heard it has XEN which allow you to run windows in Ubuntu, and that's what I want. I don't have a install disk for Windows.  So, I don't want to lose it trying to upgrade.

---

### Post by oilchangeguy on 2007-04-25
OEWELLUS, if 6.06 is running fine there's no reason to upgrade, at least not until the next LTS version is available sometime in 2009. look at all of the recent posts about problems people are having with 7.04. it's not worth it if 6.06 is ok.

---

### Post by orwellus on 2007-04-25
I didn't realize people were have problems with 7.0.4 I actuall only wanted to go up to 6.10 because of that XEN program, but couldn't find the download for 6.10. The only options on the Ubuntu get it page were for 6.0.6 and 7.0.4

---

### Post by kittyhawk63 on 2007-04-25
I would recommend that you stay with Dapper as already suggested. It is a good program and extremely stable. There are programs that run in Dapper that may not run in Feisty. I've read some threads on this. Can't confirm this.
Video problems not inherent in Dapper may show up in Feisty. I have been unable to get my ATI card to work. I had problems in Dapper and Edgy but eventually had them working. No such luck in Feisty. Either I downgrade or buy another video card. Dapper may be my most logical choice.
kh

---

### Post by JanvL on 2007-05-13
Try Qemu,

it has loads of possibilities and works for me with Win98.


good luck.

---

