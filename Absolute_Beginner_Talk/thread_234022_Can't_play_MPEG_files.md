---
title: "Can't play MPEG files"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Electroholic on 2006-08-10
Hi! I'm a Windows user that recently wanted to try out a Linux distribution, and decided on Ubuntu. I burnt a LiveCD so I could try it out without formatting my hard drive :razz: (since it's my dad's computer). Anyways, it's great! I love it, but today I decided to get some MPEG files, but now I can't play them!:mad:  I tried Totem Movie Player and it says "You do not have a decoder installed to handle this file. You might need to install the necessary plugins.[-X " How do I play it?:confused:

---

### Post by ndyguy on 2006-08-10
> **Electroholic said:**
> Hi! I'm a Windows user that recently wanted to try out a Linux distribution, and decided on Ubuntu. I burnt a LiveCD so I could try it out without formatting my hard drive :razz: (since it's my dad's computer). Anyways, I decided to get some MPEG files, but now I can't play them!:mad:  I tried Totem Movie Player and it says "You do not have a decoder installed to handle this file. You might need to install the necessary plugins.[-X " How do I play it?:confused:

I'm assuming your using Dapper Drake Ubuntu (it's the newest one).  Try System>Administration>Synaptic Package Manager (insert your password).  Then get the w32codecs package.  Hope this helps.

---

### Post by Electroholic on 2006-08-10
> **ndyguy said:**
> I'm assuming your using Dapper Drake Ubuntu (it's the newest one).  Try System>Administration>Synaptic Package Manager (insert your password).  Then get the w32codecs package.  Hope this helps.I can't find it. Is there anything else?

EDIT: What I meant to say was that I couldn't find the "w32codecs" package. I could find the Synaptic Package Manager though.

---

### Post by ndyguy on 2006-08-10
You can either use the Search button or you can look under the Libraries section.  If the box is not green click on it and click on Mark for Installation.  Then click the Apply button.

More info can be found here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You could also try Automatix, but I wouldn't bother if you're only using the Live CD (it does a lot of stuff and takes a while).

---

### Post by djsroknrol on 2006-08-10
Like ndyguy said, Automatix is the best way to get those codecs and alot more functionality..

---

### Post by Electroholic on 2006-08-10
Well, I forgot to say that I searched in the Manager and only found video codecs for Theora and DV. Anyways, I tried Automatix and I don't think it did anything except make some lines of code in the Terminal and I just tried some help I got from the restricted formats page and that didn't help much (I tried a plug-in for WMV 9, Quicktime 7, MPEG-4, etc., but then I opened Totem and it still couldn't play it...not even a Quicktime Movie!).:-( 

Now I'm thinking 5 things: Did I do something wrong, do I need a different video player, can I not do this on a LiveCD, do I need to convert the videos to Theora (or maybe DV) and play the videos like that and/or is it something else rather than the previous 4 questions? By the way, thanks for the help.:D

---

### Post by rck_hitokiri on 2006-08-10
Try out this links bro.....

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

youll need a lot of readin to do since youve just started using ubuntu. youll make it work ;)

---

### Post by nu2this on 2006-08-11
Dude, 
I hate to tell you this but when I tried teh same thing you're doing on a Live I got he same results, this is because to play MPEG in Dapper you need to have Ubuntu installed.
Sorry, I but that's the limitations of the Live cd.

---

