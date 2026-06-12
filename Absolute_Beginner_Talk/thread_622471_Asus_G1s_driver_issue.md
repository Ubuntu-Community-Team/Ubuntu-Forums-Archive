---
title: "Asus G1s driver issue"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Rcommander on 2007-11-24
Hey guys I know there are probably many posts regarding this but they aren't helping my issue.

first of all I am a noob, so before asking for a log tell me how to get it. 

Anyways I got the 8600M GT and like others I am also having an issue with video. So i tried some solutions posted, I used Envy to install and it installed 100.x.24 i guess that is the latest driver? But I do have PART of a video... I mean all i get is random pixes but not a complete image. The kernal is loading but I dont have a good display picture. How would i resolve this? and what do i type in terminal to get ubuntu to use the VESA driver again? and how do i get to terminal? or any other command prompt?

---

### Post by overdrank on 2007-11-24
> **Rcommander said:**
> Hey guys I know there are probably many posts regarding this but they aren't helping my issue.

first of all I am a noob, so before asking for a log tell me how to get it. 

Anyways I got the 8600M GT and like others I am also having an issue with video. So i tried some solutions posted, I used Envy to install and it installed 100.x.24 i guess that is the latest driver? But I do have PART of a video... I mean all i get is random pixes but not a complete image. The kernal is loading but I dont have a good display picture. How would i resolve this? and what do i type in terminal to get ubuntu to use the VESA driver again? and how do i get to terminal? or any other command prompt?

Hi and welcome, then terminal is located under applications, accessories, terminal. If you dont mind could you post the output of this command ```
 cat /etc/X11/xorg.conf
``` Be sure that is a capital X. and you can copy and paste the command and the output.

---

### Post by Rcommander on 2007-11-24
Ok I couldn't get to my cmd prompt/terminal etc...so i just reinstalled ubuntu...now how do i go about enabling my 8600M GT?

---

### Post by overdrank on 2007-11-24
> **Rcommander said:**
> Ok I couldn't get to my cmd prompt/terminal etc...so i just reinstalled ubuntu...now how do i go about enabling my 8600M GT?

Ok well speaking from my point of view on what I would do is use Envy without enabling the restricted drivers. If you have enabled the restricted drivers then disable them first before you use Envy. Then after using Envy you may have to reconfigure your xorg with these commands 
```
If you get a black screen after using Envy then you can use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
[CODE]sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hopefully this will return you to the desktop.[/CODE]
And please read this thread first before you proceed because it was successful for this user.
[http://ubuntuforums.org/showthread.php?t=620337](http://ubuntuforums.org/showthread.php?t=620337)
Good luck! :)

---

