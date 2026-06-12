---
title: "[SOLVED] Know nothing about the terminal"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by dgrspencer on 2008-01-09
Been on Linux for about 15 mins!  I don't seem to have the Flash plugins necessary to play website videos - like on Youtube.  I've followed the instructions on the adobe site but not certain why it's not working.  I really know nothing about working in the terminal so if anyone out there can help me install plugins necessary I'd appreciate it.

---

### Post by eolson on 2008-01-09
I had a bit of a tussel getting Flash to work too.   How I did it was I went to the Weather Channel site,  clicked on the map (which won't work because of no plug in),  scrolled to the bottom and clicked on the install flash (or somesuch) button,  and it installed.

---

### Post by RomeReactor on 2008-01-09
Hi. The flashplugin-nonfree package is broken at the moment; for now, [try this]("http://ubuntuforums.org/showpost.php?p=4101050&postcount=5").

---

### Post by NovaAesa on 2008-01-09
Good news it, you don't have to learn about the terminal if you don't want to.

If you want flash to work, just go to Applications -> Add/Remove -> and type restricted into the search bar at the top. Then check the box next to "Ubuntu Restricted Extras", then hit Apply changes. It will ask for your password and then should start downloading. Flash should work after that.


EDIT: I'm not 100% sure my solution will fix the problem, but it wont harm anything. Try doing what RomeReactor suggested first.

---

### Post by dgrspencer on 2008-01-09
Sorry none of the above seems to do it.  but thanks for the quick replies.  Checked through other threads - seems to be common

---

### Post by -grubby on 2008-01-09
try installing this:
[http://www.mediafire.com/?3tlmzxeofzu](http://www.mediafire.com/?3tlmzxeofzu)

---

### Post by dgrspencer on 2008-01-09
keep being told "wrong architecture '386'"

---

### Post by RomeReactor on 2008-01-09
Are you running Ubuntu 64-bit? if so, the package you need is [this one]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466").

---

### Post by dgrspencer on 2008-01-09
Yes 64 bit AMD and getting closer!  I had to download a Codec as well.  Playing you tube files now but not all video files

---

### Post by RomeReactor on 2008-01-09
Make sure you don't have Gnash installed as well; close Firefox, open a terminal and write:
```
sudo apt-get remove gnash gnash-common mozilla-plugin-gnash
```
Then open Firefox again and see if the problem persists.

---

### Post by dgrspencer on 2008-01-09
Thanks all so much - what a spectacular start to my Linux learning!

---

### Post by RomeReactor on 2008-01-09
Glad to have helped. Just for reference, when visiting for the first time a site that requires Flash, Firefox will give you two choices: to install the proprietary Adobe plugin, or the open-source Gnash plugin. Gnash isn't yet as functional as Adobe's plugin, but it is getting there. It is recommended, though, that you don't have both installed at the same time. If your problem is solved, please mark the thread as "Solved" from the **Thread Tools** dropdown menu.

---

### Post by papuccino1 on 2008-01-09
> **dgrspencer said:**
> Been on Linux for about 15 mins!  I don't seem to have the Flash plugins necessary to play website videos - like on Youtube.  I've followed the instructions on the adobe site but not certain why it's not working.  I really know nothing about working in the terminal so if anyone out there can help me install plugins necessary I'd appreciate it.

***********************************************************
PLEASE PLEASE PLEASE READ THIS:
***********************************************************

I had the same problems as everyone else, this solution works 110%:

1. [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")

2. Download the .tar.gz file. It's the first choice. If you chose save to disk it'll probably just save it to your desktop.

3. CLOSE FIREFOX COMPLETELY.

4. Open the ,tar.gz file (It's sort of like a zip file).

5. Double click flashplayer.installer and follow the instructions.


And there you have it, everything should work completely.

---

