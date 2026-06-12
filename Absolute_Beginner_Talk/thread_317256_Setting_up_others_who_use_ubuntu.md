---
title: "Setting up others who use ubuntu"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-12-12
Hi everyone,
I am setting up my brothers computer to use Ubuntu, since I am sick of removing viruses once a week.
It is currently installing, and I have a couple of questions or options for you guys (I know a abit about linux, just want some opinons).

1) What's the best desktop to use? KDE or GNOME? He just wants to play games so I'm going to use GNOME, since that's the one I have been using for the past year.

2) How do I make large icons on the desktop?

3) Is the cedega subscription worth getting? He plays Diablo 2, C&C RedAlert 2 and browses the net a bit,

4) What's a good theme to install for a 13 year old to use who has been using  Windows for years?

5) How do I install the "Radeon 9250" drivers?

Cheers,
Josh

---

### Post by Odisej on 2006-12-12
1. Gnome is an easier choice. But if you ask me, I would go with KDE instead. It allows for more exploring and finding out about what computers can do and how the machines work. Since he is 13, it maybe good for his training and stirring up his curiosity.

2. Just make them bigger. Use the right mouse button. It is not hard at all.

3. i would suggest trying wine (with winetools) first. If the games still don't work, then cedega may be an answer.

4. KDE is much closer to windows experience than GNOME. The theme, well, I do not think it is important what colours are being used. But you can find some interesting solutions at GNOME LOOK or KDE LOOK websites (just google for them).

5. Maybe this would help: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Odisej

---

### Post by Sef on 2006-12-12
> 1. Gnome is an easier choice. But if you ask me, I would go with KDE instead. It allows for more exploring and finding out about what computers can do and how the machines work. Since he is 13, it maybe good for his training and stirring up his curiosity.

Gnome would be a better choice.  Most people here use Gnome.  Therefore, more help is available.  

> 1) What's the best desktop to use? KDE or GNOME? He just wants to play games so I'm going to use GNOME, since that's the one I have been using for the past year.


Both are good desktops.  It boils down to preference.  Since you have been using Gnome, it would be easier for you to help him.

> 3. i would suggest trying wine (with winetools) first. If the games still don't work, then cedega may be an answer.


Games may or may not work on either one, so here are the links to check them out.

Check out [Wine]("3. i would suggest trying wine (with winetools) first. If the games still don't work, then cedega may be an answer.").

Check out [cedega]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1").

---

### Post by houstonbofh on 2006-12-12
> **Odisej said:**
> 1. Gnome is an easier choice. But if you ask me, I would go with KDE instead. It allows for more exploring and finding out about what computers can do and how the machines work. Since he is 13, it maybe good for his training and stirring up his curiosity.

2. Just make them bigger. Use the right mouse button. It is not hard at all.

3. i would suggest trying wine (with winetools) first. If the games still don't work, then cedega may be an answer.

4. KDE is much closer to windows experience than GNOME. The theme, well, I do not think it is important what colours are being used. But you can find some interesting solutions at GNOME LOOK or KDE LOOK websites (just google for them).

5. Maybe this would help: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Odisej
I agree with all but KDE.  There are a few tools missing with KDE that make life nice.  (The recommended way to upgrade from Dapper being an example)

Also look at easy-ubuntu or Automatix to install the graphics drivers as well as Codecs, flash, and so on.

---

### Post by hyper_ch on 2006-12-12
If he wants to run games (which aren't supported by wine) then I tend to the following:

Depending on the hardware specs (if your bro has a dual core and 2gb ram (well, 1 gb might also work) he can easily setup a virtual windows with VMWare... on a dual core it won't hog down the whole computer and Diablo2 does not make use of dual anyway I think...
The other option is having a Win98/W2k/XP (depending on the game) dual-partition. You don't need to install anything on there than security updates... not even an AV or Firewall (if it will be exlusively be used for games)... just make sure that the partition size will be big enough for installing the games he wants...

With regard to the desktop... I started out with Gnome, changed then to KDE and currenly using Xfce... I noted I don't need all that stuff the gnome and kde has and Xfce does what I want... so no need to "waste" ressources :)
Isn't that the great thing about linux? To actually have choices :)

---

### Post by Delkster on 2006-12-12
> **Josh1 said:**
> 5) How do I install the "Radeon 9250" drivers?

Basically, ATI doesn't support the 'old' R200 chips in their proprietary drivers anymore. Older versions of the driver (from early spring 2006 or so) should work.

However, whether you need the driver from ATI is another thing. With R200-based cards such as the Radeon 9250, almost the sole reason to install them would be the faster 3D acceleration they provide. For those cards, the free/open-source driver from the DRI project, which is installed and enabled by default in Ubuntu, also provides basic 3D acceleration but it's generally a lot slower than what the proprietary driver allows.

If your brother doesn't play particularly modern 3D games, the speed and features from the DRI driver are probably quite enough, and that driver is generally more stable and compatible than the proprietary driver from ATI. It's also an easier solution because you don't have to install anything.

One thing the proprietary driver (often dubbed "fglrx") isn't particularly good at is Wine compatibility. The DRI driver may be more compatible for that and thus work better but, on the other hand, its speed usually isn't enough to run modern Windows games on Wine (or even otherwise). Generally, ATI graphics cards aren't very good a choice if you plan on running modern Windows games on Linux (through Wine or Cedega). For older games the DRI driver probably works ok, and I don't suppose Diablo II and Red Alert 2 put much strain on the graphics card, so if I were you, for those I'd just try with the open-source DRI driver. It won't run newer games such as Doom III or UT2004 though, at least not decently.

If you experience stability problems with the DRI driver, try checking what AGP mode you have enabled. You can use the "glxinfo" command in the terminal for that. Look for "OpenGL renderer string" -- with the open-source radeon/DRI driver it should say AGP 1x, AGP 4x or something like that at the end of the string. For me it was originally set at only 1x (I have a Radeon 8500), and I had some stability issues with 3D acceleration. Forcing the AGP mode to 4x seemed to fix that, and I guess it also helps performance.

If you need instructions for that, just ask.

---

### Post by Josh1 on 2006-12-12
> **Odisej said:**
> 1. Gnome is an easier choice. But if you ask me, I would go with KDE instead. It allows for more exploring and finding out about what computers can do and how the machines work. Since he is 13, it maybe good for his training and stirring up his curiosity.

2. Just make them bigger. Use the right mouse button. It is not hard at all.

3. i would suggest trying wine (with winetools) first. If the games still don't work, then cedega may be an answer.

4. KDE is much closer to windows experience than GNOME. The theme, well, I do not think it is important what colours are being used. But you can find some interesting solutions at GNOME LOOK or KDE LOOK websites (just google for them).

5. Maybe this would help: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Odisej

Cheers for the tips, just last time I tried those instructions the Radeon 9250 didn't work at all in the end so I just gave up and bought myself a 6600le and gave my brother the 9250.

> **Sef said:**
> Gnome would be a better choice.  Most people here use Gnome.  Therefore, more help is available.  
Both are good desktops.  It boils down to preference.  Since you have been using Gnome, it would be easier for you to help him.
Games may or may not work on either one, so here are the links to check them out.
Check out [Wine]("3. i would suggest trying wine (with winetools) first. If the games still don't work, then cedega may be an answer.").

Check out [cedega]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1").
Cheers for that! Doesn't cedega run off Wine or something? I tried d2 on my  latest WINE and the install doesn't install...

> **houstonbofh said:**
> I agree with all but KDE.  There are a few tools missing with KDE that make life nice.  (The recommended way to upgrade from Dapper being an example)

Also look at easy-ubuntu or Automatix to install the graphics drivers as well as Codecs, flash, and so on.
Yeah, I use automatix2 for myself, saved me alot of time when I upgraded.

> **Delkster said:**
> Basically, ATI doesn't support the 'old' R200 chips in their proprietary drivers anymore. Older versions of the driver (from early spring 2006 or so) should work.

However, whether you need the driver from ATI is another thing. With R200-based cards such as the Radeon 9250, almost the sole reason to install them would be the faster 3D acceleration they provide. For those cards, the free/open-source driver from the DRI project, which is installed and enabled by default in Ubuntu, also provides basic 3D acceleration but it's generally a lot slower than what the proprietary driver allows.

If your brother doesn't play particularly modern 3D games, the speed and features from the DRI driver are probably quite enough, and that driver is generally more stable and compatible than the proprietary driver from ATI. It's also an easier solution because you don't have to install anything.

One thing the proprietary driver (often dubbed "fglrx") isn't particularly good at is Wine compatibility. The DRI driver may be more compatible for that and thus work better but, on the other hand, its speed usually isn't enough to run modern Windows games on Wine (or even otherwise). Generally, ATI graphics cards aren't very good a choice if you plan on running modern Windows games on Linux (through Wine or Cedega). For older games the DRI driver probably works ok, and I don't suppose Diablo II and Red Alert 2 put much strain on the graphics card, so if I were you, for those I'd just try with the open-source DRI driver. It won't run newer games such as Doom III or UT2004 though, at least not decently.

If you experience stability problems with the DRI driver, try checking what AGP mode you have enabled. You can use the "glxinfo" command in the terminal for that. Look for "OpenGL renderer string" -- with the open-source radeon/DRI driver it should say AGP 1x, AGP 4x or something like that at the end of the string. For me it was originally set at only 1x (I have a Radeon 8500), and I had some stability issues with 3D acceleration. Forcing the AGP mode to 4x seemed to fix that, and I guess it also helps performance.

If you need instructions for that, just ask.

Cheers for the information, will do a little more digging. :)


Cheers everyone for the help & contribution and comments,
Josh

---

### Post by Josh1 on 2006-12-12
OK got everything working how I want it to work, even Diablo 2 runs better under wine then it did under windows! Now time to try and get C&C Red Alert 2 to work :).

---

### Post by hyper_ch on 2006-12-13
If you find out how to setup a D2 BattleNet Server let me know... I'm intereste in running 1.09d again :)

---

