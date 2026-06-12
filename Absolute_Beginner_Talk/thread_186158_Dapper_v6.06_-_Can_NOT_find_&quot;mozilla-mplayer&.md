---
title: "Dapper v6.06 - Can NOT find &quot;mozilla-mplayer&quot; in the Repos"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-06-01
Hello All!

I have finally installed Ubuntu Dapper v6.06!!!

Only I have 1 problem...

I performed an > apt-get update

Then I launched Synaptic &  tried to search for the package > mozilla-mplayer

Unfortunately, it could NOT be found...

Can somebody tell me what "Repo" _line_ I need to add to my "sources.list" file, to be able to download "mozilla-mplayer" for Dapper?

Thanks.

P.S.> In the past, when I used "Ubuntu Breezy", I had ALL Repos figured out, but NOW I seem to be missing what Repos are _needed_ for Dapper...
(And I do NOT think I can use the "Breezy's Repos" into "Dapper", can I?)

---

### Post by murph2481 on 2006-06-01
try changing the word universe to multiverse in your repo list

---

### Post by dvarsam on 2006-06-01
[QUOTE=murph2481]try changing the word universe to multiverse in your repo list[/QUOTE]

Can you briefly explain what you mean?

Are you saying:

1. Use "Breezy's Repos" & change every instance of the word "universe" to "multiverse"?

OR

2. Use the "Dapper's Repos" & change every instance of the word "universe" to "multiverse"?

Which of the above 2 cases?

Thanks.

---

### Post by murph2481 on 2006-06-01
Case number 2

---

### Post by [S|G] on 2006-06-01
Edit your /etc/apt/sources.list and replace it with these lines:
```

deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

```

---

### Post by dvarsam on 2006-06-01
Dear "SIG",

Thank you for your reply!!!

I followed your instructions & managed to finally find & install the package "mozilla-mplayer"...

I now seem NOT being able to find the package "w32codecs"...:( 

What can I do, to install the "w32codecs"?

Is there any _other_ line I could add on my "sources.list" to be able to locate & install the "w32codecs" package?

Thanks in advance,

dvarsam.

P.S.> Again, I have tried to perform an "apt-get update", but nothing is found...

---

### Post by [S|G] on 2006-06-01
I can find w32codecs on my package list... But if you really can't, download the .deb from here:
[http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/w32codecs/w32codecs_20050412-1plf4_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/w32codecs/w32codecs_20050412-1plf4_i386.deb)

This is the same package you'd get from apt. To install, open a terminal, go to the directory you downloaded the file to and type the following:
```

sudo dpkg -i w32codecs_20050412-1plf4_i386.deb

```

That should install it :)

---

### Post by user1397 on 2006-06-01
[quote=dvarsam]Dear "SIG",

Thank you for your reply!!!

I followed your instructions & managed to finally find & install the package "mozilla-mplayer"...

I now seem NOT being able to find the package "w32codecs"...:( 

What can I do, to install the "w32codecs"?

Is there any _other_ line I could add on my "sources.list" to be able to locate & install the "w32codecs" package?

Thanks in advance,

dvarsam.

P.S.> Again, I have tried to perform an "apt-get update", but nothing is found...[/quote] Read the wiki: [https://wiki.ubuntu.com/RestrictedFormats#head-68524fab57e2285050069d6845f95415f8ec8404](https://wiki.ubuntu.com/RestrictedFormats#head-68524fab57e2285050069d6845f95415f8ec8404)

---

### Post by dvarsam on 2006-06-01
Dear "erik1397",

Thank you for your reply!

I know about the Restricted Formats...

...besides I own a couple of Windows OS's, so I should be OK with the Restricted Format's restrictions...

I would just like to know if there is a way to download the "w32codecs" through Synaptic Package Manager...

If anybody knows how to do it from Synaptic, I would be very happy...;) 
(I prefer to add a line in Synaptic, than to have to visit diff addresses with Mozilla to do the work...)

Thanks again for your help!

dvarsam

---

### Post by [S|G] on 2006-06-01
```

deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```

It is intended to be used with breezy though... Use at your own risk! It provides Java, Skype, Opera and W32Codecs. I haven't tested it with Dapper, but if you're not using any of those packages installed by other means it shouldn't create any conflicts on your system.

---

### Post by dvarsam on 2006-06-01
Dear "[S|G",

Thank you for your reply!

I decided to stick to your first suggestion & downloaded the "w32codecs" separately that to do the "risky" approach with the "Breezy's" Repos...

I guess for now I will stick to the First approach, until the Dapper's Repos bring up the correct "w32codecs"... (when that happens, I will - then adjust & - install - exclusively - from the Repos...)

At the same time, I need to install the "flashplayer-mozilla" package, which is also NON existant in the Repos...

Any ideas how would I go for that?

Macromedia's Site, unfortunately includes a ".tar.gz" file...

And I would like to be able to visit & see the pics of [http://www.nokia.co.uk/nokia/0,8764,18042,00.html](http://www.nokia.co.uk/nokia/0,8764,18042,00.html)...

Once again, thanks for ALL your help!!!

dvarsam

---

### Post by [S|G] on 2006-06-01
[http://www.opensourcemirrors.org/ubuntu/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb](http://www.opensourcemirrors.org/ubuntu/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb)

After downloading, install using dpkg -i exactly like you did previously. You can uninstall the packages using synaptic later if you wish, even if you install them using dpkg.

It seems that some packages aren't avaliable yet on dapper repos... I have them from my previous breezy installation and they were kept when I upgraded.

EDIT: If you want to check its dependencies, you can go to [http://packages.ubuntulinux.org/breezy/web/flashplayer-mozilla](http://packages.ubuntulinux.org/breezy/web/flashplayer-mozilla)

---

### Post by dvarsam on 2006-06-01
Dear "S|G", 

the link you provided [http://www.opensourcemirrors.org/ubuntu/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb](http://www.opensourcemirrors.org/ubuntu/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb)

is either Down OR Dead!

NO file is found in there...

Also tried to go back to some directories, to end-up in a US Robotics page, asking for a username & password...

Any other links you might have?

Thanks again for your time & effort!

dvarsam

---

### Post by [S|G] on 2006-06-01
[http://ftp.rz.tu-bs.de/pub/mirror/ubuntu-packages/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb](http://ftp.rz.tu-bs.de/pub/mirror/ubuntu-packages/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb)

Try this one. Seemed to work here.

---

### Post by dvarsam on 2006-06-01
[QUOTE='[S|G]'][http://ftp.rz.tu-bs.de/pub/mirror/ubuntu-packages/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb](http://ftp.rz.tu-bs.de/pub/mirror/ubuntu-packages/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb)

Try this one. Seemed to work here.[/QUOTE]

Thanks for your Reply!

This package is the _same_ package name & version as in "Breezy".

I hope it is going to work with "Dapper".

Thanks again for all your help!

dvarsam

---

### Post by catlett on 2006-06-01
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) If your still working at your Dapper install that guide has everything you need. Since your already an ubuntu user I won't go into anything other than to make sure you use the repository list they post in the guide. I followed it to the letter and I finally have a Dapper install that was like my Breezy.

---

### Post by jimrz on 2006-06-01
[QUOTE='[S|G]']```

deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```

It is intended to be used with breezy though... Use at your own risk! It provides Java, Skype, Opera and W32Codecs. I haven't tested it with Dapper, but if you're not using any of those packages installed by other means it shouldn't create any conflicts on your system.[/QUOTE]

I used the plf breezy free non-free via Synaptic to get W32Codecs last Saturday and all working properly on dapper rc, no problems created by this.

---

