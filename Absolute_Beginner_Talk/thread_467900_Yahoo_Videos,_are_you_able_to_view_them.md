---
title: "Yahoo Videos, are you able to view them?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by buckwheat12n on 2007-06-08
I can view video on other websites, whether it be a .wmv, .mov or flash format, but for some reason when I try viewing videos on Yahoo I can view the commercial prior to the video, but after that I get the message the I'm missing the appropriate plugin to view the video (application/x-ms-wmp).  I have installed the w32codec package as well as the "Ubuntu Restricted extras".  Is anyone else having issues viewing videos in Yahoo?  

The video I'm trying to view is:

[http://cosmos.bcst.yahoo.com/up/player/popup/?rn=207187&cl=2973570&ch=244098&src=sports](http://cosmos.bcst.yahoo.com/up/player/popup/?rn=207187&cl=2973570&ch=244098&src=sports)

---

### Post by HereInOz on 2007-06-08
I could be wrong but that looks like a Windows Media Player specific file.  A bit similar to what you get on the MSN sites.

Maybe someone will correct me if I am wrong, but I think that video will insist on Internet Explorer and Windows Media Player.

Then again, I kind of hope that I am wrong - far too much of that sort of thing happening.

---

### Post by Seisen on 2007-06-08
Its because Linux isn't supported that is why you are having problems.

---

### Post by buckwheat12n on 2007-06-08
Ugh, OK that's what I thought might be the problem.

---

### Post by NilsE on 2007-06-08
The mime type is video/x-ms-wmp which is not supported with Totem out of the box.

I tried it and mine did not work either so I  had to do the following:

1) Edit/Preferences/Content then click manage 

2) Look for file type WMP but it may not be there. 

- If it is there jump to number 4

3) If not then:

- Turn on mime type in the little clicky in the upper right corner of the file type window.  

- You may then see it in there with no file type (NONE for file type )

- Files with no file type do not automatically show up so you may have to do the following: 

- Enter   about:config    on the location bar 

- and change browser.download.hide_plugins_without_extensions to false (double click the line to toggle)

- Then go back to content/manage and 

4) find it and select to change it and then 

- select "use this plugin" and you might have Windows Media Player Plugin 10..... (Totem compatible) in the window

5) If that is not available install w32codecs in synaptic.  If it does not show up in synaptic do a search on w32codecs in the forum and you can find how to install it.

You may find that a lot of the gstreamer and other media stuff is also not installed by Dell so go to [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) and there is a lot of how to's for enabling multimedia.

I know it is a little convoluted so let me know how you make out.

---

### Post by imon9 on 2007-06-08
no problme viewing them here on my laptop with feisty 7.04... flash 9

it does show the warning saying i cant view the media but clicking on any of the clip selectable at the list below make vide play right away.. it is using flash, so no problme with codec watsoever :)

EDIT: sorry, my bad, i cant view THAT particular one that u pointed to, but the other works fine..wonder if someone tried opening it in XP box? perhaps is server problme?

---

### Post by wormser on 2007-06-09
I have had the same issue with the application/x-ms-wmp plugin error.  From my searching on the web it appears this is a new format by M$.  Right now there is not much info on the web.  Apparently Firefox has similar issues with windows.

This is my [thread]("http://ubuntuforums.org/showthread.php?t=465663") on the issue.

Does anybody know more about this issue?  Thanks

---

### Post by NilsE on 2007-06-11
Apparently the actual videos are flash but the control for it is video/x-ms-wmp which needs the media player plugin.  At one point I did have the mime type show up without an extension in the manage downloads function and it worked perfectly when I assigned the WMP plug in to it..  After I upgraded Firefox last week the mime type application/x-ms-wmp does not show up in the download functions anymore and I am back to the plugin prompt again.  Wierd.

Also noticed that if you ignore the prompt for the plugin and click on any of the other videos on the page they work.

Does anyone know if there is a way to force a mime type to show up in the manage list?

---

### Post by wormser on 2007-06-13
> **NilsE said:**
> Also noticed that if you ignore the prompt for the plugin and click on any of the other videos on the page they work.

Not all of the video are in that format.  I think the commercials are in flash and the video is in x-ms-wmp.  I am not 100% sure on that.

Has anybody heard anything more on this?

---

