---
title: "[SOLVED] Migrating settings from XP"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Tssabackus on 2007-08-29
I have an XP install with bookmarks and other browser stuff (cookies, history). Can I put those stuff in my current install? I think there was some migration option when I installed, but I don't think it worked...

---

### Post by tyggna1 on 2007-08-29
you could try exporting your bookmarks in your previous browser to a file, and then going to firefox and selecting "organize bookmarks" from the bookmarks menu and import them from that file.  Cookies, on the other hand, I'm not so sure you can transfer those to a new browser.

---

### Post by Salpiche on 2007-08-29
if you are using Firefox you could install this add-on: [https://addons.mozilla.org/en-US/firefox/addon/2410]("https://addons.mozilla.org/en-US/firefox/addon/2410")

---

### Post by TeaSwigger on 2007-08-29
Hello,

What browser are you using in XP and what do you plan to use in ubuntu?

If you're using firefox in both, you could install the extension linked to in the post above on both. Upload your bookmarks from the XP firefox and download them into the ubuntu firefox. Done. :)

If you're not using firefox in both it gets more complicated. In your "package manager" in ubuntu, you could install BookmarksBridge and see if that will "translate" your bookmarks file(s) for your new browser. 

Or if you mainly want to save your bookmarks but can't seem to get any fancy ways to work or don't want to bother with it, you can do it yourself by hand. If you're using firefox, here's how.

Go to your firefox profile in XP. That's usually located:

C:\Documents and Settings\ (put your user name here) \Application Settings\Mozilla\ 

and keep going 'till you find a folder that's a bunch-of-letters-and-numbers then .profile. That's the profile where your bookmarks were stored. You may need to find the show hidden files and folders option in explorer options to get to it. In that folder you'll find bookmarks.html. There you are! Save that file.

Now go into ubuntu. Your firefox profile should be in your user folder ( /home/ your user name ) but you may need to find the "show hidden files" option to see it (under View, I think) - it'll be .mozilla or .mozilla-firefox or .firefox... you'll figure it. In there will be another of those bunch-of-letters-and-numbers.profile folders. Just put that bookmarks.html from XP in there and you're done. Firefox will load your bookmarks.

I don't know about saving more like passwords. You could try to copy that whole bunch-of-letters-and-numbers.profile folder in XP in there and replace the profile folder in ubuntu. Start firefox and see what happens... if it doesn't work you can just delete the profile you dropped in there and it'll reset itself next time you start it. Then you'd have to do more research about backing up and restoring profiles between a windows and linux OS or someone here may give you a further hand. 

Luck and enjoy the freedom and power of ubuntu :)

---

### Post by Tssabackus on 2007-08-29
Thanks all, think I figured it out with that Foxmarks extension.

Now if I could only get some more attention in my wireless thread...thats holding me back from completely switching atm.

---

