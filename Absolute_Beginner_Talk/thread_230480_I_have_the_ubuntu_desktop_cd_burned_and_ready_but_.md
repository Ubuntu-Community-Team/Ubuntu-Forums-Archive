---
title: "I have the ubuntu desktop cd burned and ready but i cant get it to install"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by DesertFox on 2006-08-06
When it boots up i get the option install or start but when i do that it just trys to start ubuntu and then ends up at a maroon colored screen with a mouse and does nothing......so i need help?

---

### Post by Steggy on 2006-08-06
Well, it could be a bad burn of the disc--you might try reburning it at a lower speed (when I'm burning anything other than music CDs, I generally burn at the lowest possible speed to give it the best chance of working.) If that doesn't work, you might try redownloading it, then burn that image.

However, you might be unable to use the new graphic installer, like I was. I still don't know the reason why, but I do know that using the Alternate Install CD worked perfectly fine. You can find it in the same place you found your current CD image. If you don't need all the hand-holding of a graphic installer (and the alternate installer, which was used for previous versions of Ubuntu as default, is still pretty easy to use), I'd suggest that.

---

### Post by DesertFox on 2006-08-06
do you think you vould link me to the other installer cause i looked around and could'nt find it, and nice avatar

---

### Post by Steggy on 2006-08-06
Should have post instructions the first time, sorry about that.

1) Go to [www.ubuntu.com/download]("http://www.ubuntu.com/download")
2) Click on the location closest to you.
3) You should see "Ubuntu 6.06 LTS (Dapper Drake)" at the top of the page. Scroll down until you see "Alternate install CD" (it's about a page--that is, one press of the space bar--down for me.)
4) Click on the link for your computer architecture (in most cases, this would be "PC (Intel x86)"
5) Choose where you want to save the image, and you're set.

You can also scroll down to closer to the bottom of the page, and find the .torrent for the correct CD (likely "ubuntu-6.06-alternate-i386.iso.torrent") if you prefer to use that method to download.

I'm glad you like the avatar. I'm a big fan of Futurama and glad that's it's coming back :)

---

### Post by DesertFox on 2006-08-06
thanks i wil try that version, and its coming back?? i did'nt know that

---

### Post by confused57 on 2006-08-06
> **DesertFox said:**
> When it boots up i get the option install or start but when i do that it just trys to start ubuntu and then ends up at a maroon colored screen with a mouse and does nothing......so i need help?

The alternate cd may resolve your problem, but it also might be that the wrong video driver was loaded when the Live CD booted up.  If the same happens after you install with the alternate cd, hopefully it won't...if you only get a screen as you described:
press "Ctrl+Alt+F1", which will get you to a console command prompt. Login.
enter:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```
When it asks to autodetect your monitor, select "no", then just go with the defaults, except when it asks for your video driver, select "vesa" or whatever is appropriate for your video controller.  When you finished reconfiguring xserver & are back at the console, enter:
```
sudo /etc/init.d/gdm start
```

You might be able to perform the above commands running the Live CD to get to the desktop GUI...

---

