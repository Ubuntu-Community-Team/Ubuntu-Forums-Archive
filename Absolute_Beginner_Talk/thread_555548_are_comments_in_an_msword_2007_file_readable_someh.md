---
title: "are comments in an msword 2007 file readable somehow?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-09-20
A manuscript of mine has come back from the publishers with a very large number of comments and revisions I need to address: but they've done it in word 2007 format, using the comments option. I have to read and respond.: they tell me 'this is the standard format in the real world, so get real and use word'.

Surely there must be some way of reading these comments somehow, without buying a copy of word? I've tried the ms word viewer under wine, and it dosn't show the comments; open office has no luck either, at least for me.  A similar question on the open office forum got no replies whatsoever at all, either- so I'm turning in desperation to you folks.

Does anyone have any helpful suggestions? Righteous anger such as I feel will get me nowhere fast. Truly grateful for any help whatsoever.

---

### Post by pmoseley on 2007-09-22
While OpenOffice will read and write word format documents, it has trouble with additional/special features such as 'notes' or comments.

In addition Word 2007 by default uses a new compressed version of the old 2003 doc format. The new format is *.docx while the old one is *.doc. An add-on can be installed for word 2000-2003 for the new *.docx format.

To be frank I think you'll either have to fold and buy word OR contact the publishers and ask them to try saving it in a PDF format which may retain the comments. Word 2007 can have a plug-in installed from microsoft to support saving documents in PDF format.

If you can't afford the full office suite then try buying an older copy such as office XP off ebay, buy an OEM license if you built your PC or pay a visit to www - phazeddl - com

---

### Post by ginestre on 2007-09-24
Thanks for that; but it's sadly not as simple as just buying word. I'd have to buy and install windows too.....

---

### Post by Paulmd on 2007-09-24
> **ginestre said:**
> Thanks for that; but it's sadly not as simple as just buying word. I'd have to buy and install windows too.....

What happens if you open the documents in a plain vanilla text editor(or a hex editor, if necessary) ? When you open up an older Word document, you get a bunch of gibberish, but the text IS readable. 

If the comments are stored as plaintext, you should be able to find them.

---

### Post by AirRaven on 2007-09-24
Quick point- in order to read .docx files in Plaintext, you'll need to decompress them first.

Just rename the .docx file to .zip- you should be able to open it and browse its contents fine with File Roller or something similar.

---

### Post by EmmyCee on 2007-09-27
As a writer, I have the same problem. It's one reason I have a dual boot of XP on one hard drive, and Linux on my primary drive. I can write in Open Office if I want to, but when I get revisions back, I can boot over and do them on the other drive.

That said, what about Crossover Office? Will that work? I haven't tried it at all, but maybe it will let you see the comments.

---

### Post by ginestre on 2007-09-27
> **EmmyCee said:**
> 
That said, what about Crossover Office? Will that work? I haven't tried it at all, but maybe it will let you see the comments.

Thank you for that suggestion, which I hadn't thought of: looking at their site this may be the way to go- I'll see if it works tomorrow!

---

### Post by Seisen on 2007-09-27
There is an odf-converter that will allow you to read and write Office 2007 files in openoffice. Its available at [http://www.getdeb.net]("http://www.getdeb.net")

---

### Post by ginestre on 2007-09-27
> **Seisen said:**
> There is an odf-converter that will allow you to read and write Office 2007 files in openoffice. Its available at [http://www.getdeb.net]("http://www.getdeb.net")

Thanks- but I read from the developer's web page,
> 
The odfconverter-1.0.0-2.oxt file works only with Windows, and the odf-converter-1.0.0-5.i586.rpm file works only on SUSE® Linux Enterprise, SUSE Linux, and openSUSE. On both platforms, the OpenXML Translator works only with the latest Novell® edition of OpenOffice.org. 

:(

---

### Post by nine01a on 2007-09-27
Well you probably saw that article that uses RPMs but you can use the alien utility to decompress them. 

It's a matter of copying one file. I did it in Kubuntu 7.10 Tribe 5. No prob. Hth.

---

### Post by EmmyCee on 2007-09-28
Will you let me know how Crossover Office works, if you try it? The only thing tethering me to Windows is really this comments/markup issue with Word. I have to be able to see what my editor has to say! :)

---

### Post by jspangler on 2007-09-28
I don´t know if this helps, but I review and make changes to papers in open office, and people in word can read them just fine. Try showing the changes your editor gives you by going to Edit > Changes > Show

---

### Post by Seisen on 2007-09-28
That is why I said to download it from getdeb,net since it was already packaged in a .deb file.

---

### Post by EmmyCee on 2007-09-28
> **jspangler said:**
> I don´t know if this helps, but I review and make changes to papers in open office, and people in word can read them just fine. Try showing the changes your editor gives you by going to Edit > Changes > Show

The problem is going the other way around, with Comments made in MSWord not showing up in OpenOffice. I have the "Show Changes" active, and I can see insertions and deletions fine. What I'm not able to see, apparently, are the Comments (or Notes, if you like) made. My editor works in MSWord, and I'm in OpenOffice.

I wonder if it's some kind of proprietary format, or if it just hasn't been considered important enough to get in there.

Thanks for pointing that out, though! I'm glad for any pointers I can get. :)

---

### Post by bruce89 on 2007-09-28
Gutsy's OO.o can import those bloody silly "Open" XML formats.

> **ginestre said:**
> 'this is the standard format in the real world, so get real and use word'.

You wonder how MS has such a stranglehold on the industry. 

You ought to tell them that [ODF]("http://www.iso.org/iso/iso_catalogue/catalogue_tc/catalogue_detail.htm?csnumber=43485") is the ISO standard (ISO/IEC 26300:2006), which OOXML will never be.

---

### Post by mlentink on 2007-09-28
> **ginestre said:**
>  they tell me 'this is the standard format in the real world, so get real and use word'.

It's also time for us to take a stand. Because it's simply not true that 'Word' is the real world. All those editors that tell you that, have to cope with advertising creatives they need to sell your book, who will refuse to deliver their work in anything other than Mac-stuff. Get real dudes, the publishing business is a Mac environment. Editors who send back your contributions in Mickeysoft Word format, well..., should have a look around.
Hey, I know, it's difficult, but try to just think about that middle finger. Make it known that if they value your text, they should at least pay you the courtesy of sending their critiques in a standard, or even non-proprietary format. Say No.

---

### Post by antisocialist on 2007-09-28
> **mlentink said:**
> It's also time for us to take a stand. Because it's simply not true that 'Word' is the real world. All those editors that tell you that, have to cope with advertising creatives they need to sell your book, who will refuse to deliver their work in anything other than Mac-stuff. Get real dudes, the publishing business is a Mac environment. Editors who send back your contributions in Mickeysoft Word format, well..., should have a look around.
Hey, I know, it's difficult, but try to just think about that middle finger. Make it known that if they value your text, they should at least pay you the courtesy of sending their critiques in a standard, or even non-proprietary format. Say No.

thats not what gets the notes viewed. that IS what gets your chance lost (normally) as the publisher doesnt want you bs.

---

### Post by bruce89 on 2007-09-28
> **antisocialist said:**
> thats not what gets the notes viewed. that IS what gets your chance lost (normally) as the publisher doesnt want you bs.

Time to find a publisher that accepts LaTeX then.

---

### Post by EmmyCee on 2007-09-28
> **bruce89 said:**
> Time to find a publisher that accepts LaTeX then.

Let me know when you get into publishing! I'll submit a manuscript! :lolflag:

Seriously, though, it would be nice if more publishers did this, but I don't think you're going to find many writers taking a stand on it. Most of us are broke as it is, as we try to make a living doing what we love, and I just can't afford to miss the chance at being the next Stephen King or Jackie Collins because I refuse to work with a program that's an industry standard. It's much easier for me to maintain a dual boot system so I can edit in Word, or find a way to make MSWord work on Linux.

Or hope that some kind programmer makes it so we can view comments. :) Volunteers?

---

### Post by bruce89 on 2007-09-28
> **EmmyCee said:**
> [...]I refuse to work with a program that's an industry standard. It's much easier for me to maintain a dual boot system so I can edit in Word, or find a way to make MSWord work on Linux.

It isn't an industry standard, ISO / IEC 63000 is a real standard.

OO.o's commenting is useless I admit, I wish AbiWord had good commenting.

See [http://qa.openoffice.org/issues/show_bug.cgi?id=23465](http://qa.openoffice.org/issues/show_bug.cgi?id=23465), it's targetted for 2.4.

---

### Post by EmmyCee on 2007-09-28
Thanks, Bruce! I really appreciate the pointer on that. I'd really love to ditch Windows entirely. I'm trying to figure out why I didn't try Linux before...

I'm definitely going to give my publishers heads-up on the issue, at least. I don't expect them to do anything about it, but at least I can say I tried. And I'll be amazingly happy once OOooooo gets this in. It'll make my life a whole lot easier.

Thanks again for your information and efforts!

---

