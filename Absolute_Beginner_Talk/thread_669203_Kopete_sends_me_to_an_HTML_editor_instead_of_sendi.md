---
title: "Kopete sends me to an HTML editor instead of sending me to my MSN hotmail page"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by thony971 on 2008-01-16
Hi Guys,

I'm new to Ubuntu and I love it. But I have a problem, whenever I try to check my mail through Kopete it opens up my HTML editor: Screem HTML/XML editor.

Can someone help me fix this problem so when I click on "Open Inbox" on Kopete it would open up a Firefox broser. I tried checking if it's a file type problem under Screem, but I couldn't find anything about the file types. And Firefox is my default browser.

---

### Post by nonexl on 2008-02-10
Go to** Synaptic**
Install **kcontrol**
open terminal
type in **kcontrol** (*no sudo required*)
kde components
file associations
search for **html** (and/or php)
In the **Application Preferences Order** *Move Up* or *Add*    **firefox** (or any other browser you want)
Test if it works
Then go back to **Synaptic** and remove **kcontrol** (along with **kdebase-data** & **kicker**)
*_! More important show you're finger to all those KDE users who give us a hard time figuring this out !_*

Happy Kopete messaging on GNOME

---

