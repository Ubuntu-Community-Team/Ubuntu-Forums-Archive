---
title: "Help with cp command and paths; vmware tools"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by neander on 2006-10-24
I am currenly attempting to solve the nightmare of getting vmwaretools installed with ubuntu 6.06. In the course of my hours long trial, I'm attempting to copy the linux source folder which I downloaded and unzipped.

The linux folder is on my desktop, it's called linux-source-2.6.15

If I'm not mistaken I have to recompile the vmware to match this kernal, as a part of that I need to copy the linux folder to usr/src. But here is my attempt and the failure message:

me@me-desktop:~/Desktop$ sudo cp -R linux-source-2.6.15 usr/src
cp: cannot create directory `usr/src': No such file or directory

What is wrong with the command I'm entering?

Before I added the -R I was getting
cp: omitting directory `linux-source-2.6.15'

It's all guesswork and looking around in these forums.

Thanks

---

### Post by nickburns on 2006-10-24
Here is what to do...

 *vmware-config.pl fails to find the right kernel headers. It cannot find /usr/src/kernel/include and won't proceed to install.

You have a updated kernel, but not the updated kernel headers. You can install them by executing Code:

sudo apt-get install linux-headers-`uname -r`

Now you can succesfully run Code:

sudo /usr/bin/vmware-config.pl

* You don't want to install the kernel headers manually each time there is an update.

There is a package called linux-headers-*** that automatically installs the latest kernelheaders, so you don't need to install them manually each time.

There are 4 flavours of this package: 386, 686, k7, server.

If you don't know wich one you need, execute Code:

uname -r

It will give you something like 2.6.15-26-k7 or 2.6.15-26-686

Now you know the right flavour, install it by Code:

sudo apt-get install linux-headers-***

Replace the * with 386, 686, k7 or server. 

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware")

---

### Post by CatKiller on 2006-10-24
I've never used VMWare, or anything like it, to know if you need to do what you say you need to do. But the command that you're after is **sudo cp -R linux-source-2.6.15 /usr/src**. What you were trying to do was copy that directory into /home/me/Desktop/usr/src, which doesn't exist.

Hope this helps.

---

### Post by nickburns on 2006-10-24
To clairify, installing vm is really simple.  Follow the instructions on my first post and you will have no problems.  

I assume that you have already installed and since your linux kernel was updated you could not open vmware again.  So you just need to apt-get the header files.

If this is a first install, then get the headers first and then go through the install procedure found at the web link.

Good luck...

---

### Post by neander on 2006-10-24
OK, thanks to both of you, the tip re headers was the essential part. Mouse behavior is much improved. However I'd expected to be able to go above 1024x768 screen rex but I can't. There are more options than before and its at 72 MHz not 60...but I sure hope I can push the screen res up somehow? This is a vm running in a windows 2003 server host, the video card supports much higher res there?

---

### Post by neander on 2006-10-24
oh, I just recalled that the vmware tools dumped this to screen during the install, I copied it, but have no idea how to alter the choice it made of [3]...but I'll fish around.

Detected X.org version 7.0.

Please choose one of the following display sizes (1 - 13):

[1]  "640x480"
[2]  "800x600"
[3]  "1024x768"
[4]  "1152x864"
[5]  "1280x800"
[6]  "1152x900"
[7]  "1280x1024"
[8]  "1376x1032"
[9]  "1400x1050"
[10]  "1680x1050"
[11]  "1600x1200"
[12]  "1920x1200"
[13]  "2364x1773"
Please enter a number between 1 and 13:

[3]

---

### Post by nickburns on 2006-10-24
I bit confused about your question.  If you are trying to change the res on the vmware, you need to add two lines to your .vmx file in the vmware folder.

svga.maxWidth = "2560"
svga.maxHeight = "960"

where "2560" and "960" are the max size you would like the vmware to use.

after you restart the vmware, you can change your res

I should mention to, that it is highly recommended to install the vmware tools when you have a working windows os up and running.  To install go to vmware -> install tools.  It will download and install a small tool package that will make you mouse work as it transfers from linux to vmware, and will give you other helpful options.

---

### Post by neander on 2006-10-25
Ummm <g> I'm kind of confused by your reply!

I have vmware tools installed. The screen data I posted is part of what a successful install of vmware tools dumps to the screen.

My issue currently is that I can't get any screen res in ubuntu over 1024x768. I added higher res lines as you suggested to the vmx and it didn't change anything.

I think if there was a way to get back to that console for vmware tools (where the setup apparently auto selected res [3]) I'd be able to fix it but so far I've not discovered the entry point for that. Strangely, the vmware console has no handles for screen res.

---

### Post by nickburns on 2006-10-25
Ok, just so I am clear, vmware is installed and working, with tools. Are you trying to up the resolution on ubuntu desktop or your vmware/windows desktop? 

If it is the vmware, then add the two lines to the vmware file.  Set the values to what you want your vmware screen to be, then boot up your vmware OS and change the resolution with the whole RightClick -> Properties -> Settings ....

If it is the ubuntu resolution that need to be raised, then we need to take a look at one of the xorg config files.  If this is the case, go to your terminal and type:

more /etc/X11/xorg.conf

and then hit enter until you get to a 'Device', 'Monitor' and 'Screen' section.  Copy those lines into your next post and I will gladly help you through it....

You could also copy that file to your desktop, and attach it to your next post, type

cp /etc/X11/xorg.conf /home/youraccount/Desktop/

where youraccount is the name of your login.

Either way let me know....

---

