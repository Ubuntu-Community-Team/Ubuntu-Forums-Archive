---
title: "[SOLVED] Anyone running Bluefish ? Need help"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-08-21
I installed Bluefish in Feisty using Add/Remove. 

When I open an HTML file and click on "View in Browser" nothing happens.
When I try to open an URL, nothing opens.

I looked at preferences and went through all Menus but could not figure out.

Any suggestions?

---

### Post by frrobert on 2007-08-21
If Firefox is your default browser, you need to add a entry for it under external programs

Go to Preferences then External Programs

Add a new browser entry
Label it Firefox  the command should be

```
firefox -remote 'openURL(%s, new-window)' || firefox %s&
```

Then drag this entry to the top of the list.

This will cause firefox to open when you hit the globe icon.  The globe icon tries to open the first entry.


If you want to be able to select the browser from the External menu

Under Preferences, then User Interface
Select External browsers and make sure it is checked.

Hope this helps

---

### Post by dptxp on 2007-08-21
Thanks. It worked. I have both Firefox and swiftweasel, I normally use swiftweasel as new windows do not open in new tabs in Firefox (do not know why because it is configured for new tabs in preferences).

I assume that for swiftweasel I have to replace 'firefox' with 'swiftweasel' in both label and command line.

I used IBM Websphere Homepage Builder in Windows (had a sample CD), any baby can use in 'free layout mode', but I want to get into serious Web design mainly to teach my daughter. I hope that Bluefish is a good choice.

---

### Post by andrew.46 on 2007-09-04
Hi,

 Saw your message about Bluefish:

> **dptxp said:**
> [...] I used IBM Websphere Homepage Builder in Windows (had a sample CD), any baby can use in 'free layout mode', but I want to get into serious Web design mainly to teach my daughter. I hope that Bluefish is a good choice.

 I believe that you cannot go wrong with Bluefish. My [personal site]("http://people.aapt.net.au/~adjlstrong/ubuntu.html") has been built from the ground up with Bluefish and if used correctly it allows you to create very clean html.

 Mostly I answered your post because I saw your cavaliers in your id photo thingy. I have a 6 year old cavalier called Madison who is the queen of our house :-)

                       Andrew

---

### Post by brutalandkind on 2008-06-08
Hi, I know this is an old thread, but I'm having a similar problem. I'm trying to set Firefox-2 as the external browser in Bluefish. I've tried several different approaches in the "edit, preferences, external programs, browsers" screen, but no matter what I try to add, as soon as I click on "apply" the line clears to a blank. 

EDIT: Solved it myself; all I needed to do was leave the ampersand off the line and the program took the addition just fine. (Sometimes I hate being a newbie....)

---

