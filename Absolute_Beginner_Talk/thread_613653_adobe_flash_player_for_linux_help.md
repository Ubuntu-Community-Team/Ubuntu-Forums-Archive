---
title: "adobe flash player for linux help"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Mcdougan on 2007-11-15
the link says i need to "navigate to this directory and type ./flashplayer-installer to run the installer"

how do i navigate to the directory?

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
thats the link in case you want to read it

---

### Post by mikewhatever on 2007-11-15
Suppose the directory is in your home folder, then
> cd directory_name

---

### Post by Mcdougan on 2007-11-15
the package is on my desktop and when i type cd_directory_install_flash_player_9_linux it says no such file or directory

---

### Post by ghostcrab on 2007-11-15
1) drag and drop the the file install_flash_player_9_linux.tar.gz in your home folder

2) open terminal 
ghostcrab@LOL-123456:~$ sudo tar -zxvf install_flash_player_9_linux.tar.gz

3) ghostcrab@LOL-123456:~$ cd /home/ghostcrab/install_flash_player_9_linux

4) ghostcrab@LOL-123456:~$ sudo flashplayer-installer

5) /usr/lib/firefox

this should help

---

### Post by Mcdougan on 2007-11-15
[sudo] password for jason:
install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
jason@juggernaut:~$ cd/home/jason/install_flash_player_9_linux
bash: cd/home/jason/install_flash_player_9_linux: No such file or directory


this is what it said

---

### Post by ghostcrab on 2007-11-15
is it in your home directory have you checked? got root?
you could also open your home directory and slect toggel between button and text-based location and choose text-based location and just copy and past in the term and sudo cd location
 hehe i dont care I'll help anyone out because I rule

---

### Post by Mcdougan on 2007-11-15
Thank you, it installed

---

### Post by ghostcrab on 2007-11-15
no problem man enjoy

---

