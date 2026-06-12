---
title: "GhostScript..."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Niloc on 2007-05-18
I have a Canon LBP1210 laser printer which I want to use with Ubuntu 7.04.
The Canon driver says I must first install GhostScript but where do I find it and which version do I use?

---

### Post by Najand on 2007-05-18
You don't need ghostscript. Just download CNCUPSLBP2900CAPTK.ppd from the link in [http://openprinting.org/show_printer.cgi?recnum=Canon-LBP-1210](http://openprinting.org/show_printer.cgi?recnum=Canon-LBP-1210) and install it using 
System -> Administration -> Printing

---

### Post by Niloc on 2007-05-18
Well I tried that and all I ended up with is  	Driver.tar.gz, not the PPD file I was expecting, this file does not seem to contain what I need.
What do I do now?

---

### Post by Najand on 2007-05-19
Did you read the instruction at:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)
It is almost the same as LBP 2900!

---

### Post by notepad on 2008-01-21
the following is exactly what i did to setup my LBP-1210 printer on Ubuntu 7.10.
it is based on the instructions at 
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)



go to [http://software.canon-europe.com/products/0000525.asp](http://software.canon-europe.com/products/0000525.asp) and download
the Canon CAPT Printer Driver for Linux (1.30)

the filename is Driver.tar.gz

please note that the canon website mentions that you must install ghostscript
for the driver to work. ignore this. you do not need to install ghostscript.



double click on the driver file you just downloaded. it is a tarred gunzip archive
which will automatically open with file roller when you double click on it.

hit the extract button to extract the contents of the archive to your desktop.



use a program called alien to convert the extracted files into debian
packages. first need to install alien since it doesnt come with ubuntu.

run a terminal by going to Applications > Accessories > Terminal

type the following command;

sudo aptitude install alien

follow the prompts in the terminal to proceed with the installation. note that i needed
to insert my ubuntu 7.10 cd to complete the installation so have yours ready.



now use alien to convert the *rpm files to the *.deb files that we need.

note that the following commands depend on you having extracted the contents of
the driver archive to your desktop;

cd Desktop/Driver
sudo alien -c cndrvcups*
sudo dpkg -i *.deb



stop cupsys with the following command;

sudo /etc/init.d/cupsys stop



change some permissions with the following commands in your terminal;

sudo chmod 777 /var/ccpd/fifo0
sudo chmod -R a+rX /usr/share/cups/model



restart cupsys with the following command;

sudo /etc/init.d/cupsys start



register the printer driver;


sudo /usr/sbin/lpadmin -p LBP1210 -m CNCUPSLBP1210CAPTJ.ppd -v ccp:/var/ccpd/fifo0 -E
cd /usr/share/ppd
sudo ln -s /usr/share/cups/model/CNCUPSLBP1210CAPTJ.ppd


at this point there is one command on the original howto that I did not follow
yet my printer works. the command was listed as follows;
sudo /usr/sbin/ccpdadmin -p LBP1210 -o /dev/usblp0



edit the ccpd script and backup the original one. issue the following commands;

sudo mv /etc/init.d/ccpd ccpdold
sudo gedit /etc/init.d/ccpd

copy and paste the following text into the gedit window;

#!/bin/sh
#
# ccpd          startup script for Canon Printer Daemon for CUPS
#
#               Modified for Debian GNU/Linux
#               by Raphael Doursenaud <rdoursenaud@free.fr>.

DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"

test -f $DAEMON || exit 0

case $1 in
  start)
        echo -n "Starting $DESC: $NAME"
        start-stop-daemon --start --quiet --exec $DAEMON
        echo "."
        ;;
  stop)
        echo -n "Stopping $DESC: $NAME"
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        echo "."
        ;;
  status)
        echo "$DESC: $NAME:" `pidof $NAME`
        ;;
  restart)
        echo -n "Restarting $DESC: $NAME"
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        sleep 1
        start-stop-daemon --start --quiet --exec $DAEMON
        echo "."
        ;;
  *)
        echo "Usage: ccpd {start|stop|status}"
        exit 1
        ;;
esac

exit 0



save the file and close gedit. give execution rights to the script file;

sudo chmod a+x /etc/init.d/ccpd




now start the ccpd daemon and set it to start automatically when the system starts;

sudo /etc/init.d/ccpd start
sudo update-rc.d ccpd defaults 20


add 2 lines to our usr.sbin.cupsd file;

sudo gedit /etc/apparmor.d/usr.sbin.cupsd

scroll down to find the following section:

/var/run/avahi-daemon/socket rw,
/var/run/cups/ rw,
/var/run/cups/** rw,
/var/spool/cups/ rw,
/var/spool/cups/** rw,

underneath those lines we add the following 2 lines;

# needed for Canon CAPT driver
/var/ccpd/** rw,

now it should look like this:

/var/run/avahi-daemon/socket rw,
/var/run/cups/ rw,
/var/run/cups/** rw,
/var/spool/cups/ rw,
/var/spool/cups/** rw,
# needed for Canon CAPT driver
/var/ccpd/** rw,

save the file and close gedit. then issue the following command;

sudo /etc/init.d/apparmor restart



turn off your printer and reboot your system. 


After your system has restarted and you are logged in, turn your printer back on.

You may receive a message from gnome/ubuntu saying that it has installed your LBP-1210 using
LBP-1100 drivers. Ignore this message and do nothing about it.

now check our installation by issuing the following command;

sudo ccpdadmin

the output from ccpdadmin should look like this:

Usage: 
  ccpdadmin [-p Printer-name -o Printer-dev-path]
  ccpdadmin [-x Remove-Printer-name]


 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 39787

 Entry Num  : Spooler   : Backend       : FIFO path             : Device Path  : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP1210   : ccp           : /var/ccpd/fifo0       : /dev/usblp0  :


Now issue the following command in your terminal;

captstatusui -P LBP1210

this should bring up a window which after a short time will say "Ready to print"



since we ignored the printer that gnome/ubuntu installed, there will be 2 printers available
to print to in your print dialogue when you try to print something. remember to select 
LBP1210 and not the printer that gnome/ubuntu installed. enjoy your printer its done!

---

