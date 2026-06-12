---
title: "Ubuntu &amp; Zimbra"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Coinnach on 2007-03-30
Hi guys,

Wanted to find out if anyone has managed to get Zimbra (32bit app) running on Ubuntu 6.10 i686 architecture.

I have been trying unsuccessfully to get it to install - keeps throwing back an architecture mismatch.

I found this article on running zimbra in a chroot jail but I can't get it to install or work.

Any one any suggestions?

Also can anyone make any recommendation for an easy to install/manage open source email server suite?

Thanks in advance

---

### Post by haelters on 2007-03-30
Done it without any problems. Are you using AMD64 ? Can you give the complete error message ?

---

### Post by Coinnach on 2007-03-30
Hi mate, yes using AMD 64 

- error message is

When I get to the "The system will be modified. Continue? [N]" I type Y and hit enter. Next I see

"Removing /opt/zimbra
Installing packages

zimbra-core.........zimbra-core_4.5.3_GA_733.UBUNTU6_i386.deb...FAILED ###ERROR###

zimbra-core_4.5.3_GA_733.UBUNTU6_i386.deb installation failed

Installation Cancelled"

From the log file in /tmp I get

"dpkg: error processing ./packages/zimbra-core_4.5.3_GA_733.UBUNTU6_i386.deb (--install):
package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
./packages/zimbra-core_4.5.3_GA_733.UBUNTU6_i386.deb"

Anyone have any suggestions as to what I can do.

Thanks

---

### Post by haelters on 2007-03-30
then this is the problem. You cannot install i386 packages on an AMD64. There are some sites that describe the process of installing zimbra on an AMD64, but they have changing luck. The easiest solution for the moment (in my humble opinion) is to install zimbra inside a virtual machine (I did this when I installed on an AMD64 - I used VMPlayer on an existing vmware image for Ubuntu server - see [http://www.vmware.com/vmtn/appliances/](http://www.vmware.com/vmtn/appliances/))

---

### Post by Coinnach on 2007-03-30
Thanks Haelters, is there a "HowTo" anywhere on how to complete that type of setup - sorry I am new to linux.

---

### Post by JNowka on 2007-03-30
If you say you are using the i686 arch, makes me wonder.  Did you install the 64bit version of Ubuntu, or the 32bit version.

If you didn't install the 64bit version I would suggest using "sudo" infront of the command.  /opt/ is a directory that only root can write to.  Hope this helps.

---

### Post by Coinnach on 2007-03-30
Hi JNowka, I did install 64bit 6.10. I am running the script as root so shouldn't be a problem with /opt.

I did try the chroot method mentioned here - [http://www.zimbra.com/forums/archive/index.php/t-7107.html](http://www.zimbra.com/forums/archive/index.php/t-7107.html) - but to no avail still wouldn't install. Frustrating that Zimbra don't have a 64 bit build.

---

### Post by JNowka on 2007-03-30
Im not sure how far you have gotten with setting up your distro, but for now even with the 64bit version of ubuntu out, it is better to go with the 32bit version.  Basically there are more programs working on it, and it works just as good from what I hear.  If you decide to stay with the 64bit version then you will need to either find source code for the program and compile it from source, or run it in a virtual machine.  As for a howto, I would look up vmware under the tips and tricks section on the ubuntuforums main page.

---

