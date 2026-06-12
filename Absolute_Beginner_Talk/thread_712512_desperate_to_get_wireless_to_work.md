---
title: "desperate to get wireless to work"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by eshell189 on 2008-03-01
Hi, last night I gave up on Windows and installed Ubuntu on my laptop (HP dv2000) with a Broadcom 4321AG adapter. Everything works great and I was really impressed with Ubuntu, except that I just can't get the wireless to work. I have been reading and trying to figure out this general linux thing and NDISwrapper stuff for about 12 hours, and I'm just extremely confused about everything. I can't figure out how "mount" the driver to NDISwrapper, or how to turn the driver into a .INF file or anything. I just don't know what to do, or where to start. I know absolutely nothing about linux at all, so if anyone can help, I need to be started from scratch, with everything in plain English. I really like Ubuntu but I'll have to get rid of it if I can't install wireless! Help!

---

### Post by Sam Lars on 2008-03-01
Glad to hear that you like Ubuntu.
When you installed Ubuntu, could you see the card at all in Network Preferences, etc?
Do you have ndisgtk installed?  You can run
```
sudo apt-get install ndisgtk
```
in a command line or search for it in Synaptic to install it.
Once it is installed, it should be in the menus somewhere.  You will need your drivers for the wireless from Windows.  Open Ndisgtk and use it to add your Windows drivers.

---

### Post by Papa-san on 2008-03-01
My signature line has some useful links in it. 
once you determine which driver you need, use your windows disk to dig it up. It will be part of an .exe file. Right click on that .exe and make it a .zip. then extract it to wherever you want it to be, and you will find your driver. You will need the .inf and the corresponding .sys in whatever directory you point ndis wrapper to. (ndisgtk is incredibly easier than command line work to set up ndiswrapper, so I also recommend it.)

You may need to enable additional repositories for ndisgtk, but I don't specifically remember...

---

### Post by eshell189 on 2008-03-01
Hi, thanks for the speedy response;

I just actually installed that ndisgtk after finding it in the synaptics list thing, but I don't actually know how to get it to run... I installed it, but it didn't appear in any menu...

Also, Ubuntu is not recognizing my adapter at all.

---

### Post by eshell189 on 2008-03-01
Ah! I've found it. However, it requires an ".inf" file to install... I have the wireless driver in .exe format, so how do I get it to .inf format?

---

### Post by spiderbatdad on 2008-03-01
There is a tool in synaptic called cabextract that might solve that for you...though I thought the idea of ndiswrapper was to use .exe files...what do I know? But cabextract will remove the .exe (wrapper) so you can look at the files inside.

---

### Post by uberlube on 2008-03-01
the .exe file is actually a .bin file that can be extracted. Try my How to guide for broadcom chips:
[http://ubuntuforums.org/showthread.php?t=706034](http://ubuntuforums.org/showthread.php?t=706034)

---

### Post by Sam Lars on 2008-03-01
Yes, run the .exe, and you should find the .inf where it "installs" to.

---

### Post by eshell189 on 2008-03-01
Uhhh... When I run the .exe, I just get a message stating that it can't be opened...

Also, cabextractor doesn't seem to work either, I can't open the zip or the exe with that program.

Is there no way to get an inf file out of this exe?

I apologize for my incompetence... Im trying very hard haha

---

### Post by uberlube on 2008-03-01
Did you give my HOWTO a try in my last post? It give simple instructions on how to extract that file and everything else you need to do to install the driver

---

### Post by eshell189 on 2008-03-01
I didn't try it because it looks like all that terminal stuff is for different drivers, and it all looks very confusing to me... is there anything I need to change when i input that stuff?

---

### Post by eshell189 on 2008-03-01
Eh, Even when I do try it, the first line gives me "permission denied"

---

### Post by uberlube on 2008-03-01
Nope you dont need to change anything in there. just open a teminal and type in 'sudo su' and enter to make it a root terminal. It will prompt you for a password so just type it in and your good to go. Then just copy and paste in one line at a time from my howto. Press enter after each line you put in.

---

### Post by eshell189 on 2008-03-01
well, it didn't work. Everything seemed to be going well, untill the second to last line (the one just above "reboot") gave me some sort of "no such directory exists" error. I rebooted, and still my adapter remains undetected. Am I pretty much screwed?

---

### Post by eshell189 on 2008-03-01
The ndisgtk claims that hardware is present, but thats about it. So now it is detecing SOMETHING, I don't know if it is detecting my wireless adapter, but it knows something is there... not that it helps at all :(

---

### Post by uberlube on 2008-03-01
No your doing something wrong. Are you talking about 'modprobe ndiswrapper'? And what did it say when you typed in 'ndiswrapper -i bcmwl5.inf'

---

### Post by eshell189 on 2008-03-01
Well, when I do "ndiswrapper -i bcmwl5.inf" now, it says "driver bcmwl5 is already installed
"

When I do "modprobe ndiswrapper", it says:" FATAL: Could not open '/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory"

---

### Post by uberlube on 2008-03-01
go into synaptic package manager and install ndiswrapper again. Then repeat modprobe.

---

### Post by eshell189 on 2008-03-01
still gives the same error.

---

### Post by uberlube on 2008-03-01
All I can suggest at this point is trying out this howto. Its the last word on the subject. Other than this I dont know what else to do, Ive never seen that error before. 

[http://ubuntuforums.org/showthread.php?t=574501&highlight=howto+ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=howto+ndiswrapper)

---

### Post by anewguy on 2008-03-01
First, remove any existing drivers from ndiswrapper by doing the following:

sudo ndiswrapper -l

if anything is returned:

sudo ndiswrapper -e  namereturnedabove

when the list is clean:

copy your driver .inf and .sys files to your desktop

sudo ndiswrapper -i drivername.inf

sudo depmod -a

sudo modprobe ndiswrapper

Next, need to be sure ndiswrapper runs at boot (sometimes the -m doesn't seem to take, so I do both):

sudo ndiswrapper -m

cd /etc

sudo gedit modules

add the following to the end of the file:

ndiswrapper

then save and exit

Now, since you are using the Broadcom chipset, you need to disable the delivered dummy driver in Ubuntu:

cd /etc/modprobe.d

sudo gedit blacklist

add the following to the end of that file:

blacklist bcm43xx

save the file and exit.

Next, you MUST reboot.

Now see if your wireless is working.

:)

---

### Post by eshell189 on 2008-03-01
I will certainly try that, but how do I get my driver into .INF or .SYS format? The only format I have it in is the orginal .exe. this is a huge problem that no one can seem to answer, everyone just assumes that I happen to have the .INF of the driver, or that I know how to somehow derive an .INF file from the .exe. Please help!

---

### Post by anewguy on 2008-03-01
Post your driver exe file as an attachment and post here.  I'll go through it and get the files for you and post them back.

:)

---

### Post by eshell189 on 2008-03-02
I keep getting "Invalid File" (yes luck is on my side). Here is a link to the driver... just scroll down to the button that says "download only"

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=us&dlc=en&product=1817074&os=228&lang=en]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=us&dlc=en&product=1817074&os=228&lang=en")

Please... if I can't get this to wok... I have to go back to Windows...

---

### Post by anewguy on 2008-03-02
I  *THINK* I may have the files extracted for you.  In order to post them here, I had to change the file types.  When you download the 1st file, download it to your desktop and rename it to take away the ".tar" - leave the rest of the filename the same.  Do the same for the 2nd file.

Now try the stuff I posted for ndiswrapper and let me know what happens! :)

OOOOOOOOPPPPPPPPPPSSSSSSSSS>>>>>>>>>>>>> Don't use the files - I seem to have somehow gotten the .sys file twice (notice the sizes are the same).  I'll get this corrected in a minute or two.  Sorry!

---

### Post by anewguy on 2008-03-02
Okay, I'm trying to upload the files again.  Follow the instructions in my previous post.

---

### Post by Papa-san on 2008-03-02
Once you get the cd (or whatever) with the '.exe' file showing in a GUI, all you need to do is right click on it and 'open with: archive manager'. Then rename it as a '.zip' file. then extract it. You will be able to dig around and find the .inf and .sys files you need. extract those to wherever it is you want them to be so you can use ndiswrapper. 

(It took me almost a week to figure out how to do this... some people call 'archive manager' by a different name: 'file roller' That little fact kept me stumbling for a while!)

---

