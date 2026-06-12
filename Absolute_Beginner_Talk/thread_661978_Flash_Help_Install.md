---
title: "Flash Help Install"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-01-08
I'm having this weird problem when trying to install flash.

So I extract the folder from the .tar.gz that I downloaded...

Then I run it by going to **./flash-player**

Close all browsers, etc. etc.

"type the directory path where the browser is installed"
/usr/lib/mozilla/plugins/

WARNING: invalid directory blah blah blah

Meanwhile I cut/pasted that line right from  nautalis?  The hell is going on, it's a damn valid path.

I'm trying to get it (flash) to work with konqueror, and it's said that it can read the mozilla directories to scan for the plugin...but it doesn't.  In konqueror's settings I have /usr/lib/mozilla/plugins and /usr/lib/firefox/plugins and neither one is giving me the damn plugin to get flash to work with konqueror.

Also note, that flash works fine for firefox, so it's not like the plugin doesn't exist.

Anybody know how to get this working with konqueror?

---

### Post by mikewhatever on 2008-01-08
Mozilla installation directory should be /home/your_user_name/.mozilla. It should show the right one by default.

---

### Post by philinux on 2008-01-08
Try this 

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by Syndacate on 2008-01-08
> **mikewhatever said:**
> Mozilla installation directory should be /home/your_user_name/.mozilla. It should show the right one by default.

It's talking about the plugins, not the main installation.

[quote=philinux]Try this

[http://www.adobe.com/shockwave/downl...Platform=Linux](http://www.adobe.com/shockwave/downl...Platform=Linux)[/quote]

Yes, if you read the original (only)  post, that's what I did, I went there and downloaded the .tar.gz file, then went to install it, etc. etc. (the story is in the original  post).

---

### Post by philinux on 2008-01-08
Sorry .

When I followed this it didn't ask me for a destination folder.

This method installs the plugin infact it only seems to install libflashplayer.so into /home/username/.mozilla/plugins

---

### Post by Syndacate on 2008-01-08
> **philinux said:**
> Sorry .

When I followed this it didn't ask me for a destination folder.

This method installs the plugin infact it only seems to install libflashplayer.so into /home/username/.mozilla/plugins

While I was adding that folder to the list for Konqueror to scan I got this error message:
[img]http://syndacate.no-ip.org/qrs.jpg[/img]

It still doesn't work, though - works fine in firefox, just not in Konqueror :|

---

### Post by mikewhatever on 2008-01-08
> **Syndacate said:**
> It's talking about the plugins, not the main installation.

No it's not. It's explicitly asking for Mozilla installation directory.

---

### Post by Syndacate on 2008-01-08
> **mikewhatever said:**
> No it's not. It's explicitly asking for Mozilla installation directory.

Blah, I thought it was looking for the plugin directory.

Anyways I didn't get a chance to type it in because this time when I typed ./flash-installer it TOLD ME what path it was going to install it to (**/home/user_name/.mozilla**), it didn't ask me to chose anything, and then it said it installed fine.

Which is fine - it did that before, which is why it works with Firefox.

Though I have konqueror set to scan every folder i can think of for plugins (including but DEF. not limited to **/home/user_name/.mozilla**, **/home/user_name/.mozilla/plugins**, **/home/user_name/firefox/**, **/home/user_name/firefox/plugins**, etc.  It just REFUSES to work with Konqueror - works fine with firefox...I can't figure it out.

Also, I get the "KDE Crash" error message pictured above every time I A)  Go to [www.youtube.com](www.youtube.com) (into the video section), or B)  Go to ATI.com (they have a flash intro) and close the browser.

I think Konqueror's having some sort of issue/conflict with the plugin - anybody have any advice???

---

### Post by macogw on 2008-01-08
The reason it didn't ask where to go is because you didn't do ```
**sudo** ./flash-installer
``` Do that and for Konqueror I think it's /usr/lib/kde3/

---

### Post by Syndacate on 2008-01-09
> **macogw said:**
> The reason it didn't ask where to go is because you didn't do ```
**sudo** ./flash-installer
``` Do that and for Konqueror I think it's /usr/lib/kde3/

****.

Whenever I click "scan for plugins" now I get the error message pictured above.

Nobody knows what the hell that error message means, or why it's showing up??

The hell is this crap??

---

### Post by Syndacate on 2008-01-09
[img]http://syndacate.no-ip.org/qrs.jpg[/img]

Anybody  know what the hell it is and why the hell I'm getting it all the time when dealing with plugins in Konqueror??

---

