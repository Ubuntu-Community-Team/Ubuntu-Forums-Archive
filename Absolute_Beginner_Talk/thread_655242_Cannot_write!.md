---
title: "Cannot write!"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by tomor on 2008-01-01
Hi, 

I'm a new user of Ubuntu. I'm having a problem with my new OS. Sometimes I cannot rename a file, ex. I click rename but when i select the name to be deleted and write another name there no letter appears. The same thing is happening sometimes with the aMSN. Sometimes somethings happens and I cannot write nor close the conversation window when i click ESC button in my keyboard. 

I appreciate your help.

---

### Post by Sbarton on 2008-01-01
Have you tried this. Right click the the selected folder choose Rename(it is then highlighted). Either delete the existing entry or place the cursor at the end of the existing name and backspace until you erase all the name then type in the new one. Strange I know but it has worked for me.
regards

---

### Post by bernied on 2008-01-01
Could it be a problem with the keyboard? Is there another keyboard that you could try?

---

### Post by seshomaru samma on 2008-01-01
I sometimes have the same problem with renaming filesin the latest edition of ubuntu (gutsy)
what i do is choose rename then right-click and look in the `input methods` (sorry can`t remeber the exact name , now writing from a debian) and change it from Xsystem to `default`
hope that helps...

---

### Post by tomor on 2008-01-03
Hi, 

Does anyone have another solution because until now I couldn't solve this problem. Still cannot rename the files and write in the location bar. :confused::confused::confused::confused::confused:

---

### Post by PreviousN on 2008-01-03
I have problems with this too. Still looking for a fix. Usually what I do is open a terminal and type:

mv file newnamefile

But this gets tedious. I'm happy to hear I'm not the only one with the problem. It drives me crazy.

---

### Post by (((X))) on 2008-01-03
to rename file

$ sudo -s
cd /home/you
mv name newname

to quit misbehaving app
$ xkill  and click on that window

---

### Post by tomor on 2008-01-03
ok, the one with terminal is working but isn't there any other way to fix this problem .??
I tried the one with Input Method Setup but I didn't see anywhere any word like "Xsystem"

---

### Post by Sbarton on 2008-01-03
Re- xsystem suggestion, I believe it is X Input method and it is on the bottom of the input dropdown menu, Default is the top one X Input Method is the bottom one. However the poster 'seshomaru samma' did say he sometimes changed it to 'Default' and not the x method, if I understand it correctly.
regards

---

### Post by tomor on 2008-01-03
> **seshomaru samma said:**
> I sometimes have the same problem with renaming filesin the latest edition of ubuntu (gutsy)
what i do is choose rename then right-click and look in the `input methods` (sorry can`t remeber the exact name , now writing from a debian) and change it from Xsystem to `default`
hope that helps...

hey, thanks a lot, this solved my problem. 
@ PreviousN: right-click on the file you want to rename, then click on "rename". now, the filename is highlighted and you have to do a right-click again and then choose in the menu " input methods" -> "default".

---

