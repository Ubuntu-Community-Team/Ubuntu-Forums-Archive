---
title: "wireless adapter"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-12-22
I know Ubuntu is a community project, and that I should not raise a beef about documentation, but, I've spent half an hour now, having installed 7.10 as a fresh install, looking for some means by which to get my N1 Wireless adapter driver loaded properly.

In previous versions, I used Automatx2, the process was graphical and a snap.

I want to bypass Automatx this time (not certain it even serves that function anymore), but, for the life of me, I cannot find a straightfoward explanation as to what I am supposed to do.

A search in this forum led me to a link where it is recommended that I download the package, but, as I browse through Synaptic, I see that the package is already installed (how come a search on NDIS doesn't take me to that point in the list of packages??).

So, since it is already installed, what do I do to invoke it?

It isn't in any of my drop down menus.

What should I do next?

I'd be happy to do this on my own - I just don't see any documentation out there.

This is a fairly common requirement, I would think.  I'm surprised not to find more info on the forum.

Thanks for any help - I'd pull my hair out, but there isn't much left.

Caruso

---

### Post by carusoswi on 2007-12-22
I should have mentioned that I have used the "Windows Wireless Drivers" to install the driver for the wireless adapter.  The driver shows up under the Currently Installed Drivers and hardward shows as "present."

How do I make it work.

If I run iwconfig, the adapter does not show up.

Caruso

---

### Post by TheGreatSage on 2007-12-22
Did you install the 'windows drivers' with ndiswrapper ?

I am a linix noob, but I spent most of yesterday installing my wireless adapter.

---

### Post by anewguy on 2007-12-22
It would appear you are using ndiswrapper to load the Windows driver for your wireless adapter.  To further help you, can you post back the type of wireless adapter you have?  Also, after having run  "sudo ndiswrapper -i xxxxxxx"  where xxxxxxx is the Windows driver, I assume you also did a "ndiswrapper -l"  (lower case "L") to list what ndiswrapper knows about?  Did that list show more that just the driver you loaded?  If so, you'll need to "sudo ndiswrapper -r xxxxxx"  where xxxxxx is the name of the "extra" in the list until you are down to a clean list.   Some drivers, such as those for Broadcom 4300 series wireless cards, also require that you blacklist the existing driver so that the driver loaded by ndiswrapper is used instead.

Please post back with any info/questions you may have on the above, and then we can try to get you going!:)

---

### Post by carusoswi on 2007-12-22
Thanks for the reply, anewguy.  My adapter as a Belkin N1.  When I run ndiswrapper -i netmw245, I get a message that the driver is already installed.  When I use the list command, I get a message showing that driver, only that driver, and a message that the hardware is present.

What else do I need do?

Thanks again.

Caruso

---

### Post by anewguy on 2007-12-22
Do you have a network icon on the top bar?  It may look like a terminal with a line through it.  Click this and see if your network is listed.  If so, click the dot in front of it.  This will bring up the connection box - if you need a network password, etc., it will go on this screen (watch the 128-bit encryption default -> my router by default was using 64-bit encryption so I had to change the screen to 64-bit and enter the key.

If you do not have a network icon on the top bar, check via synaptic package manager that the package "network-manager" (might be called network-manager-gnome) is installed.  If not, install it.

If your network doesn't show, try the following:

via sudo ndiswrapper -r xxxxxxx, remove all drivers from the list from ndiswrapper -l

sudo ndiswrapper -i xxxxxx   install your driver

sudo ndiswrapper -l  list to be sure the driver shows

sudo depmod -a

sudo modprobe ndiswrapper

sudo modprobe ndiswrapper -m


If none of this seems to work, post back again with what failed/didn't work and we'll go from there.

Do be aware that most Windows wireless drivers that I have seen are a compressed executable file.  You will need to decompress it, then use the uncompressed files to load the driver.:)

---

### Post by anewguy on 2007-12-22
BTW - I assume that when you said "ndiswrapper -i netmw245" that you just didn't show the ending ".inf" ?  Every driver I have worked with with ndiswrapper has ended in ".inf", so in your case I would assume it would be "netmw245.inf".  If this is a ".exe" file, then it is the compressed executable containing the driver and other things, and you must extract just the driver files from that.  I have had good luck doing this by right-clicking the file and opening with another application and specifying "Archive Manager".  Then in the window I look for a folder, usually called "driver" or "DRIVER" or something similar to that.  In that folder you normally find the .inf, .sys and possibly .cat files needed.  Normally I would just highlight all the files in that folder and extract to the desktop, then run the ndiswrapper -i specifying the .inf file from there.:)

---

### Post by carusoswi on 2007-12-23
> **anewguy said:**
> BTW - I assume that when you said "ndiswrapper -i netmw245" that you just didn't show the ending ".inf" ?  Every driver I have worked with with ndiswrapper has ended in ".inf", so in your case I would assume it would be "netmw245.inf".  If this is a ".exe" file, then it is the compressed executable containing the driver and other things, and you must extract just the driver files from that.  I have had good luck doing this by right-clicking the file and opening with another application and specifying "Archive Manager".  Then in the window I look for a folder, usually called "driver" or "DRIVER" or something similar to that.  In that folder you normally find the .inf, .sys and possibly .cat files needed.  Normally I would just highlight all the files in that folder and extract to the desktop, then run the ndiswrapper -i specifying the .inf file from there.:)

Thanks for your help.
I'm not new to Ubuntu - have used 6.04, 6.10, 7.04, and now 7.10.  Had this wrapper thing solved with this wireless adapter through three previous versions - don't know why I'm having problems now (I used automatx previously - no automatix on this install).

Yes, my driver file is a driver file and includes the extension .inf.

When I run ndiswrapper -l, my driver shows, and hardware is shown as present.

However, when I run modprobe, I receive a fatal error stating that ndiswrapper was not found.  How could that be?

I am obviously doing something wrong.

Any further suggestions?

Thanks.

Caruso

---

### Post by carusoswi on 2007-12-23
Uninstalled the driver.  Copied the contents of my Belkin installation disc driver folder to a new folder on the desktop.  Installed the driver from that folder.

Same result.

When I list the drivers, the Belkin driver shows up followed by a message that the hardware is present.

Run the modprobe command, Fatal error, module ndiswrapper not found.

Doesn't make sense to me.

Caruso

---

### Post by anewguy on 2007-12-23
I know this is a real pain, but could you do the following and then copy/paste the terminal window data back here?

Using ndiswrappe -r, clean out any existing drivers.

Re-install the driver using command line ndiswrapper, including the depmod and the modprobe.

Maybe from the copy of the terminal window stuff I will be able to tell what's going on.

Obviously ndiswrapper is there - it just isn't being found by modprobe.

---

### Post by carusoswi on 2007-12-23
Ok.  Tried a few things (don't laugh, I'm pretty ignorant).  Here it is . . . see for yourself and tell me what I'm doing wrong:

jcalloway@Caruso:~$ sudo ndiswrapper -r netmw245
[sudo] password for jcalloway:
jcalloway@Caruso:~$ ndiswrapper -l
jcalloway@Caruso:~$ sudo ndiswrapper -i netmw245
installing netmw245 ...
couldn't open netmw245: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
jcalloway@Caruso:~$ ndiswrapper -l
jcalloway@Caruso:~$ sudo ndiswrapper -i netmw245
installing netmw245 ...
couldn't open netmw245: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
jcalloway@Caruso:~$ ndiswrapper -i /home/jcalloway/Desktop/Belkin/netmw245.inf
driver netmw245 is already installed
jcalloway@Caruso:~$ sudo ndiswrapper -r xxxxxxx
couldn't delete /etc/ndiswrapper/xxxxxxx: No such file or directory
jcalloway@Caruso:~$ sudo ndiswrapper -r netmw245.inf
couldn't delete /etc/ndiswrapper/netmw245.inf: No such file or directory
jcalloway@Caruso:~$ 


Thanks.

Caruso

---

### Post by anewguy on 2007-12-24
Okay, it's easy to straighten out this part!  First of all, as you learned, when you install the driver with ndiswrapper you needed to have the ".inf" on the end of the file name - that's why it gave you the error at line 181 in ndiswrapper.  Then you tried to remove but unfortunately you left the "xxxxxxxx" string as-is instead of putting in the driver name.  Lastly for some reason it seems to the driver is already installed.

So, based on what you typed in, here's is what I would do - some of these may say something like file not found, but don't worry about that:

sudo ndiswrapper -l 

to list what is know to ndiswrapper again, and again delete any that show via repitition of:

sudo ndiswrapper -r <driver name that shows in list>  <- please be sure to put the actual name that shows in the ndiswrapper -l here.  For example, sudo ndiswrapper -r netmw245    

do this for each item that shows in a ndiswrapper -l until the list returned is blank.

Now let's set the working directory to the directory you have the driver stored in:

cd /home/jcalloway/Desktop/Belkin  


Now, install the driver again:

sudo ndiswrapper -i netmw245.inf

Now check to be sure ndiswrapper knows the driver:

sudo ndiswrapper -l

Then:

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m


Now see if things are working okay.:)

Don't worry about being ignorant - that just means you don't know yet.  We all started there, and believe me I am still very ignorant about large portions of Linux/Ubuntu!

---

### Post by anewguy on 2007-12-24
Be sure to post back if you have more problems/questions or if it works.:)

---

### Post by anewguy on 2007-12-24
Oooppppssss - ignore this (I was stupid and started replying again).

---

