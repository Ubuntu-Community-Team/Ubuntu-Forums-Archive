---
title: "7th linux attemp, video card error this time"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-06-29
ok this is my 7th linux attemp, and it the best so far. Only one error that wont let me boot:

 [[IMG]http://img128.imagevenue.com/loc100/th_15832_P1010183_100lo.JPG[/IMG]](http://img128.imagevenue.com/img.php?image=15832_P1010183_100lo.JPG) [[IMG]http://img121.imagevenue.com/loc86/th_15837_P1010184_86lo.JPG[/IMG]](http://img121.imagevenue.com/img.php?image=15837_P1010184_86lo.JPG)

---

### Post by %hMa@?b&lt;C on 2006-06-29
when you get into the terminal, after going through the error type
```
sudo dpkg-reconfigure xserver-xorg
```
if you have an nVidia card, choose the "Vesa" driver, if ATI, choose "ATI" as the driver

---

### Post by catlett on 2006-06-29
If you have having lots of trouble with your hardware then you are going to have to do your homework. Go to the site of your video card and get the specs. When you run the above command choose the advanced mode. This will let you enter the vertical and horizontal refresh rates, color capability abd resolutions etc. Plus the make and model. The more info you have the better chance you have of x being configured correctly.
What kind of video card do you have? Are you using the live cd installer or the text based alternate installer?

---

### Post by IDontKnow9998 on 2006-06-29
I either have

[http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=950](http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=950)
or
[http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=947](http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=947)

[QUOTE=jeffc313]when you get into the terminal, after going through the error type
```
sudo dpkg-reconfigure xserver-xorg
```
if you have an nVidia card, choose the "Vesa" driver, if ATI, choose "ATI" as the driver[/QUOTE]

When I do that.... It wants my password. But wont let me input it. it will say "password: " and anything I hit on the keyboard will not show up. Although the little underscore thing does blink it does not work. I even tried to input my password twice (in case typo) and still no go.

---

### Post by mustang on 2006-06-30
[QUOTE=IDontKnow9998]I either have

[http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=950](http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=950)
or
[http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=947](http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=947)



When I do that.... It wants my password. But wont let me input it. it will say "password: " and anything I hit on the keyboard will not show up. Although the little underscore thing does blink it does not work. I even tried to input my password twice (in case typo) and still no go.[/QUOTE]

UNIX and most linux distributions do this on purpose---it hides the password length from anyone who shouldn't need it. Just type in your password as usual and when done, hit enter. Don't worry about the cursor moving or blinking, it's all intended for security purposes.

---

### Post by Rich3077 on 2006-06-30
I had the same problem. Do a search in the forums for "boot cannot start GUI" or something simular. I dont remember exactly what I did but a simple forum search solved my problem. Since you are a fellow nOOb I want to say that the most common problem I have had when following how-to's and such not following the EXACT command.. including EXACT spaces and capitilization. It still frustrates me when I think I could not cd to my desktop because I did not capitilize the D.
Dont give up, once you get the graphical desktop working and internet connection working, solving anything else is a breeze because you can search for answers within Ubuntu without having to boot back into Windows or going to a different computer. If you are lucky enough to have a laptop then you have it made as you can search the lappy for answers. I have a laptop and didnt even think of using it to help my install untill it was to late. Once you have it running you will be damn glad you didnt give up. 


Peace
Rich

---

### Post by IDontKnow9998 on 2006-06-30
[QUOTE=mustang]UNIX and most linux distributions do this on purpose---it hides the password length from anyone who shouldn't need it. Just type in your password as usual and when done, hit enter. Don't worry about the cursor moving or blinking, it's all intended for security purposes.[/QUOTE]

I did.... I tried twice....

edit: Also I could boot into the GUI. I went into windows. Went back to linux and I stoped working :\

edit: Third time worked. Had to input the password. Then after the error it asked my username, and after that password....

hmmm.... but it asked me all these question :( Now my resolution is screwed up :( its like 1024x768 :\ Is there anyway I can get it 2 auto detect?

---

### Post by IDontKnow9998 on 2006-06-30
ok I got linux-image-k7 & nvidia-glx....

With the nvidia install system was running much better (id move the selector around and it would lag before that :P)....

But I still cant fix my resolution :( Any ideas?

---

### Post by mozetti on 2006-06-30
Some of the questions it asks you when you reconfigure your X-server are what resolutions you want that your monitor supports. You can reconfigure X and look for that screen - it should basically list a bunch of different resolutions, and just mark each one that you want to have available to you.

---

### Post by IDontKnow9998 on 2006-06-30
[QUOTE=mozetti]Some of the questions it asks you when you reconfigure your X-server are what resolutions you want that your monitor supports. You can reconfigure X and look for that screen - it should basically list a bunch of different resolutions, and just mark each one that you want to have available to you.[/QUOTE]

I did.... I saw on X on 1600x1200, so I highlighted it and hit enter....

Hmm maybe ill do it again tomorrow and do it slower :P

---

### Post by tseliot on 2006-06-30
[QUOTE=IDontKnow9998]ok I got linux-image-k7 & nvidia-glx....

With the nvidia install system was running much better (id move the selector around and it would lag before that :P)....

But I still cant fix my resolution :( Any ideas?[/QUOTE]
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

---

### Post by IDontKnow9998 on 2006-06-30
**edit: It fixed**

[QUOTE=tseliot]Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10[/QUOTE]

I re-did step 5 about 5 times now...

As for steps 10... It already seems to have all the res I need.... But they arent in my System > preferences > screen resolution....

```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"vesa"
	BusID		"PCI:5:0:0"
	Option "UseEDID" "False"
EndSection
```

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200_60"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

All I have is a refresh rate of 85MHZ with resolution of 640x480, 800x600, 1024x768

Also, just to make sure.... all I need 2 do is logout right? I do not need 2 restart?

**Edit: I screwed around with it more (tried to change it to 640x480 and the GUI went 100% screwy), restart. Got the blue screen, re-ran the dpkg again and now the resolution is perfect**
edit2: Now its laggy tho.... I guess it was not the nvidia drivers that speed it up... it was the ultra low res :P

---

### Post by egon spengler on 2006-06-30
[QUOTE=Rich3077]It still frustrates me when I think I could not cd to my desktop because I did not capitilize the D.[/QUOTE]

You may find [this](http://linuxart.com/log/archives/2005/10/13/super-useful-inputrc/) helpful

---

### Post by steve.horsley on 2006-06-30
> Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"vesa"
	BusID		"PCI:5:0:0"
	Option "UseEDID" "False"
EndSection
If you have a 6600GT then you will be wanting to use the proper nVidia driver. Instead of Driver: "vesa", try Driver: "nvidia". This required the restricted modiles to be installed, but you sad you have already installed those.

---

### Post by IDontKnow9998 on 2006-06-30
[QUOTE=steve.horsley]If you have a 6600GT then you will be wanting to use the proper nVidia driver. Instead of Driver: "vesa", try Driver: "nvidia". This required the restricted modiles to be installed, but you sad you have already installed those.[/QUOTE]

If I do that.... I get the same error I got when I first made the tread (and I no longer use Vesa, its NV)....

But I wont be fidling with this for the next ~40 hours

---

