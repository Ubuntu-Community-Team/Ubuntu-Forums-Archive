---
title: "Adobe ebook DRM workarounds"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Monkalou on 2007-02-20
Hello all,

I am trying to download an ebook from my local library and they only support Adobe Reader.  This would work fine on Windows, but Adobe Reader (v. 7.0.9) on Linux doesn't support DRM (Digital Rights Management).  Does anybody know of any work arounds?  Has anybody tried to run the MS version of Reader on Wine?  

Any help is appreciated

---

### Post by tbroderick on 2007-02-20
Don't think you are going to get DRM ebooks to work in Linux.

---

### Post by Cherry Cotton on 2008-04-14
Here, I'll dig up this old thread.

[http://www.adobe.com/products/digitaleditions/faq/](http://www.adobe.com/products/digitaleditions/faq/)

In Adobe's "Digital Editions" FAQ, they say: "Yes, a desktop Linux [version] is under development and a public beta is expected later this year." Whether they mean later in 2008 or if they've simply forgot to update that for four months, I don't know.

(Digital Editions is their new e-book software, I think, separate from Reader...)

Now, using Adobe Reader 7 on Windows, I pried open an Adobe e-book that I bought from Powells. Now I have a PDF for it. Sadly, Adobe Reader 8 for Linux will not recognize it (yarrr), but Evince will simply ask me for a password... a password I am not aware of.

My best guess that this password is something that Adobe Reader 7 generated when it downloaded my e-book, and hell if I know what it is. Figuring out what this password is, and how it's generated, may give us a fighting chance of viewing DRM'd e-books on Linux. Our freedom to read is at stake!

(There are professional PDF-password-cracking programs available, but they're spendy, and I imagine they work best when cracking the silly, weak passwords set by your coworkers and not whatever presumably sophisticated hash goes into producing these e-book passwords. I presume some awesome programmer would have to delve into the guts of what goes on when Adobe Reader, Acrobat, or Digital Editions downloads an e-book and encrypts it... if the encryption even _happens_ client-side. My head hurts.)

(Yaagh, I've got a new idea: maybe Adobe could start respecting us as customers and stop selling us books that limit where and how we can read them. Do you own any paper books that say you can read them at home in your comfy chair, but not on the bus or at the beach? Do you own any that are licensed only for one particular brand of comfy chair? Do you own any that are licensed only for a comfy chair matching a manufacturer-specified living-room decor? No! But, yes, I know I'm preaching to the choir, here...)

---

### Post by Cherry Cotton on 2008-04-14
Okay, I have Adobe Reader 7 working on Ubuntu under Wine... It crashes a lot, but it works. I was able to "validate" the program using a Microsoft .NET Passport account (urgh...).

---

### Post by source.decay on 2008-04-25
I also used Wine to get the Windows version and activate it with some old .NET password.  What a pain.  I love having e-books, but going through all this hassle was almost not worth it.

---

### Post by Cherry Cotton on 2008-04-25
Oh! I was able to strip an e-book of its DRM in order to read it on Ubuntu, using a weird, roundabout method that I never want to do again.

First, I tried something that, in retrospect, ought to have been obvious to me: printing to PDF. (This, of course, only works if your document has the "print" permission. God save us from DRM.) Unfortunately, that resulted in thousands of pages of plaintext being saved, in a fixed-width font, to PDF, the equivalent of gibberish coming out of your printer when you try to print something. I don't know what the deal is with that. (Help?)

However, I do have a Windows partition (Vista) on my machine, which I use sometimes to do things like this and to see how the other half lives (answer: we're lucky to have Ubuntu, yes we are). I saw that Windows does not have a "print to PDF" option, which, like symlinks, must be a bit too futuristic for Microsoft. So, I downloaded CutePDF's free (as in free beer) PDF filter, and attempted to print the PDF using that, but it failed for mysterious reasons using an opaque, Microsoft-style error message (I like to call it the "General Your Fault").

However, I soon learned that Vista does come with its own "print to" filter, which is "print to XPS." XPS is the XML Paper Specification, which--hold your groans for a bit--is Microsoft's new competitor to PDF. (Now groan.) Once I printed the PDF to XPS, though, I needed a program to view it in, as Vista--contrary to what the Windows websote says--did not come with one, at least for me.

I downloaded a viewer from the Windows website. Off the subject, Microsoft's website, and its puffy cloud design and constant assertion that Microsoft loves you and is the solution for everyone and everything, really creeps me out and strikes me as vaguely fascist. I'm glad I use a community-based OS like Ubuntu. Anyway...

I opened the XPS file in the viewer, and saved it as PDF. Problem solved... I get to use a textbook that I legitimately bought on my preferred viewer and operating system, and it only took me hours of potential study time to figure out. Aaaagh.

Again, off the subject: it bugs me that companies like Adobe use these restrictions that prevent the growth of the very market they're trying to create. If I--very computer-literate compared to the average person--am turned off by it, what about somebody who just wants an Agatha Christie novel to read on the bus, the very cornerstone of the impulse market? Nobody wants to figure out confusing, competing DRM schemes, especially when they're anti-consumer by vertically segmenting the market into seperate stores, formats, and viewers, aligned in an attempt to carve up the market into irrelevance. Rant over.

If you don't have a Windows partition, or don't have Vista, I certainly don't blame you on either count (you are what's known as a "sane person"). I guess I'd like to know of a) what people with XP partitions have experienced here, and b) if y'alls can help me and others with our Wine print-to-PDF woes. Thanks much!

---

### Post by gunark on 2008-06-13
Hey Cherry just wanted to say thanks -- printing to XPS and then back to PDF worked fine for me.

I too think that the eBook companies are shooting themselves in the foot with this DRM ********. I just bought a travel guide that I intended to take with me to Europe, only to find that I couldn't open it on my Nokia N800. This experience would probably turn the average user permanently off eBooks... fortunately it's not too hard for someone who knows what they're doing to get around this crap.

---

### Post by svenskmand on 2008-07-22
also using [PDFCreator]("http://sourceforge.net/projects/pdfcreator/") (open-source, it's a virtual printer) should work without the PDF(DRM)->XPS->PDF workaround, but havn't tried it as i don't own any e-books yet.

Just my 2 cents :)

---

