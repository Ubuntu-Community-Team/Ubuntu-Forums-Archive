---
title: "Firefox stopped displaying websites...well...working!"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by dollydoll on 2005-08-30
Hi...something really-really odd just happened to me:
I restarted my computer and Firefox doesn't display:
1)its own toolbars/bookmarks/tabs/menu-bars/etc
2)any web site, including its own firefox-google start page...just some lines, and some colours, some logos...
3)konkeror and the rest of my system works fine, so it's not my G-Force Nvidia video card! :)
How can I re-install firefox? or well...how do I fix it?
Thanks!

---

### Post by aysiu on 2005-08-30
[QUOTE=dollydoll]Hi...something really-really odd just happened to me:
I restarted my computer and Firefox doesn't display:
1)its own toolbars/bookmarks/tabs/menu-bars/etc
2)any web site, including its own firefox-google start page...just some lines, and some colours, some logos...
3)konkeror and the rest of my system works fine, so it's not my G-Force Nvidia video card! :)
How can I re-install firefox? or well...how do I fix it?
Thanks![/QUOTE]

Make a backup copy of /home/*username*/.mozilla/default/*profilename*/bookmarks.html

Fill in your actual username and actual profile name for the above mentioned names.

Then, delete /home/*username*/.mozilla.
Then, relaunch Firefox.

---

### Post by dollydoll on 2005-08-30
[QUOTE=aysiu]Make a backup copy of /home/*username*/.mozilla/default/*profilename*/bookmarks.html

Fill in your actual username and actual profile name for the above mentioned names.

Then, delete /home/*username*/.mozilla.
Then, relaunch Firefox.[/QUOTE]

Hi...thx a lot!! I relaunched firefox and...it didn't work!! any other hints?

---

### Post by aysiu on 2005-08-30
[QUOTE=dollydoll]Hi...thx a lot!! I relaunched firefox and...it didn't work!! any other hints?[/QUOTE] Did you *just* relaunch Firefox, or did you do all the other things I suggested *first* and *then* relaunch Firefox?

---

### Post by dollydoll on 2005-08-31
[QUOTE=aysiu]Did you *just* relaunch Firefox, or did you do all the other things I suggested *first* and *then* relaunch Firefox?[/QUOTE]

he-he-he! of course I did what you said! :) and then...I relaunched firefox, but good news for me...
I just got another hint:
sudo apt-get remove firefox
 sudo apt-get isntall firefox
i know it's not the best...but now firefox works as it used to...
Do you know why did that happen?
BTW, since I back-up my bookmarks and settings, how do I set them up in this new firefox that I jast installed??
many thanks! :)

---

### Post by aysiu on 2005-08-31
[QUOTE=dollydoll]he-he-he! of course I did what you said! :) and then...I relaunched firefox, [/quote] I wasn't sure. Just wanted to double-check.

> 
but good news for me...
I just got another hint:
sudo apt-get remove firefox
 sudo apt-get isntall firefox
i know it's not the best... Why isn't it the best?

> 
but now firefox works as it used to...
Do you know why did that happen? No.

> 
BTW, since I back-up my bookmarks and settings, how do I set them up in this new firefox that I jast installed??
many thanks! :) I do, theoretically, but that could screw everything up. Your best bet is to just forget about your settings and restore your bookmarks. Just open up Firefox, go to Bookmarks > Manage Bookmarks > File > Import and import the bookmarks.html that you backed up before.

---

