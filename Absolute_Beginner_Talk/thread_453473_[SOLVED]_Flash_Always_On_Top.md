---
title: "[SOLVED] Flash Always On Top"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Dougie187 on 2007-05-24
So i have been having this very odd problem. Not sure if anyone else has this same problem but i will describe it and then there is a picture attached that you can check out. Also anyone can go to bestbuy.com and see if it has the same problem for them (a very common site i know has the issue for me) 

Anyways, so my problem is that when ever there is a flash item playing, it is always on top of everything. So if the website has dynamic menus the menus show up and go behind the flash movie so I cannot see when the menu holds, as well as click on any of the menu entries. I would really like to get this problem solved, so I can click on menu items. Anyways see the picture if you dont quite understand what my problem is. Thanks in advance for any help.

[ATTACH]33318[/ATTACH]

---

### Post by LaRoza on 2007-05-24
No problem here.

What version of Firefox are you using, maybe that is it.

---

### Post by Dougie187 on 2007-05-24
I am using 2.0.0.3.

---

### Post by Dougie187 on 2007-05-24
You're also in windows when you do that. Im in ubuntu. In my windows I dont have a problem. Just in ubuntu.

---

### Post by lazyart on 2007-05-24
I have this same problem, with Dapper thru Fiesty.

But real good comparing apples to oranges there.

---

### Post by mech7 on 2007-05-24
yeah have it too :(

---

### Post by Dougie187 on 2007-05-24
Anyone have any idea? Maybe something in about:config?

---

### Post by hardyn on 2007-05-24
wurd... here too... all my machines.

---

### Post by mcduck on 2007-05-24
It's a known issue in Linux version of Flash plugin. There is not really anything you can do about it, besides hope that either Adobe or Firefox developers fix it..

---

### Post by Dougie187 on 2007-05-24
I guess its a known bug. Not sure if its with firefox or flash though. Alot of people say its flash because other browsers have the same issue. heres a link for the bug.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/49613](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/49613)

Let me know if anyone finds any info out.

---

### Post by Dougie187 on 2007-05-24
Theres an attachment on this web site called updated to trunk. Im not sure what that means.. if it can help at all. here is the link let me know if you can get somewhere with this.

[https://bugzilla.mozilla.org/show_bug.cgi?id=137189](https://bugzilla.mozilla.org/show_bug.cgi?id=137189)

---

### Post by Murtadh on 2007-10-16
Even now on Gutsy RC I have the same problem ? it makes me #-o

And I think this is not a firefox problem, because I installed Opera and it has the same issue :confused:

Tested with [http://www.sonystyle.com](http://www.sonystyle.com) site

---

### Post by -grubby on 2007-10-16
never happened to me

---

### Post by bigboy_pdb on 2007-10-16
It has happened to me in Firefox with different Ubuntu installations on different computers. For Best Buy's site, you can just click on the category and it will take you to a page with all of the links. However, for other sites you might have trouble due to this issue.

**[EDIT]**
Some other workarounds would be to look at the source for the website or to use "site:*website* *search_terms*" to try to search the site in Google (where *website* is the url for the website that you want to find something in and *search_terms* are terms that might allow you to access the pages in the section the flash is blocking).
**[/EDIT]**

---

### Post by Dougie187 on 2008-01-29
Has anyone tested with the new flash plugin from adobe's site?

---

### Post by philinux on 2008-01-29
It's to do with transparency. They've changed the site now anyway.

---

### Post by michaelzap on 2008-01-29
As mcduck said, it's a known issue with Flash on Linux. It's very annoying, and there's nothing that you can do about it. Flash on Linux doesn't support wmode properly.

---

### Post by FuturePilot on 2008-01-29
No still doesn't work with the latest version.

---

### Post by Dougie187 on 2008-01-29
i know its a known bug and theres nothing you can do about it. But I heard thought I read somewhere that either adobe or mozilla was going to be working on it. And I also thought I read that it had to be done by adobe, so I thought that the new version might have helped.

---

### Post by Dougie187 on 2008-04-04
Has anyone messed with this bug yet as of firefox 3 beta 5?

---

### Post by fatality_uk on 2008-04-04
There's a few <div> hacks about on the net for this. I know it doesn't help Gecko rendering on sites you don't control, but is fixable if only the site developers took the time to investigate the options.

[http://blog.marcoos.com/2006/07/21/html-div-above-a-flash-animation-on-linux-its-possible/](http://blog.marcoos.com/2006/07/21/html-div-above-a-flash-animation-on-linux-its-possible/)

---

### Post by djuniah on 2008-04-24
could a greasemonkey script be built to accomodate that last solution client-side?

---

