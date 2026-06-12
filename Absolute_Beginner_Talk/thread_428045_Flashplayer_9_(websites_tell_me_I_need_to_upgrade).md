---
title: "Flashplayer 9 (websites tell me I need to upgrade?) [Resolved]"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-04-29
I did [this tutorial]("http://www.psychocats.net/ubuntu/flash") to install flash player 9 for Dapper. But when I go to some websites they tell me I need upgrade to flashplayer 9. Any help thanks.

---

### Post by heatpumpcontrol on 2007-04-29
> **thelocust said:**
> I did [this tutorial]("http://www.psychocats.net/ubuntu/flash") to install flash player 9 for Dapper. But when I go to some websites they tell me I need upgrade to flashplayer 9. Any help thanks.

Try this. I got it from the ubuntu howto [http://www.cs.cornell.edu/~djm/ubuntu/](http://www.cs.cornell.edu/~djm/ubuntu/)

Install Adobe Flash Player 9 plugin for Firefox

   1. Add the extra repositories. (In particular, make sure that feisty/multiverse is enabled.)
   2. Install Flash Player:

      sudo apt-get install flashplugin-nonfree

   3. (alternative; use only if previous step did not work) Install Flash 9 manually for a single user:

      sudo apt-get --purge remove flashplugin-nonfree
      wget -c -P /tmp/ [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
      pushd /tmp
      tar -vxzf /tmp/install_flash_player_9_linux.tar.gz
      popd
      mkdir ~/.mozilla/plugins
      cp /tmp/install_flash_player_9_linux/libflashplayer.so ~/.mozilla/plugins/
      cp /tmp/install_flash_player_9_linux/flashplayer.xpt ~/.mozilla/plugins/

---

### Post by autocrosser on 2007-04-29
First--goto macromedia's website. There is a test page that will tell you exactly the version of your Flash Player. If it reports you do have Flash 9 & some websites say that you need to upgrade, well that is the webdesigner's fault, not yours. If this is the case (& I have has to do this just a few weeks ago), you will find in the site index or at the bottom of a page--a way to contact the website maintainer. Very politely explain that you use the Linux version of Flash 9 & the site is mis-identifying the player. Make sure to include the ident info from Macromedia's page.

---

### Post by thelocust on 2007-04-30
I went in to ~/.mozilla/plugins and deleted the files with flash in the names. Restarted firefox and it worked. Thanks for the help anyway.

---

