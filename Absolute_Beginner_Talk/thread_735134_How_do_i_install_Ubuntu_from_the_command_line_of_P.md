---
title: "How do i install Ubuntu from the command line of PClinux using Unetbootin?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by jlhs1971 on 2008-03-25
Hi all

I tried using PCLinux but did not like it so am trying to return to Gutsy. My problem is that I do not have a CD drive and thus need to use Unetbootin to install Gutsy. I have never used the command line to do this installation (used Windows before) and thus am unable to even launch the Unebootin application. 

Does anyone know of a very simple guide to do this? (N.B. The UNebootin guide merely tells you to launch the application - I can't even achieve that!!)

many thanks in advance!

---

### Post by northern lights on 2008-03-25
From [here]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411")  download the .rpm package. If you still have Windows installed you can also boot that one up and download the .exe file. In both cases, two files are offered to download, check which is i386 and which x64 and choose the respective one.

After running it, reboot. The bootmenu should now have an entry along the lines of "Install Ubuntu 7.10". If you have some basic knowledge of how to format and partition, the unetbootin installer is pretty straight forward. If you don't wanna get stuck with command-line only, make sure to select "Ubuntu Desktop" towards the end of the installation. All other apps/packages you can install from the desktop environment.

---

### Post by jlhs1971 on 2008-03-25
thanks Northern Lights

I do not have windows installed anymore - only PCLinux. So, as I understand it, I download the .rpm file (for some reason I thought it was the .deb file for PClinux) and then how do i launch it from the command line? 

apologies for my ignorance.

thanks

---

### Post by northern lights on 2008-03-25
.deb files are for Debian and Debian-based distro's only. Ubuntu is one of those.

PCLinuxOS is a RedHat-based distro - here you'll need rpm. It should come with redhat package manager (rpm...) and you should be able to open .rpms via a double-click.

I have near zero experience with non-Debian-based distributions - I'm sorry. If double clicking fails, google something such as "rpm PCLinuxOS"...

---

### Post by jlhs1971 on 2008-03-26
Many thanks for your thoughts.


Unfortunately, I have not got very far with this so if anyone else has any further ideas I would be most grateful. 


I am actually really surprised at how difficult it is to do a simple thing such as launch an application.

---

### Post by mangurt on 2008-03-26
Greetings,
Here's a few questions:
Did you download the .rpm file?  If so, try right clicking on the file and open with package manager (should be the top choice).  From there you should be able to run the application.
Hope that helps.

---

### Post by jlhs1971 on 2008-03-26
Thanks

.rpm file has been downloaded. Right clicking on it brings up a menu with the first item being "Open". If I press this, it asks me which application to open with.

---

### Post by northern lights on 2008-03-26
obviously, you wanna choose to open with whatever package manager PCLinuxOS ships with...

[EDIT]googled it (might wanna try that once in a while also...):

Your distro ships with APT.

Needless to say, open the .rpm with APT...[/EDIT]

---

