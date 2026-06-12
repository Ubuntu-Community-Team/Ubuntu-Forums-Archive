---
title: "go gaddy don't go"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by stevehofmann21 on 2008-02-13
I am new to ubuntu and linux, I have a new website on go daddy .com and when I try tolaunch the "website tonight" account I get this message -

incompatible Browser: Mozilla 1.0.8

WebSite Tonight has detected that you are running an unsupported browser. To run WebSite Tonight 4.1, you must be running Microsoft Internet Explorer 6.0 or later, FireFox 1.0 or later (same as Netscape 5.0 or later), or Mac Platform Safari 3.0 or later.

I have Firefox 1.5, I downloaded Firefox 2 but I can't figure out how to dowmload it. I'm not even sure if I really need it??? I went to ubuntu and tried to follow instructions to load "tarballs ...???,  Help!?!?!?!

---

### Post by LRT on 2008-02-13
Ubuntu's synaptic package manager has firefox 2.0... try installing that through synaptic

---

### Post by jaytek13 on 2008-02-13
What distribution version are you using that you have such an old version of firefox? Either way, I would upgrade your firefox version to the newest and see if that takes care of the problem 

```
sudo apt-get install firefox
```, if you have the newest repositories.

---

### Post by PmDematagoda on 2008-02-13
Firefox 2 is usually preloaded on Ubuntu, could you please post the output of:-
```
cat /etc/lsb-release
```

---

### Post by sarracenia on 2008-03-15
Bumping...


Did you ever get Website Tonight to work Steve?

I'm getting the same error message, although I am already using Firefox 2.  I've tried using Wine to download IE, tried different versions of IE, tried the "useragent" firefox add-on, but nothing works.  I get close to being able to edit the text on a page, but then I get a "you are not authorized to view this page" screen displayed within the Website Tonight browser.

](*,)

---

### Post by ellaS on 2008-04-29
I have found website tonight to be very unstable and frustrating, and that was working in Windows in either Firefox or IE.  When I called tech support I was told it just doesn't work during certain parts of the day.  They didn't seem to think that considerable downtime and overall instability was a real issue.  I would suggest you not use it at all, even if you are able to find a way to get it to work in Ubuntu.

---

### Post by justin whitaker on 2008-04-29
I find most of the value added stuff from GoDaddy only really works in IE. Did you try it in IE6 in WINE?

---

### Post by dca on 2008-04-29
GoDaddy's entire operation runs on MS Windows Server 2003 so it would be no surprise to me that everything they offer would require IE6SP1 or greater...

---

