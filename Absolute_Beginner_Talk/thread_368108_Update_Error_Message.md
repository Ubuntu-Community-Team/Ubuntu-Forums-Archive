---
title: "Update Error Message"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2007-02-22
I was trying to run and install some updates on my laptop, which is running Ubunt Breezy Badger 5.10.  I know it's old but I love this version, and I learned alot from it.  But I am still learning.  So here is my questions:  What does this mean???

W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

This occurred when I was prompted that some updates where ready to download and install.  When I approved for the updates, I got this error message.

---

### Post by tgalati4 on 2007-02-22
You need to update your package repositories!  Try "reload" in synaptic.  It will download the directories for all of the repositories that you have checked in "settings"  be sure to add repositories if you need them.

If that doesn't work then appeal to the ubuntu gods.

ps:  Dapper is safe for consumption.

---

### Post by NeoGreen on 2007-02-23
thanks for the information I will try it.

---

### Post by NeoGreen on 2007-02-23
I know, I know, all my friends are telling me to upgrade to Dapper but I am Breezy and I have to many good and bad memories together.  I tried the reload and got the following message: 

The repository might be no longer available or could not be contacted because of network problems.  If available an older version of the failed index will be used.  Otherwise the repository will be ignored.  Check your network connection and the correct writing of the repository address in the preferences.  

I checked the network connection and it is good. I think I probably need to update the repository address.  The following address is what I have:

[http://www.getautomatix.com/apt/dist/breezy/Release.gpg](http://www.getautomatix.com/apt/dist/breezy/Release.gpg)

Where exactly do I need to go to make this change?

---

### Post by spoot on 2007-02-23
Your repositories are listed in the /etc/apt/sources.list file. Or, but I'm not sure on Breezy's Synaptic version, you might be able to manage repositories easier from Synaptic.

---

### Post by NeoGreen on 2007-02-23
I went into Synaptic, Settings and Repositories.  I found the one a mentioned earlier.  Should I change it to a different one?  Where can I find an updated address for my repositories?  Thanks for the help.

---

### Post by spoot on 2007-02-23
That really depends on what software you are after, you mentioned a Automatix url earlier and it looks like they do not support Breezy. Perhaps they dropped the support in favor of only Dapper and Edgy?

---

### Post by NeoGreen on 2007-02-23
Oh, okay.  So why can't I update to Ubuntu Dapper.  I get the option to update when I get an update message.  But when I try to update I get the error message stated on my first post.  Do you think maybe something is wrong with my repositories?

---

### Post by tgalati4 on 2007-02-24
Time for a fresh start.  Back up your /home data and anything else you want to keep.  Wipe and start with 6.06.1 ISO.  Be sure to check the md5 sum of the burned image using the live CD Check CD option.  You don't want the install to fail due to a wonky CD.

Good luck.  We need you in the fight.

---

### Post by NeoGreen on 2007-02-24
Looks like I may have to do that.  Thanks for the information.:)

---

