---
title: "Beryl won't load"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by spenser on 2006-11-24
Beryl will no longer load for me from startup
and when i try to open it from the terminal i get a message saying

"
beryl:  GLX_EXT_texture_from_pixmap is missing
beryl:  Failed to manage screen: 0
beryl:  No manageable screens found on display  :1.0
"

---

### Post by Zeroangel on 2006-11-24
Post your xorg.conf

---

### Post by Random20230808 on 2006-11-25
Which is your graphic card?

---

### Post by davehat on 2006-11-28
> Beryl will no longer load for me from startup
and when i try to open it from the terminal i get a message saying

"
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
"

I had problems updating from Beryl 0.1.1 to 0.1.2 and saw this error during the myriad activities I undertook trying to get it to work. I have a feeling the above error comes from running "beryl" instead of "beryl-manager" in a terminal. That's not to say that merely addressing this will fix Beryl for you...

If this command gets beryl up and running - so that beryl effects such as "cube" start working - but you have no windows decoration (borders, buttons and the like), try the following: 

1. Stop emerald. In a terminal run:

```
killall emerald
```

2. Go to the beryl manager icon and select "reload window decorator" from the drop down.

In all possibility, you'll have to do a little more work. I tried the above solution, but failed at step 1 as beryl refused to run at all. As yet, I don't know what the solution is for my problem - I'm going to have another go at installing today. Last time, when I ran beryl-manager, I got a "beryl has caught deadly signal 11" error. Alas, this problem seems to be shared by only one other person (with the same AMD64/ATI/fglrx/XGL set up). Some one was helping work through a fix on the beryl-project forums, but the site died yesterday and that thread with it. Ah well...

---

### Post by arsenaltengu on 2006-12-06
when i start beryl-manager in terminal i get: 

beryl has caught deadly signal 11
compiz.real: decoration: property ignored because version is 0 and decoration plugin version is 20061011
compiz.real: decoration: property ignored because version is 0 and decoration plugin version is 20061011
compiz.real: decoration: property ignored because version is 0 and decoration plugin version is 20061011

and it reverts to compiz with no window borders

it worked fine before i just upgraded from 0.1.1 to 0.1.2

is there a way to install 0.1.1 again?

---

### Post by joergenlie on 2006-12-08
Same here. Beryl won't work after update. I've tried everything. Reinstalled all nvidiadrivers over again, still no window borders. Worked fine before.

Jørgen

---

### Post by joergenlie on 2006-12-10
I used beryl with xgl. After upgrade to newer beryl this didn't work anymore. Then i tried running beryl in gnome session, worked like a charm!
Try it!

Jørgen

---

