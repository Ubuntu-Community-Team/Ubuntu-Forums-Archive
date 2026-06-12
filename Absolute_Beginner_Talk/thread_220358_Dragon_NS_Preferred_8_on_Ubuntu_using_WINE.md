---
title: "Dragon NS Preferred 8 on Ubuntu using WINE?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by ebeyer on 2006-07-21
I apologize if this is not the exact right forum for this question.

I am contemplating installing Dapper Drake on a PC kit I have yet to buy.  Its main point in life would be to do everything my PC laptop is currently doing.  One of the major, MAJOR functions of that machine is voice transcription using the Dragon Naturally Speaking 8 Preferred software in Win XP.  Obviously, I would like to drop kick Windows if I can.

My readings via Google suggest there has been some limited success getting this application to work under WINE.  There seems to be a wide variety of experiences, however.  Has anybody here tried this application, or one like it under Ubuntu/wine?  More to the point, has anybody gotten it to work?

Many thanks in advance,

EB

](*,)

---

### Post by Kilz on 2006-07-21
> **ebeyer said:**
> I apologize if this is not the exact right forum for this question.

I am contemplating installing Dapper Drake on a PC kit I have yet to buy.  Its main point in life would be to do everything my PC laptop is currently doing.  One of the major, MAJOR functions of that machine is voice transcription using the Dragon Naturally Speaking 8 Preferred software in Win XP.  Obviously, I would like to drop kick Windows if I can.

My readings via Google suggest there has been some limited success getting this application to work under WINE.  There seems to be a wide variety of experiences, however.  Has anybody here tried this application, or one like it under Ubuntu/wine?  More to the point, has anybody gotten it to work?

Many thanks in advance,

EB

](*,)

Both the wine application database and codewavers say that version 8 will not work. But version 7 works great.

---

### Post by ebeyer on 2006-07-21
> **Kilz said:**
> Both the wine application database and codewavers say that version 8 will now work. But version 7 works great.

Will no**w** work or will no**t** work?  I already own version 8, so making that work would be ideal.  

Thanks.

EB

---

### Post by Paerez on 2006-07-21
you can also, as a last resort, run Windows in VMWare inside ubuntu. I do this for Macromedia Flash because I am too lazy to get it to work with wine.

---

### Post by Kilz on 2006-07-21
> **ebeyer said:**
> Will no**w** work or will no**t** work?  I already own version 8, so making that work would be ideal.  

Thanks.

EB

Sorry, typo, will not work.

---

### Post by ebeyer on 2006-07-21
> **Kilz said:**
> Sorry, typo, will not work.

It's too bad your typo was not correct.  Is there some link where I can keep track of progress on this front?

Thanks.

---

### Post by Kilz on 2006-07-21
> **ebeyer said:**
> It's too bad your typo was not correct.  Is there some link where I can keep track of progress on this front?

Thanks.

[The wine application datbase is the best place I know of.]("http://appdb.winehq.org/appview.php?iAppId=2077")

---

### Post by ebeyer on 2006-07-21
> **Kilz said:**
> [The wine application datbase is the best place I know of.]("http://appdb.winehq.org/appview.php?iAppId=2077")

Seems pretty discouraging.  I have been using DNS 8 on Win XP for some time, so I'm reluctant to shell out $79 for an older version of the software.  It may come to that.

Are there any other marginally useful voice recognition solutions for Linux?

---

### Post by KingBahamut on 2006-07-21
While probably not so desireable as that, the only other Speech Recognition software that Im aware of exists is the project XVoice. 
Id have to say that limited success would go with it, but here is the nessecary information about it. 
----
XVoice is a dictation/continuous speech recognizer that can be used with a variety of XWindow applications. It allows user-defined macros. This is a fine program with a definite future. Once setup, it performs with adequate accuracy.

XVoice requires that you download and install IBM's (free) ViaVoice for Linux (See Commercial Section). It also requires the configuration of ViaVoice to work correctly. Additionally, Lesstif/Motif (libXm) is required. It is also important to note that because this program interacts with X windows, you must leave X resources open on your machine, so caution should be used if you use this on a networked or multi-user machine.

This software is primarily for users. An RPM is available.

HomePage: [http://www.compapp.dcu.ie/~tdoris/Xvoice/](http://www.compapp.dcu.ie/~tdoris/Xvoice/) [http://www.zachary.com/creemer/xvoice.html](http://www.zachary.com/creemer/xvoice.html)

Project: [http://xvoice.sourceforge.net](http://xvoice.sourceforge.net)

Community: [http://www.onelist.com/community/xvoice](http://www.onelist.com/community/xvoice)

---

### Post by ebeyer on 2006-07-21
> **KingBahamut said:**
> While probably not so desireable as that, the only other Speech Recognition software that Im aware of exists is the project XVoice. 
Id have to say that limited success would go with it, but here is the nessecary information about it. 
----
XVoice is a dictation/continuous speech recognizer that can be used with a variety of XWindow applications. It allows user-defined macros. This is a fine program with a definite future. Once setup, it performs with adequate accuracy.

XVoice requires that you download and install IBM's (free) ViaVoice for Linux (See Commercial Section). It also requires the configuration of ViaVoice to work correctly. Additionally, Lesstif/Motif (libXm) is required. It is also important to note that because this program interacts with X windows, you must leave X resources open on your machine, so caution should be used if you use this on a networked or multi-user machine.

This software is primarily for users. An RPM is available.

HomePage: [http://www.compapp.dcu.ie/~tdoris/Xvoice/](http://www.compapp.dcu.ie/~tdoris/Xvoice/) [http://www.zachary.com/creemer/xvoice.html](http://www.zachary.com/creemer/xvoice.html)

Project: [http://xvoice.sourceforge.net](http://xvoice.sourceforge.net)

Community: [http://www.onelist.com/community/xvoice](http://www.onelist.com/community/xvoice)

Thanks for that.

I am just now looking at some references for the Sphinx project.  What I have read seems to suggest that this is for developers but has not yet matured into a usable dictation solution.  Is that your understanding as well?

EB

---

### Post by KingBahamut on 2006-07-21
You would be correct. ViaVoice (ala IBM) is the only real viable voice dictation bit that exists that actually "works" as far as Im aware. But even to that affect I have never actually seen it working either.

---

### Post by ebeyer on 2006-07-21
> **KingBahamut said:**
> You would be correct. ViaVoice (ala IBM) is the only real viable voice dictation bit that exists that actually "works" as far as Im aware. But even to that affect I have never actually seen it working either.

That begs the question -- assuming I go through all of the motions of installing and setting up ViaVoice, would I end up with a usable product that would let me do my job?

---

### Post by bodhi.zazen on 2006-07-21
ebeyer

I use wine and DNS 7 and am afraid this is the only option. I have used it now almost daily for 3 months. If I can help you in any way let me know. I posted a how-to on the Ubuntu site and can e-mail you a copy with screen shots.

Wine info:

[http://appdb.winehq.org/appview.php?iAppId=2077](http://appdb.winehq.org/appview.php?iAppId=2077)

You need to start with wine-0.9.12 to install Dragon. After Dragon is installed BACK UP YOUR FAKE C-DRIVE. I have been unable to install Dragon 7 into Wine-0.9.13 or higher. After you install Dragon you can update wine without problems. You can also install any version of wine, Wine-0.9.12 or higher, into any version of Linux, and then use your above copied fake C-drive (after a fresh install of Dragon) and be up and running right away (with the exception of setting up the sound card/microphone). VERY USEFULL.

IBM via voice is outdated. If you know how to obtain IBM via voice please let me know. viaVoice is talked about, but I have never heard from anyone who actually uses it. I have been trying for almost 2 years to obtain a working copy of IBM via voice on Linux, in nothing else as an alternate to Wine.

If anyone actually has voice recognition up and running, other then DNS 7, Ubuntu or otherwise, could you give the rest of us some guidance please?

---

### Post by ebeyer on 2006-07-21
> **ebeyer said:**
> That begs the question -- assuming I go through all of the motions of installing and setting up ViaVoice, would I end up with a usable product that would let me do my job?

Not to totally change the subject, but there is now DNS 9.  Maybe it makes sense to skip over DNS 8?    Supposedly it is more accurate than DNS 8 and requires no training.

---

### Post by bodhi.zazen on 2006-07-21
If you can afford it $600 +

[http://froogle.google.com/froogle?q=dragon+naturally+speaking+9&hl=en&lr=&sa=X&oi=froogle&ct=title](http://froogle.google.com/froogle?q=dragon+naturally+speaking+9&hl=en&lr=&sa=X&oi=froogle&ct=title)

And does it run on Linux?

---

### Post by ebeyer on 2006-07-21
> **bodhi.zazen said:**
> If you can afford it $600 +

[http://froogle.google.com/froogle?q=dragon+naturally+speaking+9&hl=en&lr=&sa=X&oi=froogle&ct=title](http://froogle.google.com/froogle?q=dragon+naturally+speaking+9&hl=en&lr=&sa=X&oi=froogle&ct=title)

And does it run on Linux?

(1) Those are for the specialist (eg, legal/medical) versions.  The standard and preferred editions are much, much cheaper - $149 upgrade, $199 new.

(2) I'm sure they do not run on Linux.  My point was that whoever is going to put forth the effort to make a newer version of DNS work on Linux, either with wine or codeweavers maybe ought to focus on version 9 and forget about version 8.

Anyway, just got me a copy of DNS 7 from eBay for $11.  So if/when I get my linux box hardware, I'll run with that.

Thanks again.

---

### Post by bodhi.zazen on 2006-07-21
Not so, follow my link.

DNS 9 Medical = $ 1024

[http://froogle.google.com/froogle?q=dragon+naturally+speaking+9&hl=en&lr=&sa=X&oi=froogle&ct=title](http://froogle.google.com/froogle?q=dragon+naturally+speaking+9&hl=en&lr=&sa=X&oi=froogle&ct=title)

If you know a better price, I'm all ears (my "boss" makes me run Windows at work).

Congratulations on your new DNS 7.

I think you made the right choice, I have been 100 % Linux for 3 months, my wife included.

PLEASE contact me if you need help.

---

### Post by ebeyer on 2006-07-21
> **bodhi.zazen said:**
> Not so, follow my link.

DNS 9 Medical = $ 1024

[http://froogle.google.com/froogle?q=dragon+naturally+speaking+9&hl=en&lr=&sa=X&oi=froogle&ct=title](http://froogle.google.com/froogle?q=dragon+naturally+speaking+9&hl=en&lr=&sa=X&oi=froogle&ct=title)

If you know a better price, I'm all ears (my "boss" makes me run Windows at work).

Congratulations on your new DNS 7.

I think you made the right choice, I have been 100 % Linux for 3 months, my wife included.

PLEASE contact me if you need help.

Right.  DNS 9 medical is outrageously expensive.  Where they get off charging nearly 10 times the price because mostly doctors are going to use it is beyond me.  I have used the standard DNS 8 on XP for about 18 months now and it works just fine - except for when it screws up, which is not all that often.

[http://www.nuance.com/naturallyspeaking/preferred/](http://www.nuance.com/naturallyspeaking/preferred/)

---

### Post by bodhi.zazen on 2006-07-21
Thank you for the link. My Google is obviously broken. The upgrade is in my price range.

---

### Post by bodhi.zazen on 2006-07-21
Again, if you need help with seting up you Linux Box, I am more then happy to help.

---

### Post by bodhi.zazen on 2006-07-25
I was able to do more research into viavoice (I have a contact at IBM). I am no expert on viavoice mind you.

Via voice is a commercial product marketed at the Microsoft crowd. You can download and compile a linux version, but neither myself or my IBM contact know how.

This is the New Via Voice. The new Via Voice does 

TEXT -> to -> SPEECH. ie your computer talks.

I did not see any Speech -> to -> text (voice transcription) in the current via voice.

There was a previous version of Via Voice that does voice transcription, but as I have said I do not know where to get a copy and have had no contact with anyone running Via voice on Linux.

---

