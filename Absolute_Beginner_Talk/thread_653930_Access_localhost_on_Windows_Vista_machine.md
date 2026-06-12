---
title: "Access localhost on Windows Vista machine"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by desk2web on 2007-12-30
I know that this is going to be something really simple, so I'll apologise now, but having searched I cannot seem to find the answer,

In a nutshell, I have a Windows Vista Ultimate laptop, running with WAMP Server so that I can develop in Dreamweaver and view the sites for testing, however, I also want to be able to view those same sites on my Ubuntu box, so, what do I need to do in order to view the site?

I have tried putting the PC name in the browser bar, but thats useless, I've tried sharing the wamp folder, which works of a fashion, except that it doesn't show the page properly it shows the code for the php I have used etc.

There must be some way to do this, but I am stuck.

Any advice would be appreciated.

---

### Post by SOULRiDER on 2007-12-30
I'm guessing you need to have apache running in Ubuntu. To acces it you'll have to type the IP of your ubuntu mahcine in the address bar of your browser.

---

### Post by popch on 2007-12-30
Your Vista machine must have an IP address. If you do not know it, open a command window in Windows and enter the command ***ipconfig*** . This will output a few lines of text, one of them labelled 'IP Address' and a group of four numbers which are separated by dots, much like '192.168.0.2'.

While your WAMP server is running in the Vista box, open a browser on your Ubuntu box and enter the following URL in the browser's address field:

[http://192.168.0.2](http://192.168.0.2)

Substitute the Address of your WAMP box, of course.

---

### Post by desk2web on 2007-12-30
Perfect, thanks, as always its the simple solutions you forget to look at!

---

