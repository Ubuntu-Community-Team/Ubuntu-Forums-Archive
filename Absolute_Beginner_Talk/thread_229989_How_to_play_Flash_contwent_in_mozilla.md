---
title: "How to play Flash contwent in mozilla"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by deepank on 2006-08-05
As i surf some sites, they ask me to install flash player and they redirect me to the official website which contains flash in exe form for windows. How do i play flash content from the websites in the mozilla browser. Is there any software which I can download.

---

### Post by rapha on 2006-08-05
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
(Second hit in Google with "dapper drake install flash")

---

### Post by xpod on 2006-08-05
I used "Automatix" which installs all programs your mabey used of for watching videos and playing flash/java etc

---

### Post by deepank on 2006-08-05
This is what I get when I run this command

deepank@deepank-desktop:~$ sudo apt-get install flashplugin-nonfree Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree
deepank@deepank-desktop:~$

---

### Post by deepank on 2006-08-05
I found out a way ...
I went to the official website , downloaded the player for the x-86 platform. Extracted it in the home directory
Then from the terminal after going into the extracted directory, typed
./flashplayer-installer
and then following the instructions, the flash player was set up.:-({|=

---

