---
title: "ugly fonts"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by bluppfisk on 2006-07-11
Look at the screenshot of G-mail. I already told Firefox to use as many BitStream fonts as possibly and I also set up Gnome to use these fonts. As suggested on most pages, I switched hinting off, and anti-aliasing on, which gives me a relatively clean looking environment. Yet in Firefox, things get absolutely ugly. The menus get all spidery again and the input fields are even worse.

I'm on Dapper Drake amd 64. Any ideas what I can do? I personally like the Mac fonts, but apparently it's impossible to just use their font on linux? Because that would be awesome.

---

### Post by someusernoob on 2006-07-11
Did you install msttcorefonts? (Im only asking, not suggesting you should)

---

### Post by bluppfisk on 2006-07-11
yes I did :)

---

### Post by someusernoob on 2006-07-11
I guess thats the problemmaker then. 

I know a lot of people like the package, but i only got problems with it, or better said, i do not like it at all. When you enter a site it searches for fonts (depends on the site what font they want to use). When you got msttcorefonts installed, it uses that fonts instead of the "normal" fonts (some sitemakers only think about MS and the fonts unfortunatly :().

With both ways, with or without msttcorefonts, there are "problems". I dont like viewing sites with the msttcorefonts, they do not fit well into the rest of the desktops font theme, and besides that, i think they are ugly anyway. But without msttcorefonts some lay-outs messes up (because the site isnt build for using the standard Linux fonts, for example [www.tweakers.net](www.tweakers.net) and [www.fok.nl)](www.fok.nl)). Most sites work fine tho.

Another problem is that _some_ sites that uses flash, are searching for certain fonts. When you dont install gsfonts-x11 (this one uses a really ugly non aliased gtk1.x font) or msttcorefonts you'll find out that there are no fonts showing. Its even worse when you use XGL/Compiz, msttcorefonts wont work for flash then, so you need gsfonts-x11 (which will also affect apllications which use gtk1.X like xmms), or make the choice not installing any font stuff and just avoid those sites using flash with fonts you do not have.

I hope its clear, its kinda hard for me to explain.

Since the first time i used Linux, i got "problems" with fonts. Actually i do not care anymore now. It's not my problem, its theirs, they build a ugly site, so i do not visit it anymore.

I'll try to setup a little list to make it clear (i've only used Firefox tho, but i guess its the same for every browser):

> Firefox with standard fonts: Some sites looks weird, because the fonts do not fit in very well. I think those fonts are beautiful.
> Firefox with msttcorefonts: Sites look better now, because sites can use MS fonts, so they show up how its supposed to be under Windows. I think those fonts are ugly.
> Firefox with flash and msttcorefonts: Some flash sites using "Windows" fonts do not show any font without msttcorefonts. With msttcorefonts its working fine.
> Firefox with flash, msttcorefonts and XGL(compiz): msttcorefonts wont work for flash now.
> Firefox with flash,gsfonts-x11* and XGL(compiz). Fonts show up now in flash, but they are very ugly and hardly readable. This does also affect gtk1.x using apps like xmms, gorilla password. This is just so ugly you really do not want this on your machine.
> Firefox with (flash), msttcorefonts, gsfonts-x11 and XGL(compiz); Dont install this combination. It will mess up a lot of fonts in Firefox. all msttcorefonts will look like non aliased gtk1.X fonts.

*this package is recommended for the flashplayer-mozilla plugin, and a dependency for the flahsplugin-nonfree.

As you can see fonts is a big issue. There are some "font-tuning" howto's on this site. You'll find them with the search. There are also fixes for the uglyness of gsfonts-x11, ive searched the net for many hours, tried a lot, but its not worth it.

For your problem i'd say drop msttcorefonts and reset your font settings. but its your choice. And about the flash issue, i've actually seen only 2 sites using this way of showing fonts: [www.planet.nl](www.planet.nl) and [www.korn.com](www.korn.com). there are problably more, i dont care.

Note: Im Dutch, so i visit a lot of Dutch sites, thats why i gave those as an example. But it's only for checking the difference in lay-out with and without msttcorefonts.

---

