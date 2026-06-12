---
title: "Root Password probs"
date: 2005-06-30
forum: Absolute Beginner Talk
---

### Post by ahluka on 2005-06-30
Hey all,

I've just installed Ubuntu, and created a normal user account for working. However I don't know the password for the root account. If there is a default set could somebody tell me? I wasn't prompted to enter one and certainly wasn't shown one during installation.

Also, how the hell do I install .deb packages? I tried (at a bash prompt) 'dpkg <packagename>' when I went to install gcc 4.0

---

### Post by StacyWebb on 2005-06-30
First:
there is no root accout use 
sudo <command>
password will be the same as your user account 

Second:
use dpkg -i <package-name>

This will install the debs for you

---

### Post by ahluka on 2005-06-30
Ok cheers  ;-)

---

### Post by br14n on 2005-06-30
I also have just installed Ubuntu & have a problem with the password, I cannot use the following :- Update Manager, synaptic, gdmsetup, time & date, users & groups, when I enter my password I get 'child terminated with 1 status' or just nothing!
Also if I try to use sudo I get 'you are not in the sudoers file'
I can find no explanation for this in any searches!
I have now successfully solved thanks to a more focussed search which led me to editing the sudoers file with visudo !
 br14n

---

