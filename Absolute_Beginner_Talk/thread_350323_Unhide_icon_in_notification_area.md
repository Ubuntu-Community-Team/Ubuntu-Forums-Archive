---
title: "Unhide icon in notification area"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by rigol on 2007-01-31
Hi there,

Accidentally I right-clicked Thunderbird's icon in the Notification Area and checked "hide" (there is just "hide" and "unhide" to choose from). Now the status icon is gone (just Thunderbird's, the Notification Area is still there). 

How can I undo that? I badly need it to minimize Thunderbird to tray.


Thanks for any help!

---

### Post by rigol on 2007-02-02
Noone?

---

### Post by TwistesdTexan on 2007-02-02
I'm confused about your post. I don't have evolution but I do have Thunderbird and I don't get a icon in the notification area. But if you have the programs started, is there a box in the task bar you can minimize?

---

### Post by rigol on 2007-02-02
Yes, I really have a Thunderbird icon in the Notification area, just like Opera's. 
And yes, I can still minimize to the taskbar, but I don't want that because I dont want to see Thunderbird in the taskbar, but minimized to the tray, so that I'm just seeing its icon on the right.

---

### Post by rigol on 2007-02-03
Please?

---

### Post by rigol on 2007-02-04
*bumb* :(

---

### Post by rigol on 2007-02-05
It can't be THAT difficult?! There must be a way to bring the icon back...

---

### Post by rigol on 2007-02-06
*?* :confused:

---

### Post by ComplexNumber on 2007-02-06
**rigol**
just run thunderbird again. have a look in the settings for thunderbird in the menu for thinderbird. i don't use thunderbird but it will be something "settings", "preferences, etc.

---

### Post by rigol on 2007-02-07
I tried that, Tunderbird is running constantly.  I had a look at the settings with the Config Editor (about:config), but I couldn't figure out which one to change and all the other options don't apply to the problem. 

I also believe it has something to do with Ubuntu's settings, not Tunderbird one's.

---

### Post by rigol on 2007-02-08
Anyone?

---

### Post by rigol on 2007-02-18
:-s

---

### Post by mcduck on 2007-02-18
The setting is either in Thunderbird's preferences, or in Thunderbird's extensions menu. I can't confirm which one as I don't have Thunderbird installed right now.

Anyway, I'm pretty sure that the systray icon is not default feature of Thunderbird and getting it required installing some extra stuff. That's probably why people aren't able to give you much help with it.

---

### Post by bryonak on 2007-03-01
You might want to try searching in the gconf-editor (menu->System Tools->Configuration Editor, if you have it undhidden in the Edit Menus Dialog (right click on menu image)... or just type into a terminal: gconf-editor).
In the editor, look for apps->panel. There you can search through the settings of applets->notification area (just click on the keys in the right window to get a description) or look through the other keys in apps->panel.
Sorry for not giving any exact info, but I'm actually not able to evaluate it any further since this isn't my PC and doesn't have Thunderbird installed.. Hope it helps a bit anyway ;)

---

### Post by rigol on 2007-03-06
Thanks for your answer, bryonak. This was a close shot, but I didn't find the setting to unhide Thunderbird's icon. 

I also had a look at Thunderbird's about:config, but didn't find the setting either. 

So this is driving me nuts. There has to be a way?!

---

### Post by kristalsoldier on 2007-03-06
From what I understand there is something going on with T'Bird in Edgy (Ubuntu?). For example, if you download T'Bird via the respositories the version you get does not allow you to minimize to the tray. But apparently, if you download it independently and then untar it etc. you get the version that allows for it. So, I think it depends on which version you have.

I use the version downloadable from the repositories and don't have the minimize to tray or 'new mail' notification. So, I use the system-based Mail notification. I got that info from these threads. I'll try to find the appropriate link and will edit into this post...if that helps at all.

Also,  as someone pointed out above, there is a convoluted way to get it...I just chose not to use it, especially because the system-based received mail allows me to add all my email accounts to it so I get a notiication when I recieve email in any of them.

---

### Post by rigol on 2007-03-06
I have the repositorities' one installed (Dapper) and actually I *can* minimize to tray via the icon **that's now hidden** (just click it and it minimizes to the tray) so I can't do it right now because I don't have that icon anymore. 

For new mail notification I use the extension "New Mail Icon" so I still get a new icon in the notification area when new mails arrive - but this icon disappears as soon as I click it to bring THunderbrid to the foreground for reading the new mail.

---

### Post by kristalsoldier on 2007-03-06
> **rigol said:**
> I have the repositorities' one installed (Dapper) and actually I *can* minimize to tray via the icon **that's now hidden** (just click it and it minimizes to the tray) so I can't do it right now because I don't have that icon anymore. 

For new mail notification I use the extension "New Mail Icon" so I still get a new icon in the notification area when new mails arrive - but this icon disappears as soon as I click it to bring THunderbrid to the foreground for reading the new mail.

I wish I had the one from Dapper:(

The version I have does not allow for that plugin that you are referring to...some conflict with FF, I believe!

---

### Post by wastrel on 2007-03-13
Sounds like you're using the mozilla new mail icon extension... 

( [http://moztraybiff.mozdev.org/index.html](http://moztraybiff.mozdev.org/index.html) )

Their FAQ says it's against the Gnome user interface guidelines to have the icon visible in the system tray at all times.  (3rd question on this page:  [http://moztraybiff.mozdev.org/faq.html](http://moztraybiff.mozdev.org/faq.html) )

So it sounds like the answer is that it's only going to be visible when you get new mail.

---

### Post by wastrel on 2007-03-26
OK I may have been wrong, I installed the Thunderbird new mail extension and there is an option to have it always available in the system tray.  Go to Tools -> Extensions, hilight New Mail Icon and click Preferences, then check the box for "always show in tray"

---

### Post by rigol on 2007-03-28
Wow thanks, that's the solution! And I thought, I checked all "New Mail Icon"'s options... :oops: 

Solved, thanks to wastrel :)

---

