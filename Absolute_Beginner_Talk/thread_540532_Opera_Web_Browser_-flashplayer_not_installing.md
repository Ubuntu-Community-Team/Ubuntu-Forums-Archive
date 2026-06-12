---
title: "Opera Web Browser -flashplayer not installing"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Universered on 2007-09-01
Firefox is a beautiful browser, but i prefer opera sometimes when i open multiple page tabs (it just gives better performance).
I can't use adobe's flash player on opera. I use famous video sharing websites like y**tu(stars are 2 prevent advertising)
but the video doesn't load on the opera browser
how can i install the flash player for the opera browser.
Thank you very much :)

---

### Post by taurus on 2007-09-01
Download the .tar.gz file from [www.adobe.com](www.adobe.com).  Unpack it.  Then move those two new files to the plugins directory for opera.

---

### Post by Universered on 2007-09-01
wow u came in 2 minutes like christ and saved me:)
Thank you taurus :)

---

### Post by MikeJ1023 on 2007-09-02
I'm having the same problem.  Per another thread I tried to copy libflashplayer.so from home/user/.mozilla/plugins to /usr/lib/opera/plugins, but I get an error message that I don't have permission to write to the second folder.  I'm logged in with the account I set up on install, so I have administrator priveleges.  The only idea I had was to shut opera down and try it, but that didn't work.  

Does anybody have any idea what I need to do.

---

### Post by Perfect Storm on 2007-09-02
You need to use sudo (superuser DO)

sudo cp <file> <distination>

---

### Post by MikeJ1023 on 2007-09-02
That seems to have done it.  Thanks for the lightening quick response.  

Out of curiosity, is there any way to copy text into the terminal window?  The old windows stand by of ctrl+c and ctrl+v don't seem to work.  I'm a horrible typist, and commands like that would be easier if I could just copy the pathnames from the location bar in the open folders.

---

### Post by mysticmatrix on 2007-09-02
> **MikeJ1023 said:**
> That seems to have done it.  Thanks for the lightening quick response.  

Out of curiosity, is there any way to copy text into the terminal window?  The old windows stand by of ctrl+c and ctrl+v don't seem to work.  I'm a horrible typist, and commands like that would be easier if I could just copy the pathnames from the location bar in the open folders.

Copy the required text and then middle click in terminal window(that assuming you have a scroll mouse)
Else press Shift+Insert

---

### Post by MikeJ1023 on 2007-09-02
Excellent.  Thank you.

---

