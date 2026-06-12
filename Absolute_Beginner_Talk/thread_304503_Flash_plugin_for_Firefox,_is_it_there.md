---
title: "Flash plugin for Firefox, is it there?"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by brn on 2006-11-21
Using Dapper, I have both Firefox and Opera browsers.  Some web pages requre FLASH and suggest that I "download plugin here".  I have done so and following the instructions, to the best of my knowledge have it installed in whatever directory it wants to be.  But it does not work. What am I doing wrong?  ..

---

### Post by PurplePenguin on 2006-11-21
I'm going from memory, but I think all you need to do is go to the official flash site, download whichever file they offer for Linux, unzip it (there's only one file in there, if I remember correctly - libflashplayer.so) and place that file in your /home/*your-username*/.mozilla/plugins directory.  If it's not there, you just have to create the directory and paste it there.  Upon reboot, it should work. (Note that I didn't put it in the .mozilla/firefox directory, despite the fact that I'm using firefox)

That's all I did, and flash 9 works perfectly. :)

---

### Post by kindafunnylookin on 2006-11-21
If that doesn't work out then go [here]("http://www.psychocats.net/ubuntu/").

---

### Post by CupofDice on 2006-11-21
Going to the official site gives you flash 7. Try this howto for flash player 9 beta2 released today.

[http://ubuntuforums.org/showthread.php?t=279990](http://ubuntuforums.org/showthread.php?t=279990)

---

### Post by kindafunnylookin on 2006-11-21
> **PurplePenguin said:**
> I'm going from memory, but I think all you need to do is go to the official flash site, download whichever file they offer for Linux, unzip it (there's only one file in there, if I remember correctly - libflashplayer.so) and place that file in your /home/*your-username*/.mozilla/plugins directory.  If it's not there, you just have to create the directory and paste it there.  Upon reboot, it should work. (Note that I didn't put it in the .mozilla/firefox directory, despite the fact that I'm using firefox)

That's all I did, and flash 9 works perfectly. :)
....

---

### Post by brn on 2006-11-22
Thanks to all.

I've already done pretty much everything suggested here.  I had great hope for something from kindafunnylookin's link to pshychocats where I found a deeper link to Flash 9 beta.  I had been here before and done everything except create a link described in the last step.  But alas, still no luck.  Truth is that I have no idea what 'Flash' is or does.  I was trying to order cable TV using their online subscription and they are the ones insisting that I need flash to complete the transaction.  Given the well-known perversity of cable companies I am not beyond suspecting that they simply don't want my bottom rung business and this is their way of showing it.  Maybe I'll try satellite instead.

---

### Post by Jason_25 on 2006-11-22
Unfortunately it is a fact that many (poorly designed) web sites require flash.  My advice is to just call them.  But if you want flash anyway, get the flash 9 beta.  Stick the .so file in your /usr/lib/firefox/plugins folder and restart firefox.  You can check to see if it loaded by typing
```

about:plugins

```
 in firefox.

---

### Post by PurplePenguin on 2006-11-22
> **CupofDice said:**
> Going to the official site gives you flash 7.

It's in there somewhere.  Here's [the link]("http://labs.adobe.com/downloads/flashplayer9.html") to the Downloads area, straight from the official site. :)

---

### Post by eddie57 on 2006-11-22
Hi I just installed flash pluggin 7 yestarday and it is a bit awkard for newbies like me but i finally managed it. What you have to do is after you download the file (download it somewhere that is easy to find) preferrably the desktop. Highlight the file right click and a menu pops up giving you the option to extract it there or choose the archive manager and extract wherever  you want. It will create a directory called install_flash_player_7_linux. Open a terminal window navigate to the directory and type the following command. "sudo ./flashplayer-installer you will be entering the command as root, which will install the pluggin for all users.The next thing it will ask for the path to install the pluggin. On mine the path is  /usr/lib/opera or 
/usr/lib/firefox or mozilla depending on the browser or browsers you run. Mine works fine. Hopefully this is helpful.

---

### Post by Afishionado on 2006-11-22
> **brn said:**
> I had been here before and done everything except create a link described in the last step.

That's kind of a crucial step. ;-) That's the step people seem to get hung up on when installing Flash on Linux.

---

