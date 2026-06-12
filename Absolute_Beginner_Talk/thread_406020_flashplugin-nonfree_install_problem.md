---
title: "flashplugin-nonfree install problem"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Idrive on 2007-04-10
Here is what is happening when trying to install:

dustin@dustin-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a kdelibs4c2a libvorbisfile3 kdelibs-data
  kdebase-data liblualib50 libpcre3 kicker libkonq4 libavahi-qt3-1
  libxcomposite1 libqt3-mt liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~edgy1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
dustin@dustin-laptop:~$

---

### Post by happymellon on 2007-04-10
Did you add the multiverse repositories? Or you could just use Automatix instead of the command line.

---

### Post by igknighted on 2007-04-10
Easiest way to install flash is to go to the adobe site, click on the download flash player icon and get it in tar.gz format.  then extract the archive, and read the read-me.  It should say to put the file libflashplayer.so into the folder /usr/lib/mozilla/plugins/.  Do this with sudo (either open nautilus w/ a gksudo nautilus or use the mv command in the terminal.  After that restart FF and it should work fine.

To get rid of the first part about the files no longer needed, simply run the command apt-get autoremove.

---

### Post by aysiu on 2007-04-10
> **igknighted said:**
> Easiest way to install flash is to go to the adobe site, click on the download flash player icon and get it in tar.gz format.  then extract the archive, and read the read-me.  It should say to put the file libflashplayer.so into the folder /usr/lib/mozilla/plugins/.  Do this with sudo (either open nautilus w/ a gksudo nautilus or use the mv command in the terminal.  After that restart FF and it should work fine. Actually, the easiest way to get it installed is to just visit in Firefox a site that needs Flash and then click on *Install missing plugin*.

If you want to go the other way (what you described), this page has explicit step-by-step instructions to copy and paste:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by igknighted on 2007-04-10
> **aysiu said:**
> Actually, the easiest way to get it installed is to just visit in Firefox a site that needs Flash and then click on *Install missing plugin*.

If you want to go the other way (what you described), this page has explicit step-by-step instructions to copy and paste:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Does that actually work?  Mine always tells me that no plugin is available.

---

### Post by aysiu on 2007-04-10
> **igknighted said:**
> Does that actually work?  Mine always tells me that no plugin is available.
It worked for me when I did [this tutorial](http://psychocats.net/ubuntu/flashubuntu), that is now slightly out of date because Flash 9 is universally available. As you can see from the screenshots, it does work, though... or did in Dapper. I hope that functionality didn't get lost in Edgy.

FYI: it installs Flash only locally (for the currently logged in user), not globally (for all users). Of course, if you have only one user, that may be fine...

---

### Post by igknighted on 2007-04-10
> **aysiu said:**
> It worked for me when I did [this tutorial](http://psychocats.net/ubuntu/flashubuntu), that is now slightly out of date because Flash 9 is universally available. As you can see from the screenshots, it does work, though... or did in Dapper. I hope that functionality didn't get lost in Edgy.

FYI: it installs Flash only locally (for the currently logged in user), not globally (for all users). Of course, if you have only one user, that may be fine...

If you took a chance and ran FF as root would it install globally or just for root user?

---

### Post by aysiu on 2007-04-10
> **igknighted said:**
> If you took a chance and ran FF as root would it install globally or just for root user?
I believe it would install it only for the root user. It looks to install in ~/.mozilla/plugins. So if you're logged in as *user*, it'd install in /home/*user*/.mozilla/plugins. If you're logged in as root, it'd install in /root/.mozilla/plugins. I don't see how it would try to install to /usr/lib/firefox/plugins

---

### Post by igknighted on 2007-04-10
> **aysiu said:**
> I believe it would install it only for the root user. It looks to install in ~/.mozilla/plugins. So if you're logged in as *user*, it'd install in /home/*user*/.mozilla/plugins. If you're logged in as root, it'd install in /root/.mozilla/plugins. I don't see how it would try to install to /usr/lib/firefox/plugins

Well, I guess I was hoping that whoever coded it might have been nice enough to throw a "if user=root, then install to /usr/lib/..., else ~/.mozilla...", but oh well.

---

### Post by jzero88 on 2007-04-10
This might help you.its a script i wrote up to install Flash.Just chmod 777 the flash-install.txt file and run it as sudo. sudo ./Flash-Install.txt that should get you flash player 9

---

### Post by aysiu on 2007-04-10
> **jzero88 said:**
> This might help you.its a script i wrote up to install Flash.Just chmod 777 the flash-install.txt file and run it as sudo. sudo ./Flash-Install.txt that should get you flash player 9
For those who don't want to launch a text editor: ```


sudo echo "deb http://3v1n0.tuxfamily.org edgy 3v1n0" >> /etc/apt/sources.list

sudo echo "deb-src http://3v1n0.tuxfamily.org edgy 3v1n0" >> /etc/apt/sources.list

sudo wget http://3v1n0.tuxfamily.org/EDD1E155.gpg -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install flashplugin-nonfree flashplayer-nonfree

``` Alternatively, you could create a text file in your home folder called *installflash* with these contents: ```
#!/bin/bash
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
rm install_flash_player_9_linux.tar.gz
rm -r install_flash_player_9_linux
``` Save the text file and in the terminal, paste in ```
cd ~/
chmod +x installflash
./installflash
``` Or if you already have the Multiverse repositories enabled: ```
sudo apt-get update & sudo apt-get install flashplugin-nonfree
``` Or, as mentioned before, if you're the only user on the computer, just visit a website that requires Flash and then follow the *install missing plugin* wizard in Firefox.

---

