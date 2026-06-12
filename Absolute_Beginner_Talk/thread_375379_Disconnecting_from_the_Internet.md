---
title: "Disconnecting from the Internet"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by hakunamatata on 2007-03-03
Hello, I am new to Ubuntu. I have installed 6.10, with Netgear DG834G modem router. Can someone help me with regards to connecting / disconnecting from the Internet. I have checked the modem settings and the idle time out is set to 0, but it could not be modified. I do not wish to remain always connected, but be able to connect/disconnect whenever I like. Is it possible to have a desktop shortcut?
Thank you.

---

### Post by mikewhatever on 2007-03-03
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#modems](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#modems)

---

### Post by hakunamatata on 2007-03-04
Hi, Thank you for the link. Tried the steps under basic procedure. However I do not see the Activate / Deactivate button(?) when I click the Network Connection icon. The connection properties indicate Name: eth0 Status: Idle (!!) I am using PPPoA, if  that is any help. Is GNOME PPP any good -anyone tried it?

---

### Post by mikewhatever on 2007-03-04
Scroll down the page to ADSL section
>    2.

      In the terminal type:

      sudo pppoeconf

   3.

      A text-based menu program will guide you through the next steps, which are:
         1.

            Confirm that your Ethernet card is detected.
         2.

            Enter your username.
         3.

            Enter your password.
         4.

            If you already have a PPPoE Connection configured, you will be asked if it may be modified.
         5.

            Popular options: you are asked if you want the 'noauth' and 'defaultroute' options and to remove 'nodetach' - choose "Yes".
         6.

            Use peer DNS - choose "Yes".
         7.

            Limited MSS problem - choose "Yes".
         8.

            When you are asked if you want to connect at start up, you will probably want to say yes.
         9.

            Finally you are asked if you want to establish the connection immediately.
   4.

      Once you have finished these steps, your connection should be working.

To start your ADSL connection on demand, in a terminal type:

sudo pon dsl-provider

To stop your ADSL connection, in a terminal type:

sudo poff dsl-provider



There is also another way from [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
>  How to install Broadband ADSL/PPPoE Client (RP-PPPoE)

    * Read #General Notes
    * Read #How to install Basic Compilers (build-essential) 

wget -c [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)
sudo tar zxvf rp-pppoe-3.8.tar.gz -C /opt/
sudo chown -R root:root /opt/rp-pppoe-3.8/
gksudo gedit /usr/share/applications/RP-PPPoE.desktop

    * Insert the following lines into the new file 

[Desktop Entry]
Name=RP-PPPoE
Comment=RP-PPPoE
Exec=gksudo /opt/rp-pppoe-3.8/go-gui
Icon=pppoeconf.xpm
Terminal=false
Type=Application
Categories=Application;Network;


---

### Post by hakunamatata on 2007-03-04
Hi, I think there is a misunderstanding here, forgive me if I am wrong.
I do get internet connection when I switch on the PC and the modem. The connection is configured in the Netgear's software, however it stays connected because the idle timeout of 0 minutes cannot be changed.
What I am looking for is something similar to Gnome PPP (which is for dial up), so that when I have finished with the internet, I can disconnect from it, and carry on with whatever I am doing. Switchig off the modem at the mains supply does not seem like a good idea to me, but that is what I am currently doing!!

---

### Post by yigals on 2007-05-11
I guess you'll have to enter this in the terminal (or Alt+F2) in order to disconnect:
sudo poff dsl-provider
and this for connecting again:
sudo pon dsl-provider

---

