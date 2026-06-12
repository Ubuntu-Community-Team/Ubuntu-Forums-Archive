---
title: "[SOLVED] 6.10 or 7.04?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Officer Dibble on 2007-08-30
Ubuntu 6.10 and Ubuntu 7.04... are they very different? The reason I ask is there doesn't appear to be any versions in between the two, so I was wondering which I should have installed as a newbie.

At the moment I have 7.04 and find myself struggling slightly with driver issues, etc. So would it have been easier for me to have gone with the potentially more established version of 6.10 if that's the way it works?

Many thanks.

---

### Post by DEagleson on 2007-08-30
Personally i think that new users should get the latest build of Ubuntu.
Its strange that you got any driver issues, because Ubuntu is made to work after install.

Hope someone here can help you out.

Sincerely,

DEagleson

---

### Post by SunnyRabbiera on 2007-08-30
well 7.04 is the latest version, also known as feisty fawn.
The previous version of ubuntu is edgy eft, 6.10.

there are a number of differences between the two, Fawn offers the newest stuff available from the ubuntu developers while edgy was meant to be an experimental stepping stone for what the 7 series would offer.

now there is a good chance that if drivers dont work under Feisty it probably wont work under edgy or even dapper Ubuntu's current LTS variation.

now what exactly are you having a probelem with under Ubuntu?
perhaps we can offer you help.

> **DEagleson said:**
> Personally i think that new users should get the latest build of Ubuntu.
Its strange that you got any driver issues, because Ubuntu is made to work after install.

Hope someone here can help you out.

Sincerely,

DEagleson

Personally I would take older versions rather then newer versions as stability can be an issue, and yes therre are cases where stuff works in the older version better...
take me for example i got the annoying ata bug that was never fixed before Ubuntu feisty came out, and as a result I switched distros due to my issues

---

### Post by AndyCooll on 2007-08-30
Either choose 6.06 (since this is extremely stable being a LTS, long term support version) or 7.04 as this is the latest version. 7.04, for me at least, works fine.

:cool:

---

### Post by Dark Star on 2007-08-30
Yep 7.04 for new user .. No need to get older 1..

---

### Post by timcredible on 2007-08-30
if you're wondering if there's more support for 6.10 because it's been out longer, no, that's not how it works.  typically, as soon as a new version is out, all work on the on the older versions stops.  so, you might as well install 7.04.  check out [www.ubuntuguide.org](www.ubuntuguide.org) for help on everything/anything.

---

### Post by sdim on 2007-08-30
I agree.It seems logical that 7.04 has got whatever Edgy Eft has,and probably some more amenities.I can only guess,though,as I am using Feisty Fawn,but I think that's the way it goes.7.04 must be an imroved version of 6.06.

---

### Post by Officer Dibble on 2007-08-30
All I want to do is install Wine.

The WineHQ site has instructions for doing this, but as I started I hit another brick wall when before it installs Wine it wants me to install the "Universe"... :confused:

I'm wondering where this ends now. Have I done something wrong in my initial installation? I'm currently duel booting with XP, so there are no backwards steps to make here.

When I can be bothered to work out how to install this "Universe", will I find that our Universe is but a bubble in a bigger Universe? I suppose I need to ask if there is a comprehensive guide (or preferably an automated feature) to installing Wine that tells you everything you need for 7.04, rather than just skipping around different websites trying to knit solutions together when an unexpected problem rears up at me.

Should I expect any problems after eventually installing the "Universe"?

---

### Post by Majorix on 2007-08-30
If you are experiencing driver problems with the newest stable version (that is 7.04) you might want to give the testing version a go. It will be the next LTS version, so they are working hard on it. And so far I don't see much problems with it except for:
-pam-keyring
-external hdds
and I believe they will be fixed soon.

---

### Post by fjf314 on 2007-08-30
"Universe" is simply the name of one of the Ubuntu repositories. In order to install the files needed for Wine, the Universe repository needs to be enabled. You can find information on enabling repos at the following location:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

---

### Post by Tiekyl on 2007-08-30
[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

I *think* this might be the universe your talking about, they probably want you to enable the universe repository. It just lets you get access to more software to download. To start, you can check to see if they are commented out in /etc/apt/sources.list . (Prolly is an easier way, but I'm at school and can't check.)

Edit: or just listen to the person above me.

---

### Post by Officer Dibble on 2007-09-01
This was resolved in another thread dealing with another problem I had. The end result is that my problems were down to a duff image download or disc issue. Anyway, all is well and I'm happy again. :)

Thanks for your help guys.

---

