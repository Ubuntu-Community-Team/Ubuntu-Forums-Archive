---
title: "Help: Firefox prompts to save .php instead of displaying the webpage"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by 2ig2ag on 2007-11-18
Hi!
I am using firefox 2.0.0.8 and I have searched for solution with google but in vain.
Often when I click a link, instead of showing the webpage, a window pops up to asked me to save a .php file( such as when downloading a file). After saving the .php file ,I open it with text-editor but the file is blank - it's a empty file. Thus I can't view the webpage.

I don't know why is this. All I want is to know how can I view the page normally.

Thx in advance!

---

### Post by llamakc on 2007-11-18
Is this a page on YOUR webserver, or somewhere else on the web? If it's elsewhere on the web, it isn't your problem. The webmaster/admin of the site needs to fix the issue.

---

### Post by handaxe on 2007-11-18
I have seen this behaviour, sometimes when downloading a file.  A refresh of the page or clicking again on the file usually gets the desired result.

So, not a chronic problem for me but definitely irritating....  If you encounter this, does it ALWAYS try to save the *.php file and never deliver the right page / file?
HA

---

### Post by 2ig2ag on 2007-11-19
Thx!
I am viewing the page on the web.
Sometimes after I refresh the page, the desired page would appear. But sometimes it always prompt to save the .php no matter how many times I have tried, such as the following page:
[https://addons.mozilla.org/extension...info.php?id=60](https://addons.mozilla.org/extension...info.php?id=60) 
What's more, I have also asked some campus mates who are also using firefox in linux to try the page above, and they don't have any problem viewing the page. In addition, I have never encountered such problem in Windows even when using the windows version of firefox. 

Thus I draw the conclusion that something is wrong with my ubuntu system. How can I deal with it?

---

### Post by handaxe on 2007-11-19
Hi

The page you referred works for me - it has an error in that the page/file is missing, but it loads properly.  Groping in the dark here.  There is a bug report that seems similar / same ballpark,

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/139009](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/139009)

Secondly: is the fact that this is a https page significant?  Ie do  http pages give the problem? SSL can be flaky under Firefox in Gutsy, at least IME.

HA

---

### Post by 2ig2ag on 2007-11-19
Thx. Problem solved.
Quite to my suprise, it's something wrong with my network in Ubuntu.-_-!

---

### Post by handaxe on 2007-11-20
Glad to hear.

In order to be most helpful to others who may later come looking for answers to this problem, would you mind writing what was the matter with your ubuntu network setup and what you changed to make it work.

Regards,

HA

---

