---
title: "Konqueror help"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by YourFriendlyGopher on 2007-03-18
Hi everyone,

Does anyone know how to disable the little animation that plays when you open files/folders in Konqueror? It just seems unnecessary and seems to make opening files/folders take longer. Also, I removed the sidebar (the one with metabar etc) and can't seem to find a way to get it back.

If anyone has any ideas it'd be appreciated, thanks. :)

---

### Post by natman on 2007-03-18
I think if you go to system control panel ( not sure whats its called exactly, but the one that gives you control over all devcives and stuff ) go to winodws poperties and tell it to tone the extra graphics down a bit.

---

### Post by YourFriendlyGopher on 2007-03-18
Yeah I've had a good search through the GUI options but so far I've found nothing. I was thinking there could be a configuration file lying around somewhere?

---

### Post by YourFriendlyGopher on 2007-03-18
Bumpification!

---

### Post by YourFriendlyGopher on 2007-03-18
bump *= 2; :confused:

---

### Post by Bachstelze on 2007-03-18
I have no animations here in Konqueror.. Or do you mean the bouncing cursor when you start an app ?

---

### Post by YourFriendlyGopher on 2007-03-19
I mean the little dashed box animation (I'll post a screenshot soon, don't have time at the moment). Perhaps you have a different version? I know I'm being picky with this but little things like this are what bugs me. I mean, I open a lot of folders and that little slowdown makes a difference.

---

### Post by 454redhawk on 2007-03-19
> **YourFriendlyGopher said:**
> I mean the little dashed box animation (I'll post a screenshot soon, don't have time at the moment). Perhaps you have a different version? I know I'm being picky with this but little things like this are what bugs me. I mean, I open a lot of folders and that little slowdown makes a difference.


I think what you are after is called launch feedback (bouncing cursor). I am using Mepis at the moment and its located under system settings.

BTW it has no effect on how fast the apps open and does not slow anything down. That is a factor of HDD and CPU.

---

### Post by Songwind on 2007-03-19
The sidebar should come back if you press "F9"

---

### Post by Lexyboy on 2007-03-19
Right click on the animation or anywhere on toolbar & you'll get a dialogue allowing you to customise the toolbar.  Just move the animated logo from the current toolbar buttons on the right to the left...

---

### Post by YourFriendlyGopher on 2007-03-20
Ugh, I finally fixed it. Some of the slowdown was contributed to the animations (because the contents of windows render slowly with Beryl + my ATI card). Although, it was mostly because of the metabar which I've managed to break and can't seem to find a way to reinstall it. And the sidebar was also hidden since something modified the HideTabs option in the konqsidebartng.rc file.

---

### Post by freedom on 2007-09-16
So, do you finally manage to disable icon animations in Konqueror when you click on them?

---

### Post by freedom on 2007-09-19
Well, I found it myself...
In Control center>Peripherials>Mouse Visual feedback should be unchecked.
;)

---

