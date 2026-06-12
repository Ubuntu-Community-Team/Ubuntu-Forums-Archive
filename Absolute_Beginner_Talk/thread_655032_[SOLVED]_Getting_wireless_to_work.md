---
title: "[SOLVED] Getting wireless to work"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by boballen55 on 2007-12-31
Ok, so I'm new at this and I'm trying to get my DLink DWA-130 USB wireless adapter to work.  I have been attempting to follow the directions for using Ndiswrapper from :

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-4b7c00c6654b2d109b9330c28d9210db329ba573]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-4b7c00c6654b2d109b9330c28d9210db329ba573")

I've figured out I'm supposed to use the drivers from the CD that came with the adapter and I've gotten ndisgtk, the graphics part to show up.  I copy pasted what I am almost certain is the correct .sys and .inf files onto the desktop in Ubunutu then used the "Windows wireless drivers" pointed it to .inf file and it says the driver name and "Hardware present: yes.  Then it does not seem to find the wireless connection.  I've tried restarting, still won't work.  

With my limited knowledge I can think of one or 2 things that likely are my problem.  Either there is another step I need to take to get it to work or I do not have the driver set up enough.  In the directions on the posted page above it states:
"Unpack the Windows driver by using the unzip, cabextract and/or unshield tools (run from the Terminal), and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). You may first need to install cabextract and unshield."

I more or less skipped this step because I don't know how to do those things.  I can open a terminal but I don't know how to use unzip, cabextract or unshield, or even understand what they do.  So I was hoping someone smarter than me could help out with that.

Thanks!

---

### Post by spiderbatdad on 2007-12-31
did you try using ndis-gtk? as suggested in that how-to?

---

### Post by boballen55 on 2007-12-31
> **spiderbatdad said:**
> This might be what you're looking for: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

I pretty sure that site does not help, I'm trying to get a wireless adapter to work, that sounds to me like it is for plugging in directly to the modem.

Also I did type:

ndiswrapper -l

Into terminal and it did not come up with anything.  So I think I need to do the unpacking the Windows driver thing with unzip, cabextract and/or unshield tools.  That is what I believe I need help with.

Maybe what you linked helps somehow but I'd need you to explain it to me a little.

Thanks!

---

### Post by spiderbatdad on 2007-12-31
sorry that was a mis-post. did you try using ndis-gtk as suggested in that how-to?

---

### Post by spiderbatdad on 2007-12-31
sorry I keep posting in between replies.:( did you install cabextract from synaptic?

---

### Post by spiderbatdad on 2007-12-31
i suggest try the graphical method if you are not familiar with the command line. Or read ```
man cabextract
``` then return to the how-to if you want to get more involved with hacking than with getting your wireless going.

---

### Post by boballen55 on 2007-12-31
Ok, well I tried to look at the manual for cabextract and said there was no manual so I assume it is not a package that came on the Ubuntu CD.  So I need help with installing it without an internet connection in Ubuntu.  I managed this some how with ndisgtk, the graphics part of ndiswrapper but now I can't figure out how to get cabextract.  So I need some help, I have a flash drive to bring files over to Ubuntu.

Thanks!

---

### Post by RomeReactor on 2007-12-31
Hi. You can get cabextract [here]("http://mirrors.xmission.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb"). To install it, just double click on the package. Once it's installed, you can then read some of the options you can use with it:
```
cabextract --help
```
or read the full manual:
```
man cabextract
```

---

### Post by zipperback on 2007-12-31
> **boballen55 said:**
> Ok, so I'm new at this and I'm trying to get my DLink DWA-130 USB wireless adapter to work.  I have been attempting to follow the directions for using Ndiswrapper from :



Here are the exact steps I used to get it wifi working on my laptop.

apt-get update
apt-get install wget tar build-essential -y
wget [http://umn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz](http://umn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz)
tar xvfz ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make uninstall
make
make install

cd [LOCATION OF YOUR WINDOWS NETWORK DRIVER]
ndiswrapper -i [NETWORK DRIVER].inf
modprobe ndiswrapper
ndiswrapper -m
ndiswrapper -ma

There is a newer version of the ndiswrapper source available on their website, but when I needed to get my wifi up and running, it wasn't available at that time.

Management of your network connections will be made much simpler if you use WICD instead of network manager.

You can download it from the following URL:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Follow the install instructions on their homepage and it should install without any problems.

Hope this helps you.
- zipperback
:popcorn:

---

### Post by boballen55 on 2007-12-31
Sweet!  I just did a little more experimenting with the help of the page I had in my original post and I finally got it.  Thanks everyone that tried to help me, you really helped me narrow down what I was doing wrong.

Thanks again, the Ubuntu Community is AWESOME!

---

### Post by zipperback on 2007-12-31
> **boballen55 said:**
> Sweet!  I just did a little more experimenting with the help of the page I had in my original post and I finally got it.  Thanks everyone that tried to help me, you really helped me narrow down what I was doing wrong.

Thanks again, the Ubuntu Community is AWESOME!



Welcome to Ubuntu! :) 

- zipperback
:popcorn:

---

### Post by ornespike on 2008-04-22
I've done the above mentioned list but when I restart my machine hags up at ***Starting OpenBSD Secure Shell server sshd**.  Any thoughts?

---

