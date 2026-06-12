---
title: "Associate Firefox with Kmail ?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by robertpolson on 2007-03-09
I have Kubuntu and like KDE a lot and everything in it but one thing. I like Firefox more than Konqueror, but I like KDE Kontact. My problem is that Firefox does not work with Kmail.

When I press in Firefox - File - Send Link, nothing happens.

How can I associate Firefox - send link with Kmail ?

---

### Post by C-A on 2007-03-09
> **robertpolson said:**
> I have Kubuntu and like KDE a lot and everything in it but one thing. I like Firefox more than Konqueror, but I like KDE Kontact. My problem is that Firefox does not work with Kmail.

When I press in Firefox - File - Send Link, nothing happens.

How can I associate Firefox - send link with Kmail ?

Check [this ]("http://jatshergill.com/blog/2006/05/16/how-to-setup-the-default-web-browser-in-kubuntu/") out. It worked for me. You end up changing the setting in Konqueror which seems kinda backwards.

Edit: OK I tried to send a link in firefox and that does not work for your problem but it will set firefox as your default browser for many apps.

---

### Post by zubrug on 2007-03-09
system settings - default applications

---

### Post by C-A on 2007-03-09
I found [this]("http://opensource.weblogsinc.com/2006/03/27/send-email-from-firefox-with-kmail/"). It looks like an answer to your problem.

---

### Post by C-A on 2007-03-09
> **C-A said:**
> I found [this]("http://opensource.weblogsinc.com/2006/03/27/send-email-from-firefox-with-kmail/"). It looks like an answer to your problem.

I got it to work following the above link. However, the instructions in the link said to edit: user.js but I edited :  prefs.js and got it to work.

---

### Post by C-A on 2007-03-09
OK, back again for another edit. Here are the comments on the second link I posted which explain the proper way to set the default mail app for sending a link:
> If you observe the warning in the pref.js file. Do not hand edit the file. (At least in 1.0.x of fx (aka firefox)), your changes can be overwriten when you exit fx. So what is the pref way?

Enter "about:config" (less the ") into the url field of fx, this will bring up the config & perf data for your browser. Right click on open space and select New -> String. This opens up a name box and entry field where you put;

"network.protocol-handler.app.mailto" (less the ")

Then after you hit enter, it opens up the string box were you will now put;

"kmailservice" (less the ")

Then restart your browser.

---

### Post by robertpolson on 2007-03-10
Thank you, that worked.

---

