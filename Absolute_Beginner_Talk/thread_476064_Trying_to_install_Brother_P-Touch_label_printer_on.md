---
title: "Trying to install Brother P-Touch label printer on Ubuntu OS"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by ever_ready on 2007-06-16
I have been trying to install the CUPS driver for the P-touch Printer family. I found the driver on [http://etc.nkadesign.com/Printers/QL550LabelPrinterCUPS](http://etc.nkadesign.com/Printers/QL550LabelPrinterCUPS). According to [http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting) it is the recommended driver for the Brother P-Touch Family label printers.

I have downloaded the  ptouch-driver-1.2.tar.gz
file  and did the following at the terminal
# tar zxf ptouch-driver-1.2.tar.gz
# cd ptouch-driver-1.21
# ./configure

The ./configure fails and gives me the following
ever_ready@HOME:~/Desktop/ptouch-driver-1.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Since the config failed, I can not continue with the rest of the install. I have Ubuntu 7.04 "Feisty Fawn" installed. I have also tried apt-get install gcc and make, both of which I already had installed. So, I do not know where to go from here. I have attached the config.log for review.

I am new to installing applications and drivers in Linux so any help on this printer install would be appreiaciated.

Thanks

---

### Post by ever_ready on 2007-06-17
Well, I sloved my problem with configure: error: C compiler cannot create executables. Read through the forum some more and found I needed to "apt-get install build-essential" to get the proper C compiler and dependencys.  Then I entered "make" while in the directory where the installation files are located. Seem to go fine, but that command ended with make: *** [all] Error 2.

I continued anyway by using "make install" and that commmand ended in
make:*** [rastertoptch-rastertoptch.o] Error 1.

I will not know till I return to work to see if install went alright, printer is at work. Any insight or comment on this install would be welcomed.

---

### Post by jay019 on 2008-02-21
How did you go? Did you get it working?

---

