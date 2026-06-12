---
title: "Why FIREFOX won't check for updates in Gutsy?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Shlomir on 2007-10-20
Gutsy has Firefox 2.0.0.6, but I need to update to 2.0.0.8...HOWEVER the update options are all greyed out...How do I overcome this. I tried to run firefox in sudo, but it made jack of a difference!

---

### Post by mewt on 2007-10-20
Firefox doesnt update through the normal update system provided by itself..however it is upgraded through normal ubuntu updates. So when an update is available you will get notified of it along with other updates

---

### Post by mikewhatever on 2007-10-20
Wait for a few days and it should get updated trough the system updates. This is the way it's done in all Ubuntu versions. Hope you don't mind me asking, but, what's in 2.xxx.8 that is not in 2.xxx.6?

---

### Post by Soarer on 2007-10-20
Why do you *need* to update?

If you installed Firefox with Ubuntu, it won't update until the version in the repositories is updated. This may take a few days, even a few weeks if it's not critical. 

If you want to install the latest version then [this]("http://ubuntuzilla.wiki.sourceforge.net/#Script_Features") will help.

---

### Post by Shlomir on 2007-10-20
OK, no worries..I think there are some vulnerabilities in 2.0.0.6 and hence the need to update pronto...well NOt so pronto as all the repos are chocka-block clogged!!!!

---

### Post by nanotube on 2007-10-20
> **mikewhatever said:**
> Wait for a few days and it should get updated trough the system updates. This is the way it's done in all Ubuntu versions. Hope you don't mind me asking, but, what's in 2.xxx.8 that is not in 2.xxx.6?

some security updates:
[http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox2.0.0.8](http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox2.0.0.8)

---

### Post by Dr Small on 2007-10-20
> **Shlomir said:**
> OK, no worries..I think there are some vulnerabilities in 2.0.0.6 and hence the need to update pronto...well NOt so pronto as all the repos are chocka-block clogged!!!!
Any browser has vulnerabilities so you just need to always play it safe.

---

### Post by nanotube on 2007-10-21
> **Dr Small said:**
> Any browser has vulnerabilities so you just need to always play it safe.

yes, for example, by using noscript! :) [http://noscript.net/](http://noscript.net/), since a lot of vulnerabilities tend to be script-related.

---

### Post by FredB on 2007-10-21
> **Shlomir said:**
> OK, no worries..I think there are some vulnerabilities in 2.0.0.6 and hence the need to update pronto...well NOt so pronto as all the repos are chocka-block clogged!!!!

Firefox 2.0.0.8 packages are currently tested. Just wait a day or two before they will be uploaded.

---

### Post by jdong on 2007-10-21
Ubuntu uses a significantly customized variant of Firefox that integrates better with our applications. Installing an upgraded Firefox from an official, plain Mozilla build will likely break every HTML rendering application in the default system.

Ubuntu does have a full-time developer who does Mozilla stuff, and we get timely updates. Please be patient, as we'd like to be able to fully test the updates for regressions before releasing them out to the public.

Hastily rushed security updates can do more harm than good.

---

### Post by FredB on 2007-10-21
> **jdong said:**
> Ubuntu uses a significantly customized variant of Firefox that integrates better with our applications. Installing an upgraded Firefox from an official, plain Mozilla build will likely break every HTML rendering application in the default system.

Ubuntu does have a full-time developer who does Mozilla stuff, and we get timely updates. Please be patient, as we'd like to be able to fully test the updates for regressions before releasing them out to the public.

Hastily rushed security updates can do more harm than good.

I saw build options are different. But as there is only security updates, not a brand new version (like 3.0 will be), I think 2.0.0.8 will be out before next wednesday ;)

---

### Post by jdong on 2007-10-21
> **FredB said:**
> I saw build options are different. But as there is only security updates, not a brand new version (like 3.0 will be), I think 2.0.0.8 will be out before next wednesday ;)

Not just build options, the source code differs by around 10,000 lines between Ubuntu 2.0.0.6 and official 2.0.0.6. Updates are disabled for a reason.

---

### Post by nanotube on 2007-10-21
> **jdong said:**
> Not just build options, the source code differs by around 10,000 lines between Ubuntu 2.0.0.6 and official 2.0.0.6. Updates are disabled for a reason.

wow, that's quite a bit. is there any detailed documentation on specifically what changes to firefox have been made between the mozilla build and the ubuntu build?

---

### Post by FredB on 2007-10-21
> **jdong said:**
> Not just build options, the source code differs by around 10,000 lines between Ubuntu 2.0.0.6 and official 2.0.0.6. Updates are disabled for a reason.

Which parts are such modified ?!

Just wanting to know, of course ;)

---

### Post by jdong on 2007-10-21
You can grab the source package and there will be a debian/patches dir with the patches that we apply. Most of it is for internationalization or for ripping out Mozilla-bundled libraries with Ubuntu system ones, and so on.

---

### Post by FredB on 2007-10-21
> **jdong said:**
> You can grab the source package and there will be a debian/patches dir with the patches that we apply. Most of it is for internationalization or for ripping out Mozilla-bundled libraries with Ubuntu system ones, and so on.

Ok. So libpng and so ? Well, I think it will be a little harder with Gran Paradiso, because of use of younger libs than the ubuntu ones. I think about cairo (a 1.5 version) for example, instead of the 1.4.10 of Gutsy.

Anyway thanks for the answer !

---

### Post by Niniel on 2007-10-21
Haha, timely updates, that's good. There's not even a 2.0.7 ready so what makes you think 2.0.8 will be made available?

Some of this customization is really pointless and stupid though. Eg. why move the Preferences from Tools to Edit? Because that's how it used to be in Netscape and in the old Mozillas? There's absolutely no reason to not keep the Ubuntu version of FF as close as possible to the original. It is, after all, still labeled FF, and not Ubuntu Browser.

---

### Post by aysiu on 2007-10-21
> **Niniel said:**
> Haha, timely updates, that's good. There's not even a 2.0.7 ready so what makes you think 2.0.8 will be made available? Because the patches for 2.0.0.7 applied to only Windows.

I've been using Firefox on Ubuntu for two and a half years and the updates have taken anywhere between one day and two weeks. Never longer.

---

### Post by FredB on 2007-10-21
> **aysiu said:**
> Because the patches for 2.0.0.7 applied to only Windows.

I've been using Firefox on Ubuntu for two and a half weeks and the updates have taken anywhere between one day and two weeks. Never longer.

half years, I suppose.

Anyway, fx 2.0.0.7 was a windows only bug. I bet on wednesday for fx 2.0.0.8 ;)

---

### Post by FredB on 2007-10-21
> **Niniel said:**
> Haha, timely updates, that's good. There's not even a 2.0.7 ready so what makes you think 2.0.8 will be made available?

Some of this customization is really pointless and stupid though. Eg. why move the Preferences from Tools to Edit? Because that's how it used to be in Netscape and in the old Mozillas? There's absolutely no reason to not keep the Ubuntu version of FF as close as possible to the original. It is, after all, still labeled FF, and not Ubuntu Browser.

What ?

Firefox for linux uses Edit / Preferences since its birth ! For Windows, it is tools / options.

Just look at official builds before saying such nonsense !

Or do you just want to be a troll ?

---

### Post by aysiu on 2007-10-21
> **FredB said:**
> half years, I suppose. Whoops! Thanks for catching that.

---

### Post by Niniel on 2007-10-21
> **FredB said:**
> What ?

Firefox for linux uses Edit / Preferences since its birth ! For Windows, it is tools / options.

Just look at official builds before saying such nonsense !

Or do you just want to be a troll ?

Yeah, that's it, I want to be a troll. You found me out. You are great.

If what you say is true, that's still stupid though. Why do it differently? I don't see any compelling reason. It used to be Edit/Prefs in Windows as well, at least in Mozilla, so they could have just left it that way, it's not like people weren't used to it.

Well, I guess it doesn't really matter. I'm just surprised that there is this seemingly arbitrary difference.

---

### Post by jdong on 2007-10-21
It's probalby because Edit->Preferences complies with the GNOME HIG while Tools->Options doesn't.

---

### Post by FredB on 2007-10-21
> **Niniel said:**
> Yeah, that's it, I want to be a troll. You found me out. You are great.

Oh ?

> If what you say is true, that's still stupid though. Why do it differently? I don't see any compelling reason. It used to be Edit/Prefs in Windows as well, at least in Mozilla, so they could have just left it that way, it's not like people weren't used to it.

System integration to be more user-friendly.

Windows (crappy copy of MacOS) use tools / options.

MacOS-X is using Apple Menu / preferences.

Gnome Interface wants edit / preferences.

> Well, I guess it doesn't really matter. I'm just surprised that there is this seemingly arbitrary difference.

Sigh...

---

### Post by FredB on 2007-10-21
> **aysiu said:**
> Whoops! Thanks for catching that.

You're welcome. :)

---

### Post by aysiu on 2007-10-22
> **Niniel said:**
> Haha, timely updates, that's good. There's not even a 2.0.7 ready so what makes you think 2.0.8 will be made available?

Some of this customization is really pointless and stupid though. Eg. why move the Preferences from Tools to Edit? Because that's how it used to be in Netscape and in the old Mozillas? There's absolutely no reason to not keep the Ubuntu version of FF as close as possible to the original. It is, after all, still labeled FF, and not Ubuntu Browser.
The update just came today, after one day.

---

### Post by FredB on 2007-10-23
Yes, I noticed it this morning. And by the way, how can a person could be so *lazy* - to be gentle - for not looking at freely available release notes ?!

It is horrible :(

---

### Post by FredB on 2007-10-23
> **Niniel said:**
> Haha, timely updates, that's good. There's not even a 2.0.7 ready so what makes you think 2.0.8 will be made available?

Did you ever read the 2.0.0.7 release notes ? It was a windows only fix.

[http://en-us.www.mozilla.com/en-US/firefox/2.0.0.7/releasenotes/](http://en-us.www.mozilla.com/en-US/firefox/2.0.0.7/releasenotes/)

> Release Date:September 18, 2007Security Update:The following [security issue]("http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox2.0.0.7") was fixed.

[http://www.mozilla.org/security/announce/2007/mfsa2007-28.html](http://www.mozilla.org/security/announce/2007/mfsa2007-28.html)

> On his blog [**Petko D. Petkov** reported]("http://www.gnucitizen.org/blog/0day-quicktime-pwns-firefox") that QuickTime Media-Link files contain a qtnext attribute that could be used on Windows systems to launch the default browser with arbitrary command-line options. When the default browser is Firefox 2.0.0.6 or earlier use of the -chrome option allowed a remote attacker to run script commands with the full privileges of the user. This could be used to install malware, steal local data, or otherwise corrupt the victim's computer.> Some of this customization is really pointless and stupid though. Eg. why move the Preferences from Tools to Edit?I ran Firefox since its birh back in 2002. Using that is just following GUI guidelines. You can find easily any live-cd using firefox and see that edit / preferences is the way to go for preferences under linux distros.

> Because that's how it used to be in Netscape and in the old Mozillas? There's absolutely no reason to not keep the Ubuntu version of FF as close as possible to the original. It is, after all, still labeled FF, and not Ubuntu Browser.Just downloaded a GENUINE firefox from mozilla.org website. And see where is the preferences dialog.

By the way, Firefox 2.0.0.9 wille be released sometimes next week because of some regressions in 2.0.0.8 :

[http://developer.mozilla.org/devnews/index.php/2007/10/22/firefox-2008-update-to-be-updated/](http://developer.mozilla.org/devnews/index.php/2007/10/22/firefox-2008-update-to-be-updated/)

---

### Post by Niniel on 2007-10-23
> **FredB said:**
> Yes, I noticed it this morning. And by the way, how can a person could be so *lazy* - to be gentle - for not looking at freely available release notes ?!

It is horrible :(

I can tell you - some people like to do other things besides reading release notes all day long that don't mean much to them anyway. Call that whatever you want.

---

### Post by jdong on 2007-10-23
> **Niniel said:**
> I can tell you - some people like to do other things besides reading release notes all day long that don't mean much to them anyway. Call that whatever you want.

That's totally fine and understandable, but those people should *ask* about updates instead of assuming that they are direly necessary and that Ubuntu is being negligent, without knowing the circumstances of the release :)

---

### Post by Niniel on 2007-10-23
> **FredB said:**
> Did you ever read the 2.0.0.7 release notes ? It was a windows only fix.
Just downloaded a GENUINE firefox from mozilla.org website. And see where is the preferences dialog.


Now this was all very interesting, and I thank you for taking the time to educate me on this, but seriously I do download "genuine" FFs from the Mozilla website, and they have the preferences under Tools. Just because it's the Windows version it's suddenly not the real thing? Lol. 

But I think we've talked about this enough. I didn't know that there were different versions, and why, and now I do. I learned something, you were able to show me how ignorant I am, so now we can all be happy and move on to other things.

---

### Post by Niniel on 2007-10-23
> **jdong said:**
> That's totally fine and understandable, but those people should *ask* about updates instead of assuming that they are direly necessary and that Ubuntu is being negligent, without knowing the circumstances of the release :)

You are absolutely correct. It just never occurred to me that the Windows and Linux versions might be updated differently. Now I know better.

---

### Post by jdong on 2007-10-23
> **Niniel said:**
> You are absolutely correct. It just never occurred to me that the Windows and Linux versions might be updated differently. Now I know better.

No problem :) rest assured that Ubuntu takes security very seriously and has a team of people who are subscribed to all the major channels of security news, and are very much aware of what's going on in that department. Be patient waiting for updates, as history has shown time and time again that a rushed security update can be worse than no update at all.

---

### Post by aysiu on 2007-10-23
> **Niniel said:**
> Now this was all very interesting, and I thank you for taking the time to educate me on this, but seriously I do download "genuine" FFs from the Mozilla website, and they have the preferences under Tools. Just because it's the Windows version it's suddenly not the real thing? Lol. Nobody said that the Windows version isn't the real thing.

We're talking about the difference between Ubuntu's Firefox package *for Linux* and Mozilla's Firefox package *for Linux*. The Ubuntu Firefox package (the "fake" one) has Preferences under Edit. The Mozilla firefox package (the "genuine" or "real" one directly from the Mozilla website) also has Preferences under Edit. There's no inconsistency in the interface in that regard.

Mozilla packages Firefox to integrate with the system people are using it on:
[list][*]Windows programs typically have preferences in Tools > Options, so that's where Mozillla puts it for Firefox for Windows [*]Mac OS X typically has preferences in the name of the program > Preferences, so that's where Mozilla puts it for Firefox for Mac [*]Gnome typically has preferences in Edit > Preferences, so that's where Mozilla *and* the Ubuntu developers put it for Firefox for Linux/Ubuntu[/list]

---

### Post by FredB on 2007-10-24
> **Niniel said:**
> Now this was all very interesting, and I thank you for taking the time to educate me on this, but seriously I do download "genuine" FFs from the Mozilla website, and they have the preferences under Tools. Just because it's the Windows version it's suddenly not the real thing? Lol. 

As a long time firefox user on all majors platform (Linux, Mac, Windows), every single version is specific for their preferences settings location.

> But I think we've talked about this enough. I didn't know that there were different versions, and why, and now I do. I learned something, you were able to show me how ignorant I am, so now we can all be happy and move on to other things.

Ignorant ? Really ? Or just a person who wants to get some more points on the forum ?

---

### Post by FredB on 2007-10-24
> **Niniel said:**
> I can tell you - some people like to do other things besides reading release notes all day long that don't mean much to them anyway. Call that whatever you want.

You buy an hardware for cooking or for your computer without reading how it works ? ;)

It is the same for software. Just read notes, just not to make some mistakes.

---

### Post by Soarer on 2007-10-24
> **FredB said:**
> You buy an hardware for cooking or for your computer without reading how it works ? ;)


Yes, Fred, most people do. 'It's intuitive' don't you know. :)

---

### Post by Bakon Jarser on 2007-10-24
I switched to Swiftfox recently because I was having trouble with firefox.  I was wondering if anybody could tell me the difference between Ubuntu Firefox, Mozilla Firefox, and Swiftfox.

---

### Post by alienexplorers on 2007-10-24
Mozilla firefox is a generic build.  Swiftfox is compiled for seperate cpu's. Don't know what the difference is with ubuntu firefox.  Pretty much looks like and runs like mozilla firefox other than not being able to directly update from the web.

---

### Post by FredB on 2007-10-24
> **Soarer said:**
> Yes, Fred, most people do. 'It's intuitive' don't you know. :)

Big mistake.

> **alienexplorers said:**
> Mozilla firefox is a generic build.  Swiftfox is compiled for seperate cpu's. Don't know what the difference is with ubuntu firefox.  Pretty much looks like and runs like mozilla firefox other than not being able to directly update from the web.

In some ways, it is the truth.

Switfox only uses arch flag of gcc, and more "agressive" optimization : -O3 instead of -O2.

And also a different branding. That's all.

---

### Post by jdong on 2007-10-24
Wait a second.... you go to SWIFTFOX for better security? A closed-source fork of Firefox? An author who had a statement like THIS on his website explaining why he chose to closed-source it?

> 
Please also note that the licensing restrictions were put in place to safeguard Swiftfox users against the possibility of obtaining tainted versions from anyone who may wish to maliciously alter the binary and redistribute it.


So closed-source is safer because it cannot be tainted? Has the guy ever heard of a virus?

Note that Mozilla Firefox in Ubuntu is compiled against the stack protector GCC that's used by default in Ubuntu, and may be more resilient to buffer/stack overflow based attacks than other firefoxes, which are not compiled with such a kernel.

---

### Post by Bakon Jarser on 2007-10-24
> **jdong said:**
> Wait a second.... you go to SWIFTFOX for better security? A closed-source fork of Firefox? An author who had a statement like THIS on his website explaining why he chose to closed-source it?


I went to Swiftfox because when I did a clean install of Gutsy, Firefox crashed after a couple of hours and nothing I could do would get it to stay open for longer than a second.  I reinstalled gutsy and the same thing happened.  I read that someone else having the same problem fixed it by installing Swiftfox so I tried it and have not had any problems since.  It wasn't a security issue, it was a usability issue.

---

