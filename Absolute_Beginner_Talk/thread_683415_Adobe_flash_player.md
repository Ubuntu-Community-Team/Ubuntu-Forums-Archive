---
title: "Adobe flash player"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by majikhotline on 2008-01-30
thanks to all with the previous help!
I download adobe flash player but dont know how to install it for firefox.
Yes, I'm a newbie so be gentle and need step by step instructions.

thanks

---

### Post by wolfen69 on 2008-01-30
download this [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install. easy enough?

---

### Post by jleaker01z on 2008-01-30
click Applications>Accessories>Terminal

type cd/home/user-name/Desktop/Install_Flash_Player_9  (this is the folder that you extracted

type sudo ./flashplayer-installer

---

### Post by Ainab on 2008-01-31
click system
point to administration
select synaptic package manager
type your root password
click search
enter "flash-nonefree"
in the result select flash-nonefree
click apply
and then you done.

---

### Post by wolfen69 on 2008-01-31
> **Ainab said:**
> click system
point to administration
select synaptic package manager
type your root password
click search
enter "flash-nonefree"
in the result select flash-nonefree
click apply
and then you done.

the help is appreciated, but, 1#, it's nonfree, not nonefree. 2# the MD5 sums do not match if installed in synaptic or apt-get. therefore wont work. see first 2 responses for installation.

---

### Post by Ainab on 2008-01-31
> **wolfen69 said:**
> the help is appreciated, but, 1#, it's nonfree, not nonefree. 2# the MD5 sums do not match if installed in synaptic or apt-get. therefore wont work. see first 2 responses for installation.
it worked for me and second you right is not nonefree (spelling error).

---

### Post by wolfen69 on 2008-01-31
and when did you install it? it had to be a few weeks back. adobe updated flash, and (now) will not work via synaptic. trust me, i do many installs.

---

### Post by Ainab on 2008-01-31
> **wolfen69 said:**
> and when did you install it? it had to be a few weeks back. adobe updated flash, and (now) will not work via synaptic. trust me, i do many installs.
indeed it was months ago. in order to prove your claim I re-installed flash and it did not work.
thanks for clarification.

---

### Post by nicolito on 2008-01-31
Mr. Wolfen... Do you know where to find the nonfree package for x86 64 bit versions of ubuntu? I cant find any working installer for my firefox :(

---

### Post by hyper_ch on 2008-01-31
there is no 64bit flash version as far as I know.

---

### Post by RomeReactor on 2008-01-31
Hi. For Flash in Ubuntu 64-bit, download [this flashplugin-nonfree package]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466"), close Firefox, double click on the package to install, then open Firefox again; Flash should work then. More information on the bug [here]("http://ubuntuforums.org/showthread.php?t=636397").

---

### Post by qazwsx on 2008-01-31
> **nicolito said:**
> Mr. Wolfen... Do you know where to find the nonfree package for x86 64 bit versions of ubuntu? I cant find any working installer for my firefox :(
Install nspluginwrapper and some i32libs  (check depency issues with synaptic) and 32 bit flash plugin. Then you may have to configure  nspluginwrapper via command line and remember to use full path for libflashplayer.so 

How long the package is going to be broken? It is just so much easier with that.

---

### Post by derred on 2008-01-31
download [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.g](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.g) from the adobe website. Extract the archive to somewhere easy to find (I used my home directory). Open a console and "cd" to the flash folder that you extracted(in my case "install_flash_player_9_linux"). then do a "sudo ./flashplayer-installer" to install flash for all the users on the machine. When it asks for a path, use:"/usr/lib/firefox" to enable flash in firefox(just replace firefox with mozilla or opera if you use those browsers)

Hope this helps.:popcorn:

---

### Post by majikhotline on 2008-02-01
thanks derred it works and now i know how to install for the firefox plugins.
thanks again\

---

