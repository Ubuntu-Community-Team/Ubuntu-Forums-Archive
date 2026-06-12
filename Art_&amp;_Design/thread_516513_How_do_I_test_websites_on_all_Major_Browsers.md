---
title: "How do I test websites on all Major Browsers?"
date: 2007-08-03
forum: Art &amp; Design
---

### Post by Rohen on 2007-08-03
Hello All.

I am designing a website right now from my Ubuntu machine, and apparently It's pretty crappy when you find out that something that works perfectly well on Firefox, looks like it got run over by tank on Internet Explorer or Opera.  So my question to you guys is:

Is there any way to check how the website looks on all major browsers from Ubuntu?

:confused:

---

### Post by Lord Illidan on 2007-08-03
First, I'd make sure that it is conforming to W3C standards.

Opera is also available in Linux, too.

---

### Post by Nuverde on 2007-08-03
Check out [ies4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") ([http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page))
This wrapper is basically a simplified process for installing IE and/or wine under linux.  Sometimes the fonts and alignments don't look the same in IE under Linux as they do under Windows, but this is still a good tool to check your CSS, Javascript, etc.  I would still suggest going to a real windows box every once in a while to do some testing before things go live.

---

### Post by LaRoza on 2007-08-03
Not really, but you can do a lot from one OS.

I suggest testing in these:

0. IE 6
1. IE 7
2. Firefox 2.x
3. Opera 9.x
4. Safari/Konqueror
5. Lynx

Using IE is neccessary, especially with CSS, so you should find a way to use a Windows box for this.

Firefox and Opera are available for Ubuntu.

Safari is only available for Macs and Windows, but it is the same as Konqueror in terms of rendering, so use that. (Watch out, Scripts have behaved weird on Safari for me in the past)

Lynx is neccessary because you will see how screen readers and search engines will see your site. If you want to add a special link for those with screen readers, use css to hide it, so only those using a screen reader or text browser will see it.

Remember to test at various resolutions, get the web developer extension for Firefox, it makes life easier.

Also, you can make an image with the various dimensions, 800x600, 1024x768, etc as coloured boxes and set it as your background, then all you have to do is resize.

---

### Post by Lord Illidan on 2007-08-03
Also, FF on Windows and Linux may be different..I've seen this in a couple websites.

---

### Post by Rohen on 2007-08-03
Thanks LaRoza!

Great tips.  I guess I'm gonna have to use Windows for IE right?  I mean there's no way to have a 100% way of looking at a IE page from Linux...  You know there's a firefox extension called "IE Tab" but its not available for Linux, which really bytes, its actually a great way to check.  

Now for the sake of simplicity, if I install IE using wine, will it be good enough for web site testing?  Know any guides on how to go about doing that?

Also, there's something called ELinks in the repositories, it's sorta like the lite version, any experience with that or should I stick with the Lynx?  Thanks!

8-[

---

### Post by LaRoza on 2007-08-03
> **Rohen said:**
> Thanks LaRoza!

Great tips.  I guess I'm gonna have to use Windows for IE right?  I mean there's no way to have a 100% way of looking at a IE page from Linux...  You know there's a firefox extension called "IE Tab" but its not available for Linux, which really bytes, its actually a great way to check.  

Now for the sake of simplicity, if I install IE using wine, will it be good enough for web site testing?  Know any guides on how to go about doing that?

Also, there's something called ELinks in the repositories, it's sorta like the lite version, any experience with that or should I stick with the Lynx?  Thanks!

8-[

Stick with Lynx, if you really want to, you can get a Firefox extension called, Yellowpipe Lynx View or something, which gives you a good idea of what it would look like.
 
Sadly, with IE you should use Windows, almost nobody will be using IE from Linux. I suggest for testing, use an actual Windows and IE.

I design for Firefox first, test in Opera, then go to IE. If you are aware of CSS issues in IE and avoid them, it should work fine, if the others have no trouble. See my sig for a CSS forum and wiki.

With Lynx, the main issue is getting to see how your site handles with just text, a good homepage should have very little images, and content and links. If you use image links, provide text links also.

-EDIT IE7 is pretty good for most things, if it works in Firefox and Opera, it will almost certainly work in IE 7, IE 6 is the problem.

---

### Post by Dragonbite on 2007-08-03
You know what would be a great project? A website where you enter the URL of another website and it generates an image/snapshot of the website as it would be seen in 
[LIST]
[*]Internet Explorer (Windows)
[*]Firefox
[*]Opera
[*]Safari (Apple)
[*]Konquerer (Linux)
[/LIST]
So you can see how a page will look in each without having to go and mave multiple test boxes, or having to use IE4Linux or Virtual Machines or the like.

Can even control the size/resolution of the screen it would be viewed on?

---

### Post by Rohen on 2007-08-03
> **Dragonbite said:**
> You know what would be a great project? A website where you enter the URL of another website and it generates an image/snapshot of the website as it would be seen in 


Well yesterday I found a site that sorta does that, downside is that you wait at least 30 minutes to get back the results, if you want you here's [the link.]("http://browsershots.org/")

I think the site is down right now err something cuz I can't get to the site.

---

### Post by costa_g on 2007-08-04
I found out about this on Life Hacker: [http://v04.browsershots.org/](http://v04.browsershots.org/)

---

### Post by ashvala on 2007-08-05
Download Opera... Test on Opera
Get QEMU... get Windows.img from the web...
Emulate IE on QEMU

---

### Post by rejser on 2007-08-05
trouble is that that only tests the layout...
what about functionality?
I hade a site where you could browse other pages within the frame and different browser engines was used according to choices made in the beginning. Will se if I can find it.

---

### Post by RAV TUX on 2007-08-29
> **Rohen said:**
> Hello All.

I am designing a website right now from my Ubuntu machine, and apparently It's pretty crappy when you find out that something that works perfectly well on Firefox, looks like it got run over by tank on Internet Explorer or Opera.  So my question to you guys is:

Is there any way to check how the website looks on all major browsers from Ubuntu?

:confused:[http://browsershots.org/](http://browsershots.org/)

---

### Post by Aethelwine on 2007-09-10
Hi

This issue is major issue in web page creation, both internet explorer and netscape we can view same error no change in that browser,  but firefox opera different, always firefox only give some trouble while creating page

one solution is you can read it about this in W3School , it will give good solution to this problem , one more thing you can also use mac to rectify this , because mac only give clear error and any over laped done  in web page than pc , in pc we couldn't see the error

:KS

---

