---
title: "Over a network, printing to Brother MFC 9700 printer connected to Windows XP machine"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by ubjm on 2008-04-01
I just instaled Ubuntu 7.10
I am able to Add Printer and see Brother MFC 9700 printer attached to a Windows XP machine.  
When I print, nothing happens.  The print job just gets spooled locally.


When I checked [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
I saw drivers for RedHat and Debian.    I should choose Debian driver?

I also saw an ominous message:
"For users of Ubuntu based 64bit distributions:
Referenced directories for 32 bit applications has been changed.
Please refer the FAQ for the detail."

which takes me to a FAQ on creating sym links:  
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142)
I am using the 64 bit version of Ubuntu 7.10. I have installed the drivers, but I am still unable to print.


The reference directories for 32 bit applications have changed on the 64 bit version of Ubuntu7.10.
If your version shows the following files after the installation, you will have to make symbolic links for them under /usr/lib32.

Example of the command (Issue the command as a superuser);
ln   -s   /usr/lib/libbrcomplpr2.so   /usr/lib32/libbrcomplpr2.so

List of files required to make symbolic links

    /usr/lib/libbrcompij2.so
    /usr/lib/libbrcompij2.so.1
    /usr/lib/libbrcompij2.so.1.0
    /usr/lib/libbrcompij2.so.1.0.2

    /usr/lib/libbrcompij.so.1
    /usr/lib/libbrcompij.so.1.0
    /usr/lib/libbrcompij.so.1.0.4

    /usr/lib/libbrcomplpr.so

    /usr/lib/libbrcomplpr2.so

    /usr/lib/libbrcompcl1.so
    /usr/lib/libbrcompcl1.so.1
    /usr/lib/libbrcompcl1.so.1.0
    /usr/lib/libbrcompcl1.so.1.0.0





I also found instructions for  [http://vanzante.net/matthew/?p=12](http://vanzante.net/matthew/?p=12)   which is the instruction for Ubuntu 6.


Configuring Brother MFC-9700 in Ubuntu Dapper 6.06.1

   1. First, create symbolic links to facilitate install the lpr driver

      # sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd
      # sudo ln -s /etc/init.d/cupsys /etc/init.d/lprng
   2. Download the lpr driver from here, and the cupsys driver from here (make sure to get the Debian versions for both!!!).
   3. Then, run the following commands to create spooling directories

      # sudo mkdir /var/spool/lpd
      # sudo mkdir /var/spool/lpd/MFC9700
   4. Now, run the following command to install the LPR driver

      # sudo dpkg -i ~/Desktop/mfc9700lpr-*.i386.deb
   5. Now create a symbolic link since the brother drivers expect the cups file to be /etc/init.d/cups instead of /etc/init.d/cupsys

      # sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
   6. Now install the cups wrapper driver.
      #sudo dpkg -i /home/gandalf/Desktop/cupswrapperMFC9700-*.i386.deb
   7. Finally, check the configuration settings via
      System &#8594; Administration &#8594; Printing
      Especially be sure to check the connection tab.

---

