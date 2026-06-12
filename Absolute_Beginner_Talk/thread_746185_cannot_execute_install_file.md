---
title: "cannot execute install file"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-04-05
i'm trying to re-install vmware workstation 6 (same versions that i had installed previously) based on this article i found when i first installed it:

[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

since part 1 and part 3 (part 2 doesn't apply to me) under the tarball installation have already been completed from my first installation (nothing was changed since that time) i would assume that running the install script from part 4 should run smoothly. but instead i get an error message in the terminal windows stating no such file or directory- even if i try executing the script directly from the folder... and the syntax i am using is correct since i am copying/pasting directly from the instructions.

any suggestions would be greatly appreciated.

---

### Post by mikeyphi on 2008-04-05
Are you saying that the required files are actually in /usr/bin and won't install?

If so - I'd suggest doing a full reinstall - as per that website

---

### Post by Matt26 on 2008-04-05
i have already tried executing the instructions for the files in /usr/bin but i get the message stating that they have already been installed... and unless i am misunderstanding your suggestion regarding the full reinstall, that is what i am trying to do- workstation has already been uninstalled and i am now trying to install it again.

---

### Post by mikeyphi on 2008-04-05
Sorry - I'm a bit confused now!!
In your first post you said that the file wasn't found? Now you're saying the message is that it's already installed?

You didn't answer my previous question - are the files actually in /usr/bin? Have a look!

The only other cause of problems is that, often, removing non-ubuntu provided software doesn't correctly remove all traces - so it's quite possible that the software is removed but that the system thinks it's still installed! (That's why I suggested reinstalling-following all the steps on that site)

---

### Post by Matt26 on 2008-04-05
sorry, my mistake... the instructions that i had followed which gave me the message stating that the files have already been installed were for part 1 of the installation process... i will review this and the /usr/bin files when i have a chance to... 

unless i am missing something on that page about reinstalling workstation- the instructions that i am referring to are the only instructions that i can see for performing this task.. how else would you suggest i go about the reinstallation process if there are indeed traces of the installation still existing?

thanks.

---

### Post by upthelum on 2008-04-05
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

---

### Post by Matt26 on 2008-04-05
thanks for the link, but i am looking for a way to reinstall workstation, not server (plus it's on ubuntu 7.10, not 7.04)... if i'm not mistaken, their install procedures are not the same...

---

### Post by mikeyphi on 2008-04-06
> **Matt26 said:**
> sorry, my mistake... the instructions that i had followed which gave me the message stating that the files have already been installed were for part 1 of the installation process... i will review this and the /usr/bin files when i have a chance to... 


Any update on files in /usr/bin??

---

### Post by Matt26 on 2008-04-06
yes, the file is there.. by looking at the command (i'm still learning linux command line) i would assume that i am just looking for a file called gcc-3.4 (no folders/directories)...

---

