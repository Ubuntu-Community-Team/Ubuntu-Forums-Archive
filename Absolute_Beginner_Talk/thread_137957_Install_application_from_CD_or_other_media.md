---
title: "Install application from CD or other media"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-01
I am finding it really painful to install Ubuntu applications (packages) that I downloaded using Windows. It seems an Ubuntu user must have internet connection to be able to install packages.

True, I have a dialup connection but I can only use it in Windows not Linux.

What does a confused mind do? Can anyone help me how I can download Gstreamer, for example, using Windows and later install in Ubuntu? If I was able to access internet in Ubuntu, I would not be asking these questions.

---

### Post by swamytk on 2006-03-01
Could you tell me your actual problem in configuring dial up internet connection in Ubuntu? Pl. provide modem model, type also.

---

### Post by AtinLango on 2006-03-01
I use a Huawei Wireless modem which connects from USB on PC to DB9 COM on handset. It came with a CD for Windows driver only.

When I try configuring the modem in Ubuntu, it cannot be detected. Ihave tried using wvdial as well as the configuration tool in GNOME.

At the back of my mind, it is clear that a driver needs to be installed first, unless not in Ubuntu.

---

### Post by aysiu on 2006-03-01
[QUOTE=AtinLango]I am finding it really painful to install Ubuntu applications (packages) that I downloaded using Windows. It seems an Ubuntu user must have internet connection to be able to install packages.[/QUOTE] I feel your pain. That's why a bunch of forum members are working on [this project](http://www.ubuntuforums.org/showthread.php?t=136955).

---

### Post by ivanhelguera on 2006-03-01
You will surely get better answers here, but here's my 2cents: 
If you have the relevant .deb package , you can go to the directory where it is located and issue the command from the command line: 
```
sudo dpkg -i package-name.deb
```
where  package-name.deb is the name of the package. 
The cdrom directory could be /media/cdrom/, so you have to put 
```
cd /media/cdrom/
```
before, if you're installing from cdrom. 
Unfortunately, this approach is much more complicated then the standard one (synaptic or apt-get). This is because sometimes there are other packages that need to be installed in order for a given package to work. They take care of that and download and install all the necessary packages (all you have to do is to confirm that you accept installing the additional stuff). 
The method I mentioned doesn't do this. If  no other packages are required, it will istall the .deb properly. But if it is not the case, things get complicated. Nevertheless, it is very possible to achieve success with this method. (I used it quite heavily in order to install the stuff I needed for my ADSL modem to work)
Best, 
IH

---

### Post by AtinLango on 2006-03-01
I have already tried using "sudo dpkg -i package-name.deb" to install gstreamer bacause I was lucky enough to locate and download the .deb file.

I got down to the bottom of the problem when I encountered dependencies that I could not easily locate on the net for download. Then I gave up.  I beleive if there were no dependencies, I would have succeeded.

You see, when I installed Ubuntu, I could not (and can not) play mp3 because it complains of lack of a decoder. Thats why I was tring to install gstreamer.

---

### Post by AtinLango on 2006-03-01
So, I managed to download "gstreamer-0.8....lame...deb" and its dependency "liblame0_3.96.1-1_i386.deb".

Now when I run

"sudo dpkg -i liblame0_3.96.1-1_i386.deb" followed by "sudo dpkg -i gstreamer-0.8....lame...deb", it runs fine without any errors.

But, how do I run gstreamer now? Where is it anyway?

---

### Post by engla on 2006-03-01
[QUOTE=AtinLango]So, I managed to download "gstreamer-0.8....lame...deb" and its dependency "liblame0_3.96.1-1_i386.deb".

Now when I run

"sudo dpkg -i liblame0_3.96.1-1_i386.deb" followed by "sudo dpkg -i gstreamer-0.8....lame...deb", it runs fine without any errors.

But, how do I run gstreamer now? Where is it anyway?[/QUOTE]
Good, it was successfully installed. But you can't run gstreamer itself, it  is a library of shared code; what it does is giving extra features to totem, rhythmbox and other media apps.

By the way, if you use this excellent site which lists all packages i ubuntu, you can download every package in the repository there!
[http://packages.ubuntu.com/breezy/](http://packages.ubuntu.com/breezy/)
Find the package there, each of them has a download link (you have to take the one for your architecture, i386).

---

### Post by engla on 2006-03-01
[QUOTE=AtinLango]I have already tried using "sudo dpkg -i package-name.deb" to install gstreamer bacause I was lucky enough to locate and download the .deb file.

I got down to the bottom of the problem when I encountered dependencies that I could not easily locate on the net for download. Then I gave up.  I beleive if there were no dependencies, I would have succeeded.

You see, when I installed Ubuntu, I could not (and can not) play mp3 because it complains of lack of a decoder. Thats why I was tring to install gstreamer.[/QUOTE]
Oops, I think you got the wrong package. lame enables you to encode (make) mp3 files. To play them you want gstreamer0.8-mad, found at this link:
[http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad](http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad)

When you have installed that package all your media players should be able to play mp3s

---

### Post by AtinLango on 2006-03-01
engla, thanx for great info. Otherwise I was thinking gstreamer is an app which I just run.

But, are you saying I should download and install gstreamer0.8-mad. If I remember well, it has so many dependencies some of which I failed to locate before. i'll try again.

And I have just visited the repository site you referred to above and looks interesting. I'll get time to re-visit.

---

### Post by swamytk on 2006-03-02
Let me take privilege of suggesting to go for permanent solution of getting your modem working on Linux.
Option 1: Pl. post the output of "lsusb" command. Check for the entry of your modem in it. If it is 3410 model, you have already driver available in the linux.
Option 2: In case of Option 1 not possible, you can go for ndiswrapper (which will use windows driver to install in linux).
Come on, let us solve the issue. Post your lsusb output.

---

### Post by AtinLango on 2006-03-02
Output of "lsusb" is:

Bus 005 Device 001 : ID 0000:0000
Bus 004 Device 001 : ID 0000:0000
Bus 003 Device 001 : ID 0000:0000
Bus 002 Device 001 : ID 0000:0000
Bus 001 Device 001 : ID 0000:0000

So I cant see "3410" there.

I type ndiswrapper, it says bad command, or something? I guess I have to do some research on ndiswrapper.

---

### Post by sankz on 2008-07-03
> **AtinLango said:**
> I am finding it really painful to install Ubuntu applications (packages) that I downloaded using Windows. It seems an Ubuntu user must have internet connection to be able to install packages.

True, I have a dialup connection but I can only use it in Windows not Linux.


Hope this helps you...

[http://fasterthanlight.wordpress.com/2008/07/02/install-applications-from-live-cd/](http://fasterthanlight.wordpress.com/2008/07/02/install-applications-from-live-cd/)

---

