---
title: "Opera for Linux errors"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Rosemere on 2007-08-02
When I try and access certain web sites a screen opens giving me errors.
Here is an example:

CSS - [http://www.thestar.com/App_Themes/TheStar/style.css](http://www.thestar.com/App_Themes/TheStar/style.css)
Linked-in stylesheet
Expected ruleset
Line 1559:

CSS - [http://www.thestar.com/App_Themes/TheStar/ratingComments.css](http://www.thestar.com/App_Themes/TheStar/ratingComments.css)

CSS - [http://ca.yahoo.com/_ylh=X3oDMTFia3RsNG4xBF9TAzE1NjI5MzQzBHBpZAMxODY2MjEEdGVzdAMwBHRtcGwDY2FfaW5kZXg-/](http://ca.yahoo.com/_ylh=X3oDMTFia3RsNG4xBF9TAzE1NjI5MzQzBHBpZAMxODY2MjEEdGVzdAMwBHRtcGwDY2FfaW5kZXg-/)


Is there something I can do to turn this screen of Error Console" off or should I repair something first. Using Feisty 7.04
[B][COLOR="Blue"]
Opera Information [/COLOR][/B]
Version  9.22 Build  655 
Platform  Linux    System     i686, 2.6.20-16-generic   Qt library  3.3.7
Java
Java Runtime Environment installed

---

### Post by LaRoza on 2007-08-02
Tools->Advanced->Error Console

-EDIT I am using 9.10. Are you being alerted to these errors?

---

### Post by LaRoza on 2007-08-02
I do get the errors in the console, but I am not alerted to them.

---

### Post by Rosemere on 2007-08-02
yes a whole page opens up with error after error. I have my home page set to yahoo. If I close the error page I can then click and log into Yahoo but it the error page shows every time I do a new opration. example click to open an email.

It also happens when I try and open web site for the Toronto Star.

---

### Post by LaRoza on 2007-08-02
I am assuming you have a recent version of Opera, but Opera 9.10 doesn't alert you. I am looking into some more.

-EDIT I found it, go to Tools->Quick Preferences->Edit Site Preferences->Scripting

Uncheck "Open Console on Error"

---

### Post by Rosemere on 2007-08-02
Sorry I did that and I still get errors when I choose [www.yahoo.com](www.yahoo.com).
Any other ideas. 

I also noticed in Preferences I have **two Sun Java Plugin Contol Panel **
Version 1.4 & 6 

**I also have two Policy Tools: **Version 1.4 & Version 6

---

