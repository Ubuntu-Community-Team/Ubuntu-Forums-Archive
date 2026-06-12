---
title: "Legal Answers Not Just ?'s"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by ddbann2 on 2006-12-09
I have been reading here and on another Linux board and I am getting confused as to what's legal and what's not. I live in canada. Are there other Canadians here?

I want to install Flash and support for MP3's. Is there a legal way to do this for linux in general and specifically Ubuntu?

I don't want DVD codecs or Microsoft codecs if they are not legal.

Is using Automatix or Easy ubuntu for MP3 and Flash installing legal?

I want to make use of websites that use flash and I want to play mp3's but I want the easiest way ti legally instally what i need for flash and mp3s.

I am not into open source as a political statemnet against anyone else, I just want to legally use Linux with at least flash and mp3

---

### Post by aysiu on 2006-12-09
The general consensus for America (and I'm guessing Canada, too) is that MP3 and Flash are legal to install but *libdvdcss2* and *w32codecs* are not.

---

### Post by max.diems on 2006-12-09
Although most people ignore this

---

### Post by ddbann2 on 2006-12-09
well i don't know what to do. if i have to pay to have a legal solution like linspire or mandriva i guess i will. i don't like to ignore the law just because something costs money

---

### Post by az on 2006-12-09
> **ddbann2 said:**
> I have been reading here and on another Linux board and I am getting confused as to what's legal and what's not. I live in canada. Are there other Canadians here?

I want to install Flash and support for MP3's. Is there a legal way to do this for linux in general and specifically Ubuntu?



I suggest this:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Flash is freeware.  There is no legal problem with running it.  Since it is binary-only software, it is not part of the main Ubuntu repository.  You have to get it from a third-party (macromedia, now Adobe).

The second beta of the flash 9 player is the most current and seems to work fine.

As an end-user, it is completely legal for you to install and use the mp3 codec/format.  There are software patents in play and that gets in the way of Ubuntu actually shipping MP3 support.  Not only is that again contrary to the ptinciples of free software, but the distributer (Canonical) would have to pay a royalty to the mp3 patent holder.

You can legally use most of the windows codecs by using the gstreamer implementation.  The w32codecs (used by mplayer and xine) are not codecs that are licenced to be redistributed.  Since the gstreamer codecs are made from scratch, they are fine.  Again, there may be patents in play which get in the way of them being distributed to you (shipped and turned on by default) unless Canonical payed the royalty, but they are legal to use.

---

### Post by Simon80 on 2006-12-10
> **aysiu said:**
> The general consensus for America (and I'm guessing Canada, too) is that MP3 and Flash are legal to install but *libdvdcss2* and *w32codecs* are not.

w32codecs may have legal issues because of their being redistributed without authorisation, but libdvdcss2 is most definitely legal in Canada.  It's only illegal in the US because of the DMCA, which is a very flawed piece of work.  The DMCA outlaws anything to do with circumvention of copy protection, even if the circumvention was being done for legal purposes such as fair use, backing up a legally purchased DVD, or even **watching your legally purchased DVD**.  Canada has no such legislation in place, and thus libdvdcss2 is legal in Canada.  However, it's also important to realize that the law is not equivalent to what is morally correct.  Just because something is in law does not mean that it is morally right to follow that law and morally wrong to defy it.

---

### Post by beefcurry on 2006-12-10
I think what simon is trying to say is that if you dont think the Law is right, dont follow it ;) . It would say it is like boycotting a law, the state cant possiblely arrest all of the people watching **Legally Purchased DVD's, or backing UP their LEGALLY Purchased DVD's**.

I suppose if you are TOTALLY against going against the LAW in anyway possible then CONVERT all your MP3's into OGG vorbis. OR be a man and RIP all your CD's into FLAC (thats assuming that your MP3's comes from legally obtained CD's. If you downloaded your Mp3's from iTunes it may not be legal *not in the US anyway* to convert them)

---

### Post by Delkster on 2006-12-10
> **ddbann2 said:**
> I want to install Flash and support for MP3's. Is there a legal way to do this for linux in general and specifically Ubuntu?

I'm not Canadian, but...

I don't see why using Flash wouldn't be legal. Legal problems generally arise from either copyright issues (such as in the case of w32codecs) or patents.

The codecs in w32codecs are actually software originally produced by companies who wrote them for Windows, usually as part of their applications, and they probably haven't allowed redistribution, at least not separately from the application, and that's obviously done in w32codecs. That's why there's a problem with the copyrights.

However, for many file formats there's also an open source implementation available that's been written from scratch. Those aren't affected by the copyrights of the corresponding proprietary Windows codecs because they're a completely independent implementation.

However, some algorithms and software technologies have been patented. Decoding certain types of files may require the use of those algorithms, and a separate implementation doesn't help because it's the idea that is protected by the patent, not the implementation of the idea. The aforementioned open source codecs for certain formats can be hit by patents even if there are no issues with copyright.

The most commonly used flash player has been written by Macromedia/Adobe which distributes it free of charge. Thus, it's completely legal with regard to copyright to acquire and use it, and if there are any patent issues, Adobe is responsible for them. They've obtained patent licenses to the technologies they use when required.

However, you may not be allowed to redistribute the flash player. You may definitely download and use it, however.

As for mp3, the patent holders don't really go after non-commercial decoders. I'm not sure about encoders (if you want to rip CDs to mp3, for example).

There's something about the subject on [mp3licensing.com](http://mp3licensing.com/help/index.html#5).

Actually, I guess the decoders from Fluendo (or their binaries anyway, not the source code) are even licensed with regard to patents. You can search for "fluendo" in the Synaptic Package Manager (once you have the 'universe' channel/repository enabled) and install the codecs if you want. I really wouldn't be worried about decoding (i.e. playing) mp3 files in a non-commercial setting, though.

---

