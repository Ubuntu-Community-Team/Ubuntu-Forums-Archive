---
title: "Xubuntu and OpenOffice.org 2.3 Menu Issue"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by VoodooLoveDog on 2007-12-21
Before I get into my problem, I'd just like to say that this is my first post even though I've been lurking the boards for over 6 or so months. Most of my questions were answered in previous posts about installation of various Ubuntu favors. These boards have been awesome. I still can't find a reasonable resolution to my hibernation on my D610 laptop, but I digress.

I'm having an issue with Xubuntu and OpenOffice.org. It seems I've installed all of the appropriate packages from the libs in order for the software to both work and look like the Xubuntu default desktop. However, in the Application Menu, the OpenOffice.org icons open only a generic window for OpenOffice. In other words, if I click the icon for the writer, it just opens a default OpenOffice window. Same as if I click the spreadsheet or presenter icons. 

I checked the /usr/share/applications folder to see if it was a problem with the .desktop file but everything seems to be in order. The arguements are there for all of the apps but it's like the launcher is ignoring them. (e.g. ooffice -writer %U executes as just ooffice) If I click the icon within the applications folder it works correctly. 

Any thoughts how to fix this?

---

### Post by jken146 on 2007-12-21
Try the command **oowriter** -- I have the same problem (only noticed it because of your post, and this fix works.

---

### Post by overdrank on 2007-12-21
> **jken146 said:**
> Try the command **oowriter** -- I have the same problem (only noticed it because of your post, and this fix works.

Hi and oowriter --   dose work but I just go to the file new in the generic window and choose weather I want a spread sheet or word processor. I have no idea why xubuntu is set that way :)

---

### Post by VoodooLoveDog on 2007-12-21
Awesome. By changing the EXEC= line the .desktop file to oo%app%, the menu now launches the appropriate software. Thanks so much.

---

