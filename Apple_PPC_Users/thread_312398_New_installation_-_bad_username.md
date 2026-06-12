---
title: "New installation - bad username"
date: 2006-12-04
forum: Apple PPC Users
---

### Post by samden on 2006-12-04
After a long process trying to get Ubuntu installed on my iMac G3, I finally managed to get it to work today. I have no idea why it worked this time, but that is beside the point! I am using the Ubuntu 6.06.1 alternative install cd. However when I reboot the computer and type in my username and password I get the message:

"Incorrect username or password. Letters must be typed in the correct case."  

I cannot believe it is finally installed but it won't let me log in! I have tried every variation on my username and password I can think of that I might have mistyped it as during the installation process, and am still stuck.

What should I do here? I don't want to have to try reinstalling again - who knows if it will work again. I have no idea why it worked this time and don't know whether it will work again. Can I hack into this and change my username and password?

There are a number of threads discussing this in the PC side of the forums (eg [http://www.ubuntuforums.org/showthread.php?t=302090&highlight=incorrect+username](http://www.ubuntuforums.org/showthread.php?t=302090&highlight=incorrect+username)) but they all talk about the GRUB menu etc, and I cannot see how to follow the instructions given on the PPC. Someone who knows more about how ubuntu works on the PPC may be able to see how to modify these instructions for the iMac. Thankyou.

PS. 
For any further info on my installation check the thread [http://www.ubuntuforums.org/showthread.php?t=300122](http://www.ubuntuforums.org/showthread.php?t=300122)

---

### Post by EuroCity on 2006-12-04
IIRC, some keyboard layouts aren't correct in the Alternate installer: for example, for some strange reason, in the "it" layout pressing the Q key gave an A (maybe, thus, Qwerty was Azerty?), or something similar; anyway, I remember that there was a problem like that (only in the installer), when I used an Alternate CD some time ago...

---

### Post by bapoumba on 2006-12-04
Hi, I do not know PPCs, but if you installed the alternate cd, you *should* have given a password. If it is the same as alternate install on a PC, the user is "oem".

If you can login that way, just enter sudo **oem-config-prepare** in a terminal, the oem user will be deleted on next reboot, and you will be prompted to create a new login and password. At least, this is the procedure on a PC ;)

---

### Post by bodhi.zazen on 2006-12-04
Login and password is case sensitive.

Otherwise the information on the thread "Lost username or password !!" is good....

HTH ...

---

### Post by samden on 2006-12-05
> **bapoumba said:**
> Hi, I do not know PPCs, but if you installed the alternate cd, you *should* have given a password. If it is the same as alternate install on a PC, the user is "oem".

If you can login that way, just enter sudo **oem-config-prepare** in a terminal, the oem user will be deleted on next reboot, and you will be prompted to create a new login and password. At least, this is the procedure on a PC ;)

I cannot log in using "oem" as the username.

---

### Post by bapoumba on 2006-12-05
Sorry then. This was just a common problem with users installing Ubuntu alternate on PCs. Cheers.

---

### Post by samden on 2006-12-05
> **bodhi.zazen said:**
> Login and password is case sensitive.

Otherwise the information on the thread "Lost username or password !!" is good....

HTH ...
I am being careful to take the case into account with my username and password. I wish it was a simple error like that... :) 

The information on the thread "Lost username or password" sounds good. However I cannot understand how to boot the computer in rescue mode. I cannot see how to boot in rescue mode from the hard drive. When the computer boots, initially it puts up a small amount of text briefly asking whether to boot from hard drive or cd, this disappears within a few seconds and it starts to boot from the hard drive.

Then I get the prompt "boot:". If I leave this, within a few seconds Ubuntu starts to boot. I can type other things on this prompt. I have tried typing things like "rescue", "boot rescue" etc on this prompt and pressing enter - nothing works. I get a message like
/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:3,\\rescue: No such file or directory
If I press tab at this prompt it only lists the boot option "Linux". After this it says the word "old", but if I type "old" and press enter I get the same message as above.

If I just press enter at this prompt Ubuntu boots and ends up at the screen where I am asked for my password.

What I do not understand is how to boot in rescue mode to start with, so I am able to type in the commands given in the other thread. The other thread simply says "Reboot into rescue mode by selecting it in the bootloader". What I do not understand is where is the bootloader and how do I select rescue mode?

Sorry if this is very simple and obvious.

I can boot the alternate install cd in rescue mode. But it just boots into the installer, and I do not want to install the entire system again. If I need to use the alternative install cd to boot into rescue mode, again I do not know where to type in the commands given in the other thread. And I certainly don't want to install it again and risk messing up this installation, as I have been trying to install for 3 weeks and this is the first time it has worked!

Thankyou for your help. I hope I have explained myself a bit better now.

---

### Post by lucky_chouhan on 2006-12-05
same problem as mine. when i set the username as a root and password is xxxxx then i am not login. then i say new username & password now i am login with root privileges.

---

### Post by samden on 2006-12-05
By the way, the fact that I don't see the grub menu could possibly have something to do with the fact that I have done a clean install of ubuntu to this computer and have no other operating system on it???? :-k

Edit:
Ooops, no Grub - I now know PPC uses yaboot instead.

---

### Post by samden on 2006-12-05
> **lucky_chouhan said:**
> same problem as mine. when i set the username as a root and password is xxxxx then i am not login. then i say new username & password now i am login with root privileges.
Where do you say new username & password? This is what I cannot figure out how to do. Thanks.

---

### Post by samden on 2006-12-05
Hmmm, aren't the x86s using GRUB and the PPCs using Yaboot? When I follow the instructions given in [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) to reinstall grub from the alternative install cd (just because I have no idea what to do so its worth a shot), instead of the option "reinstall grub boot loader" I get given the option "reinstall yaboot boot loader". If I am using yaboot, not grub, the instructions to boot in rescue mode could be completely different to those given to people on x86 computers in other threads. How do I boot in rescue mode with yaboot?

Edit:
Ok, I think I'm starting to understand the problem a little better. Many people have had a similar username / password problem to me when using x86 computers with Grub. Grub allows them to boot in rescue mode and change the username and password this way. This is not very secure but extremely handy! However yaboot does not appear to do this. (refer [http://www.ubuntuforums.org/showthread.php?t=143309&highlight=rescue+mode+yaboot](http://www.ubuntuforums.org/showthread.php?t=143309&highlight=rescue+mode+yaboot) ) I can reinstall yaboot from the cd, but after doing so it still just boots ubuntu and asks me for my username and password, which it will not accept.

I need some way of changing the username and password WITHOUT logging in to the computer first, as I cannot log in without my username and password. Any other threads on this problem appear to be using GRUB, which is irrelevant to my iMac using yaboot.

How do you hack into a PPC install of Ubuntu without the username and password? I am sure someone will have done this before, whether for innocent reasons like my own or for some more interesting purpose! Help, please! There must be some way of doing this from the alternative install cd, but I don't know what it is.

Edit:
I am able to rescue boot using the alternative install cd, and execute a shell to give me access to the command line. When I enter the commands given in previous threads (passwd[username] etc) they do not appear to work, but there may be other commands I can use. I can type passwd, and it allows me to set a new Unix password. I have done this, but I cannot log in to Ubuntu using this password.

---

### Post by samden on 2006-12-05
Frustrating as this all is, it is certainly teaching me a lot about Linux and the command line! The best crash course in Linux is to try and install it!

I can now boot in rescue mode with the alternative install cd, execute a shell on my root file system, and search for users. I am able to edit the root password using the command passwd. But I cannot find the username I entered during installation, nor the password it thinks I used.

The commands I am using are:

passwd [username]
(substituting my username for "username") This returns:
passwd: unknown user [username]
So it does not appear to be recognising the username I entered during the installation process.

I am also using:
cat /etc/passwd | grep [name]
(substituting for name my full name, part of my full name, my username etc). Each time it returns about 20 lines of writing, none of which appears to be related in any way to my username at all. Apparently this command should allow me to hunt for my username, but I am not sure how to use the output.

As my username does not appear to exist any more, I would like to create a new username (a primary user with access to sudo, not a restricted user) and password from the command line. I could then try to log in using this new username and password. How can I add a new user with sudo access from the command line? :-k 

I have tried the command
useradd [username]
but then when I try
passwd [username]
the computer returns
passwd: User not known to the underlying authentication module

Thankyou for your help. :)

---

### Post by samden on 2006-12-06
Another option would be if I could enable automatic login from the command line. This would bypass logging in for me. 

I found the page [http://doc.gwos.org/index.php/Automatic_Login_No_Authentication](http://doc.gwos.org/index.php/Automatic_Login_No_Authentication) which gives instructions on how to do this. So I started up the computer in rescue mode from the alternative install cd, executed a shell on my root file system, and typed in
sudo apt-get install gcc-4.0
(as it couldn't find gcc-3.4)
This seemed to work fine, lots of text streamed up the screen for a few minutes before I had a command prompt again.

Then I opened a terminal, and entered
nano autologin.c
This started a new blank file (I think), and I typed into it:
#include <unistd.h>
int main() { 
execlp( "login", "login", "-f", "your_user_here", 0); 
}
I then entered ctrl-x to save it.

But then when I typed in 
gcc -o autologin autologin.c
the computer returned
/bin/sh: gcc: not found

When I exited the terminal back to the shell and typed in 
gcc -o autologin autologin.c
the computer returned
sh: gcc: command not found

I believe this could be due to the fact that I am running from cd, but the gcc file was saved on the computer hard drive, so Linux can't see where it is. What should I do now?

I could be on the wrong track entirely with these instructions, but they seem good to me. If you have any other ideas please tell me. Thankyou.

---

### Post by samden on 2006-12-08
I can't believe I'm actually saying this after 3-4 weeks of trying but

I HAVE A WORKING XUBUNTU 6.06 INSTALL ON MY IMAC!!! :D 

As you can see I'm rather pleased. I gave up on this password thing and reinstalled the system a number of times until it finally relented and worked. Not on the net yet, but I'm sure that will follow soon. 

Thanks everyone for your help.

---

