---
title: "Bypassing Flash Detection (Solved)"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-10-11
I have Flash, but that's not the issue. I find that almost every site I visit that requires Macromedia Flash Player tells me that I don't have it. I know I have it and I know it's working correctly because there are some sites that give you the option of bypassing Flash detection.
Is there anything at all that I can do to manually bypass Flash detection by web sites?
I'm in dapper by the way. And using the latest version of Firefox.

---

### Post by aysiu on 2006-10-11
Try [this workaround](http://ubuntuforums.org/showthread.php?p=1488981#post1488981).

---

### Post by voodoonirvana on 2006-10-11
Okay, so when I try to do this:

> Open the file ~/.mozilla/firefox/pluginreg.dat ( or ~/.mozilla/pluginreg.dat )
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

I can get into the firefox directory, but I cant open the pluginreg.dat

How do I do this?

EDIT-NEVERMIND, I GOT IT! :)

---

### Post by partsdale on 2006-10-11
Here is a stupid question......

I am quoting the work-around here...

"Open the file  [COLOR="Red"][SIZE="2"]~/.mozilla/firefox/pluginreg.dat[/SIZE][/COLOR] ( or ~/.mozilla/pluginreg.dat ) "

what folders would i find that in?   var?  usr?  bin? 

hope you can help

Thanks
Dale

---

### Post by ~LoKe on 2006-10-11
> **partsdale said:**
> Here is a stupid question......

I am quoting the work-around here...

"Open the file  [COLOR="Red"][SIZE="2"]~/.mozilla/firefox/pluginreg.dat[/SIZE][/COLOR] ( or ~/.mozilla/pluginreg.dat ) "

what folders would i find that in?   var?  usr?  bin? 

hope you can help

Thanks
Dale

~/ is the equivalent to your home/user directory.  ~/.mozilla would be /home/username/.mozilla

---

### Post by aeon on 2006-10-11
~/ is your home directory, so [COLOR="Red"]~/.mozilla/firefox/pluginreg.dat[/COLOR] is found under [COLOR="Blue"]/home/insert_your_username_here/.mozilla/firefox/pluginreg.dat[/COLOR]

---

### Post by Sweet Spot on 2006-10-11
Hey, I tried that workaround, but it doesn't work because it just keeps re-creating the original file, no matter what I do. I can delete it, re name it, whatever, but the original file just keeps popping up again with the original settings. Any thoughts ?

Doug

---

### Post by podunk on 2006-10-11
You have to closee firefox before changing the file.

---

### Post by partsdale on 2006-10-11
thanks for your help.

~LoKe, aeon

Dale

- till next time

---

