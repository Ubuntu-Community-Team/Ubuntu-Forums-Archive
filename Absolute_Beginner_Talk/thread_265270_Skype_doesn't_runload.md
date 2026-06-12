---
title: "Skype doesn't run/load"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by shanghaielaine on 2006-09-25
I installed kubuntu recently. 
While the installation of skype went fine, however when I try to start skype, there's only a jumping icon shown for seconds, then nothing happens. If I try to run skype from terminal, it returns:
*** glibc detected *** free(): invalid pointer: 0x08aa89e8 ***
Aborted

Anybody had the same problem? How to slove? crying for help !!!

---

### Post by Dinerty on 2006-09-25
Seems to be a problem with scim

[http://ubuntuforums.org/showthread.php?t=189126](http://ubuntuforums.org/showthread.php?t=189126)

How did you install skype, through the .deb or through repo's?

---

### Post by shanghaielaine on 2006-09-26
Hi, Dinerty, 

thank you for your reply.

I firstly installed skype with easyubuntu, deb, as it didn't work out, I downloaded it from skype site, but the same result.

Followed what is suggested in the link you sent me, when I tried to download the skype-dsp-hijacker, got a 404 error, it is outdated. 

Do you by chance know a chinese input other than scim, does't conflict skype?

---

### Post by Dinerty on 2006-09-26
> **shanghaielaine said:**
> Hi, Dinerty, 

thank you for your reply.

I firstly installed skype with easyubuntu, deb, as it didn't work out, I downloaded it from skype site, but the same result.

Followed what is suggested in the link you sent me, when I tried to download the skype-dsp-hijacker, got a 404 error, it is outdated. 

Do you by chance know a chinese input other than scim, does't conflict skype?

Sorry I don't know :(, seems to be quite a popular bug

---

### Post by kswnsn on 2006-10-10
If you are/have run KDE, and selected a certain GTK style under the KDE control center, you will have a ~/.gtkrc-2.0 file that will prevent certain GNOME apps from running. First rename this file to see if it clears the issue, and if so, try a different theme. I was using "Glider" but changed to "Human" to correct this issue.

---

