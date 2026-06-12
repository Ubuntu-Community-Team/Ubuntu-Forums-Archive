---
title: "Webkit"
date: 2008-03-26
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-03-26
So I'm hearing a lot of raving about webkit and figured I'd give it a go. Really, I have no idea where to start as I haven't read much on the subject. Can it be done with firefox3? I'm using gnome and wouldn't mind ephphany too much either.

---

### Post by chris_ak on 2008-03-26
I just googled webkit and I still don't know what the hell it is.  What is it?  Why get it?

---

### Post by bruce89 on 2008-03-26
WebKit is a browser engine, which is what Gecko is to Firefox. It isn't a Web Browser however. Epiphany is one of the browsers that can use WebKit, but Firefox can't (and never will).

As I speak, I am compiling it, see [http://trac.webkit.org/projects/webkit/wiki/BuildingGtk](http://trac.webkit.org/projects/webkit/wiki/BuildingGtk).

---

### Post by PurposeOfReason on 2008-03-26
Firefox is really taking a hit in my book then. Webkit is supposed to be amazing and since FF3B4 is so buggy, it's not looking good.

---

### Post by bruce89 on 2008-03-26
> **PurposeOfReason said:**
> Firefox is really taking a hit in my book then. Webkit is supposed to be amazing and since FF3B4 is so buggy, it's not looking good.

Quite ironic that I can't compile WebKit from SVN just now then.

---

### Post by chris_ak on 2008-03-27
> **PurposeOfReason said:**
> Firefox is really taking a hit in my book then. Webkit is supposed to be amazing and since FF3B4 is so buggy, it's not looking good.

I really don't know what the big fuss is about ff3.  I know it integrates gtk themes and what not, but I find it to be kind of sluggish... particularly when typing in a new url.  I tried opera for a while, and while it seemed to have a lot of potential, it just didn't quite do it for me.  That being said, what are the supposed advantages to the webkit engine?

---

### Post by smartboyathome on 2008-03-27
> **bruce89 said:**
> Quite ironic that I can't compile WebKit from SVN just now then.

I am succeeding so far with the latest nightly build. Try that.

---

### Post by SunnyRabbiera on 2008-03-27
Webkit is alright and it seems to be growing in popularity as of late, but Firefox will always be my mainstay.

---

### Post by blu3ness on 2008-03-27
webkit does not offer many benefits, in fact, although it is standard compliant, not a lot of websites support it. By websites I refer to enterprise websites, education platforms, online banking access, and not the hyped web 2.0 websites.

In terms of performance, it is comparable to gecko 1.9, the nightly-builds are faster, but they won't get implemented into a real application in years.

The linux webkit browser is supposedly epiphany -webkit, the usability is just not up-par with firefox.

Firefox 3 is great, gtk themeing makes the entire OS looks consistent, the url bookmarks REALLY starts to shine when you start adding more bookmarks into the system. It's your personaly delicious. (i.e., I see a good page, ^D, tag it, then i just type the tag in location bar to open it).

I don't see myself going with webkit for a long time, and maybe never. Webkit is great, but the way Safari exploits it just doesn't cut it for me.

---

### Post by chris_ak on 2008-03-27
> **blu3ness said:**
> webkit does not offer many benefits, in fact, although it is standard compliant, not a lot of websites support it. By websites I refer to enterprise websites, education platforms, online banking access, and not the hyped web 2.0 websites.

In terms of performance, it is comparable to gecko 1.9, the nightly-builds are faster, but they won't get implemented into a real application in years.

The linux webkit browser is supposedly epiphany -webkit, the usability is just not up-par with firefox.

Firefox 3 is great, gtk themeing makes the entire OS looks consistent, the url bookmarks REALLY starts to shine when you start adding more bookmarks into the system. It's your personaly delicious. (i.e., I see a good page, ^D, tag it, then i just type the tag in location bar to open it).

I don't see myself going with webkit for a long time, and maybe never. Webkit is great, but the way Safari exploits it just doesn't cut it for me.

well... maybe I need to give ff3 another shot.  I didn't notice much of a speed difference right off the bat.  I'll try it again.

---

### Post by jdhore on 2008-03-27
Basically, as was stated before, Webkit is a browser engine similar to Mozilla's Gecko. As of right now on GNOME, i only know of 2 frontends to it: Midori and Epiphany.

Webkit is damn fast, it's extremely standards compliant (first browser to pass Acid3 test 100%) and it's pretty lightweight all things considering. The downsides are basically that some sites don't support it, and well...It's not firefox so no extensions...Also, all the linux implementations are pretty incomplete so that's a bit of an issue too :( As of right now, i'd say Firefox 3 is the best browser...It's almost as good as Webkit and it's MUCH better in every possible way than Firefox 2.

---

### Post by SunnyRabbiera on 2008-03-27
> **blu3ness said:**
> webkit does not offer many benefits, in fact, although it is standard compliant, not a lot of websites support it. By websites I refer to enterprise websites, education platforms, online banking access, and not the hyped web 2.0 websites.

In terms of performance, it is comparable to gecko 1.9, the nightly-builds are faster, but they won't get implemented into a real application in years.

The linux webkit browser is supposedly epiphany -webkit, the usability is just not up-par with firefox.

Firefox 3 is great, gtk themeing makes the entire OS looks consistent, the url bookmarks REALLY starts to shine when you start adding more bookmarks into the system. It's your personaly delicious. (i.e., I see a good page, ^D, tag it, then i just type the tag in location bar to open it).

I don't see myself going with webkit for a long time, and maybe never. Webkit is great, but the way Safari exploits it just doesn't cut it for me.


actually technically the main webkit browser of linux is konqueror as it uses the KHTML engine, and by now KHTML has merged back with webkit.

---

### Post by fuoco on 2008-03-27
has anyone built a deb from epiphany-webkit? is it available in some PPA?

---

### Post by bruce89 on 2008-03-27
> **jdhore said:**
> The downsides are basically that some sites don't support it, and well...It's not firefox so no extensions...Also, all the linux implementations are pretty incomplete so that's a bit of an issue too :( As of right now, i'd say Firefox 3 is the best browser...It's almost as good as Webkit and it's MUCH better in every possible way than Firefox 2.

WebKit is a browser engine, not the actual browser. It is up to the browser to provide extensions.

> **fuoco said:**
> has anyone built a deb from epiphany-webkit? is it available in some PPA?

I couldn't get it to build as a package, sorry.

---

### Post by Lord Illidan on 2008-03-27
Firefox 3b4 works great over here. I love the bookmarks, and so far it's quite stable, given its beta status.

---

### Post by Erunno on 2008-03-27
> **SunnyRabbiera said:**
> actually technically the main webkit browser of linux is konqueror as it uses the KHTML engine, and by now KHTML has merged back with webkit.

No, KHTML has not merged with WebKit and there are no concrete plans for the time being. The developers occasionaly exchange patches though, especially for the JavaScript engines I hear.

---

### Post by jdhore on 2008-03-30
> **bruce89 said:**
> WebKit is a browser engine, not the actual browser. It is up to the browser to provide extensions.

True, but since it technically doesn't support XUL, it doesn't ever have extension support whereas if Epiphany-gecko added XUL stuff to the browser, it could support firefox extensions

---

### Post by el mariachi on 2008-04-05
the latest svn revs compile fine. enable svg support to get those cool 100 points in acid3

---

### Post by PurposeOfReason on 2008-04-12
Trying out epiphany with webkit. It feels faster but is nowhere ready for daily use. Can't open in a new tab and cookies are broken. It's nice having gtk widgets though.

---

### Post by Maupertus on 2008-04-29
@ Purpose:

Can I ask how you built Epiphany with the webkit engine?

---

### Post by Cifra on 2008-04-29
Konqueror is a great browser and it uses WebKit.

---

### Post by PurposeOfReason on 2008-04-29
> **Maupertus said:**
> @ Purpose:

Can I ask how you built Epiphany with the webkit engine?
There is an AUR package for arch and I just grabbed that. And to the poster above me, that is only in Kubuntu and is not offocial as of yet.

---

### Post by ProbablyX on 2008-05-03
> **Cifra said:**
> Konqueror is a great browser and it uses WebKit.

I like Konqueror too, but it does not use WebKit. It still uses KHTML, which WebKit is a fork of.

However Konqueror supports WebKit and AFAIK it will move to using it. There is a liveCD somwhere of Kubuntu which has a Konq using WebKit but Hardy Heron's Konqueror (for KDE4) still uses KTHML.

---

### Post by PurposeOfReason on 2008-05-14
Just an update that with the latest webkit and epiphany, cookies and tabs are fixed. Screenshot for proof (purple link proves cookies).

I take that back, I can't upload pictures with it. Irony.

---

### Post by smartboyathome on 2008-05-14
You also don't get cookies with it so you can save your login. :(

---

