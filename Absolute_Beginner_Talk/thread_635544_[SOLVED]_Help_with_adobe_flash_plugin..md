---
title: "[SOLVED] Help with adobe flash plugin."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by famous3warriors on 2007-12-08
This is what I get when i try to manually install the plugins for adobe flash.
eduardo@padresputer:~$ sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins/
mv: cannot stat `install_flash_player_9_linux/libflashplayer.so': No such file or directory
eduardo@padresputer:~$ sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
mv: cannot stat `install_flash_player_9_linux/flashplayer.xpt': No such file or directory
eduardo@padresputer:~$ 
What do I have to do to fix this problem.  Thanks.

---

### Post by Sef on 2007-12-08
1) Much easier to use Applications > Add/Remove to installl.  (Just set the top right box to 'All Available Applications.'

2) Did you download the [tar package]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW&promoid=BONRN")?

3) Did you read the directions from [adobe]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW&promoid=BONRN")?

---

### Post by famous3warriors on 2007-12-08
yes i sure did but i fixed it by removing the libflashplugin.so I found it in some thread I was reading and I cant find it again so that I could post it here so other people can look at this thread and fix there problem.  Thanks for your advice.

---

