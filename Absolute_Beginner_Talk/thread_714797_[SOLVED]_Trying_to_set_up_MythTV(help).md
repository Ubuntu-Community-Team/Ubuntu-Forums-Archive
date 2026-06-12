---
title: "[SOLVED] Trying to set up MythTV(help)"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-04
Ok, so i have mythbuntu. and when i try to start up mythtv it starts up fine but when i select watch tv it says 

```
MythTV is alread using all available iputs for the channel you selected. If you want to watch an in-progress recording, selcet one for the play back menu. If you want to watch live TV, cancel one of the in-progress recordings from the delete menu.
```

i've never used this before now so i don't know what it's wanting me to do...

---

### Post by Calash on 2008-03-04
For better support you will find the Mythbuntu forum at the following address.

[http://ubuntuforums.org/forumdisplay.php?f=301](http://ubuntuforums.org/forumdisplay.php?f=301)


The error that you are seeing is when MythTV thinks all the inputs are being used.  If you are not recording anything then it means there is likely an error in the setup of the capture card.  Run mythbuntu-control-centre, from there you can run the Mythtv setup utility and make sure the card is correctly configured.

---

