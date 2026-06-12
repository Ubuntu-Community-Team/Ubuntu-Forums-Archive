---
title: "Install Flash Player on Xubuntu"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Scrtcwlvl on 2006-07-29
I need to install Macromedia Flash Player on this computer which is running Xubuntu.  I downloaded the linux version to my desktop, unpacked it to my desktop, ran terminal then typed the command ./flashplayer-installer as the online instructions told me to do [online instructions](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash), yet this is the error I get.
"morgan@morgan-desktop:~$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory"

My friend who runs Ubuntu fallowed those instructions and it worked flawlessly for her.  Can it not run on Xubuntu?  If not then how would I go about installing it, am I doing anything wrong?

---

### Post by avender on 2006-07-29
Please check this site...

[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

It has the solution to your problem. :)

---

### Post by Scrtcwlvl on 2006-07-30
morgan@morgan-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

This is what I get when I put in the code I got from [your link](http://doc.gwos.org/index.php/DapperGuide#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox) I am very new to linux.

---

### Post by Scrtcwlvl on 2006-07-30
I have tried fallowing everything that website told me to do and nothing, I also have a problem with Wine, anyway the current problem is Flash Player.  Still I can't get it to work.

---

### Post by Perfect Storm on 2006-07-30
I don't know if you have tried this:

Download flash from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
save it to your **Desktop**
```
cd Desktop
tar zxvf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer

```
Then it guides you through.



> morgan@morgan-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

This is what I get when I put in the code I got from your link I am very new to linux.

You havn't set up your sourcelist correctly then.

---

### Post by chalex on 2006-07-30
Flash is also described on this nice page: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Just make sure you set up the repositories correctly as described in a number of places including the link above.

---

### Post by Jagot on 2006-07-30
You need to enable the multiverse repo:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by Scrtcwlvl on 2006-07-30
> **Artificial Intelligence said:**
> I don't know if you have tried this:

Download flash from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
save it to your **Desktop**
```
cd Desktop
tar zxvf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer

```
Then it guides you through.





You havn't set up your sourcelist correctly then.

This worked perfectly.  Thank you very much, watching videos now.

---

