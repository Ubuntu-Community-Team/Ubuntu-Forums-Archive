---
title: "Photomatix Linux port coming?"
date: 2008-12-17
forum: Art &amp; Design
---

### Post by Neon Lights on 2008-12-17
So, I got interested in HDR Photos and I was poking around on Photomatix's website, since that's what the majority of people (at least on Flickr, haha) use, and while providing no download trial for Linux users, I noticed in the FAQ this:
> **Is there any chance you will release a Linux version of Photomatix?**
We have no plans for releasing a Linux version of the software.
However, it is possible to run the Windows version of Photomatix Pro under Linux through Wine.
To run Photomatix Pro after version 3.0, you will need to install the .NET framework under Wine. The instructions to install Wine and the .NET framework under Fedora and Ubuntu are [detailed here]("http://www.hdrsoft.com/support/linux.html").

-[http://www.hdrsoft.com/support/faq_photomatix.html#linux](http://www.hdrsoft.com/support/faq_photomatix.html#linux)So I clicked the link and saw this: 
> You need the .NET framework loaded in Wine to be able to run Photomatix Pro version 3.

Important: From Microsoft's license conditions it appears that to legally install the .NET framework, you need a license for a copy of Windows that you are not currently using, or at least a copy where you are not going to install the .NET framework. (Bear in mind that the .NET framework comes pre-installed on some Windows versions like Vista.)Hmm, I thought. That's not very nice. So I emailed there support, asking if they had considered porting to Mono and releasing a native Linux version of Photomatix.

After receiving a link to the FAQ as I expected, and also saying they haven't had the time to look into a Mono port yet, I explained that it wasn't exactly legal to use Photomatix then on Linux if you don't also have a Windows license, and also asked if they at least made sure everything worked in WINE.

I then received:> Dear Brian,

Sorry for the late follow-up on this.

I think that if you have an old version of Windows you don't use
anymore, you will still be able to use its license for installing the
.NET Framework on a newer computer on which you would only have
installed Linux.

We did make sure that the steps outlined in the link I sent you would
make Photomatix Pro working under WINE. We tested this on the 2
configurations we listed and several persons verified the procedure.
[B]
We however decided to increase the priority on looking into Mono, so
there is someone of our team who is currently looking into this.
Hopefully, this will result in us releasing a Linux version of
Photomatix Pro soon.[/B]

Sincerely,
FrancoisTo which I responded:> Dear Francois,

Yes, that is true. But as I said before, if you don't have a Windows license at all, it's not legal.

Thank you very very much, I really appreciate it, as does the rest of the Linux community I'm sure. :)
Will anything be added to the announcements list, or is there anyway I can keep updated on how things are going with this?

Thanks so much again,
BrianAlthough I know half the people here hate Mono, it's still a step in the right direction, right? Photomatix is pretty popular. Figured I'd just post it and see if it interested anyone. I'll keep everyone updated with any further emails I get.

---

### Post by directhex on 2008-12-18
[http://mono-project.com/MoMA](http://mono-project.com/MoMA)

Send that their way. It'll analyse their binaries & report on any non-portable sections

---

### Post by Neon Lights on 2008-12-19
I sent another email off, thanks :)

got this back:> Dear Brian,

You are very welcome.

We won't announce the Linux version on our announcements mailing list
because this list doesn't have a Linux category.

We will however be happy to notify you personally by email, once we
have a beta version, in case you wish to help us test it.

Thank you also for the link to MoMA, we were actually already aware of
this tool but it is still nice from you to share this information with
us.

Sincerely,
Francois

---

### Post by tuxx on 2009-09-09
It would be really really AWESOME for a Linux-port.

At the moment I use my old XP licence under VirtualBox, but it's only for my Photomatix licence - I'd really dig if I could go 100% Linux!

---

### Post by Whiffle on 2009-09-09
Pretty cool that they're as responsive as they are.

---

### Post by Neon Lights on 2009-09-09
sadly, this was actually near a year ago, with no new news on it. Send off some emails to them, see if you can move them along a bit people. They'll listen if there's a demand. ;)

---

### Post by Neon Lights on 2009-09-29
Well, I wrote off an email to check up on it, and woohoo! Got a quick response as always:
> Hi Brian,

Thank you for your enquiry.  We do have plans to to develop a Linux version of Photomatix Pro through a port to Mono, and had started work on it around the time of your last message.  However, this has turned out to be more difficult than expected, unfortunately, as Photomatix makes calls directly to Windows APIs, which are not supported by Mono.  Because of this, our work on the Linux version has not progressed much during the last months.  The two of us who are involved in the Mono port are very busy at the moment, and so it's difficult to tell when we may be able to continue the work.  Rest assured that it is definitely on our "to do" list however.

Best regards

Matthew
[COLOR=#888888]Photomatix Support Team
[www.hdrsoft.com]("http://www.hdrsoft.com/")[/COLOR]

Good to know it's still on the todo list at least. =]

---

### Post by Tom Tiger on 2011-02-06
Sorry to revive an old thread but unfortunately we are now again a Year further and still no native Linux version.....  I no longer have any confidence in Photomatix bringing  out a Linux version.

So what would be a good alternative?  I'm using QTpfsgui at the moment.

---

### Post by jcolyn on 2011-02-06
Enable getdeb and download Luminance..

---

### Post by prokoudine on 2011-02-07
> **Tom Tiger said:**
> Sorry to revive an old thread but unfortunately we are now again a Year further and still no native Linux version.....

In early May 2009 I met Francois at Libre Graphics Meeting in Montreal. He was looking for developers, but stood at the conference for just one day. He seemed like a very nice guy to talk to, but when asked, never specified if he was looking for **Linux** based developers :)

> **Tom Tiger said:**
> So what would be a good alternative? I'm using QTpfsgui at the moment. 

There's no such thing as Qtpfsgui anymore. It's called Luminance HDR now :) And it's the only real HDR tool so far. Alternatively you can either use Enfuse (via Hugin, if you want to) or simple HDRish merge in Fotoxx. Last year GEGL, new GIMP's core, got basic HDR merging and tonemapping, but you won't see this is regular GIMP quite a while (tonemapping ops will be available via testing GEGL ops tool though).

---

### Post by Neon Lights on 2011-02-07
Yeah. Who knows. Send em some emails of your own, show there's still interest. I might poke em and see if anything's up.
I noticed there's now a native command line version for Linux now, so there's a start.

Glad to hear Qtpfsgui got a much needed name change haha.

---

### Post by Neon Lights on 2011-02-09
Another response:

> Hi Brian,

You are right, there is now a native Linux build of our command line program, so at least there is a sign of progress :)

Though we are still considering offering a native Linux GUI at some point, developing a GUI takes a lot of time, and that time would come at the expense of improving our current Windows and Mac GUI at a moment when we have a lot of competition.  In fact, I would say that the GUI is our weakest point compared to the current competition, so our priority at the moment is to focus on our Windows and Mac GUIs.

This means a Linux GUI is not our priority for the moment, but we have not forgotten about it.  One option we had been considering was to set up an open-source project to build a GUI out of our native Linux libraries and command line program.  However, we are not sure how this will work with licensing.  Also, it seems to me that it would be difficult to attract open source programmers for a project built on closed and proprietary code.

Kind regards,

Geraldine Joffre
Managing Director, HDRsoft


Personally, if I were a programmer I would want to at least try to work with them a little, it would be a huge asset to Linux photographers. unfortunately programming is not among my skills though -___-

Again, sending off some emails of your own might bump it up on the priority list. Also, if you know someone who'd be willing to work with them, let em know.

---

### Post by xtremethegreat1 on 2011-02-12
Cool!

---

### Post by zephyr707 on 2011-04-19
Has anyone tried the native Linux build of our command line program?  I've been playing around with the trial version of photomatix pro, do you need a full license to get a copy of the linux cli?  I'll send an email expressing an interest in a linux version of the software.  I can't seem to get color profiling working on the trial with the wine version...  seems to work great with a virtualbox machine though (albeit a bit slower).

---

### Post by Francois Joffre on 2011-09-06
Hi all,

As I saw my name in one of these threads, I would just like to mention that we have eventually posted a job description for a Senior Linux GUI Developer, to help us develop a native Linux version of Photomatix. 

The job description is there:

[http://www.hdrsoft.com/jobs/dev_nix_gui.html](http://www.hdrsoft.com/jobs/dev_nix_gui.html)

Please, feel free to spread the words about this to developers you might know.

Thanks,

Francois Joffre
Photomatix Engineering Team

---

