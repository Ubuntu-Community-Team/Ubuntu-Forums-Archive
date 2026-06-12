---
title: "opening files"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by jesse c on 2008-02-04
i need a step by step tutor to show me how to download a file in GUTSY. As an example,today i went on line to CNET.com to view cnet tv which ive done hundreds of times.This time a window opens and says i need to upgrade a FLASH plug in,so i go to Flash web page and it gives a couple of download options for linux including rpm and tar(meaningless to me).Ive tried both and they both take me to the small download window that finishes with open/remove then a larger window opens  with words like open / extract so ive poked around but im totally clueless.I even went out and bought Linux For Dummies book but that seems to be less than helpful in that chapter.It seems to assume that im not really a dummie!By the way in this example there is actually a yellow bar up top that asks if i want to install missing plug ins when i hit ok it says plug ins are already there.If there already there why does it keep asking me to install them? Thats why i went to Flash web page to download the latest version.

---

### Post by Cypher on 2008-02-04
[These instructions]("http://www.smorgasbord.net/2007/06/29/how-to-install-firefox-flash-plugin-in-ubuntu-linux/") references Breezy, but it should work in Gutsy as well..

---

### Post by LowSky on 2008-02-04
this will download and install the newest version

in terminal type

```
wget http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb

```
then type
```
sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb
```

then restart firefox

your all set

---

### Post by mikewhatever on 2008-02-04
Here is the direct link [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
Insert it into address bar and download to your home directory. If you do not know how to install it, look here [http://ubuntuforums.org/showthread.php?t=633095&highlight=adobe+flash](http://ubuntuforums.org/showthread.php?t=633095&highlight=adobe+flash)

PS: The thread title reads 'opening files'. What do you want to open?

---

### Post by jesse c on 2008-02-04
thanks for quick reply.Flash is now installed but i still dont know how to use the download windows system for future work.Apparently i dont even know the difference between opening a file and installing a file. Also,what is the proper way to acknowledge/thank/post as solved to a Forum reply?

---

### Post by mikewhatever on 2008-02-05
> **jesse c said:**
> thanks for quick reply.Flash is now installed but i still dont know how to use the download windows system for future work.Apparently i dont even know the difference between opening a file and installing a file. Also,what is the proper way to acknowledge/thank/post as solved to a Forum reply?

To download flash from adobe site [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) you had to right click on 'Download tar.gz file' and select 'Save link as'. A different browser, such as Opera, would have a slightly different wording - 'Save target as'.

To open a file, it is usually enough to double click it. Ubuntu then opens the file with the default application. You can also right click a downloaded file and go for 'Open With' to choose another application.

For installing files in Ubuntu read here [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/).

---

### Post by erginemr on 2008-02-05
To mark a thread as solved, you need to go up to the start of the page and select "Mark as SOLVED" from the "Thread Tools" drop down menu on the right.

---

