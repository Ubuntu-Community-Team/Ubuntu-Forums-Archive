---
title: "Firestarter"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by IDipSkoalMint on 2006-03-28
Quick question. I know in Windows you can change what starts up when first load the computer. My question is about having Firestarter (the Firewall program) load up as soon as I log in so I don't have to start it manually each time. I looked around, and the only thing I could find was under "System" > "Administration" > "Services" that seemed to deal with that type of thing, but Firestarter wasn't on the list, and I didn't see an "Add service" button or anything. If this is possible and someone could point me in the right direction, that would be great. Thanks.

Regards,
Matthew

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=IDipSkoalMint]Quick question. I know in Windows you can change what starts up when first load the computer. My question is about having Firestarter (the Firewall program) load up as soon as I log in so I don't have to start it manually each time. I looked around, and the only thing I could find was under "System" > "Administration" > "Services" that seemed to deal with that type of thing, but Firestarter wasn't on the list, and I didn't see an "Add service" button or anything. If this is possible and someone could point me in the right direction, that would be great. Thanks.

Regards,
Matthew[/QUOTE]

Hi, Try [ this ](http://ubuntuforums.org/showthread.php?t=110320&highlight=automatically+start+firestarter)

---

### Post by endersshadow on 2006-03-28
System>Preferences>Sessions

Go to the Startup Programs tab, add firestarter as the command at level 50.

Click OK

You're all set :-D

---

### Post by IDipSkoalMint on 2006-03-28
Thank you both for your help. I did a search for "set up startup programs" in the Search menu before I posted, but no titles really popped out at me that seemed to be very relevant. In hindsight, I probably should have searched for "firestarter startup" or something more along those lines, but problem is solved (or so I think). Thank you both again, and good day.

---

### Post by endersshadow on 2006-03-28
Note that the command has to be this:

```
sudo firestarter &#8211;start-hidden
```

Sorry I didn't specify this earlier :-|

---

