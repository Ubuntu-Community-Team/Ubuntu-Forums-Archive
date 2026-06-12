---
title: "I have 2 printers but its the same printer a fix please"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by nu2this on 2007-01-22
My problem is this I got a new printer HP C3180. I installed this way 1st: System>Administration>Printing> global settings
I went with the Fowards all the way & My printer works, but I couldn't find out my ink levels.
System>Preferences>HPLIP toolbox got me a "you have no devices installed box."
So in my reading thru the forums I found that HPLIP comes with Ubuntu. All I had to do was 
do a sudo hp-setup. 
So, I went thru as done in the 1st only this time deleting the printer listed in Printers.
Then using hp-setup installed my printer I could see ink levels, but the printer would not work
the only way print was to reboot & scanning forget it!
What I did next was to leave the printer installed by hp-setup then I added in the same printer the 1st way.
Now it works again & I can see ink levels now, but I show 2 printers.  I think it'd be nice if I had one printer listed that 'd be Default that'd work & tell me ink levels instead of one that works but doesn't tell ink levels & one that tells me ink levels but doesn't work.
Is there a fix for this or have I hopelessly screwed up?!

---

### Post by nu2this on 2007-01-23
To anyone that does a printer install the way I did & ended up with a situation similar to my own. It was all because I forgot to set a Default Printer. To fix just do this:
1)System>Administration>Printing then right click a printer click Properties click "test page"
2)If it prints GREAT! If not right click the 2nd do as in step 1
3)Right click the one that does print set it as default.
4)Leave the 2nd printer in the  box **do not delete it** the reason is because when you do
System>Preferences> HPLIP toolbox that's where you'll find out your ink levels under the Supplies tab.

---

