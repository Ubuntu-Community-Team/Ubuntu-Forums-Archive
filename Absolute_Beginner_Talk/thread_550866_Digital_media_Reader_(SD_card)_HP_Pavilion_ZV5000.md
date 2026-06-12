---
title: "Digital media Reader (SD card) HP Pavilion ZV5000"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by krasnapolski on 2007-09-14
Hello forum members

HP Pavilion ZV5000 has a digital media card reader which is located on the laptop ontop of the only PCMCIA card slot which makes me believe that it too is PCMCIA unit. Moreover my assumption is supported by the fact, that it's not working plug'n play style :)

So... i went to hp.com to see if there's any drivers for windows which would make my life a little easier but to no avail...

I've googled for ours and old posts seem to have my problem without solution. Anyhting new on the market. As ubuntu beginner i've thought that eventhough there's no ubunut specific drivers i could still get some progress with .inf's (as i did with wlan card installation - thanks to this forum).

Similar problem remains unanswered at the time of this post for other HP product in here: [http://ubuntuforums.org/showthread.php?t=501850](http://ubuntuforums.org/showthread.php?t=501850)

So far the progress i've made is that i have found an sp29788.exe installer for very close HP product line, but i can't get that to work for the obvious reasons.

Any insight for this would be greatly appreciated. Eventhough it's not a "showstopper" it would be a finalizing a proof of concept over here.


thanks in advance. 

br, Kras

---

### Post by cubeist on 2007-09-14
The best place to start is type "lspci" in the terminal and look to see if your computer recognizes the drive.  I have an hp dv9000 and it recognizes it as a ricoh... see here
--
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
--

Unfortunately, endless hours of searching on the web and following tutorials never worked for me and I cannot use the card reader in linux.  I search the web every once in a while to see if there is a driver or workaround of any sort for it, but nothing yet.  Hopefully you have a different brand card reader.  Some hp's use a toshiba reader that people have gotten working...

---

