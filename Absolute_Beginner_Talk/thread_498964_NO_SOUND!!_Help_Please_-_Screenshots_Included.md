---
title: "NO SOUND!! Help Please - Screenshots Included"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by IXOYE777 on 2007-07-12
Just installed Ubuntu CE. I have NO sound! Had XP installed, sound worked fine, then with CE I get nothing - any ideas?

[IMG]http://img483.imageshack.us/img483/9431/screenshotsoundpreferenkn1.png[/IMG]

[IMG]http://img483.imageshack.us/img483/434/screenshotvolumecontroljn3.png[/IMG]

[IMG]http://img483.imageshack.us/img483/7199/screenshotvolumecontroltl7.png[/IMG]

---

### Post by wolfen69 on 2007-07-12
did you disable the onboard sound in the BIOS?

---

### Post by expatCM on 2007-07-12
If you type 

asoundconf list

at the command line, the sound cards your system recognizes will be listed.


If you then type 

asoundconf set-default-card CARD

where CARD is the name of your preferred sound card from the list then that card will be set as default.

Perhaps you could try that and test .....

---

### Post by Inxsible on 2007-07-12
Follow this link and try out all the suggestions given there

[http://ubuntuforums.org/showthread.php?t=498801](http://ubuntuforums.org/showthread.php?t=498801)

---

### Post by expatCM on 2007-07-12
You may find this interesting

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by eeeek on 2007-07-12
I didn't have any sound even though everything seemed to check out. I got wind of the link expatCM mentioned. I typed "alsamixer" into the command line and found that my system was muted. Sound worked fine after unchecking it there. (It will look like a graphic equalizer, just as the wiki explains.)

---

