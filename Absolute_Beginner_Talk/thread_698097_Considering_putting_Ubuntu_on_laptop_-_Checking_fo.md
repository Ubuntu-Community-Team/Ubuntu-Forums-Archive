---
title: "Considering putting Ubuntu on laptop - Checking for compatibility (Voip, Palm OS, &#20013;&#25991;)"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by ipsi on 2008-02-15
I've just realized that I don't do much on my laptop that's Windows-specific, and that I might actually be able to install Ubuntu, which would be quite nice.

Anyway, first up, it's a Toshiba A10 Satellite (not Pro). Anyone aware of any compatibility problems with it? From what I've seen, Toshiba laptops seem to be reasonably painless, which is good to hear. :). It runs 1024x768, and the Live CD worked fine. Not sure about sound and stuff though - would it working (or not) from the Live CD be a good indication of whether it'll work once I've installed it on the hard drive? 

Wireless card is a Netgear WG511v2, which will cause me some headaches, sadly. Have done a search though, and it seems fixable. Unless anyone wants to chime in and tell me otherwise?

In terms of software, it's mostly the following:

Firefox
Thunderbird
OpenOffice
Pidgen
VLC
Flashget
LaTeX
Winamp

They all either work or have good equivalents under Ubuntu. Not sure what the name of the TeX distro is, but I'm sure it's not that hard to find.

I also use the following:

Super
EmEditor
VoipBusterPro

And I'm not sure if there's any equivalent for them. Super is a little utility that seems to be able to convert *any* video type to something sensible. e.g. I can't play RMVB files, but I can use that to convert them to something sensible. There's no entry in the WINE AppDB for it, so I'm wondering if there's any equivalent?

EmEditor is just a text editor that has a nice, plain GUI, basic Macros, regular expressions, and (more importantly) a really efficient way of working with text files in various encodings. I mostly use it if I need to convert a file from GB2312 to UTF-8 or UTF-16 or whatever. Is there anything out there that's much like this?

Finally, I also use VoipBusterPro to make cheap international calls. It's not Skype, and I actually found out about from these very forums (I think). I'm just not sure what I need to use on Ubuntu. The other thing is that I've set some contact names and suchlike as Chinese characters, and they're encoded in GB2312 (rather annoyingly), so I'd like some advice as to how to make this work under Ubuntu.

I also do some programming for PalmOS. I see that it's possible to get Code Warrior running under WINE - what success have people had with that? Otherwise, is it possible to use the Palm OS Development suite under Ubuntu? It's not really essential, but it would be nice.

I also saw an entry for synching Palm OS devices in the Live CD menu, so synching my Treo 680 shouldn't be a problem?

Finally, I also need Chinese Input and Display. Will that be installed/enabled by default? I assume it at least comes with fonts and such to display Chinese characters, but how easy is it to set up an IME for it? I'm expecting something at least as good as Microsoft's IME, though maybe not as good as Google's. If it's possible, I assume it'll be Pinyin. Does anyone know if there's a Wubizixing IME for Ubuntu? 86 is ok, but 10803 would be ideal.

EDIT: A couple more things that I remembered I need to check up on: I've currently got an Epson Stylus CX5900 hooked up. Will I still be able to use all the functions on that with Ubuntu?

Also, do Firefox/Thunderbird keep their settings somewhere system-independant? It'd be damn annoying to lose my various cookies, bookmarks, settings and plugins. Will I be able to restore those to their correct locations in Ubuntu and have everything as I'm used to?

Thanks everyone!

- ipsi

---

### Post by djbsteart1 on 2008-02-16
for your hardware you could look at the hardware compatibility list:
[HTML]http://ubuntuforums.org/showthread.php?t=361236[/HTML]
or here for printer:
[HTML]http://doc.gwos.org/doku.php[/HTML]

try kate for a text editor, it is very good. there are also lots of voip programs around. as for the chinese support, post in a separate thread and im sure someone will have done the same thing as you want. for alternates to programs there are many threads with lists of equivalents, or you can look through the repositories. 

as for the other things i wouldnt like to commit to them, but if the livecd agreed with you then it should be ok. also if you have two partitions on your disk you can always move the data off one and install there and that way if it doesnt work well nothing is lost. 
i would add that friendly that ubuntu is, be prepared for a shock as it takes time. but in the end if all works it is worth it.

---

### Post by ipsi on 2008-02-16
Thanks for the advice. I actually found a link to alternative programs, which was quite good.

So far, everything looks good. My printer, while not officially supported, will work which is good. The hardest part will be making my wireless card work. :(

I will post about the Chinese stuff, but that's less essential. All-in-all, it seems like the majority of the work will be backing up all my stuff... *sigh*.

Anyway, thanks for your help. I'll begin backing up over the next couple of days. Hope it all turns out alright. :)

---

### Post by djbsteart1 on 2008-02-17
Thats good to hear. Wireless is annoying, but ndiswrapper can manage most things. As for the language, there are distrobutions with excellent language support if what you are looking for isnt supported in ubuntu. Well good luck with the backups, and see you on this side.

---

### Post by ipsi on 2008-02-17
Woot! I am now posting from my Ubuntu-enabled laptop. The wireless was distressingly easy, actually. I'd been expecting something much harder. It basically consisted of four commands, and now it's working fine. It actually took more time to get it working under Windows as I had to install the proprietary software as well...

Anyway, everything seems to be working. Ekiga works with my VOIP provider (though it isn't able to show my balance or my contacts, which should have been expected I suppose).

I'll add Chinese support once it's done updating. Hopefully that shouldn't be too long.

---

### Post by djbsteart1 on 2008-02-17
thats great to hear. i had a smiler experience with wireless, and was also if it can be said, disappointed. thats good about viop and everything else. the fun really starts when you turn the os into your own with customizations. hope the chinese goes well and that ubuntu treats you well.

---

