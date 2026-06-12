---
title: "server error in '/' application"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Xiequn on 2007-05-23
Hi, I got this, repeatedly, today on the net.
[HTML]Server Error in '/' Application.
The resource cannot be found.
Description: HTTP 404. The resource you are looking for (or one of its dependencies) could have been removed, had its name changed, or is temporarily unavailable. Please review the following URL and make sure that it is spelled correctly.

Requested Url: /WebForm/Bill/BillPrdInfo.aspx[/HTML]
I understand this is not really about Feisty but I MUST get into this site for my business and when I logged into XP it opened immediately. Is it a Firefox thing? I used the 'user agent switcher' without any effect
So...what, how and where do I go to remedy this, please.
Any ideas?
thanks in advance.
jen

---

### Post by Pragmatist on 2007-05-25
It could help if we know the website.

---

### Post by Cypher on 2007-05-25
You used IE on XP to get into the site? It might be using some active-X control that will not run in Firefox on Linux..

---

### Post by Xiequn on 2007-05-29
Hi, sorry to take so long but I've been flat out.
Thanks for your replies.
OK, the website is a local business in china
[http://scm.sgcs.com.cn/](http://scm.sgcs.com.cn/)
and I usually, every day, access this from IE in XP.
I tried to use the 'user agent switcher' but it made no difference. If its 'active x' controls how can I load them up? Where? etc.

Thanks again, I appreciate your help.
I hope this can be fixed so I can move from XP, the virus stuff is really concerning me.

---

### Post by Pragmatist on 2007-05-29
I am able to get to the link you gave (see attached screen shot) and I use firefox.  Just to make sure I understand correctly, your not able to get to this page?  Or, does the problem occur when trying to log in??

---

### Post by Xiequn on 2007-05-30
Sorry, I didn't make myself clear. I log on to this site and in trying to view a particular page gives me this error. Its a page regarding goods orders to and from this company, which is why its important.
It takes about 3 steps or levels to get to where the error occurs.
Is It active-x stuff?

---

### Post by Pragmatist on 2007-05-30
> **Xiequn said:**
> Sorry, I didn't make myself clear. I log on to this site and in trying to view a particular page gives me this error. Its a page regarding goods orders to and from this company, which is why its important.
It takes about 3 steps or levels to get to where the error occurs.
Is It active-x stuff?

Since we can't log in, it is hard to tell.  From what you've told us, you either own this site, or know who does.  They (or whoever made their website) would be in a good postion to tell you if it uses ActiveX.

However, if you really want to test it, you can install an ActiveX plugin for firefox (Note, you need to use an earlier version of firefox 1.5 or below):
[http://kb.mozillazine.org/ActiveX](http://kb.mozillazine.org/ActiveX)

---

### Post by Xiequn on 2007-05-31
Hi Pragmatist, I had a look at that link, thanks.
It seems that ActiveX is a program for audio/video on a site, which seems odd for this site as its just a spreadsheet style for orders. I go there and download the latest orders for goods. I've never seen any video on it or heard any music whatever.
When they open up I'll call their system people and ask.
That link mentioned 'crossoveroffice' as having the activex installed, so I just tried it (via automatix) but it made no difference.
Changing firefox backwards sounds really complex for me.
Thanks for your help.

---

### Post by Xiequn on 2007-06-03
Hi guys, the owners of the site in question swear they don't use ActiveX.
i guess I'm back to square 1.

---

### Post by Pragmatist on 2007-06-03
FYI, the error you got demonstrates that you DID connect, but the website was delivering you an error without explanation.  Here is wikipedia's explanation of the HTTP 404 Error:

> 
[SIZE=3]The **404 or not found error message**  is an http standard response code indicating that **the client was able to communicate with the server**, but either the **server could not find** what was requested,** or it was** **configured not to fulfill the request and not reveal the reason why**. [/SIZE][SIZE=3]**404 errors should not be confused with "server not found"** or similar errors, in which a connection to the destination server cannot be made at all.[/SIZE]
You can find the wikipedia article here: [http://en.wikipedia.org/wiki/404_error](http://en.wikipedia.org/wiki/404_error)

.aspx  seems to be .NET technology and I personally have had no problem using sites with .aspx

So, just to summarize, you are in the website, but the website is not delivering the results page to you for some reason.  Now if your sure you can get the results with IE, the best thing is probably to "view source" on IE, save it, and post it here.  If we see the source of the page your reaching on IE, but not reaching with Firefox, we have some chance of finding out why.  You can "view source" or "view page source" by Right-Clicking on the page.  If I remember correctly, it is one of the last choices on the menu.  Then you should be able to go to File-->Save As  and save the page.  Email the file to yourself, download it to your Ubuntu machine, and post it here.

---

### Post by Xiequn on 2007-06-03
I have discovered the problem, thanks tp your leads. There is a check box for automatic loading that gives this error when not in IE. I have to uncheck it, then straight in.
So easy in the end.
Thanks again for all your help and effort.
Now back to my PDA stuff

---

