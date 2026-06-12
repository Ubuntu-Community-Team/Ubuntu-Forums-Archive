---
title: "Flash Player 8"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-06
I am sure you all heard of that dandy website called myspace

It says i need to install flash player 8

Anyone have any good links i can click to install flash player 8

haha

Thanx

---

### Post by IrishGangsta on 2006-07-06
Actually i installed Wine - the Internet Explorer simulator

I added it in the add/remove programs list and typed sum code in terminal

But how do i actually put Wine to work so i can download Flash Player 8????

---

### Post by crystal on 2006-07-06
You are using Firefox, right? I was in a daze when I did it, but I think I clicked on the "no flash installed" icon, and then downloaded what Firefox suggested.

---

### Post by FredB on 2006-07-06
[QUOTE=IrishGangsta]Actually i installed Wine - the Internet Explorer simulator

I added it in the add/remove programs list and typed sum code in terminal

But how do i actually put Wine to work so i can download Flash Player 8????[/QUOTE]

Wine is not the IE simulator. It is a win32 translator for using win32 programs on linux.

And Flash 8 ? It will never be on Linux. Since Adobe bought Macromedia, flash for linux is not their top priority !

---

### Post by kigina on 2006-07-06
[http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by FredB on 2006-07-06
No. Wrong version.

Version:  	7,0,63,0

Same player, try again !

---

### Post by kigina on 2006-07-06
I have Flash 7 and all of the myspace stuff works just fine.  I even used that installer (on Mandriva, Ubuntu I used Automatix).

---

### Post by kigina on 2006-07-06
actually, just try this.

[http://getautomatix.com/](http://getautomatix.com/)

---

### Post by FredB on 2006-07-06
[QUOTE=kigina]I have Flash 7 and all of the myspace stuff works just fine.  I even used that installer (on Mandriva, Ubuntu I used Automatix).[/QUOTE]

So why in first post we can read :

"It says i need to install flash player 8"

I am kinda lost ;)

---

### Post by crystal on 2006-07-06
> So why in first post we can read :

"It says i need to install flash player 8"
Perhaps Flash Player was not installed at all, so the website suggested Flash Player 8.

---

### Post by Nikusan on 2006-07-06
[QUOTE=crystal]Perhaps Flash Player was not installed at all, so the website suggested Flash Player 8.[/QUOTE]

Correct.

Just install the package flashplugin-nonfree. Couldn't be simpler. You might be interested in this adobe blog about flash player 9 for linux: [http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)

---

### Post by aeto on 2006-07-06
there'd b no flash player 8 for linux. not even 8.5. However, a team is getting ready a "Flash Player 9 for Linux" sometime next year (2007). For the time being, u cant access any flash player 8 site. I'v been trying ways to access [www.dimarzio.com](www.dimarzio.com) but nothing works. So tough luck. And no, i dont think if u install any flash player then a site with ver 8 would recognise it. They r simply made to work only with 8.

---

### Post by aysiu on 2006-07-06
If you absolutely need Flash 8, just install Windows Firefox through Wine and install Flash 8 through that.

---

### Post by JerryC on 2006-07-06
Can we get a 64 bit flashplayer anywhere?

JC

---

### Post by FredB on 2006-07-06
I think it is like flash 8 for linux... So...

---

### Post by IrishGangsta on 2006-07-06
i am glad to see all of the feedbak for this
I guess i'll just donwload flash player 7 for now until 9 comes out.

---

### Post by IrishGangsta on 2006-07-06
Ok here is a beginners question. 
I downloaded flash player 7 and then it opens in the archive manager
And wen i click it 5 more files open up.

From the archive manager, how do i actually install the flash player

Thanx

---

### Post by aysiu on 2006-07-06
From the archive manager, extract the .tar.gz to be a regular folder.

Then from the terminal *cd* (change directory) to that folder. For example, if the folder is called *flashplayer*, you would do ```
cd ~/Desktop/flashplayer
ls
``` The last command will list what files are in there. One should be an installer. I don't know the name of the installer, but you can modify these instructions accordingly: ```
sudo ./flashplayer_installer_7
``` and then install it to the /usr/lib/firefox directory.

===========================

Of course, I think it's a lot easier to just [enable more repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

---

### Post by IrishGangsta on 2006-07-06
yesterday i have done the enable more repositories thing

So all i had to do was enter that single line into the terminal
Then the terminal did its thing

so i guess its installed
thank you

---

### Post by IrishGangsta on 2006-07-06
ok i guess i installed flash player 7 i suppose
im not sure how to verify i installed it but i beleive i did

But then on sum website it says i need flash player 8

SO am i S.O.L. until flash player 9 for linux???

Any input would help thanx

Also, what totem should i use to play windows media movies from websites

---

### Post by aysiu on 2006-07-06
No, you're not SOL. Read [post #13](http://www.ubuntuforums.org/showpost.php?p=1220626&postcount=13).

---

### Post by IrishGangsta on 2006-07-06
I think i have tried to install Wine or something
But i am clueless in how to use it
I am not sure if it even works

If you have any instructions it would be greatly appreciated
thanx

---

### Post by aysiu on 2006-07-06
Before you follow these instructions, you should

1. Make sure you have extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. Install Wine: ```
sudo aptitude update && sudo aptitude install wine
```

Then you can follow the instructions:
[http://www.ubuntuforums.org/showpost.php?p=1219573&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1219573&postcount=6)

---

### Post by IrishGangsta on 2006-07-06
Install it to /home/anubix/firefox in the setup wizard. Finish the rest of the wizard, but do not launch Firefox at the end.
Code:

mv ~/firefox ~/.firefox wine ~/.firefox/firefox.exe


-----------------------------------------------------------------------------------------------
I do not understand how to save it to that location
All i found was /home/mike/firefox

I saved it to that location then i typed that code into the terminal and it said location not found.

But everything before that last step worked.

---

### Post by aysiu on 2006-07-06
All you found was /home/mike/firefox? That's where you're supposed to install it.

Once you've installed it, this command just makes it a hidden folder (so it's not cluttering up your home directory: ```
mv ~/firefox ~/.firefox
``` Then this command launches the Wine Firefox ```
wine ~/.firefox/firefox.exe
``` If you don't want to make it a hidden folder, just do this ```
wine ~/firefox/firefox.exe
```

---

### Post by deanlinkous on 2006-07-07
> **aeto said:**
> there'd b no flash player 8 for linux. not even 8.5. However, a team is getting ready a "Flash Player 9 for Linux" sometime next year (2007). For the time being, u cant access any flash player 8 site. I'v been trying ways to access [www.dimarzio.com](www.dimarzio.com) but nothing works. So tough luck. And no, i dont think if u install any flash player then a site with ver 8 would recognise it. They r simply made to work only with 8.

:)
[http://img208.imageshack.us/img208/2544/screenshot7nw.png](http://img208.imageshack.us/img208/2544/screenshot7nw.png)

little tricks to trick the tricksy

---

### Post by deanlinkous on 2006-07-07
Does anyone have other flash sites that do not work? I would be very interested.... Thanks

---

