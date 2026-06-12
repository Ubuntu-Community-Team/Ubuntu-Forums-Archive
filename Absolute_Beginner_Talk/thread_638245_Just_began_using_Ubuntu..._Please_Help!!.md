---
title: "Just began using Ubuntu... Please Help!?!?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by XtremeBlaze on 2007-12-11
OK, so I've recently made the switch, and I'm liking it a lot! I've got the hang of everything else, but just not installing .tar.gz files... :(

I have 2 on my desktop that need to be installed, and I can't figure out how to do it. I've searched but it's all too hard to understand....

Can someone quickly explain how to do it, preferably using the terminal...?

Thanks in advance for any help :)

---

### Post by taurus on 2007-12-11
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by XtremeBlaze on 2007-12-11
thanks for the speedy reply...!

I have read the whole thing, and the section that suits me says that I need to download some compiler tools using Synaptic. But the only thing is that the computer with Ubuntu on it has no internet connection, and even when I do connect it up to my internet connection I'd have to configure the setting for my modem, and the thread which has my modem in it basically tells me it's gonna be painful setting it up.... :(

Can i get hold of those compiler tools that I need in .deb extension. I'd look for them myself, but I don't know what exact software I'm looking for :confused:

---

### Post by Rocket2DMn on 2007-12-11
You can download the build-essential .deb installer to your working internet connection, then put the file on a USB flash drive and transfer it to your Ubuntu computer.
[http://packages.ubuntu.com/gutsy/devel/build-essential](http://packages.ubuntu.com/gutsy/devel/build-essential)

---

### Post by fenian on 2007-12-11
Another thing to be aware of is that the programs you need to build may require other programs in addition to the compilers.You should look for a read me file in the uncompressed  filder and see if it mentions any dependencies you need.

---

### Post by leeper69 on 2007-12-11
XtremeBlaze 
                        to unpack a tarball.gz file using the terminal first type su. the terminal will ask for your administator password just type in your password. the  type in man tar. this will show you the man page for the tar command. I think the command you are looking for would be typed in as follows.
                                             tar -xvvzf name of file with extentions
here is an example: tar -xvvzf myfile.tar.gz
          hope this helps!

---

### Post by Warren Watts on 2007-12-11
Another thing to consider is if you need to compile the particular applications you have downloaded at all (Assuming they are apps you want to install).

Ubuntu's repository is HUGE, and 9.9 times out of ten, the program you are looking to install is already in the repositories.  If is IS in the repositories, you can use The Synaptic Package Manager or apt-get from the command line to install the application.  You won't even have to bother to try and compile anything or worry about satisfying any dependencies.

---Just my two cents...

---

### Post by XtremeBlaze on 2007-12-12
Thank you Warren Watts, but again no internet connection on my computer so Synaptic is basically useless for me :(

And thank you to everyone else also. I learned the Sudo method for installing .tar.gz files first, but then found the checkinstaller method to be much easier :) it's all good!!

thankyou for all your help, it is much appreciated :) :)

now I just gotta get everything else sorted out and I'll be laughing ;)

---

