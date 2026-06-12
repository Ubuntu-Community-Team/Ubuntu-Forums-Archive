---
title: "I think I have broken my installation..."
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-05-15
When I open **Synaptic** I get this error;
> W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

Also, I tried installing wine to install Ragnarok Online, and it didn't work. How do I remove ragnarok, *and* the animaro patch, *and* wine?

I'm *_also_* having trouble with **Gaim.** I can't log into my MSN account all of a sudden. The error is about authentication... It was working yesterday, just fine...

---

### Post by macdo on 2006-05-15
It looks like you've changed your sources.list but not updated.
try typing at the command line: 
```
sudo apt-get update
```
That should solve your first problem...

---

### Post by Raavea on 2006-05-15
I tried that, thanks for it, but it didn't work.. This is what happened;
> raavea@bernardette:~$ sudo apt-get update
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://theli.free.fr](http://theli.free.fr) ./ Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Err [http://theli.free.fr](http://theli.free.fr) ./ Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
  404 Not Found
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release.gpg
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Fetched 5B in 4s (1B/s)
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz)  404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
raavea@bernardette:~$


 Perhaps I should do a system wipe and start over... :lol: Easy way out, but then I won't learn anything, except not to try and use wine. :lol:

---

### Post by tc10b on 2006-05-15
The problem in synaptic is caused by the repositories not existing. 
You are getting the 404 error which means they aren't there/server down.
Just remove the ones labelled 404 in that list and synaptic should work fine.

As regards your second problem, I haven't tried wine yet so I don't know.

As regards your third problem, have you tried logging in to another account i.e a friends or onto a different server i.e. icq etc. If not try that and see what happens. Have you also tried a different client such as aMSN? Sometimes the msn server is down so just wait patiently and it might start working again.

---

### Post by Raavea on 2006-05-15
Er... As regards the 404 thing... What? *is a complete noob*

 And my girlfriend, on windows, was using MSN fine, so it wasn't that. I gave up, but it's working again now. I think it may be something to do with the combination of GnomeMUD, Firestarter, and Gaim, all running at once...

---

### Post by aysiu on 2006-05-15
[QUOTE=Raavea]Er... As regards the 404 thing... What? *is a complete noob*[/quote] A 404 error means that the server you're trying to reach is not available--either because you're trying to type a web address that doesn't exist or the server is temporarily unavailable.

You have some weirdo repositories in your /etc/apt/sources.list
Get a fresh list and you won't have those 404 errors:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Raavea on 2006-05-15
I know what a 404 *is*, just not how to 'delete the entries'. :$

 And ah, how do I uninstall the stuff I installed with wine?

---

### Post by aysiu on 2006-05-15
[QUOTE=Raavea]I know what a 404 *is*, just not how to 'delete the entries'. :$[/quote] You have some weirdo repositories in your /etc/apt/sources.list
Get a fresh list and you won't have those 404 errors:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Raavea on 2006-05-15
Well, after a little deliberation, I wiped both my hard-drives and made a fresh install. It sounds extreme, but I couldn't get rid of the old install on the other HD and there were some other things too. :)

 However! I think that it's Automatix causing my problem. Until I used it to install the crap I had before, everything was fine. Now, I'm getting this error;
> W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory) This only occurs in Synaptic, not in Add Apps.

 If I install a new sources list, will it bum my programs? I've upgraded the lazy way with automatix to the newest firefox, and so on.


 Hang on... instead of replacing the whole thing.. If I just remove these lines;
> deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
 It should fix the error, right?

---

### Post by catlett on 2006-05-15
Yes. That was all you had to do before. You didn't have to reinstall.

---

### Post by Raavea on 2006-05-15
Yar, I know I didn't. As I said, there were other, more complex issues, and so forth. ^_^

 Thanks for the help all.

---

### Post by catlett on 2006-05-16
Automatix replaces your /etc/apt/sources.list with it's list. That is why that repository is on there. If you ever reinstall choose to not let Automatix rewrite your list. If you just hit enter it will rewrite. Aysiu's thread will give you a list you can replace your Automatix list with.
Also putting a "#" in front of a line will cause the entry to be ignored in case you want the entry around at a later date.

---

### Post by macdo on 2006-05-16
Changing your sources.list will not bum your programs. However, if you have programs that were in repositories that were in the old sources.list, but aren't in the new, they won't be updated. 

Oh, and 404 errors in repositories aren't really that important, as long as you have working main - universe - multiverse reps, and security reps, of course, 90% of your programs wwill be updated in the regular fashion. 

To be honest, if you comment out (add a # to the beginning of the line) the koti.fi reps, the Automatix reps are fine.

---

### Post by Raavea on 2006-05-16
Okay, thanks guys. The new install means my hd is cleared of a lot of clutter, and my slave drive is empty now too (so it all boots up more smoothly ^_^ )

 But, I have yet another problem, and I can't use any internet forms except this quick reply, or firefox crashes.

 Anyone know what's up with that? I can't use the search feature, or make new threads, or use the google search box in my toolbar. If I type in -ANY- form other than this thing, ff goes kaput...

---

