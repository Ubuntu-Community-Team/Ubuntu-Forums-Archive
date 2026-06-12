---
title: "Installing Macromedia Flash Player"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by sanderella on 2006-06-21
I'm stumped by the instructions on the Download Centre's web page.
It reads
"1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.

2. Save the Installer to your desktop and wait for the file to download completely.

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line)."

I've got as far as 3, but now I don't understand the instruction 4." *Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line)."*
 Can someone please tell me how to do this?

Sorry to be such an idiot.

---

### Post by Jasper Houtman on 2006-06-21
Just use the synaptic package manager, it's much easier.
It's under system > administration

---

### Post by bukwirm on 2006-06-21
Open Applications > Accessories > Terminal, navigate to the directory where you downloaded the file (type 'cd *dirname*'), then type './flashplayer-installer'. You may also want to find a basic tutorial on the use of the command line for future reference.

---

### Post by fer5437 on 2006-06-21
You must go to the folder directory install_flash_player_7_linux to run ./flashplayer-installer.

---

### Post by Jasper Houtman on 2006-06-21
sudo ./flashplayer-installer 

That will prob work better.

---

### Post by aysiu on 2006-06-21
You should either [enable the multiverse repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
``` or ```
cd ~/Desktop/install_flash_player_7_linux
sudo ./flashplayer-installer
``` and install it to /usr/lib/firefox/plugins

---

### Post by sanderella on 2006-06-21
:D Thanks folks! Installed now.

---

### Post by sanderella on 2006-06-21
Thanks especially to **aysiu**. Your web pages are really helpful.

---

### Post by flyingsolo on 2006-06-24
I'm trying to solve the same problem of installing flash plugin to firefox and followed aysiu's instructions above but when I specify the installation path:
[COLOR="Blue"]/usr/lib/firefox/plugins[/COLOR]
it responds with a warning and instructs to specify a valid path name.
If I use the path:
[COLOR="Blue"]/usr/lib/firefox[/COLOR]
(leave off the plugins) it will accept it but I didn't want to proceed in case this fouled things up somehow.  Why wouldn't it allow the plugins part of path?  Also, I had already tried using the installation via Synaptic but still doesn't seem to work.  If a site requires Flash 8, will it not play at all with Flash 7 or will it just be limited somehow?
Thanks

---

### Post by aysiu on 2006-06-24
It's been a while since I've done the manual install. It's possible that the Flash installer may be looking for a plugins folder in whatever directory you specify. For example, if you type ```
/usr/lib/firefox/plugins
``` it may be looking for /usr/lib/firefox/plugins/plugins and say it doesn't exist.

And if you have Flash 7 and it requires Flash 8, the Flash simply won't play.

---

### Post by sanderella on 2006-06-24
Although the terminal told me that flash player was installed, I found that it wasn't actually working. I did install Flash 7. Today I tried to install Flash 8, but failed again.

Any advice about any Flash player would be welcome, if it stops those little messages that say I haven't got the right plug-in.

---

