---
title: "C compiler cannot create executables"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by latheesan on 2007-10-20
I decided to switch over to linux, Ubuntu in specific after hearing all the good things about it.

My instalation of Gutsy went smooth. Everything worked, except the internet, because getting internet via SpeedTouch ADSL Modem to work with linux isnt straight forward as i thought.

So, I tried this tutorial first:

> [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)
It did not work, so i tried one other tutorial, which is:
> [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
This didn't work either, so i kept searching for solutions and finally landed on something which i thought "might" work, because lots of people have claimed it has.

This last solution i found is called **speedtouchconf** by a dev called **Steve Parker** at [http://steve-parker.org/speedtouchconf](http://steve-parker.org/speedtouchconf)

So i downloaded the latest build and extracted it into :

/home/latheesan/speedtouchconf-dd-mm-yyyy

Then i downloaded the microcode package **rev4fw.zip** into the same directory (because my rev is 4.0).

Then, I got on my terminal, and did the following:

chmod +x speedtouchconf.sh
./speedtouchconf.sh

I got these following errors:

> checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

So i started to look at what could be wrong and i found out that i dont have something called "build-essential", so i downloaded that and extracted it to my home directory again, i did this:

chmod +x configure
./configure

I got another error saying "dpkg" was not installed. So, i downloaded that and tried to install that and i got another error saying "gcc" was not installed. So, i downloaded that and tried to install it and found out there were no "configure" or "make" files in there, so im stuck...

When i say "i downloaded", i mean i switched to my Windows OS and downloaded the necessary files onto my DVD-RW Disk and logged onto Ubuntu and transfered them. If i had internet on ubuntu, i would have simply used:

sudo apt-get install <package name>

Can someone help me with this please :(

---

### Post by steve.horsley on 2007-10-20
Now you're in a jam. The stock answer to your compiler problem is to install package **build-essential** - use Synaptic graphically, or the command line commands:
[B]sudo apt-get update
sudo apt-get install build-essential[/B]
But this requires internet access to go fetch the relevant files. I don't think they're on the installer CD.

build-essential relies on the following packages:
libc-dev or libc6-dev (either will do)
gcc
g++
make
dpkg-dev

Downloading these and double-clicking them to install them will get you there eventually. But it would be easier to borrow an internet connection if possible. Personally, I use an ADSL router with Ethernet port, so I never have problems finding drivers, and can use Macs here too.

---

### Post by latheesan on 2007-10-20
The only "possible" internet borrowing i can do is by using the free WiFi at my university. But then again, i have another problem with that. 

This is how my university setup their network:

1. We connect to their WiFi network
2. Setup a VPN connection with my uni username and password and Dial it after connecting to the WiFi
3. Setup our IE7/FireFox browser to use a certain proxy, so we authenticate our self, EVERY time we open the browser to connect to a site

Is this all possible with Ubuntu?

By the way, what did u mean by this:

> Downloading these and double-clicking them to install them

The downloaded packages are either *.tar.tar or *.tar.gz files, if i double click them, archive manager opens, how do they get installed by double clicking

---

### Post by latheesan on 2007-10-20
I am on this page [http://packages.ubuntu.com/feisty/libdevel/libc6-dev](http://packages.ubuntu.com/feisty/libdevel/libc6-dev) trying to manually download the first package i need. 

I see these two download links:

[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/glibc_2.5.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/glibc_2.5.orig.tar.gz)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/glibc_2.5-0ubuntu14.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/glibc_2.5-0ubuntu14.diff.gz)

Which one do i get? and how do i install from them?

---

### Post by steve.horsley on 2007-10-20
The files you need are .deb files (for the correct architecture of course). Whsn you double-click a .deb file, you get the option to install it.

---

### Post by latheesan on 2007-10-20
I see. Well, it just so happens my friend had a router, so i set it up to install build essentils on my ubuntu. Luckily, with a router, the internet "just works".

So, i went back to my orginal problem and did this:

> chmod +x speedtouchconf.sh
./speedtouchconf.sh

First, it asked for VPI/VCI values. My internet company uses 0 51, so i entered that. Then, it asked for my user/pass to conenct, i also entered those.

Then it asked me, if those variables were correct, i entered Y and hit enter. It loaded the driver and did all the stuff. Then it showed me this error:

> *** Configuration finished. Starting the connection ***

Sat Oct 20 13:06:34 BST 2007
The modem lights should start flashing for approx. 60 seconds...
You might see some messages about USBDEVFS_BULK failed - you can ignore this.
Sat Oct 20 13:06:34 BST 2007
The modem_run command failed (code 235)
modem_run results:
Mutex value not OK
FAILED because of modem_run error 235
latheesan@laptop:~/speedtouchconf-27-Jun-2006$ Oct 20 13:06:34 laptop modem_run[28541]: modem_run version 1.3.1 started by latheesan uid 0 
Oct 20 13:06:34 laptop modem_run[28541]: modem_run version 1.3.1 started by latheesan uid 0

---

### Post by steve.horsley on 2007-10-20
I can't help you with that, and the subject line is now wrong. I suggest you start a new thread with an appropriate title, and see if you can hook up with someone who knows about the speedtouch driver.

---

