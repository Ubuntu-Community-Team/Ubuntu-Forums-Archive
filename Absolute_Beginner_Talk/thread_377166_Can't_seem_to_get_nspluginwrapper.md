---
title: "Can't seem to get nspluginwrapper"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-03-05
Firstly can I mark this post as resolved, the issue has evolved & I have posted a follow-on question.





I tried to install flash player for firefox on x64 but it errored out, saying there was no support for x64.

So I found [this post](http://www.ubuntuforums.org/showthread.php?t=341727&highlight=nspluginwrapper) as a possible remedy.

This led to me learning a bit about packages and stuff which was all good, but when I tried to get the nspluginwrapper from the suggested site [janvitus](http://www.janvitus.netsons.org/repository/), I ran into a problem.

```

wget (addy).gpg -O- | sudo apt-key add -

```

gave me

```

HTTP request sent, awaiting response... 200 OK
Length: 2,084 (2.0K) [application/octet-stream]
100%[====================================>] 2,084         --.--K/s
01:20:24 (238.98 KB/s) - `-' saved [2084/2084]
gpg: no ultimately trusted keys found

```

Whilst

```

gpg &#8211;keyserver hkp://wwwkeys.eu.pgp.net &#8211;recv-keys 2C4C84CC && gpg 
&#8211;export &#8211;armor 2C4C84CC | sudo apt-key add -

```

seemed to be completely disliked, giving me just

```

usage: gpg [options] [filename]

```

Then, when I went to add the package in System > Administration > Software Properties > [password] > [select package] > Add > Add > Close > Reload,

it seemed to downloaded 28 files ok, but gave me an error about a public key not being available something not being verified or other.. 
Kicking myself because somehow I lost the exact error message, and it doesn't seem to be giving it anymore. 

However still, when I try what appears to be the clincher:

```

sudo apt-get install nspluginwrapper gsfonts-x11

```

I get

```

neil@ubuntu:/$ sudo apt-get install nspluginwrapper gsfonts-x11
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nspluginwrapper

```

Where might the problem be?

Bearing in mind, really I'm more interested in learning the system at the mo than specifically in installing flash.

[edit/update]

I went to the authors site and saw that he had some different url's listed there, so I tried them in sources.list too

Then I discovered the existence of the Package Manager - found a whole slew of packages from the added repository,
Installed the lot. Still no joy with flash & didn't see a 'nspluginwrapper' in the list of packages. 

Bit foxed here now! Why on earth will it have no truck with this 'nspluginwrapper'?

[edit again]

aah.. now I notice, he has a different key on his site, to what is reported in the forum post! Something is amiss here...?
Yes, it doesn't give 'gpg: no ultimately trusted keys found' in terminal anymore..

No joy. Maybe the package isn't there anymore in the repository?

Okay. It doesn't look like it's there under the dapper link on his site, but it *is* there under the edgy link

Hurrah! it's turned up in Package Manager, now I've added the edgy lines in sources.list 

I can't install it though, unresolvable dependencies

lib32gcc1
libc6
libc6-i386
libglib2.0-0

are all to old, one of them allowed me to upgrade, but couldn't get any of the others to go up to a higher version number.

I kinda have a feeling that to install flash player on x64, I would be best either waiting for things to catch up, or installing edgy instead of dapper?

One heck of a learning tool though!

---

