---
title: "Trying to install flash plugin"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by ColdCanadian on 2008-01-08
I'm trying to manually install by copying the files.

Error while copying to "/usr/lib/firefox/plugins".
You do not have permissions to write to this folder.

How do I gain permission to write?
And yes I'm a complete newb!!

Thanks

---

### Post by philinux on 2008-01-08
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Follow option one.

---

### Post by SomeGuyDude on 2008-01-08
Open up your terminal and type "sudo nautilus". That'll give you a file folder window that has root privileges and you should be able to copy things right over.

---

### Post by bobosky on 2008-01-08
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

I am following option one suggested by philinux. 

Those instructions are:
.tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

I have done steps 1-2 and in step 3 in think Unpackage mean extract intall_flash_player_9_linux on to my desktop.
I go to the terminal and type "./flashplayer-installer" and get " bobo@bobo-desktop:~$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory "
So I am stuck at step 4.

ColdCanadian, I hope this helps get the answer. 

Bobo

---

### Post by blithen on 2008-01-08
> **bobosky said:**
> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

I am following option one suggested by philinux. 

Those instructions are:
.tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

I have done steps 1-2 and in step 3 in think Unpackage mean extract intall_flash_player_9_linux on to my desktop.
I go to the terminal and type "./flashplayer-installer" and get " bobo@bobo-desktop:~$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory "
So I am stuck at step 4.

ColdCanadian, I hope this helps get the answer. 

Bobo

chmod +x flashplayer-installer
then run
./flashplayer-installer

---

### Post by bobosky on 2008-01-08
I don't know what that means!

---

### Post by philinux on 2008-01-08
> **bobosky said:**
> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

I am following option one suggested by philinux. 

Those instructions are:
.tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

I have done steps 1-2 and in step 3 in think Unpackage mean extract intall_flash_player_9_linux on to my desktop.
I go to the terminal and type "./flashplayer-installer" and get " bobo@bobo-desktop:~$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory "
So I am stuck at step 4.

ColdCanadian, I hope this helps get the answer. 

Bobo

3. unpackage file means just double click it.

4. in terminal type 

cd /Desktop/cd install_flash_player_9_linux   (note the capital D)

Then type 
./flashplayer-installer

---

### Post by bobosky on 2008-01-08
Thanks for the help I am really new to Ubuntu and using a Terminal.

3. double clicking opens the contents of the package in a window.

4. I get this message 
bobo@bobo-desktop:~$ cd /Desktop/cd install_flash_player_9_linux
bash: cd: /Desktop/cd: No such file or directory
bobo@bobo-desktop:~$ cd/Desktop/cd install_flash_player_9_linux
bash: cd/Desktop/cd: No such file or directory

What am I doing wrong?

bobo

---

### Post by chinchilla2392 on 2008-01-08
i suggest this, its automated,
[http://homestarrunner.com]("http://homestarrunner.com")
just click where it says plugins are needed and it automatically installs flash,
(well for me it does)

---

### Post by philinux on 2008-01-08
> **bobosky said:**
> Thanks for the help I am really new to Ubuntu and using a Terminal.

3. double clicking opens the contents of the package in a window.

4. I get this message 
bobo@bobo-desktop:~$ cd /Desktop/cd install_flash_player_9_linux
bash: cd: /Desktop/cd: No such file or directory
bobo@bobo-desktop:~$ cd/Desktop/cd install_flash_player_9_linux
bash: cd/Desktop/cd: No such file or directory

What am I doing wrong?

bobo

too late at night should be

cd /Desktop/install_flash_player_9_linux

---

### Post by Ludwix on 2008-01-08
This solved it for me:

Uninstall the synaptics package:
sudo apt-get remove flashplugin-nonfree

Download the deb package:
wget [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

Install the package
sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb

Hope it helps,
Greets

---

### Post by philinux on 2008-01-08
It's a nice solution but the adobe fix gets you progress bar and full screen operation. The way its meant to be.

---

### Post by bobosky on 2008-01-08
It works! Okay here is what I did in great detail. I think the  [http://homestarrunner.com](http://homestarrunner.com) might work just great but I did not get a chance to try it.

1. go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)
2. Pick Option 1   .tar.gz installation
3. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
4. Save the .tar.gz file to your desktop and wait for the file to download completely.
3. Unpackage (double left click on) the file called install_flash_player_9_linux.tar.gz . A directory called install_flash_player_9_linux will open in a window.
5. Right click once on _flash_player_9_linux and then click on Extract
6. A folder of the same name will appear on your desktop left double click to open it.
7. left double click on flashplayer-installer and the click on Run in Terminal.
8. The installer will run and there will be more written instructions. Click Enter. The installer will instruct you to shut down your browser(s).
9. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

I hope that helps the next person with this problem. 
Sorry I am still not very good a the terminal. 

bobo

---

### Post by slolerner on 2008-01-11
i don't see 'run in terminal' as an option..my newb-ness is showing.

what am i missing?

---

### Post by cutaflip on 2008-01-11
Hi, I've been lurking for awhile and I've managed to find an answer to all the questions I've had except for this one... I'm trying to install this flash plugin as well, but apparently it's not compatible with my amd 64 system. Is there a way to get around this?  Thanks!!

---

### Post by itmanvn on 2008-01-12
> **Ludwix said:**
> This solved it for me:

Uninstall the synaptics package:
sudo apt-get remove flashplugin-nonfree

Download the deb package:
wget [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

Install the package
sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb

Hope it helps,
Greets

worked for me too :guitar:

---

### Post by Bri0 on 2008-01-12
Without the terminal.

1. Down the **.tar.gz** file to your desktop.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN)

2. Right click it and hit 'Extract Here' (The extracted folder will appear). In the extracted folder copy the **libflashplayer.so** file.

3. Go into your home folder and show hidden files (View > Show Hidden Files). Now go into the **.mozilla** folder. If you don't see a **plugins** folder create one and past the **libflashplayer.so** file into it.

4. Close Firefox and start Firefox back up.

You now have flash!


Note: Save the extracted folder for next time in case of a reinstall of the OS. Also check back at Adobe every so often to see if there is a new version. If there is a new version repeat above and replace it with the new **libflashplayer.so** file.

---

