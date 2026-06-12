---
title: "[SOLVED] Help with Qemu 0.9.0"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by ertrules22 on 2007-08-08
I need help installing qemu!!!  I already have the package downloaded, if this is what I need, but I am slightly new to this and need to know where to go from here.  The package I have is called qemu-0.9.0-i386.tar.gz.  If you need any more info I can probably help out with that part!
:guitar:

---

### Post by ertrules22 on 2007-08-08
I really need help with this!  It's not spam (apparently my last post was! :| )  I need this so I can test other flavors of ubuntu without installing on my system.  Please, any help is appreciated!

---

### Post by bwtranch on 2007-08-08
Usually you want to check and see if there's a deb package that you can use. That will take care of any dependencies you may have. If not, then you have to do it the old-fashioned way and it's not always fun. Maybe I'll figure out, (or somebody will tell me)  how to do those little boxes some day, but...

Open a terminal and create a sub-directory under your home directory called qumulll or whatever it's called. Uncompress it to that directory with tar xzf <filename>.tar.gz

Now you have a new sub-directory called <filename>. Change to it and read all the readme and/or install files. Follow that to the letter. Hopefully, there will be a file called configure. Now run

./configure  this won't install anything, it will just check for dependencies and find out if your computer can install the package. You must resolve any dependencies and you may have to do the same as above for the dependency packages.

Now you can run

make

make install

Some packages are compatible with

make check  to test errors  and make clean to get rid of installation files. (or makedistclean is even better.

Now, see if you can run the program. Good luck. :)

---

### Post by ertrules22 on 2007-08-08
I'm not sure exactly how to do what you are saying (I get most of it, and the code box, if that's what you are talking about that you don't know how to do, it is the sharp sign up there when you edit it).  Please explain a little better, thanks for the help, but remember, I am a n00b.

---

### Post by Kralizec on 2007-08-08
All you need to do with the package that you've downloaded is to change directory in terminal to your system root, "/":
```

cd /

```
and untar the archive with super-user priveleges:
```

sudo tar -xvf /path/to/qemu-0.9.0-i386.tar.gz

```
That should do it, as you've downloaded the binary package (precompiled). Hopefully it will work for you; if not you'll have to download the other package and install it manually.

This page should help you set up what you want. [http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/QuickStartGuide]("http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/QuickStartGuide")

---

### Post by ertrules22 on 2007-08-08
Thanks, and then how do I run it after it installs?  Do I use the terminal?  What command is it exactly?
thanks,
ertrules22

edit:
I mean, what do you type at the terminal to run qemu?

---

### Post by ertrules22 on 2007-08-08
I really need to know this one too!  I am bumping it up to the top!

---

### Post by Kralizec on 2007-08-08
First off, you have to create a 'hard drive image'.  Running this command from terminal:
```

qemu-img create -f qcow c.img 3G

```
should create a HD image called c.img that is 3 gigabytes in size.

Then to run qemu, either execute this command from terminal:
```

qemu -cdrom /dev/cdrom -hda c.img -m 256 -boot d

```
to launch qemu using your physical CD-ROM drive as the boot device, booting onto the image you just created and using 256 RAM memory...OR...
Use this command
```

qemu -cdrom install.iso -hda c.img -m 256 -boot d

```
to do essentially the same thing except instead of your physical drive you'll be using the specified .iso file as the boot device.

Once you've installed the OS, you no longer need to specify the boot drive; qemu saves all the information to that HD image, c.img; simply run
```

qemu -hda c.img -m 256

```
after installing to run your system.

***Things to note:***
[LIST]
[*]**install.iso** and **c.img** are just example names, they can be named other things as well (i.e. could be **ubuntu-7.04.iso** and **blahblah.img** instead)
[*]256 is the minimum RAM you should use; if qemu crashes, then 256 is probably not enough and you should allocate more by increasing that value in the command you've issued.
[*]You can make a larger HD image by simply increasing the amount in your 1st command from 3 to whatever you want. You could probably even specify an external device as your HD with something like ```
qemu -hda /media/EXTERNAL_DEVICE -m 256
```
[/LIST]

---

### Post by ertrules22 on 2007-08-08
Hey, thanks, that's exactly what I needed!  Thanks a lot.  It worked perfectly, and now I can test other flavors!  
:popcorn::):KS

---

### Post by Kralizec on 2007-08-08
No problem. I'm glad I could help.

---

