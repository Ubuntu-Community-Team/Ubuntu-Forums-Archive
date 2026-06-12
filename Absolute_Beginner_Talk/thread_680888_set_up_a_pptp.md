---
title: "set up a pptp"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by manzoor on 2008-01-28
how to set up the pptp config software in sourceforge

so that i can connect to the net


I have got a Pentium D 2.66ghz processor

now which file to download here

[http://sourceforge.net/project/showfiles.php?group_id=33063](http://sourceforge.net/project/showfiles.php?group_id=33063)


help please

---

### Post by manzoor on 2008-01-28
help plz

---

### Post by manzoor on 2008-01-28
Hi I'm new to the forums and to Ubuntu and Linux

I discovered the internet connection type of mine :D which was a difficult task for me :)


The pptp client website is in sourceforge

[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)


here it tells that install pptp client but don't tell me how to install it.

Nor I know which files do download for a Intel Pentium D 2.66 ghz processor, Idk which architecture it is i.e. either 64, 386, x86 things :confused:

So some one tell me which files to download and then tell me how to install them after I have downloaded them.

NOTE: I can't connect to the net so I can't download from any repository things in Ubuntu, though I can download the files from Windows and then paste them in Ubuntu drives so I can install them.

thanks for help in advance ;)

---

### Post by jan quark on 2008-01-28
I think it does say how to install it

it says
> Ubuntu Gutsy 7.10

    * install the network-manager-pptp package, using the Add/Remove, Synaptic package manager, or apt-get,
    * click network icon, choose VPN Connections then Configure VPN, then add a VPN with the wizard,
    * click network icon, then VPN Connections then the VPN you created. 

If you have a problem after doing this, watch the logs to see if it worked:

sudo tail -f /var/log/syslog

To increase logging, add debug dump to the /etc/ppp/options and try again.

you have to use either the add(remove application 
or the terminal
to install via the terminal type
sudo apt-get install network-manager-pptp

---

### Post by jan quark on 2008-01-28
here is a great guide how to install anything in ubuntu
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
perhaps it will help you for your future installations:)

---

### Post by emarkd on 2008-01-28
If your Ubuntu computer has no internet connection, you can download the packages you need from [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/) and install them by just double-clicking them from your desktop

---

### Post by manzoor on 2008-01-28
will the terminal download the package

or it doesnt need to download

and by the way which architecture does the Intel Pentium D 2.66ghz has ?

---

### Post by emarkd on 2008-01-28
I don't understand.  What terminal?  I thought you were going to download the package using a web browser and transfer them to your Ubuntu PC.

You have a 64-bit processor but unless you have more than 4 gigs of RAM or really need 64-bit compatibility, I'd recommend sticking to the 32-bit versions.

---

### Post by manzoor on 2008-01-30
which files to download to set up a pptp ?

network-manager-pptp (0.6.5+svnhead2574-0ubuntu1)
pptp-linux (1.7.0-2ubuntu2)

are they equivalent to the 

pptp client in sourcforge ?

[http://sourceforge.net/project/showfiles.php?group_id=33063](http://sourceforge.net/project/showfiles.php?group_id=33063)

i mean are they the same ?

---

### Post by manzoor on 2008-01-30
i downloaded both pptp-linux and network-manager-pptp

but can't install network-manager

it starts installing, after few seconds, the window is gone :(

so when I again open the installer i.e. network manager , to install, the option is still saying

Install Package whereas when I installed pptp-linux and then click the the setup again then the option there was Reinstall Package

so with this observation :) I'm sure that network manager has not been installed

how to install them

and which files to download from sourceforge

[http://sourceforge.net/project/showfiles.php?group_id=33063](http://sourceforge.net/project/showfiles.php?group_id=33063)

which one will work with Ubuntu ?

tg ones ? rpm ? source ?

---

### Post by manzoor on 2008-01-31
i downloaded both pptp-linux and network-manager-pptp

but can't install network-manager

it starts installing, after few seconds, the window is gone

so when I again open the installer i.e. network manager , to install, the option is still saying

Install Package whereas when I installed pptp-linux and then click the the setup again then the option there was Reinstall Package

so with this observation I'm sure that network manager has not been installed

how to install them

and which files to download from sourceforge

[http://sourceforge.net/project/showf...group_id=33063](http://sourceforge.net/project/showf...group_id=33063)

which one will work with Ubuntu ?

tg ones ? rpm ? source ?

---

### Post by manzoor on 2008-02-02
help pleasee

---

