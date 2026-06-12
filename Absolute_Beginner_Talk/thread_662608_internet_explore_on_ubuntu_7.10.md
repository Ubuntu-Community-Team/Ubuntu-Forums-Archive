---
title: "internet explore on ubuntu 7.10?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by arvindenrique on 2008-01-09
can we use internet explorer in ubuntu 7.10? if yes then how to install it?

---

### Post by Pevichaey5 on 2008-01-09
you can install internet explorer 4 on linux with wine

but i really don't see why you would want it, firefox is better

---

### Post by Paqman on 2008-01-09
> **thexero said:**
> 
but i really don't see why you would want it, firefox is better

The most common reason is for web designers to do browser checks of their work.

Check out: [IEs4Linux](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by zabien1970 on 2008-01-09
> **thexero said:**
> you can install internet explorer 4 on linux with wine

but i really don't see why you would want it, firefox is better

I've run into a few issues like trying to listen to radio simulcasts of sports and such where the popup said 'sorry, this is only available for internet explorer', really sucks but what can you do?

---

### Post by Pevichaey5 on 2008-01-09
cheers

i never really thought about that lol :guitar:

---

### Post by Sef on 2008-01-09
There is a plug in for Firefox that makes the sites think Firefox is IE.   Also you could download [Opera]("http://opera.com") and set that to be IE.

---

### Post by Pevichaey5 on 2008-01-09
i think the plug he is on about is called 'agent switcher' or something

i remember installin it las night

---

### Post by Zip247 on 2008-01-09
As Paqman stated above, IES4linux works great.  I had to install it on my edubuntu 7.10 for my kids to be able to play on webkinz world.  After you follow the instructions on the link do not forget to get any ad-ons that you may need.  

You can choose what I.E you want to install also not just I.E. 4

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by Trampis on 2008-01-09
> **Sef said:**
> There is a plug in for Firefox that makes the sites think Firefox is IE.   Also you could download [Opera]("http://opera.com") and set that to be IE.

I got opera but I am not sure how to make it be IE, also what is that plugin for firefox. I need IE to run MathXL player for my online school. [MathXL]("http://asp.mathxl.com/wizard/wizard_install.asp")

---

### Post by eolson on 2008-01-09
The Firefox plus in is called "User Agent Switcher"  when you install it, it will appear under "tools" in Firefox.   Get it at the Firefox site.

I just went over the the MathXL site and I'm afraid your out of luck   Mac and Linux are specifically not supported.  Unless you are planning on running Firefox on Windows.

---

### Post by SeanHodges on 2008-01-09
I don't think a browser pretending to be IE is going to fix this particular problem, as the site needs ActiveX. 

Check wdecker's post further up for using IE in Linux, its your best bet.

---

### Post by SeanHodges on 2008-01-09
I can confirm that the website appears to work using IE4Linux (using Internet Explorer 6). I'm installing the required plug-in's as dictated by the site and haven't had any problems so far...

---

### Post by staticvoid on 2008-01-09
i think there is also a firefox addon which will open a new "ie tab"
[http://webexpose.org/2007/01/07/internet-explorer-7-on-linux/](http://webexpose.org/2007/01/07/internet-explorer-7-on-linux/)
[http://www.downloadsquad.com/2006/05/08/internet-explorer-for-linux/](http://www.downloadsquad.com/2006/05/08/internet-explorer-for-linux/)
[http://www.liewcf.com/blog/archives/2006/04/install-internet-explorer-6-on-linux/](http://www.liewcf.com/blog/archives/2006/04/install-internet-explorer-6-on-linux/)

:) go go google

sv

---

### Post by Trampis on 2008-01-09
> **SeanHodges said:**
> I can confirm that the website appears to work using IE4Linux (using Internet Explorer 6). I'm installing the required plug-in's as dictated by the site and haven't had any problems so far...

Thank you so much, IE4Linux runs the program and I can do my homework, the only thing that happened was when i attempted to install quicktime it failed, but i can just use mozilla for my quicktime content, thanks again!

---

### Post by ByteJuggler on 2008-01-09
> **zabien1970 said:**
> I've run into a few issues like trying to listen to radio simulcasts of sports and such where the popup said 'sorry, this is only available for internet explorer', really sucks but what can you do?

Some sites block other browsers by default and does so by checking the identification string sent by the browser.  You can configure e.g. Firefox to effectively lie to websites so they will think that it is IE.  Sometimes that's all you need to do to use it on an "IE only" site.  Of course, on some sites, the site functionality might actually contain IE anachronisms, and so then will probably break somewhere along the line.

I [quote]("http://aspnet.4guysfromrolla.com/demos/printPage.aspx?path=/articles/050504-1.aspx"): "Whenever a Web browser requests a page, it sends along a User-Agent string in the HTTP headers that is used to identify the browser. Internet Explorer, for example, sends the User-Agent string Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; .NET CLR 1.0.3705; .NET CLR 1.1.4322). Mozilla FireFox sends [something like] the User-Agent string Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.6) Gecko/20040206 Firefox/0.8. Some browsers don't send a User-Agent string, or send a "fake" User-Agent string. For example, with Opera you can instruct it to send the IE6 User-Agent string. There's an extension for Mozilla that offers the same functionality as well. (Interested in seeing what User-Agent string your browser is sending? Check out the [User-Agent live demo]("http://aspnet.4guysfromrolla.com/demos/UserAgent.aspx").)"

The extension/add-on for Firefox that allows you configure the indentifaction string easily for certain websites is the ["User Agent Switcher"]("https://addons.mozilla.org/en-US/firefox/addon/59")

---

