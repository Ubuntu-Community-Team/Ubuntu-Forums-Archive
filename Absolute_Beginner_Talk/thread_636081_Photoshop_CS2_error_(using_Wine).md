---
title: "Photoshop CS2 error (using Wine)"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Locutux on 2007-12-09
Yesterday, I was running Photoshop CS2 on Wine and it worked perfectly.
Today I'm trying to start it again, and I'm getting this error message:

"Unable to continue because of a hardware or system error. Sorry but this error is unrecoverable." 

Can anyone help me locating and solving this problem?

---

### Post by Locutux on 2007-12-09
Anyone?

---

### Post by nikoPSK on 2007-12-09
do you need ti specifically for something? you could always try the gimp.

---

### Post by Arwen on 2007-12-09
What version of wine do you use?

---

### Post by Locutux on 2007-12-09
@nikoPSK,

I need Photoshop, I tried GIMP but it doesn't satisfy my needs and habits. :) 

@Arwen,

My version of Wine is 0.9.46. Should I update?

---

### Post by Locutux on 2007-12-09
I tried removing PS CS2 from the Wine virtual Program Files folder, and coping it again from the NTFS partiton and it doesn't work. Also, removing the entries in the virtual registry didn't worked.

---

### Post by Locutux on 2007-12-10
I know I'm pushing this, but I really need a solution. :(

---

### Post by Locutux on 2007-12-12
Still having the problem. :/

---

### Post by nikoPSK on 2007-12-12
I do not unfortunately know. If you just want the feel of photoshop you can get gimpshop...:D
 
Niko

---

### Post by GeorgiaBoot on 2007-12-12
Well I understand you want CS2 and I would much rather have my CS3 on Ubuntu than Gimp but I feel it just is not worth it.

One day it might work the next it won't. These programs are to unstable under wine.

What are you using CS2 for? 

Honestly (Gimp) is close to CS2. Unless you ACTUALLY need those extras it is not worth it.

I personally can't be without CS3 (For Work) so I just dual boot to XP. 

Do you have a windows Machine?

---

### Post by disturbedite on 2007-12-12
> **Locutux said:**
> @nikoPSK,

I need Photoshop, I tried GIMP but it doesn't satisfy my needs and habits. :) 

@Arwen,

My version of Wine is 0.9.46. Should I update?

you're using a very outdated version of wine.  (0.9.50 is the latest).  set up the official wine repo & install 0.9.50.

newer versions of wine have much better support for PS CS2.  but unfortunately, not for PS CS3 last time i checked.

---

### Post by Locutux on 2007-12-13
GeorgiaBoot, I need Photoshop with my plugins, brushes and everything installed on it. :) If it wasn't so necessary, I wouldn't bother you, and myself. :)

Anyway, I'll try updating Wine, or I'll just boot in WinXP.

Thanks.

---

### Post by disturbedite on 2007-12-15
gimp 2.4.x supports photoshop brushes now...

btw, wine 0.9.51 is out now.

---

### Post by Locutux on 2007-12-19
I updated Wine, I'm using the latest version (0.9.51), and Photoshop still doesn't work.

---

### Post by Kiwilad on 2007-12-30
I upgraded from Ubuntu 7.04 to 7.10 last night, and for the first time ever, I managed to get photoshop to run by right clicking photoshop.exe and open using wine. It took a long time to open and when I started working on a photo it hung on me, but it was promising. 

This morning I tried to run it again, and now it won't open at all, and gives me the error message "Unable to continue because of a hardware or system error. Sorry but this error is unrecoverable." 

I have no idea how to work out whether I'm using the latest version of wine, but I'm assuming it's the latest version since I completed updated everything last night.

Any help would be appreciated, but bear in mind that detailed instructions for a complete newbie would be real handy.

Thanks heaps

---

### Post by frenchsquared on 2007-12-30
I really want CS3 on ubuntu so I would love to know what you guts come up with

it has nothing to do with photoshop, CS3 has 7 other programs that I need everyday

---

### Post by pointyblue on 2007-12-30
Have you tried using Crossover Linux in stead of Wine?

Don't know if it'll work better than Wine but you could give it a try with a trial version.

[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

You should probably uninstall Photoshop, install Crossover and then install Photoshop again.

---

### Post by Kiwilad on 2007-12-31
I did a google search and came up with the following website

[http://kb.adobe.com/selfservice/viewContent.do?externalId=333240&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=333240&sliceId=1)

I took the first option which was to "Start the application while holding down Ctrl+Alt+Shift. Click Yes to the message "Delete the Adobe Photoshop Settings file?" when it appears." and hey presto, photoshop opens. There's definately some bugs in the system though, when I go to open a new photo from file, I cant use the arrow keys to scroll through the photos without the system hanging... if I use the mouse to click on them, it's fine... haven't really explored it much more than that for the time being

.... to be honest, the updated version of GIMP that came with 7.10 looks pretty interesting, I may persist with that for a while too

---

### Post by kenboyles72 on 2007-12-31
I had the same problems with cs2, even with the latest version of wine. Even though the latest wine did offer more, cs2 still bugged out like you. I read that cs2 had different configuration than older versions that made it unstable in wine. I too, prefer photoshop over gimp and was getting upset that I couldn't get it to work. But fortunately, I also had ps7 which I installed with no problems and works great. At least I have ps installed. I'm dual booted with XP, so if there's something that I absolutely have to do in cs2, then I'll just reboot into XP.

---

### Post by AcidicChip on 2008-03-24
Let me start by saying, I can't stand GIMP... It's a great tool, I know, but it's just not the same...

Second, the solutions is to open up your terminal and type:
```
wget http://kegel.com/wine/winetricks
sh winetricks corefonts vcrun6
```

That should install some additional fonts that the "Registration" dialog needs to nag at you about, and allow you to continue using it.

Let me know if this ends up working for you.

---

