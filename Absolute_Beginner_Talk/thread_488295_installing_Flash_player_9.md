---
title: "installing Flash player 9"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by ross2p on 2007-06-30
> ross@ubuntu:~$  cd /home/ross/install_flash_player_9_linux
ross@ubuntu:~/install_flash_player_9_linux$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

ross@ubuntu:~/install_flash_player_9_linux$ 

this is how far ive gotten, and i am so confused... this is the first thing ive done in a terminal so bear with me...

below is the read me

> Installation instructions
-------------------------

Installing the plugin tar.gz using Install script:
   o Unpack the tar.gz file
   o In terminal, navigate to the unpacked directory and enter:
          + $ ./flashplayer-installer
          + Click Enter key and follow prompts

Installing the plugin using RPM:
   o As root, enter in terminal:
          + # rpm -Uvh <rpm_package_file>
          + Click Enter key and follow prompts

Installing the standalone player:
   o Unpack the tar.gz file
   o To execute the standalone player,
          + Double-click, or 
          + Enter in terminal: ./flashplayer






so thats what I've pieced together from reading other posts and the read me... HELP!

---

### Post by Outrunner on 2007-06-30
Seems fairly obvious to me, you can't install flash on a 64 bit Ubuntu machine. There seems to be a workaround , not sure how well it works though, so be careful [http://ubuntuforums.org/showthread.php?t=202537&highlight=flash](http://ubuntuforums.org/showthread.php?t=202537&highlight=flash)

---

### Post by ross2p on 2007-07-02
i downloaded swiftfox and it installed flash just fine! woo... long live ubuntu

---

