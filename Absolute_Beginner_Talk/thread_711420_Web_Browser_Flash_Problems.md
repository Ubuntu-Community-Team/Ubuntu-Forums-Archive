---
title: "Web Browser Flash Problems"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by platypi on 2008-02-29
When I go to a web-page with some type of flash image, the image tends to overlap everything. This happens in both firefox and epiphany so I'm assuming it's not the browser. An example is at [www.nvidia.com](www.nvidia.com). The flash image below overlaps the pull down menus right above it.

---

### Post by ajgreeny on 2008-02-29
Perhaps related to your resolution.  I've just tried it on my 1280 x 1024 and all is perfectly OK.  Do you run a lower resolution than that?  Presumably the flash animation is a fixed resolution so will be bigger if the screen resolution is lower than mine.

---

### Post by VoiceOvGod on 2008-02-29
Which version of Flash did you install?

I always had problems with the one in the Repos, and I just went to Adobe.

---

### Post by jan quark on 2008-02-29
try to install flash via the adobe site 
tutorial here
[http://laiconic.quotaless.com/tutorial3.html](http://laiconic.quotaless.com/tutorial3.html)

---

### Post by Hospadar on 2008-02-29
I've had that kind of issue before with flash and banners.  I usually just use Adblock Plus (firefox addon) to block the flash banner and then it works fine.

---

### Post by VoiceOvGod on 2008-02-29
See, the only time I've had any kind of trouble with Flash and Ubuntu is on some myspace pages. They have that profile mod that converts their entire profile page to Flash. Clicking on things doesn't respond. I figure it's due to the mod being windows oriented.

---

### Post by platypi on 2008-02-29
Firefox is telling me that i have adobe installed. I tried changing resolution and its set to its highest: 1280x 800 and also does it in smaller resolutions.

---

### Post by VoiceOvGod on 2008-02-29
> **platypi said:**
> Firefox is telling me that i have adobe installed. 

Where did you get the plugin from?

---

### Post by platypi on 2008-02-29
At first I had the flashplug-nonfree installed but removed it, and installed the one from the adobe site. I downloaded the .deb file and installed it that way.

---

### Post by VoiceOvGod on 2008-02-29
Ok.

Have you at all restarted since the install?

---

### Post by platypi on 2008-02-29
Yes, I have restarted and it still does it. Should I remove the plug-in and try again?

---

### Post by VoiceOvGod on 2008-02-29
This is a shot in the dark...

Try closing going to the add/remove programs, and install the restricted bundle. (Ubuntu restricted extras)

If I remember correctly, I have both the adobe plug-in, and that seems to fix the majority of my problems. Again, except the occasional myspace issue.

---

### Post by platypi on 2008-02-29
Ok.Ill try it.

---

### Post by VoiceOvGod on 2008-02-29
Ok, and don't forget to restart the browser.

---

### Post by platypi on 2008-02-29
Hrm. Can't find the restricted bundle in add/removes. Where is it exactly?

---

### Post by platypi on 2008-02-29
Oh. nevermind. i just used the terminal to download it. I'll inform you once its done downloading.

---

### Post by VoiceOvGod on 2008-02-29
Ok...

Applications -> add/remove...

Make sure "Show" says "All available applications"

then search for "restricted"

---

### Post by VoiceOvGod on 2008-02-29
After you get it installed, go to:

```
http://www.bestbuy.com/
```

Mouseover on the little arrows near the top, and let me know what happens.

---

### Post by platypi on 2008-02-29
Well the drop down menus seem to appear cut off. They only show up to five items in each.

---

### Post by VoiceOvGod on 2008-02-29
Ok...

Good to know.

That at least confirms that it's not improper coding on the website. We will continue to use this site for retesting.

Have you installed both the plugins in Firefox?

---

### Post by platypi on 2008-02-29
I will try to uninstall the adobe plugin and the one i just downloaded, right now.

---

### Post by platypi on 2008-02-29
Sorry. misread your post. thought it said re-install. You said 'both plugins', what two are u talking about?

---

### Post by VoiceOvGod on 2008-02-29
By both plug-ins, I mean when you navigate to a site, and a plugin is not installed, it prompts you.

With Flash, it has two plugins. Try installing both.

So, to recap, you'll have the following:

2 firefox plugins
1 official Adobe (from the site)
1 from the restricted package.


After that, restart the browser, go back to the site. 

If it does not work, grab a screenshot of it not working, please.

---

### Post by platypi on 2008-02-29
Ok. here's an screenshot.
[URL="http://img255.imageshack.us/my.php?image=screenshotzk0.png"]
http://img255.imageshack.us/my.php?image=screenshotzk0.png[/URL]

---

### Post by VoiceOvGod on 2008-03-02
Sorry it took me so long to respond.

Had a bunch of stuff going on here.

I am at my desktop rig now, and I can repeat the exact same thing as you.

Looks like it's something that we can't do anything about at this time. Likely will be fixed for FF 3.0

---

### Post by Papa-san on 2008-03-02
It seemed like I never got to my ´desktop´ directory (everything got ´bashed´), but when I go to the bestbuy site, I get the whole dropdown. Is it reasonable to assume it was installed right?

---

### Post by VoiceOvGod on 2008-03-03
Interesting....

What steps did you take to get to that point?

---

### Post by Papa-san on 2008-03-03
I extracted it to my desktop, and every time I tried to navigate to it, it seemed to not be able to find it. I don't know if it was the dollar sign or what, but it just didn't like it... I just kept trying to go through the steps of the tutorial that was linked to here: [http://laiconic.quotaless.com/tutorial3.html](http://laiconic.quotaless.com/tutorial3.html)

Out of frustration and confusion, I just went ahead and ran```
sudo apt-get install flashplugin-nonfree
``` I don't know what it was, but I get good results now. One of MY problem sites was Crosswalk.com. (I think theirs is bad due to bad coding...) However, they are pretty good now as well!

---

