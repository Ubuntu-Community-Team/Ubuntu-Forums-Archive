---
title: "Please tell me how to &quot;Unpackage&quot; a file to install Flash?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-19
I read the instructions on the Adobe site, which has instructions about installing Flash in my Mozilla Firefox browser.

Would any of you tell me how to install "Adobe Flash"? I don't understand what "unpackage" means, here:

[quote="Adobe"]Unpackage the file. A directory called install_flash_player_9_linux will be created.[/quote]
Source: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by philinux on 2008-02-19
for newbies this is easier. Download it then just double click it. 

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)

---

### Post by pedro_orange on 2008-02-19
First. Find where you downloaded the tar.gz

Then, right click on it.

Then left-click on "Extract Here" (Or something along those lines. Maybe unpack here)

Unpacking is just like "Unzipping"

A new folder will be created which is the "Unpacked" folder. You just cd to that folder in terminal and run the install script.

---

### Post by seventhc on 2008-02-19
when you click on the file to download, you should get prompted to either save it to disk or open in it with *'Archive Manage*r"
Choose open with *archive manager* then a box will pop up and you just click the button that says extract.
Now it's unpacked.
now open a terminal and if you extracted it to your desktop type this in the terminal
```

cd Desktop/install_flash_player_9_linux
./flashplayer-installer

```

---

### Post by hyper_ch on 2008-02-19
if it's a tar.gz file use

```

tar xfvz FILE.tar.gz

```

that will unpack it.

---

### Post by ubuntu27 on 2008-02-21
In your other threads, you have installed the "restricted-extras" so, you should have Adobe's Flash installed now :)

Visit a website with Flash to verify it.

---

