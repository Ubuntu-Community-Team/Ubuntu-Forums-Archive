---
title: "Dictionary Applet in Gutsy"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by jamere on 2007-10-28
The dictionary applet doesn't seem to allow input. Worked OK in Feisty. Any ideas?

Thanks much...jim m

---

### Post by daengbo on 2007-10-29
Can you give more details. Is the text input area blanked out? What happens or doesn't happen. How are you starting it?

You aren't by chance using SCIM for multi-keyboard input, are you?

---

### Post by jamere on 2007-10-29
Hello daengbo,

Thanks for the reply. The applet in the panel looks normal. The text entry space to the right of the little dictionary icon will not accept the word to look up. I added the applet by right clicking on the panel and clicking "add to panel" option. The applet worked fine in Feisty but doesn't work in Gutsy. You might try adding it to your panel to see if it works for you. Pretty straight forward...just doesn't work.

Thanks,
jim m

---

### Post by jamere on 2007-10-29
> You aren't by chance using SCIM for multi-keyboard input, are you?

Nope...just new install of Gutsy.

---

### Post by erginemr on 2007-10-29
Quite strange issue I'd say... :confused: I am using Gutsy and can perfectly write to it and get feedback.

There is a second applet (address book search) that is almost identical to the dictionary applet in terms of operation. Can you write to it either?

Also please try the applets with and without Compiz enabled to see if Compiz has anything to do with this strange issue...

---

### Post by jamere on 2007-10-29
erginemr, thanks for the reply. You put me onto the solution. I don't know if this has anything to do with Compiz or not (suspect it does), but this fixed the problem...

System>preferences>appearance>visual effects>NONE (was set to NORMAL originally and changed to NONE)

Thanks much,
Jim M

---

### Post by erginemr on 2007-10-29
You are most welcome jamere. 

I am not using compiz effects (they are good to impress friends and relatives, but are resource hog and useless in terms of productivity) 

Out of curiosity, I have also checked the situation by enabling desktop effects and adding the dictionary applet to the panel. The result was the same as yours: I could not write to the edit box in there, either with Compiz enabled. So, this is probably a bug, which is very strange to say the least.

Take care and happy 'bunting...

---

### Post by daengbo on 2007-10-30
jamere,

You might try accessing the dictionary lookup through the deskbar applet. It should be on your panel by default.

To use it, simply press ALT-F3 and type the word you want to look up. Press the down arrow (it's always once for me) and press enter. the dictionary should appear and give you tour definition.

You can change the preferences in the Deskbar Applet to use the clipboard by default, so you can then double-click on the word, press ALT-F3, and down arrow, enter. There are many other plugins and the order in which they appear can be adjusted.

If you are addicted to the effects, try the Deskbar.

---

### Post by sagara on 2008-02-24
There is an easy fix for **Gutsy** available.  Ive posted the steps for this in this [thread]("http://ubuntuforums.org/showthread.php?p=4395979#post4395979") [[link]("http://ubuntuforums.org/showthread.php?p=4395979#post4395979")].

As a nice reminder, please remember to **search the forums** for previous post with the same problem as in this case.  This **ubuntu ONLY** search engine is a great place to start: [http://www.uboontu.com](http://www.uboontu.com)

---

