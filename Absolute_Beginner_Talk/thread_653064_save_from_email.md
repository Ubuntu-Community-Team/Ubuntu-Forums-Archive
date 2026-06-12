---
title: "save from email"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by wolfnov67 on 2007-12-29
hi all .. my first day here .. i dont know how to save images that my friend sent by email .. it says restricted to save in my personal folder .. how can i do that

---

### Post by pjkoczan on 2007-12-29
> **wolfnov67 said:**
> hi all .. my first day here .. i dont know how to save images that my friend sent by email .. it says restricted to save in my personal folder .. how can i do that

Welcome.

I'm happy to help, but I'll need a few more details on what you're trying to do before I can give you specific help. If you answer these questions, I should be able to help you.

Are you using a web-based client (do you open up a page in Firefox or another web browser) or a stand-alone client (like Evolution or Thunderbird)?

Where are you trying to save your images?

What is the full text of the error message you get?

---

### Post by nick_h on 2007-12-30
Have you tried right-clicking on the image and looking for an option like "Save Image As..."?

You will normally only have permissions to save the image under your own home folder.

---

### Post by wolfnov67 on 2007-12-30
hi guys..thanks for your replies..i am opening up my mail with a browser..firefox..i have tried right clicking and save as but it says i dont have access to save to the folder i am indicating..i tried saving it to the desktop and dragging into the folder same problem..i dont have rights..my user on this terminal has been created as admin..so i dont get it..its fine if i open up through windows and try using netscape..not in linux..

thnks for your help again

---

### Post by nick_h on 2007-12-30
Check the permissions on the folder.  Right-click on the folder and select "Properties" and then look in the Permissions tab.

Or from the command line type:
```
ls -ld <directory>
```

---

### Post by pjkoczan on 2007-12-31
> **wolfnov67 said:**
> hi guys..thanks for your replies..i am opening up my mail with a browser..firefox..i have tried right clicking and save as but it says i dont have access to save to the folder i am indicating..i tried saving it to the desktop and dragging into the folder same problem..i dont have rights..my user on this terminal has been created as admin..so i dont get it..its fine if i open up through windows and try using netscape..not in linux..

thnks for your help again

This could be a few things...

You're either trying to save to some folder you don't have access to, or you're trying to write to a filesystem that you can't (either it's read-only or barely-supported NTFS or something). Or it could be that you don't have proper permissions on a higher-level directory (I'm not trying to confuse you or anything, I'm just thinking out loud, or thinking in typing form).

Check the properties on the folder, like the other user suggested, and then get back to us. Also be sure to tell us which folder you're trying to save to.

---

