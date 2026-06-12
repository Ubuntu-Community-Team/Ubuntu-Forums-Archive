---
title: "Trouble updating firefox and using root terminal"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-02
Hi I have Ubuntu 5.04 and am using the Firefox that came with it but Ebay wants me to update. I have downloaded Firefox from the Mozilla site and read everything in sight about this but I don't know how to install or unpack? to the opt folder. I guess that is with the root terminal but I don't know how to do this. I guss also I have to do it offline? There is just not enough detail in the how to things I have seen/read.

---

### Post by kingmonkey on 2007-02-02
Hoary is no longer supported. 

You need to upgrade to at least 5.10 and in 3 months that wont be supported, your leaving yourself open to security attacks.

You obviously dont like updating a lot therefore I would install dapper which is supported for 3 years, rather than 18 months.

[http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake](http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake)

---

### Post by steve.horsley on 2007-02-02
Press Ctrl-F2 and enter **gksu nautilus**. Use this window to copy the tar.gz file to /opt. Then right-click and extract here. Then you can delete the tarball you just unpacked.

Still using this nautilus window that has root privilege, navigate to /usr/bin and delete (or rename  to firefox-old) the firefox link. 

Still using this nautilus window, pull down File->New Window to get a new window. Use the new window to navigate to the new firefox directory in /opt. 

Using the middle mouse button (or both left and right if you don't have a middle button), drag and drop /opt/firefox/firefox to the old window  on /usr/bin. This pops up a Move/Copy/Link menu - choose Link.

This shoud get your new firefox installed. You may need to instal plugins of course. Come back for specific help on those if needed.

---

### Post by rapattack1 on 2007-02-03
My friend only installed Ubuntu a few weeks ago and I don't have enough ram to go to a higher version. I have installed 6.10 on my primary machine but there is a lot to be done before that one is operational as I am very new to Linux. We had many delays in getting this done as my friends mother was dying over a very long period of time. Hopefully my friend will come soon and get that going so I can ditch this machine but at least I am on the net and surfing without all the windoze crap happening.
Will try what you suggest Steve. Don't worry I don't have much in the way of plugins from memory.
:)

---

