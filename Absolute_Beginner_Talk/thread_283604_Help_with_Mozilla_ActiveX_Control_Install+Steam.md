---
title: "Help with Mozilla ActiveX Control Install+Steam"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by darthcoder on 2006-10-24
Hi Guys,

Am back again :D.

OK, So ave been fiddling around with steam, and came to know that I need to update my Mozilla ActiveX Control for the Steam client to show HTML Pages.So, I downloaded the Mozilla ActiveX .exe file and ran it through wine, but at the end of the installation it asks for the location of the Mozilla Library files, so what am I supposed to do now??:(, should I install mozilla through steam in ./wine/drive_c/Program Files??(cos its looking for a certain mozilla dll file mscvp60.dll).

Secondly, I also installed Steam through Wine in C:/Program Files i.e. ./~wine/drive_c/Program Files, now for steam to update those files to be able to play CSS, it has to download 4 gigs of data through steam (that means running my internet for months), so can I dump the contents of my old up-to-date steam folder from my windows installation into the steam folder in the wine Program Files/Steam folder in order to avoid the downloading of the files again??(I have mounted the drive containing the steam folder and copied steam folder on the linux desktop).


Please help me guys!!

Thank you :).
Darthcoder.

---

### Post by dbd on 2006-10-24
No sure about the first question, but you might as well try installing firefox.

Yeah, if you copy the .gcf files from your windows install to Program Files/Steam/steamapps/ and then when you start steam it will see these as up to date, so you don't have to download them again. :)

---

### Post by darthcoder on 2006-10-24
Thanks dbd for your quick reply :).
This community rocks :D.

Could someone help me with the Mozilla ActiveX control thingy though??That would mean I will have to dload the mozilla setup and install it through wine in order to install the Mozilla ActiveX plugin??

Could someone answer my first question in the first post of this thread please??

Thank you :).

Ever Grateful :D,
Darthcoder.

---

### Post by dbd on 2006-10-24
Sorry, didn't really read the first question, I had a look around on the wine page on steam and I think there info there should help. 

here is post there that may help
[http://appdb.winehq.org/commentview.php?iAppId=1163&iVersionId=1554&iThreadId=10859](http://appdb.winehq.org/commentview.php?iAppId=1163&iVersionId=1554&iThreadId=10859)

And here is the steam wine hq page itself, with loads of discussion, including on your problem:
[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)
(there is one called "i got working steam on kubuntu 6.06", which may be useful if the first one fails

Also, came across this, it may help if all the above fails:
[http://www.iol.ie/~locka/mozilla/control.htm](http://www.iol.ie/~locka/mozilla/control.htm)


Hmmm, seems like wine steam support seems to be much better than when I first tried it, I may give it another go on my system. CSS here I come :)

---

### Post by darthcoder on 2006-10-24
w00t!Thanks dbd.
I shall try it out tomorrow morning(Its 1 AM here :() and then be back to bug you guys some more :D.

Really helpful links there dbd.Much appreciated!!

Thanks guys :).

And a big thanks to dbd :D.

Darthcoder.

---

### Post by dbd on 2006-10-24
hehe, no probs,

good luck :D

---

