---
title: "aMSN, How we get in?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by bkios on 2008-03-20
HI, I am a beginner and I am trying to get in amsn but still nothing. 

It tells me

that It can't execute application: mozilla $url. Check preferences

Thanx for the help..

---

### Post by ohzopants on 2008-03-20
That means it's trying to open a web page with mozilla, which isn't installed.  Just open up the preferences and change mozilla to firefox (or opera, or konqueror, or whatever browser you use) and it should work.

Also, you should give pidgin a try.  In my opinion it is superior to aMSN, except it does not support webcams.

---

### Post by soapytheclown on 2008-03-20
if all you're after is the MSN protocol give emesene a try its just reached version one and because its written in python/GTK it doesnt look out of place on your desktop and isnt a memory / processor hog like (IMO) aMSN

[http://www.emesene.org/](http://www.emesene.org/)

or just add

deb [http://apt.emesene.org/](http://apt.emesene.org/) ./

to your sources.list (sudo gedit /etc/apt/sources.list) then update and install it:

sudo apt-get update
sudo apt-get install emesene

---

### Post by drubin on 2008-03-20
> **ohzopants said:**
> 
Also, you should give pidgin a try.  In my opinion it is superior to aMSN, except it does not support webcams.

Not for msn support,

I use pidgin but then I like the idea of having msn, jabber, gtalk, all under one client. :)

---

### Post by cometa2k7 on 2008-03-20
I only actually use MSN, even though I hate Micro$oft, my friends all use Windows still, so they all have MSN.

I first used aMSN when I had PCLinuxOS2007, I liked it, but it is a bit slow sometimes. I'll have to try emesene when I get time, but I'm having to use Windows for my homework atm :(

Emesene does look quite clean though, and it would fit in well with Ubuntu.

**EDIT:**

I just tried Emesene, it's ok. It looks good, and functions alright, but it just doesn't do as much as aMSN, so for now, I'm sticking with aMSN.

What's in aMSN but not Emesene?
[LIST]
[*] GMail checker, with a plug-in
[*] Conversation logging (might be possible in Emesene, but I couldn't see it.)
[*] More things possible, from what I could see
[/LIST]

However, I did like the simple interface, but that won't sway me, I've used aMSN too long.

---

### Post by bkios on 2008-03-24
> **ohzopants said:**
> That means it's trying to open a web page with mozilla, which isn't installed.  Just open up the preferences and change mozilla to firefox (or opera, or konqueror, or whatever browser you use) and it should work.

Also, you should give pidgin a try.  In my opinion it is superior to aMSN, except it does not support webcams.

Please be more specific about preferences and mozilla, I didn't det it..

What it is supposed to change there?

---

### Post by rich257 on 2008-03-24
Account menu, preferences, Others tab, Application group and then Browwer field.  Change that to the appropriate command for your browser, for me it's "opera -newpage $url" since I use Opera

---

