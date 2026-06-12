---
title: "Installing from a windows disk"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-05
While I am online let me ask this as well.

Being unable to get on internet with Linux/Ubuntu, I am trying to update and install new applications via windows.

Here is what I do. I download with XP and add the files on a windows (NTFS) disk. I restart my PC into Linux. Mys disks are already mounted. So I look for the file on the NTFS drives. Then what?

Get-apt does'nt seem to be suitable, unless I am completely wrong about it. My files is in .tgz or something, and hopefully it will solve some of my harware problems, like the onboard sound from Intel, or so the website says. I choose the Red Hat driver, would that be OK?

To get online I need to do the following. Sorry if it sounds "windowy," but this is it.
Get USB going. (My USB scanner is OK, so I guess that's solved.)
Get Bluetooth Widcomm going.
Add Bluetooth modem
Add drivers for my cell phone. (I use it to access Internet.)
Set up dail-up
Hopefully then I should be able to do get-apt.

---

### Post by jkndrkn on 2005-07-05
You need to mount the NTFS disk. This will let you read (but not write) to data on that disk.
Once you have mounted it, you can copy files over from the NTFS disk as needed.

Here is how you can do that:

[http://ubuntuguide.org/index.html#mountunmountntfs](http://ubuntuguide.org/index.html#mountunmountntfs)

---

### Post by GrootBrak on 2005-07-05
[QUOTE=jkndrkn]You need to mount the NTFS disk. This will let you read (but not write) to data on that disk.
Once you have mounted it, you can copy files over from the NTFS disk as needed.

][/QUOTE]

Yeah the copy bit I have under control, what then? How do you install the app? Its not as easy as modern day windows. All the install guides use apt-get install *program* but there is a bunch of files on the installation and its not like there is one that says "install" or "setup" like with windows.

---

### Post by jkndrkn on 2005-07-05
Oh.

They are all tar.gz files?

You need to untar them, enter the directory they spit out, and then read each respective README file using cat or pico or gedit or whatever. Most of them will then tell you to run make and then make install. This will install the files.

---

### Post by senning on 2005-07-05
[QUOTE=GrootBrak]Yeah the copy bit I have under control, what then? How do you install the app? Its not as easy as modern day windows. All the install guides use apt-get install *program* but there is a bunch of files on the installation and its not like there is one that says "install" or "setup" like with windows.[/QUOTE]
 tgz files are zipped files which (if you got them to install a program) are probably the source code with which you can compile the program.  If you are using Ubuntu Hoary, the current stable release, you should look at [http://archive.ubuntulinux.org/ubuntu/pool/](http://archive.ubuntulinux.org/ubuntu/pool/) .  Unfortunately, if you are searching in windows, you will have to look through each of main, multiverse, restricted and universe manually, but if you can get the internet working on Ubuntu, you can use Synaptic, which will also obviate the next step.
Once you have the package you want, go to console and type sudo dpkg -i (your package) .deb and it should be installed.

---

### Post by knewbix on 2005-07-05
From a fellow n00b who had a lot of problems connecting (k)ubuntu to the net via dialup: How are you trying to connect exactly? Do you have a winmodem? I would really hang in there and try to get internet working because the beauty of apt-get is that it d/ls all the dependencies for you. If you manually install stuff, I'm sure you will end up in a seemingly endless loop of manually downloading dependencies, and a lot of rebooting into Windows (or whatever you use to connect) and so forth and so on. 

[These](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialup%29) are the exact instructions that helped me out, but I suspect you would have tried that already. Maybe it helps though. Good luck.

---

### Post by GrootBrak on 2005-07-05
[QUOTE=knewbix]From a fellow n00b who had a lot of problems connecting (k)ubuntu to the net via dialup: How are you trying to connect exactly? Do you have a winmodem? I would really hang in there and try to get internet working because the beauty of apt-get is that it d/ls all the dependencies for you. If you manually install stuff, I'm sure you will end up in a seemingly endless loop of manually downloading dependencies, and a lot of rebooting into Windows (or whatever you use to connect) and so forth and so on. 

[These](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialup%29) are the exact instructions that helped me out, but I suspect you would have tried that already. Maybe it helps though. Good luck.[/QUOTE]
 I use a seperate PC(laptop) to download on the LAN. At home, I'm stuck with a cellphone and GPRS. Max download speed 28.8kb/s. (The LAN is only faster late afternoon...) That is the best for fixed line as well in this country. If you are very close to an exchange, in my case ****NOT*** you can get up to 56kb/s. The broadband option is very expensive. In fact it is the most expensive broadband country in the world. I am not yet sitting in 3G coverage.... Darn.

---

### Post by knewbix on 2005-07-05
Sorry, man. I was referring to how did you try to connect to the net via Linux? (I am stuck on dialup too at the moment) I have no clue about mobile phones & LANs and all that techno stuff. Specifically: what methods did you use to try to connect your dialup to the net in Linux? Is your LAN even using dialup? I guess I am asking you to be more specific. (It helps a lot for people trying to help) :) I'm not sure I can even help but I stand by my post about getting the internet working, it's the only way unless you want to spend a lot of time working stuff out (way more time than the time it takes you to get the internet working) Please answer these questions as best you can, in regards to getting connected:

1 - what methods have you used to try to connect to dialup so far via your own PC? (I'm presuming that is where you use dialup)
2 - do you have a WinModem? A WinModem is an internal chip kinda thing that functions as a modem and you probably won't have much luck getting it to work under Linux.

Also, there is some way to add CDs to your apt-get repository so maybe if you have some other distros lying around, that might help. 

I am a genuine n00b so I hope I helped in some way.

---

### Post by GrootBrak on 2005-07-05
Good heavens, I was being specific!!! But let me go over it again. Currently I have nothing working as internet on Linux. I have an onboard modem, but no phone line. My "phone line" is a cell phone. To connect my cellphone to my PC I have Bluetooth. Specifically the Bluetooth driver is from Widcomm. The Bluetooth dongle sits in my USB port. Widcomm have an excellent "Bluetooth modem" feature for Windows, so I do not even have to have "phone drivers" installed. That's it. It was pretty simple to get it running in windows!

---

### Post by UbuWu on 2005-07-05
You might look into apt-zip, but it doesn't work on windows:
[http://packages.debian.org/unstable/admin/apt-zip.html](http://packages.debian.org/unstable/admin/apt-zip.html)
It is in the repositories.

---

### Post by UbuWu on 2005-07-05
another way would be to download the .deb's from the repositories (see packages.ubuntu.com, download all dependencies as well) and then:

dpkg-scanpackages ./ /dev/null | gzip > Packages.gz

in the package-dir (or somewhere else, to have the packages in a subdir, if you want).

After that you can add this dir (or, after burning, the cd) as repository in sources.lst and use it with apt-get or synaptic.

---

