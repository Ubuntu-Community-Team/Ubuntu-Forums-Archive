---
title: "Tricking Firefox and Ubuntu"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2008-02-13
Recently I was shown how to change Firefox so that Turbo Tax would think it was windows. This has worked very well. I wonder if there is a way to trick Firefox into using the Microsoft 
Money Central Investment Toolbox?

 	 The MSN Money Investment Toolbox requires a more recent version of Microsoft Windows or Microsoft Internet Explorer. Windows NT 4.0, versions of Windows earlier than XP, and versions of Internet Explorer earlier than 6.0 no longer support the MSN Money Investment Toolbox. You can either upgrade your version of Windows and Internet Explorer to continue using the MSN Money Investment Toolbox, or you can continue using your current system and use the MSN Money Basic Tools

I have a screen shot of the upgrade to Money Central upgrade page but do not know how to attach so here is the url.:)

[http://moneycentral.msn.com/investor/controls/netchoice.asp?target=http%3A%2F%2Fmoneycentral%2Emsn%2Ecom%2Fstock%5Fportfolio](http://moneycentral.msn.com/investor/controls/netchoice.asp?target=http%3A%2F%2Fmoneycentral%2Emsn%2Ecom%2Fstock%5Fportfolio)

---

### Post by macogw on 2008-02-13
It might use ActiveX controls to do fancy-shmancy programming tricks, in which case changing the User Agent String won't help any.  You can install [IEs4Linux](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu) and use that for it.

---

### Post by rosswmcgee on 2008-02-13
So using the link you gave me I just use the sudo's shown, I can do that, is there anything else I need to beware of ? In noticed the commands are 
Edgy, do I sub Gutsy?

---

### Post by maestrobwh1 on 2008-02-13
I might misunderstand your question, but if you are installing IES4LINUX, you should not use "sudo"

I used IES4linux sometimes, but be aware that:
Flash works
Java does not.

If you have an installation CD for windows, you could use VirtualBox and install Windows as a Virtual Machine.

---

### Post by macogw on 2008-02-13
> **maestrobwh1 said:**
> I might misunderstand your question, but if you are installing IES4LINUX, you should not use "sudo"

I used IES4linux sometimes, but be aware that:
Flash works
Java does not.

If you have an installation CD for windows, you could use VirtualBox and install Windows as a Virtual Machine.

The sudos s/he's referring to are the part where Wine and cabextract get installed.

And yes, you'd replace "edgy" with "gutsy" to use Wine's Gutsy repos.

---

### Post by jaytek13 on 2008-02-13
I can't seem to find it atm, but there are certainly firefox addons that you can use that would make firefox report to websites that it is actually IE7 on Windows XP. I'd do some searching for this and see if it works first before trying to go through the hassle of installing erroneous software, if only because while it certainly may be the case that the site uses activex, this isn't necessarily what is preventing you from doing so. I've encountered many sites like this that require you have a certain browser and a certain OS only because, from what I can see, the web developer who wrote the page doesn't know what he's doing or decided to be lazy and create the page in IE while not caring what it looked like in other browsers.

---

### Post by macogw on 2008-02-13
> **jaytek13 said:**
> I can't seem to find it atm, but there are certainly firefox addons that you can use that would make firefox report to websites that it is actually IE7 on Windows XP. I'd do some searching for this and see if it works first before trying to go through the hassle of installing erroneous software, if only because while it certainly may be the case that the site uses activex, this isn't necessarily what is preventing you from doing so. I've encountered many sites like this that require you have a certain browser and a certain OS only because, from what I can see, the web developer who wrote the page doesn't know what he's doing or decided to be lazy and create the page in IE while not caring what it looked like in other browsers.

S/he said s/he already tried that though.

---

### Post by jaytek13 on 2008-02-13
> **macogw said:**
> S/he said s/he already tried that though.

Well, the OP mentioned having firefox report it was under Windows, but didn't make mention to whether he used the addon he is currently using is reporting a different browser. The page he, and I assume everyone else is seeing (since I'm seeing the same "error" as the OP stated) is usually a redirect when an incompatible browser or OS is being reported. If it was an activex issue it would more likely be an error that related to enabling activex, not upgrading the software.

In fact, since the title of the page is "Netscape Choice," I would assume that is the redirect when the page detects netscape/mozilla(firefox), which would indicate that IE7 isn't being reported.

Of course, that said, since it is a MS product the chances that it uses activex for it to work properly are pretty high, so everyone else's suggestions are still valid, but I thought it would be best to try the simple solution first just to make sure.

---

### Post by macogw on 2008-02-14
OK, sorry jaytek13, you're right.  The OP didn't say whether it was changing what browser it reported or not.  I've heard of ActiveX being used to determine whether or not a page like that should show up before, though.

---

### Post by rosswmcgee on 2008-02-14
Well the reason behind all this is because I have been unable to find any other stock or mutual fund app that allows you to chart total return. Most apps just chart the price. Is there such an app in Linux? I have never found one in windows other thatn MicorSoft money deluxe.

---

### Post by Cypher on 2008-02-14
Firefox has the User Agent switcher add-on that allows you to charade as IE or Opera..and if a website is just checking the browser agent info, then this will work but most MSN sites use ASP.NET or ActiveX code, as **macogw** initially suggested, that will not work in Firefox and thus yield a broken site.

In this case running IE is the only recourse either on Windows, as IE4Linux orthrough Virtualbox/VMWare..

---

### Post by rosswmcgee on 2008-02-14
The user agent add on worked as it let me get to the download page and click on download, but nothing is downloaded. So I suppose it is time to give up this venture, but I did learn about the user agent switcher and that is good. I guess if I really wanted to fool around and do the wine thing, it might work. It just easier to go to my wifes windows machine and get the info. Thanks Ross

---

