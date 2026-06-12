---
title: "Opera as IE"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by deNoobius on 2005-11-23
Note--this is solved

In my quest to make Ubuntu an OS I can actually use, I would like to be able to access my work email via Ubuntu, and this requires IE 6.0.  I have tried both the Firefox user agent switcher (no joy) and Opera.  With Opera, I can see my mail, which is good, but the toolbar that would allow me to reply is not visible (no menu item for that function either), so I'm still back to Windows if anything to which I need to respond comes up.  The Opera page yields a message:

Browser name and version detected: Microsoft Internet Explorer 4.0 (compatible; MSIE 6.0; X11; Linux i686; en)

My question is, is there any tweak or add-on that anyone knows about that would let Opera emulate IE 6.0, which I believe would solve the problem?  

Thanks.

---

### Post by kont.raen on 2005-11-23
[QUOTE=deNoobius]In my quest to make Ubuntu an OS I can actually use, I would like to be able to access my work email via Ubuntu, and this requires IE 6.0.  I have tried both the Firefox user agent switcher (no joy) and Opera.  With Opera, I can see my mail, which is good, but the toolbar that would allow me to reply is not visible (no menu item for that function either), so I'm still back to Windows if anything to which I need to respond comes up.  The Opera page yields a message:

Browser name and version detected: Microsoft Internet Explorer 4.0 (compatible; MSIE 6.0; X11; Linux i686; en)

My question is, is there any tweak or add-on that anyone knows about that would let Opera emulate IE 6.0, which I believe would solve the problem?  

Thanks.[/QUOTE]


Hmmm - not that I would be aware of one - but what about trying to set up a mail client, that fetches your mail via POP3 or IMAP? Wouldn't that be a possibility?

---

### Post by kperkins on 2005-11-23
Which version of Opera did you try?  The newest  (8.51) can be set to show as MSIE 6.0 (and I thought earlier versions could, too).
(This is what shows for a user agent at grc.com--User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; X11; Linux i686; en) Opera 8.51)
You might try that.
[rant]
I really don't understand why anyone should need a specific browser to read email, and I think that any business using a web-based email would be better off using an open source client (like squirrelmail, or horde) which works in all browsers, rather than some proprietary one that you need a specific browser for. I would, also, think that a business would be leary about something like that, just because of all the security problems with IE (theres a new one just found the other day, which is a doosie), and would want there employees to use a different browser.
[/rant]
Sorry about the rant, but some things just get my goat, and need to be said.  If I worked for this company, I'd be putting in suggestions all the time about changing email services. :D

---

### Post by aysiu on 2005-11-23
You can use IE6 in Linux, too.
Get extra repositories (see my sig).
Type this in a terminal ```
sudo apt-get install wine cabextract
``` Then go to [IEs4Linux](http://www.tatanka.com.br/ies4linux/) and download their .tar.gz. Extract it and run it.

---

### Post by deNoobius on 2005-11-23
[QUOTE=kperkins]
I really don't understand why anyone should need a specific browser to read email[/QUOTE]

First of all, thanks for responding.

I'm not too thrilled about the Firefox incompatibility either, but that's how they set it up.  If you try to use any other browser, it actually throws an error saying that it will only work with IE 6.0 and other browsers are not permitted.

I used Automatix to get the Opera, so I think it's up to date, but I do get some errors on opening Opera.  They didn't look like anything critical, but I'll take a closer look when I get home.  Maybe I'm missing a critical plug-in or java library or something.  

Otherwise, the 4.0 "compatible with" 6.0 doesn't seem to work...the system has to actually "see" IE 6.0.  I am pleased about Opera allowing me to READ my email, though.  Worst comes to worst, there's a page somewhere about using IE 6.0 with Wine, and I'll try that if nothing else works.  I may need help, though (see my screen name).

---

### Post by deNoobius on 2005-11-23
[QUOTE=aysiu]You can use IE6 in Linux, too.
Get extra repositories (see my sig).
Type this in a terminal ```
sudo apt-get install wine cabextract
``` Then go to [IEs4Linux](http://www.tatanka.com.br/ies4linux/) and download their .tar.gz. Extract it and run it.[/QUOTE]

Thanks Aysiu, if I can't get Opera to work, I will do that.

---

### Post by deNoobius on 2005-11-23
Thanks, IE in Wine does the job.  A bit slow (probably due to my ancient computer that is my Ubuntu test bed), though, but at least no rebooting into Windows.

---

### Post by tim15856 on 2005-11-24
The email must use activex if it requires IE. There are some activex plug-ins that work on certain versions of other browsers.

---

### Post by aysiu on 2005-11-24
[QUOTE=tim15856]The email must use activex if it requires IE.[/QUOTE] It *must* use ActiveX? I would hope so, but I don't think it's true. I think some people design things to work with only Internet Explorer for absolutely no good reason.

---

### Post by tim15856 on 2005-11-25
[QUOTE=aysiu]It *must* use ActiveX? I would hope so, but I don't think it's true. I think some people design things to work with only Internet Explorer for absolutely no good reason.[/QUOTE]

Poor choice of words. Might or probably would be better.:rolleyes:

---

### Post by deNoobius on 2005-11-27
Everyone, thanks.  IE4linux works well enough for the one thing I need it for.

---

