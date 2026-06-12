---
title: "flash in dapper"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-06-01
Hi

For some reason flash will not install in kubuntu Dapper....

---

### Post by Klaidas on 2006-06-01
Maybe this will help: [https://wiki.ubuntu.com/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://wiki.ubuntu.com/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)

---

### Post by Kobalt on 2006-06-01
What method have you tried to install flash-plugin : Via Synaptic ? Manually ? 
Take a look at this post, it might help : 
[http://ubuntuforums.org/showthread.php?t=164521&highlight=flashplayer]("http://ubuntuforums.org/showthread.php?t=164521&highlight=flashplayer")

---

### Post by mrvgarg on 2006-06-01
I have tried automatix and it did not work for flash and I also tried 
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
which did not download or install anything either.

---

### Post by Klaidas on 2006-06-01
What browser are you using?

---

### Post by xael on 2006-06-01
[QUOTE=mrvgarg]I have tried automatix and it did not work for flash and I also tried 
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
which did not download or install anything either.[/QUOTE]

Please, be careful when installing software from alternate sources. They could take over the repos & render Synaptic unusuable.

---

### Post by bruenig on 2006-06-01
>  I have tried automatix and it did not work for flash and I also tried
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
which did not download or install anything either.

First, the only way this works is if you have enabled the extra repositories. To do so graphically go to **Sytem>Administration>Synaptic Package Manager** and when there go to **Settings>Repositories**. After there click on the add button. The Channel should say Ubuntu 6.06 LTS. Click **Community maintained (Universe)** and then on **Non-Free (Multiverse)**. Click add and then do the same thing 3 more times on the other channels. Now try the commands.

Second, this will not work on 64 bit dapper only on 32 bit.

---

### Post by catlett on 2006-06-01
[http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide](http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide) Follow this guide (exactly, make sure you change your repository list like it tells you to) and you will have dapper set up with just about everything you need for day to day use .
In section 12 it walks you through firefox add-ons including flash.
P.S.If you still want to try Automatix, [http://www.ubuntuforums.org/showthread.php?t=177646&page=7](http://www.ubuntuforums.org/showthread.php?t=177646&page=7)  make sure you are using the Dapper version of Automatix. And do not worry about it taking over synaptic. It is made by forum members to help new people. It basically takes everything that is in that guide and installs it via a script so peopl don't have to use the command line.
If you get errors post the errors and someone will help.

---

### Post by Klaidas on 2006-06-01
[QUOTE=Klaidas]What browser are you using?[/QUOTE]
Ok, I didn't get the answer, but if you're using Firefox, this might help. I did that in Ubuntu a few hours ago (fresh installed dapper):
Install Macromedia Flash manually (from their website). Then, there might be a problem with sound (was for me). To fix: [https://wiki.ubuntu.com/RestrictedFormats#head-832969c4301548599ecbe6393e2682a4e343af67](https://wiki.ubuntu.com/RestrictedFormats#head-832969c4301548599ecbe6393e2682a4e343af67) 
Then, restart firefox and it should work! :)

---

### Post by mrvgarg on 2006-06-01
I am using swiftfox and 32 bit dapper

---

### Post by blue_thunder on 2006-06-02
I've got the same troubles as Mrvgarg, with the minor exception that I'm on ubuntu, not kubuntu, and firefox rather than swiftfox. 

I've tried automatix, easy ubuntu, and BUMP, in addition to the quick easy terminal flash install, but all to no avail.

Any help would be greatly appreciated.

---

### Post by blue_thunder on 2006-06-02
Alright. I've got it working somehow. The problem now is that video and audio will be out of sync. For example, I'm watching something at google video, by the time I'm fifteen seconds in, the video and audio are noticeably off.

---

### Post by mrvgarg on 2006-06-02
I have looked at the Firefox plug ins folder and they are all there. But when I look in the swiftfox plugins some are missing..](*,)

---

### Post by Daremo on 2006-06-02
[QUOTE=mrvgarg]Hi

For some reason flash will not install in kubuntu Dapper....[/QUOTE]

Try this link:  [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

This worked well for me...

---

### Post by mrvgarg on 2006-06-02
Nope still did not work.

---

### Post by brin on 2006-06-04
On Dapper, I have found that by simply installing the esound-client package solved the sound problem. Run "sudo apt-get install esound-client" and reboot the system.

By using a sound server such as esd or arts, you do not have to kill all other applications that are sending audio feeds and allows for multiple audio input to the dsp device.

---

