---
title: "Weird colors on video playback (imac 9,1, karmic 9.10)"
date: 2009-11-05
forum: Apple Hardware Users
---

### Post by jamesey on 2009-11-05
I upgraded from 9.04 to 9.10 without any issues. Everything including video worked fine. then i did a upgrade that included a linux kernel update, and all my video looks like the picture below. it's like the negative is being shown. this happens on all video players, across multiple video formats. Anyone know what's going on? 

[IMG]http://i63.photobucket.com/albums/h138/jameseyjamesey/Screenshot-CurbYourEnthusiasmS07E07.png[/IMG]

---

### Post by rjcalifornia on 2009-11-05
it happened to me.... I did a clean reinstall... :(

---

### Post by ceasol on 2009-11-06
If you have Nvidia Driver downgrade from 185 to 173 that works for me

---

### Post by ad5 on 2009-11-06
Before you downgrade your graphics driver check whether your color balance in Totem is correct!
Go to: Edit > Preferences then to the display-flag and choose the "Reset to Defaults"-button. 
That worked for me since the color balance was somehow displaced after upgrading to karmic.

---

### Post by madverb on 2009-11-06
Haha, can't believe you would do a reinstall for that. I had the same problem at the last post.
Changed the Hue back to default and all was good.

---

### Post by ceasol on 2009-11-06
> **ad5 said:**
> Before you downgrade your graphics driver check whether your color balance in Totem is correct!
Go to: Edit > Preferences then to the display-flag and choose the "Reset to Defaults"-button. 
That worked for me since the color balance was somehow displaced after upgrading to karmic.

The problem is not just Totem, any video player is affected for this issue (VLC, Mplayer and so) in all the other applications the colors are OK (pictures, desktop, etc).

The problem was reported @ [Nvidia forum]("http://www.nvnews.net/vbulletin/showthread.php?t=133613") with Ubuntu 9.04 and Nvidia 185. There're some pictures.

---

### Post by jamesey on 2009-11-06
anyone know if the 190 drivers will fix this?

edit: they dont

---

### Post by madverb on 2009-11-06
Yes, it happens in everything video, even MythTV.
But changing the setting in Totem changes it system-wide.

---

### Post by rjcalifornia on 2009-11-06
is that curb your enthusiasm?

---

### Post by jeraldm on 2009-11-07
Open totem movie player and navigate to edit -> preferences -> Display and click on Reset to defaults.  No need to restart.  This fixed the issue.
The problem is due to the wrong hue setting.

---

### Post by catalin.soare on 2009-11-08
I do agree with you about the solution but why does the problem apear again and again?

For me, I think it's a bug... :sad:

---

### Post by firesock on 2009-11-08
thank you very much! worked for me... karmic it's amazing...

---

### Post by gavinhughes86 on 2009-11-25
> **ad5 said:**
> Before you downgrade your graphics driver check whether your color balance in Totem is correct!
Go to: Edit > Preferences then to the display-flag and choose the "Reset to Defaults"-button. 
That worked for me since the color balance was somehow displaced after upgrading to karmic.


Cheers worked for me too!
Im using nvidia 185 drivers on a dell m1330 and 64 bit ubuntu

---

### Post by Duanebuntu on 2009-12-06
Awesome. This solved it for me.

---

### Post by bcn17 on 2009-12-07
The fixed I used after upgrading from 9.04 to 9.10. 

In terminal:
```
gstreamer-properties
```

Select Video tab, then under Output, choose the Plugin drop down menu, and change the value to X window system (No XV)

I'm not exactly sure what this is, or if it is different than the default settings fix in the end but it worked!

---

### Post by shuck on 2009-12-11
Open movie player. Edit>preferences>Display>Reset to Defaults... it works for me too..

---

### Post by kedmond on 2010-02-15
> **jeraldm said:**
> Open totem movie player and navigate to edit -> preferences -> Display and click on Reset to defaults.  No need to restart.  This fixed the issue.
The problem is due to the wrong hue setting.

THANKS!  You rock.

---

### Post by bangbong on 2010-02-23
thanks! , work for me too...

---

### Post by hellblazer on 2010-06-07
Yeah! Works after kernel update for Lucid too. Thanks!

---

### Post by domonics on 2010-08-30
> **bcn17 said:**
> The fixed I used after upgrading from 9.04 to 9.10. 

In terminal:
```
gstreamer-properties
```

Select Video tab, then under Output, choose the Plugin drop down menu, and change the value to X window system (No XV)

I'm not exactly sure what this is, or if it is different than the default settings fix in the end but it worked!

This worked for me. 10.04 64bit:o:o:P:P

---

### Post by braincookie on 2010-11-13
For me, resetting default values did not work, instead I had to put the Hue to minimum value:

In a console window type

totem

then go to the Edit preferences->View tab and put the hue (the very last slider) all to the left.

Confirm and even VLC works fine afterwards.

---

### Post by Drone4four on 2010-11-25
> **bcn17 said:**
> The fixed I used after upgrading from 9.04 to 9.10. 

In terminal:
```
gstreamer-properties
```

Select Video tab, then under Output, choose the Plugin drop down menu, and change the value to X window system (No XV)

I'm not exactly sure what this is, or if it is different than the default settings fix in the end but it worked!

Thank you, bcn17.  This worked for me on 10.10, although I gstreamer-properties was already installed.

---

### Post by eviljoel on 2012-03-27
> **ad5 said:**
> Before you downgrade your graphics driver check whether your color balance in Totem is correct!
Go to: Edit > Preferences then to the display-flag and choose the "Reset to Defaults"-button. 
That worked for me since the color balance was somehow displaced after upgrading to karmic.

Thanks.  This totally worked for me!

---

