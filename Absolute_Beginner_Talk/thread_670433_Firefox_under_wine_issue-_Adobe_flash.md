---
title: "Firefox under wine issue- Adobe flash"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by pollywog on 2008-01-17
Hi,  I'm trying to set up a desktop launcher that will bring my young daughter to a particular website (PBS Kids), which I was initially able to do easy enough by creating a desktop launcher with the command "firefox http://pbskids.org/". This launched me directly to the desired website, but unfortunately, Adobe Shockwave player is needed to use much of the content. I next downloaded the windows version of Firefox, installed it under Wine, and installed the Shockwave plug in. All great except that I also need Adobe Flash plug in, which will not install for me under Wine. When I attempt to install it, the installer immediately tells me that Firefox is not installed- which it is- and goes no further. A second issue is that I don't know how to create a launcher that will launch the Wine Firefox to that particular site, if that is even possible. Any suggestions would be greatly appreciated.

---

### Post by stchman on 2008-01-17
> **pollywog said:**
> Hi,  I'm trying to set up a desktop launcher that will bring my young daughter to a particular website (PBS Kids), which I was initially able to do easy enough by creating a desktop launcher with the command "firefox http://pbskids.org/". This launched me directly to the desired website, but unfortunately, Adobe Shockwave player is needed to use much of the content. I next downloaded the windows version of Firefox, installed it under Wine, and installed the Shockwave plug in. All great except that I also need Adobe Flash plug in, which will not install for me under Wine. When I attempt to install it, the installer immediately tells me that Firefox is not installed- which it is- and goes no further. A second issue is that I don't know how to create a launcher that will launch the Wine Firefox to that particular site, if that is even possible. Any suggestions would be greatly appreciated.

Is there something wrong with Firefox under Ubuntu?  

Install the Flash 9 plugin for Firefox and make pbskids.org the homepage.

Problem solved.

---

### Post by pollywog on 2008-01-17
No complaints about Firefox. Adobe just never made a Linux version of it's Shockwave player. To access this content you MUST use a Windows based browser-hence Firefox under Wine. Adobe Flash Player will not play Shockwave Flashes.

---

### Post by nikoPSK on 2008-01-17
can't you just use firefox under ubuntu?

---

### Post by pollywog on 2008-01-17
Well I do use Firefox under Ubuntu. I love It!  Works Great!- Except that it doesn't play Shockwave Flashes. It tells you that plugin is missing, then let's you know that the required plugin doesn't exist.

---

### Post by pollywog on 2008-01-17
By the way, just to clarify, my question is not so much pertaining to getting this Shockwave Flash to work under Linux- feel free to correct me if you know me to be wrong here- but my research so far has indicated that Shockwave can't be run natively under Linux. I'm mainly trying to figure out why the plain Adobe flash is not installing under this Wine Firefox install. I see no mention of anyone else having issues. Again I do have Adobe Flash installed on my Linux Firefox, and it is working fine.

---

### Post by pollywog on 2008-01-18
After re-booting a couple of times, I was able to install adobe reader into my wine-firefox install. I just wonder if anyone who is savvy with the command line could show me how to open firefox, under wine, and navigate to a particular website. Wouldn't I then be able to enter that command into my launcher?

---

### Post by FuturePilot on 2008-01-18
That site seems to use Flash, not Shockwave.
The fact that you cannot seem to install the Flash plugin in Ubuntu may be attributed to the flashplugin-nonfree md5sum mismatch bug. See here for a solution
[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")

---

### Post by pollywog on 2008-01-18
Thank You for the advice.  I've just about got this whipped. Here's the deal. The reason that I'm trying to do this in the 1st place is that my wife wants to get this new gizmo for the kids that hooks up to the computer, and has buttons which can be configured to bring the child directly to a particular website, thus not requiring navigating in a browser. I, being a cheapskate, said "Oh, I'm sure I can rig something up that's comparable." I figured out that I could make launchers on my desktop, each with a custom command such as "firefox http://pbskids.org/games/index.html" to easily bring them directly to a particular site, and by de-selecting all of the toolbars, I could keep them from navigating away from the site. Then I found that some pages such as

[http://pbskids.org/barney/children/games/imagination_game.html](http://pbskids.org/barney/children/games/imagination_game.html)

required Shockwave to work. You can't use Shockwave natively under Linux, so I installed the windows version of Firefox, under Wine. I was then able to install the Shockwave player, and the above site worked. I tried to install Adobe Flash, but initially ran into problems getting it to install. Turns out that all I needed to do was re-boot the machine, then install the flash player. I guess Wine is more like Windows than I thought. So I now have a Wine version of Firefox with both Adobe Flash and Shockwave install and working!:)  After some further research, I found that using a launcher with the command  ```
wine "c:\program files\Mozilla Firefox\firefox.exe"
```  I could directly launch this application. I still don't know how ho to make the launcher bring me to a particular page, so I did just settle for setting PBS Kids as the home page for this particular browser, and use the native linux app for the rest of the launchers associated with this little project. I hope that this helps someone.

---

