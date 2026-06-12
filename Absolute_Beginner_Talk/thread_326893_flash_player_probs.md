---
title: "flash player probs"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2006-12-28
ok im not sure why but i cannot play any web videos music anythign and it say i need shockwave flash player, i click on it  and get to the flash player website and download it but i cant figure out how to install it even with the directions

---

### Post by wpshooter on 2006-12-28
Have you looked to see if this is available for installation in Synaptic ?

---

### Post by raul_ on 2006-12-28
I lost the count of how many times i've answered this question :P google "linux flash player 9" enter the page, download the flash player 9 update, copy the files inside the .tar.gz to your firefox/plugins folder, and you're good to go :)

---

### Post by antgul3382 on 2006-12-28
ive installed two flash player in synaptic : gnash and klash, they dont do anything i go on the web page and its the same


here are the directions that adobe gives you when dl thiers
> Installation Instructions

1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.

2. Save the Installer to your desktop and wait for the file to download completely.

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).

5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Get answers about Adobe Flash Player privacy practices, licensing, Macromedia Flash content development, and more in our list of Frequently Asked Questions (FAQ). 



when i get to nuber 4 i get confused, go to that directory, ya got that, where is the command line???

---

### Post by antgul3382 on 2006-12-28
> I lost the count of how many times i've answered this question :P google "linux flash player 9" enter the page, download the flash player 9 update, copy the files inside the .tar.gz to your firefox/plugins folder, and you're good to go 


where is that located??? the firwefox folder???

---

### Post by raul_ on 2006-12-28
```

locate firefox/plugins

```

you're installing the old version (flash 7) . install flash 9 update. you should navigate "through" the command line (with the cd command). If you want to do that with the gui just type "sudo nautilus" in the terminal (a.k.a command line) and navigate from there

---

### Post by Delkster on 2006-12-28
> **antgul3382 said:**
> ive installed two flash player in synaptic : gnash and klash, they dont do anything i go on the web page and its the same

I don't know about klash but gnash is the free flash player from the GNU project. It's not particularly compatible with all the flash videos out there yet so you may want Adobe's Flash player.

Go to **Applications > Add/Remove** and search for "flash". That should show you an application called "Macromedia Flash plugin". Select it for installation. Add/Remove Applications will probably tell you that it needs to enable an extra software channel (or repository) in order to install the flash player -- go ahead and allow it to do that.

After that click either Ok or Apply, and the Adobe Flash player will be downloaded and installed for you. After that restart your browser (make sure that all windows have been closed before reopening it) and it should work.

However, note that this way the standard Ubuntu installation will only give you version 7 of the flash plugin. Some flash videos on the 'net require flash 9, and if you want to play those, you'll need to install the beta (test) version of Adobe's flash player 9. That's available in the so-called backports repository which has some software that has been released since the original release of your Ubuntu system. If you're running Ubuntu 6.10 (Edgy), you can find the backported flash player 9 [here](http://packages.ubuntu.com/edgy-backports/web/flashplugin-nonfree). A similar backported package for Ubuntu 6.06 (Dapper) is [here](http://packages.ubuntu.com/dapper-backports/web/flashplugin-nonfree). Find the download link for the i386 architecture near the bottom of the page, download the .deb package it offers, and after the download has finished, double-click on the .deb package to install it.

---

### Post by raul_ on 2006-12-28
If you're wondering, with flash 7, you'll see the lips moving 5 seconds after you hear it :)

---

### Post by antgul3382 on 2006-12-28
ok but i dont have x64  tho

---

### Post by antgul3382 on 2006-12-28
> I lost the count of how many times i've answered this question :P google "linux flash player 9" enter the page, download the flash player 9 update, copy the files inside the .tar.gz to your firefox/plugins folder, and you're good to go




ive gotten to the plugin directory but how do i copy the files now???

---

### Post by raul_ on 2006-12-28
if you're in the directory as root...just extract the files from the .tar.gz you downloaded, cut or copy the files and paste them there.

---

### Post by antgul3382 on 2006-12-28
what??? i can move files from a folder to the terminal??? im so confused, you told me to get to the firefox/ plugins folder using the cd command in the terminal---ok ----did that how do i copy files to it

---

### Post by antgul3382 on 2006-12-28
ok i might sound like a dumbass but i can do this!!!!! i did what flash told me to do

> Installation Instructions

1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.

2. Save the Installer to your desktop and wait for the file to download completely.

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).

5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.




and this is what came up

slave@slave3:/tmp/flash7$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Macromedia Flash Player installer.

does this mean there is no flash player for 64 bit????   im a myspace user and without flash its useless.....

can anyone help????

---

### Post by Verlaine on 2006-12-28
This worked for me.

[http://gatito.co.uk/?p=37]("http://gatito.co.uk/?p=37")

---

### Post by raul_ on 2006-12-28
sorry, i was out. Let's start again. Extract the files to some folder you want. Keep that window open. Now go to the terminal and "sudo nautilus" . Then, navigate to your firefox/plugins folder and drag the file from the folder you extracted them to, to your plugins folder, and restart firefox.

---

