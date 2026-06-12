---
title: "Automatix - how does it work?"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by Algorab on 2006-02-07
Hello all!
I just installed Breezy and followed up with Automatix. Clicked a number of applications I'd like and the program downloaded them. Question: are they installed? I find some in the application bar (Acrobat reader, dvd ripper), but other have not shown up..such as firefox 1.5 and firestarter. Other I don't know whether they are installed or not (multimedia and DVD codecs, Java)...What is the next step? 

Thank you for your help! I am a hopeless n00b... :(

---

### Post by Kyral on 2006-02-07
Automatrix is broken (No starting flame wars here, its been hashed out before)

Try EasyUbuntu or referencing the Starters Guide in the Help Menu (the little Life Preserver icon)

---

### Post by tntc1978 on 2006-02-07
In your homedrive you can see all the installed programes in the file called: automatix.log, If you want to be sure to see all installed programs in the menues, try installing debianmenu, which is also a part of the automatix. If you install it, it will appear in the top of the "start"menu.

---

### Post by seakiwi on 2006-02-07
[QUOTE=Kyral]Automatrix is broken (No starting flame wars here, its been hashed out before)

Try EasyUbuntu or referencing the Starters Guide in the Help Menu (the little Life Preserver icon)[/QUOTE]

I don't plan on starting a flame war but as a new user of Automatix who has had *no* problems with it whatsoever, I'm curious to know what you mean by "Automatix is broken". I haven't been posting here long so I have not seen where it's been hashed out before - would you mind elaborating or pointing me to a relevant thread?

---

### Post by tntc1978 on 2006-02-07
> 
Quote:
Originally Posted by Kyral
Automatrix is broken (No starting flame wars here, its been hashed out before)

Try EasyUbuntu or referencing the Starters Guide in the Help Menu (the little Life Preserver icon)

I don't plan on starting a flame war but as a new user of Automatix who has had no problems with it whatsoever, I'm curious to know what you mean by "Automatix is broken". I haven't been posting here long so I have not seen where it's been hashed out before - would you mind elaborating or pointing me to a relevant thread?

Me 2, I haven't experienced any problems either, but if there's problems with it, I will take that into my considerations. Is it an actual fact, or is more a matter of opinion?

---

### Post by arnieboy on 2006-02-07
[QUOTE=Algorab]Hello all!
I just installed Breezy and followed up with Automatix. Clicked a number of applications I'd like and the program downloaded them. Question: are they installed? I find some in the application bar (Acrobat reader, dvd ripper), but other have not shown up..such as firefox 1.5 and firestarter. Other I don't know whether they are installed or not (multimedia and DVD codecs, Java)...What is the next step? 

Thank you for your help! I am a hopeless n00b... :([/QUOTE]
FIREFOX 1.5 will not show up individually. if u click on the firefox icon, it will just launch firefox 1.5

as for firestarter, have u checked applications --> system tools

for java, type the following in terminal:

```
java -version
```

as for audio and dvd codecs.. just put your dvds and mp3s to the test.

---

### Post by Lord Illidan on 2006-02-07
[quote=Kyral]Automatrix is broken (No starting flame wars here, its been hashed out before)

Try EasyUbuntu or referencing the Starters Guide in the Help Menu (the little Life Preserver icon)[/quote]

Do not state that something is broken without stating the reason, please.

Firefox 1.5 should be launchable by clicking the normal firefox icon.

Also, to see if multimedia codecs have been installed, try playing multimedia...
Same goes for java.

I used Automatix 2 days ago to configure a school pc. Worked perfectly, and icons showed up where they were supposed too. Not broken.

---

### Post by Kyral on 2006-02-07
Its kinda a fact (this is why I said I didn't want to start the War again), but people have experianced problems with it, and it was enough people to note. And there was a small issue with the licensing (again not going to bring it up, it was resolved  for all intents and purposes a month or so ago). But yah.

Just be careful with it. EasyUbuntu is nearing completion and we won't release until the bugs are cleaned out (EasyUbuntu was forked from Automatrix which in turn was forked from EasyBreezy)

Arnieboy can indulge you if you want. I don't want to remember the flame wars ;P

---

### Post by Algorab on 2006-02-07
Ok,
when I turn on the firefox webb browser (through applications -> internet) I get 1.0.7. And firestarter has not shown up in the system tools menu. Should I try to do it install the apps one more time?

---

### Post by arnieboy on 2006-02-07
[QUOTE=Algorab]Ok,
when I turn on the firefox webb browser I get 1.0.7. And firestarter has not shown up in the system tools menu. Should I try to do it install the apps one more time?[/QUOTE]
yes please redo the options. in the meanwhile make sure you are not behind a proxy which is preventing wget from working. A possible reason why it didnt work could be because of a possible breakage in your internet connection. Please make sure you are connected to the internet w/o breakages whe using automatix.

and run firefox from the applications--> internet menu

---

### Post by kennethb on 2006-02-07
I looked at using Automatix to fix a problem I was having with my DVD drive not playing DVDs in Totem. I got scared when I read the warning of "do not install if you are in the United States". Is this true?

---

### Post by Algorab on 2006-02-07
Oki, thank you for your help (the java worked! :) ). Trying again. Focusing on aMSN, Firestarter, debian menu and Firefox 1.5

---

### Post by arnieboy on 2006-02-07
[QUOTE=kennethb]I looked at using Automatix to fix a problem I was having with my DVD drive not playing DVDs in Totem. I got scared when I read the warning of "do not install if you are in the United States". Is this true?[/QUOTE]
the warning is not up there for fun. u install these codecs at your own risk.

---

### Post by Lord Illidan on 2006-02-07
[quote=kennethb]I looked at using Automatix to fix a problem I was having with my DVD drive not playing DVDs in Totem. I got scared when I read the warning of "do not install if you are in the United States". Is this true?[/quote] 
It all revolves around the patent problem. Libdvdcss2 and some other codecs violate several patents, which means that it is theoretically illegal to even view dvds on your pc. Basically, install them at your own risk.

EDIT :: NEED TO TYPE FASTER!

---

### Post by arnieboy on 2006-02-07
as for easy ubuntu.. lots of people have tried it already and it only ends up breaking boxes even though it has just 10 or so options and the "team" of developers working on it fix one bug every one month.. this pace of work wont get them anywhere.. senselessly bashing automatix's achievement will only dig their burial hole a little deeper... so let it be :)

---

### Post by Kyral on 2006-02-07
IMO if you paid for a DVD player, then you paid for libdvdcss2, and therefore its not illegal ;P

---

### Post by arnieboy on 2006-02-07
Paying for a DVD player has got nothing to do with the proprietary codecs that make it run on a certain operating system on a computer. If they are proprietary and somebody is charging for them and there are no other options, you need to pay for them.

---

### Post by Lord Illidan on 2006-02-07
> **Kyral]IMO if you paid for a DVD player, then you paid for libdvdcss2, and therefore its not illegal  said:**
> 

I am quoting from the Wikipedia :

[QUOTE] libdvdcss is not to be confused with [DeCSS]("http://en.wikipedia.org/wiki/DeCSS"). While DeCSS uses a cracked DVD player key to perform authentication, libdvdcss uses a generated list of possible player keys. If none of them works (for instance, when the DVD drive enforces region coding) it tries to unscramble the DVD using a [brute force]("http://en.wikipedia.org/wiki/Brute_force") algorithm, so the [region code]("http://en.wikipedia.org/wiki/Region_code") of a DVD is ignored. Unlike DeCSS, libdvdcss has never been fought over in a courtroom.


 In many countries it is forbidden to sell or document programs that provide ways around [copy protection]("http://en.wikipedia.org/wiki/Copy_protection") systems. CSS is not a copy protection system, but thwarts attempts to play the DVD without proper software. Despite this fact, many [Linux distributions]("http://en.wikipedia.org/wiki/Linux_distributions") do not contain libdvdcss (for example [SUSE Linux]("http://en.wikipedia.org/wiki/SUSE_Linux"), [Debian]("http://en.wikipedia.org/wiki/Debian") and [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_Linux")) for reasons concerning [patents]("http://en.wikipedia.org/wiki/Patent"). In most of these cases, the library can be easily [downloaded]("http://en.wikipedia.org/wiki/Download") from the [Internet]("http://en.wikipedia.org/wiki/Internet").


Basically, ok, so it might not be illegal, but I wish those stupid patents would get out of the window. Why in hell can't a normal user play a dvd on his computer without having to pay for propietary software??

---

### Post by Kyral on 2006-02-07
[quote=Lord Illidan]I am quoting from the Wikipedia :



Basically, ok, so it might not be illegal, but I wish those stupid patents would get out of the window. Why in hell can't a normal user play a dvd on his computer without having to pay for propietary software??[/quote]

Welcome to why I joined the FSF (Free Software Foundation)

---

### Post by nocturn on 2006-02-08
[QUOTE=kennethb]I looked at using Automatix to fix a problem I was having with my DVD drive not playing DVDs in Totem. I got scared when I read the warning of "do not install if you are in the United States". Is this true?[/QUOTE]

In the USA, circumventing any copy protection device is illegal, even on content that you own.

To play encrypted DVD's in Linux, you need to get DeCSS to decode the movie.

The law that is causing this problem is called the DMCA, you can google it for the exact contents, but it makes many things illegal.

Ironicly, when Sony infected customer's PC's with a rootkit, it turned out that cleaning up the infection was also a violation of the DMCA because the rootkit is part of a copy protection device.

---

### Post by nocturn on 2006-02-08
[QUOTE=Lord Illidan]It all revolves around the patent problem. Libdvdcss2 and some other codecs violate several patents, which means that it is theoretically illegal to even view dvds on your pc. Basically, install them at your own risk.

EDIT :: NEED TO TYPE FASTER![/QUOTE]

DeCSS does not violate any patent, the codecs and mp3 support do depending on your country of origin.

DeCSS just uses a prime number to attack the flawed encryption scheme on DVD's.  It is legal in many countries (like mine), but not in the USA.

---

### Post by nocturn on 2006-02-08
[QUOTE=Kyral]IMO if you paid for a DVD player, then you paid for libdvdcss2, and therefore its not illegal ;P[/QUOTE]

Again, DeCSS is not a patent or copyright problem.    It is illegal because it breaks a copy protection device (an weak encryption scheme in this case).

It is not illegal because it violates patents or copyright.

---

### Post by nocturn on 2006-02-08
[QUOTE=Lord Illidan]I am quoting from the Wikipedia :



Basically, ok, so it might not be illegal, but I wish those stupid patents would get out of the window. Why in hell can't a normal user play a dvd on his computer without having to pay for propietary software??[/QUOTE]


Thank you for posting this!

So, disregard my previous posts, I thought it was based on DeCSS.

Still it is illegal to use in the US, but safe in any country that does not have software patents.

---

### Post by moontide on 2006-02-08
I installed Automatix a week ago and have already had to update it twice.  Last update to 5.3.4 was required to get Avidemux to install. Apart from the need to update, everything has installed perfectly and very quickly using Autmatix.

I can't get over how good a desktop I've got with Breazy Badger.

Must have taken a lot of work, so a sincere thanks to all who made it a reality.

---

### Post by kennethb on 2006-02-08
Well, it worked. After installing Automatix my DVD player now plays DVDs. The audio and video display is a bit fuzzy/buzzy. Any suggestions on teaking the DVD dispaly?

---

