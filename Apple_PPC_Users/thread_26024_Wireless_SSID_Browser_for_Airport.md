---
title: "Wireless SSID Browser for Airport"
date: 2005-04-11
forum: Apple PPC Users
---

### Post by pumaman on 2005-04-11
I am tying to find some software that will allow me to browse a list of available wireless networks a la kismac (for the MacOS). Kismet doesn't seem to like working (or I can't get it to work) on 5.04 with an Airport [regular]. I don't need anything fancy, just a list of what is around me.

Thanks.

---

### Post by khc on 2005-04-14
The default airport driver doesn't include scanning support, however you can get the version from cvs which does support scanning. Once that's installed you can use programs like netapplet or the command 'iwlist scan' to see a list of networks.

---

### Post by Jæd on 2005-05-13
So how does one go about getting that and installing it...?

---

### Post by khc on 2005-05-14
sudo apt-get install cvs
cvs -z3 -d:ext:anoncvs@savannah.nongnu.org:/cvsroot/orinoco co orinoco
make
sudo make install

Note that you need to do:
make clean && make install

Every time the kernel is upgraded.

---

### Post by svref on 2006-02-27
This is a metaphorical sketch of the steps involved, the real steps involved are downloading and buiding a custom kernel, making the orinoco driver roughly as above (passing it the path to the kernel build tree as an argument), and then installing both, right?

---

### Post by svref on 2006-02-27
More explicit HOWTO here:

[http://ubuntuforums.org/showthread.php?p=777397#post777397](http://ubuntuforums.org/showthread.php?p=777397#post777397)

---

