---
title: "My Website doesn't display right in Linux, shame on me! (how do I fix it)"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Thenotsowyzewun on 2006-08-11
Hi,

My Website (well, sort of, it's just an eBay About Me page at the moment (and probably for awhile to be honest) is at [www.dvdextras.co.uk]("http://www.dvdextras.co.uk")

It displays correctly in Internet Explorer in Windows, but not in Firefox 1.5.0.5 (admittedly not the stable release then) in Ubuntu 6.0.6.

How does it show up for you? I'm not sure how to make it display properly under Linux (but the problem may be with Filmloop and not my HTML).

Thanks very much,

Duncan

P.S: Got any suggestions how I can improve it? As you can see from my member stats I've just started!

---

### Post by aysiu on 2006-08-11
Why don't you explain what's not appearing "correctly"?

---

### Post by fjm03 on 2006-08-11
At the moment your server appears to have been slash dotted.

But are you sure it's a Linux/Ubuntu problem and not a browser idiosyncracy?

Try viewing your site with Opera 9 on Dapper and see if the discrepencies persist.

---

### Post by goatflyer on 2006-08-11
Looks good in my ff 1.5.0.5

The film strip scrolls left to right.
Hovering over any of the small pictures calls up the bigger picture with the info in the main part of the screen.

I don't see any problem.

---

### Post by Thenotsowyzewun on 2006-08-12
Oops I assumed it wouldn't just be my browser.

[Here's]("http://i109.photobucket.com/albums/n65/DVDExtras/WindowsScreenshot.jpg") how it looks in Windows

and [here's]("http://i109.photobucket.com/albums/n65/DVDExtras/Screenshot.png") how it looks in Linux Dapper 6.0.6 (Firefox 1.5.0.5).

As you can see it doesn't centre justify in Linux, none of the item info is available, and the title and subtitle within the Filmloop applet don't appear either.
The font isn't right on Linux either, but that's because I don't have MS fonts installed (nor want them) so that parts fine).

Thanks for your quick replies :)

---

### Post by aysiu on 2006-08-12
Maybe for a better comparison, you should try Firefox in Windows.

I doubt very much this has to do with Windows/Linux.

It probably has a lot more to do with Internet Explorer/Firefox.

---

### Post by Jagot on 2006-08-12
Attached is the site in Firefox on Windows.  Looks the same as IE.

EDIT: No it doesn't - for other people reading this thread see comments after this one.

---

### Post by GuitarHero on 2006-08-12
I looked at the source.  Why are you using a p tag to center it?  Use <div align="center">blah blah blah</div>

---

### Post by aysiu on 2006-08-12
> **Jagot said:**
> Attached is the site in Firefox on Windows.  Looks the same as IE.
No, Firefox in Windows doesn't look the same as IE. It's not centered--just as the OP noted about Firefox in Linux.

I'm getting descriptions in my Firefox in Linux.

---

### Post by DirtDawg on 2006-08-12
The only thing I can find that could be considered a problem is the positioning of the Flash window, so I assume that's what's bothering you. 

In both Internet Explorer and Opera, the window's position is in the center, but in Firefox, it is not. The problem has nothing to do with Ubuntu.

```

<P align=center><EMBED name=looplet pluginspage=http://www.macromedia.com/go/getflashplayer align=middle 

src=http://static.filmloop.com/looplets/flash/v2/gallery.swf width=700 height=380 type=application/x-shockwave-flash quality="high" 

scale="noscale" flashvars="base=looplets.filmloop.com&amp;weblinkid=Inx2VFL0foiM1GnksbeIX8/Rjs2Xa3D7&amp;incr=1&amp;title=XBox 

Games on Sale!&amp;description=&amp;link=http%3A%2F%2Fwww.filmloop.com%2F&amp;color=8594D9&amp;ntype=ebay" 

bgcolor="#333333"></EMBED></P>

```

I'm no expert at the <EMBED> tag, but there's an "align=middle" attribute in there I'm guessing doesn't sit well with Firefox. One would think the <P align="center"> tag would force the window to center, but apparently not?

Hmm.

---

### Post by Jagot on 2006-08-12
> **aysiu said:**
> No, Firefox in Windows doesn't look the same as IE. It's not centered--just as the OP noted about Firefox in Linux.

Aha - didn't notice that - haven't been running Firefox maximised.

---

### Post by DirtDawg on 2006-08-12
Nevermind :-?

---

### Post by fjm03 on 2006-08-12
Finally got through to your site.

FireFox does not present as apparently intended.

Opera does.

It's FireFox, not Linux or Ubuntu.

No surprise. Opera is the more standards compliant of the 3 browsers.

---

### Post by DirtDawg on 2006-08-12
Yikes this thread's cruisin'!

---

### Post by aysiu on 2006-08-12
I'm just expressing my opinion (you don't have to agree with it), but I don't think this matters.

The majority of users out there use Internet Explorer (and adding Opera to the mix doesn't hurt), and will thus see your site as intended.

The minority that use Firefox will probably not care that the Flash window isn't centered (I didn't even notice until you pointed it out). How would they know you intended it to be centered?

---

### Post by Thenotsowyzewun on 2006-08-13
Hi, thanks for all your replies!

> **GuitarHero said:**
> I looked at the source.  Why are you using a p tag to center it?  Use <div align="center">blah blah blah</div>

Just tried that, and it worked cheers :).

To Aysui (who might not remember but she's helped me with stuff before when I was first using Linux a few weeks ago (I'm so comfortable with it now, despite having always used Linux for 10 years prior! anyway I'll finish my sentence!!)

(This) is an is an issue for me 'cos this 'lil promotional tool is @ work in all my listings too, and they're background is centered, so here's [before]("http://i109.photobucket.com/albums/n65/DVDExtras/Before.png") 'n' [after]("http://i109.photobucket.com/albums/n65/DVDExtras/Screenshot-1.png") GuitarHero's tip in the listings

Brilliant :D

I'm still wondering why the content doesn't appear for me though, but if it's working for everyone else then that's fine - can't see the woods for the trees me (I've got bigger issues to sort out since I'm just starting up!).

Thanks for your help :)

Duncan

---

### Post by GuitarHero on 2006-08-13
Its always good to validate your html.
[http://validator.w3.org/](http://validator.w3.org/)
If its valid it *should* work for everyone.

---

### Post by Thenotsowyzewun on 2006-08-13
Hehe I'm surprised how non-compliant eBay's code is! I've fixed mine too (had HTML and HEAD tags but didn't realize I wasn't allowed them) and a closing </P> tag left over from before.
Still leaves about 100 errors in Filmloop and eBay's part though lol.

---

