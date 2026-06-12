---
title: "Voice dictation, MP3 recorder, and Ubuntu"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by vavroom on 2007-06-02
Hello all,

I'm hoping some of you might be able to make suggestions as to the best application for my needs here.  I'm on Feisty.

I am looking for voice dictation software of the kind "you talk, it types", similar to Dragon Naturally Speaking which is available on WIndoze.  Also, a feature I am looking for, which is available in Dragon, is the ability to dictate straight from an MP3 recorder, so I can take notes, and transcribe them without having to actually type them.

This is not lazyness on my part, it's arthritis playing nasty tricks on my hands.

Any ideas?

---

### Post by vavroom on 2007-06-02
By voice dictation, I meant "speech recognition".

Hunting on Google gives me loads of info, but it's all 5 years old!!!

---

### Post by Dougie187 on 2007-06-02
not sure if any of these help you out, but have you looked at any of these?
[http://sound.condorow.net/speech.html]("http://sound.condorow.net/speech.html")

---

### Post by vavroom on 2007-06-02
Thanks for the response Dougie, much appreciated.

Unfortunately, yes, I had looked at that page.  Over half are for text-to-speech.  Those that are speech-to-text are old, old projects.  Most of the links are 404Not&*@&&#Found.  The few links that work, projects were never completed, or are for developers to include in their own applications.

Things don't look very good for me :(

---

### Post by freebird54 on 2007-06-02
The sum total of my knowledge here is zero - but whatever became of the speech-to-text functions in OS/2 Warp.  I thnk it wsa Warp 4 that included it by default.  Have you tried enquiring through IBM in case they have open-sourced anything from that project?  If you can't find it on Google, it might take a while to come to fruition, but you might be able to give something a push....

Do 'on-screen' keyboards give you any assist?  That, with a trackball and a bar at the heel of the hand should be relatively easy to navigate (depending, of course, on severity and location of the trouble).  Of course the ultimate help is a private secretary - start one young (10 yrs?) and they will gain valuable keyboarding skills as well as exposure to adult thought patterns and language usage  :)

---

### Post by vavroom on 2007-06-02
IBM efforts seem to be around ViaVoice and Websphere and spending quite some time on their website this afternoon, I was not able to find anything useful.

on-screen keyboards/trackball combos aren't helpful, and are painfully slow to boot.  I can type about 80WPM when my hands aren't giving me trouble, but doing it for any length of time gives me trouble.  

It's just frustrating that I *know* software is available on WIndoze but not Ubuntu.  And I don't want to spend a couple hundred $$$ on software hoping that it'll run under Wine, maybe, if I'm lucky, because if it doesn't, then i'm up the creek with costly software I can't use :(

---

### Post by vavroom on 2007-06-02
> **freebird54 said:**
>  Of course the ultimate help is a private secretary - start one young (10 yrs?) and they will gain valuable keyboarding skills as well as exposure to adult thought patterns and language usage  :)

Ahhh yes, well, I thought about re-training my mobility assistance dog, but her paws aren't particularly well suited to typing.  She's good enough to fetch the phone, get light-switches, open doors and pull my wheelchair, but typing, she refuses ;)

---

### Post by freebird54 on 2007-06-02
Damn - I had hopes of better than that from IBM.  Have you tried contacting CodeWeavers to see if they have ever tried it?  They have the CrossOver Office product as well as wine on the go...

It seems strange that there isn't anything handy - as the original work (so far as I know) was done on Unix boxes... (sigh)  Good Luck - and I'll keep an eye out!

Say hi to your assistant - and maybe a pat on the head? :)

---

### Post by freebird54 on 2007-06-02
does Sphinx4 have any possibilities?  [http://cmusphinx.sourceforge.net/sphinx4/doc/Sphinx4-faq.htm](http://cmusphinx.sourceforge.net/sphinx4/doc/Sphinx4-faq.htm)

I haven't been through it much, but at least it mentions Linux (and it is apparently written for Java)

---

### Post by vavroom on 2007-06-02
> **freebird54 said:**
> Damn - I had hopes of better than that from IBM.  

Reading through many entries on the web, it appears IBM did surprise and disapoint many people with what they've done in that area :(

> **freebird54 said:**
> Have you tried contacting CodeWeavers to see if they have ever tried it?  They have the CrossOver Office product as well as wine on the go...

No, I haven't, I'll do that next, thanks for the suggestion.

> **freebird54 said:**
> It seems strange that there isn't anything handy - as the original work (so far as I know) was done on Unix boxes... 

Yes, very very strange.

Nuance, the makers of Dragon (Winblows) are not even considering making their version Linux friendly, despite Vista's apparently rather good speech-to-text native application.  <shrug>

> **freebird54 said:**
> Say hi to your assistant - and maybe a pat on the head? :)

Done.  She's a slut, she'll take love from anyone, anywhere, anytime ;)

> **freebird54 said:**
> does Sphinx4 have any possibilities?  

I got really excited when I found Sphinx4, but it appears it's all stuff to build applications on, nothing that's ready to use "as is" (unless I missed something big, which is always a possibility).

Thanks for keeping an eye out.

---

### Post by bodhi.zazen on 2007-06-02
LOL

What you want, I got it !

[http://ubuntuforums.org/showpost.php?&p=991194&postcount=2](http://ubuntuforums.org/showpost.php?&p=991194&postcount=2)

BUT the absolute easiest is to install VirtualBox :

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

Then install Windows in VirtualBox. The sound quality will be quite poor, but I got you covered there as well :)

Install the low-latency kernel :

[http://packages.ubuntu.com/feisty/admin/linux-lowlatency](http://packages.ubuntu.com/feisty/admin/linux-lowlatency)

works like a charm. Dragon 7,8, and 9 all work in VirtualBox (with low latency kernel).

You will need to dictate to linux native apps in virtualbox, but there are many many ways to file share with Ubuntu.

---

### Post by vavroom on 2007-06-02
Thanks for that.  I was hoping to not have to purchase Dragon.  It's a big chunk of money, particularly when you're not buying in US$.  Also, your wine method says that it works with Dragon 7, but not 8.  Dragon is now at version 9, and some of the features I'm looking for (speech-to-text from an MP3 recorder for instance) were only working right only in 8 and later.

The VirtualBox is not an option for me, not enough system resources to run the requirements of Ubuntu+VirtualBox+Windows.  I'm a bit RAM poor :(

See, that is one of my problems, I don't want to fork out money for Dragon and find out it wont' work under Wine, as your post showed :(

Any idea?

---

### Post by bodhi.zazen on 2007-06-02
> **vavroom said:**
> Thanks for that.  I was hoping to not have to purchase Dragon.  It's a big chunk of money, particularly when you're not buying in US$.  Also, your wine method says that it works with Dragon 7, but not 8.  Dragon is now at version 9, and some of the features I'm looking for (speech-to-text from an MP3 recorder for instance) were only working right only in 8 and later.

The VirtualBox is not an option for me, not enough system resources to run the requirements of Ubuntu+VirtualBox+Windows.  I'm a bit RAM poor :(

See, that is one of my problems, I don't want to fork out money for Dragon and find out it wont' work under Wine, as your post showed :(

Any idea?

No.

Your best bet is ~ More RAM + VirtualBox + The version of Dragon you have.

Viavoice is like way old (I do not know if you can even get a copy of it any more), everything else if in like pre-pre-alpha at best (meaning be ready to write code for yourself).

You can look here : [http://ubuntuforums.org/showthread.php?&t=143535](http://ubuntuforums.org/showthread.php?&t=143535)

Somewhere here someone posted on a "new" project. Only 1 post that I know of and I can not find it now.

[list=number][*]Needle in a haystack.[*]Shows how active the project is :([/list]

EDIT: 

Ah, there is is :

> The open source community is working hard on speech recognition (SR) software, but still has a lot of work to do. SR is very complex and people with the required knowledge rare.

To speed up this process we, normal users, can contribute 'our voice'. That helps in developing the necessary 'Acoustic Models'. If you want to help out go to [http://www.voxforge.org/](http://www.voxforge.org/) and find out how (quite easy).

Robin

[http://www.voxforge.org/](http://www.voxforge.org/)

---

### Post by freebird54 on 2007-06-02
This link appears to have some ideas - but whether they are up-to-date I don't know.

[http://www.faqs.org/docs/Linux-HOWTO/Speech-Recognition-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Speech-Recognition-HOWTO.html)

investigation continues... :)

Edit:  It really does appear as though the category has languished severely in the last 4-5 years (with the possible future of Sphinx4).  People tried it with great enthusiasm, found it was not really ready yet, and put the program on the shelf.  The resultant sag in the market would appear to have left only one real player (as you know) and they are not interested in porting off the Win platform.  The TAP (passes keystrokes to host system) system holds possibilities - but I suspect that it has cost issues...  Sorry - no luck so far!

---

### Post by vavroom on 2007-06-02
Thanks for this.

> **bodhi.zazen said:**
> 
Your best bet is ~ More RAM + VirtualBox + The version of Dragon you have.

Ah, yes.  Well.  That assume that I can add more RAM to my machine, that I can afford it, and that I can afford a copy of Dragon, which I do not currently own.

It's a LOT of money I don't have.

It is really disapointing that there is no Linux option.  I understand how these things go, and I'm not whining and monaing about it, but it is disapointing.  I'm sold on Ubuntu, I don't want to go back to Winblows, particulalry with Vista around.  But sometimes, the Linux world isn't making it easy :(

---

### Post by bodhi.zazen on 2007-06-02
As much as I hate to admit it, voice recognition was a great idea from Microsoft.

I tend to agree with the overall assessment, Linux does well with general computing and servers, but there are a wide range of programs, such as voice recognition, that are just plain old lacking.

Another example is in personal accounting, things like Turbo Tax or Microsoft Money.

Yes there are some open source offerings but not enough as of yet ...

---

### Post by freebird54 on 2007-06-03
I am not familiar with NZ's health care system - but are there any agencies that assist in making of these things available?  I know that here there are a number of places (ODSP for one) that I would go to if I were in a like situation.  Sometimes some of your tax dollars come back?

Do any of the sphinx4 demos output text files so you can import to WP and fix them up? Even if more for development, that could be useful (as would be the wav file conversion).

All the thoughts I have at the moment....(sleep deprived)

---

### Post by vavroom on 2007-06-03
> **freebird54 said:**
> I am not familiar with NZ's health care system - but are there any agencies that assist in making of these things available?  

The NZ health system is generally pretty good.  But for such things, I fall between the cracks.  Not "buggered up" enough to get help for some things.  Employed and therefore able in theory to pay for low cost stuff like that.  Oh hummm.

> **freebird54 said:**
> Do any of the sphinx4 demos output text files so you can import to WP and fix them up? 

Not sure.  Seems more complicated to install and test the demos than my knowledge allows, but I might have to fiddle, see what I see.

> **freebird54 said:**
> All the thoughts I have at the moment....(sleep deprived)

Thanks, much appreciated.

---

### Post by freebird54 on 2007-06-03
Hmm - maybe we'll have to try a 'project' here and see what we can find out/set up for you... not tonight though! ( it would undoubtedly speech to screech, and text to test!)

L8R

---

### Post by vavroom on 2007-06-03
I'll be grateful for any assistance.  

Speech to screech, I like that :)

The question is, what are you still doing up in the wee hours like that? :)  It's half past 6pm here (Sunday), must be 2:30am or so (Saturday) for you.  Night out in town? :)

---

### Post by freebird54 on 2007-06-03
Nahh - just too bloody hot to get to sleep easily (hasn't been worth installing the A/C yet).  However, not being able to sleep != being awake!  And yes, about 02:30 hrs Sat here....

---

### Post by vavroom on 2007-06-03
Here we have the opposite problem, it's getting cold.  Cold wet and miserable.  Been colder in NZ in Winter when it's about 0C than in Toronto when it was -10 or so.  <shrug>

---

### Post by freebird54 on 2007-06-04
Know what you mean - though we get those 'raw' days too :)  BTW - no  wonder you want your computer more usable for the upcoming season!  The best prevention for cabin fever in winter....

---

### Post by jcconnor on 2007-06-08
Looks like xvoice may be what you (and I) are looking for.

Here's the link:
[URL="http://xvoice.sourceforge.net/"]
http://xvoice.sourceforge.net/[/URL]

---

### Post by jcconnor on 2007-06-08
Never mind - it depends on viavoice which as you have seen is dead.

Sorry!

---

### Post by vavroom on 2007-06-08
Thanks for the heads up.  None of the links to ViaVoice work, and the project at IBM seems dead, however, I've just joined the mailing list, almost dormant, but not quite dead.  I'll see there if anyone can help as well :)

---

