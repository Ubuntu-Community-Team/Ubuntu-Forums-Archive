---
title: "Devilspie - error on setting workspace"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Juninho1 on 2008-01-11
Hi - I hope this has not been asked before. I promise I have searched carefully and the closest match I could find is someone who resolved this as they were using compiz.

I am trying to use Devilspie to direct applications to workspaces as they open. 

I have followed the tutorial on the Ubuntu forums as well as read the documentation on both the main site and the wiki site I found BUT

I still get this error: 

** (devilspie:11136): WARNING **: Workspace number 2 does not exist

(devilspie:11136): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed


I am running Ubuntu Gutsy 7.10 and I don't think I am running compiz (95% sure am not!!). BUT I did try the persons fix in that I tried setting the viewport but it had not effect.

I have four workspaces (I added two to the default two provided) and the parsing seems fine.

Any help anyone can provide will be greatly appreciated!! 

Ta

---

### Post by drs305 on 2008-01-11
Can you post one of the .ds files that is causing the error?

You seem to have a debug.ds file since you have seen the errors. The file causing the problems should be the one for the app loaded just prior to the warning message. 

I had a similar error but when I changed it to "set_viewport 2" it fixed it. Apparently this didn't work for you, unless you didn't change the offending .ds file. 

One other thing: if you just right click on the title bar of any app and select "Move to Workspace Right" does that work correctly?

---

### Post by Juninho1 on 2008-01-15
Thanks ! The set viewport _did_ work. I didn't realise that devilspie only parses all the .ds files on startup so all the editing I was doing to play with these files was not having an effect until I restarted devilspie (duhh... don't feel too bright now).

It only seems to work with workspaces 1 & 2 but that is all I want it to so thats ok 

(and interestingly enoguh - if I am in workspace 3 and start a program which has set viewport = 1- it just goes to the left!)

---

