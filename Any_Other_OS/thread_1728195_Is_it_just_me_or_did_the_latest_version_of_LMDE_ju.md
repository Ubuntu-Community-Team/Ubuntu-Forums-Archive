---
title: "Is it just me or did the latest version of LMDE just get a lot harder to deal with?"
date: 2011-04-13
forum: Any Other OS
---

### Post by Rubi1200 on 2011-04-13
I originally gave the first Linux Mint Debian Edition a trial run because I liked what they had done with it.

Installing was easy, updating was easy, configuring was easy.

I am now trying the latest version:
[http://distrowatch.com/?newsid=06425](http://distrowatch.com/?newsid=06425)

Pros:

worked really nicely from the LiveUSB

installation was a breeze; just 10 minutes from start to finish

has nice applications and features, even though I won't use all of them

I can choose to NOT install a bootloader :-)

Cons:

why is it that I need to add the UUID for swap to fstab manually?

the MintUpdater, which seemed to me to work flawlessly before, gave me an unconfigured packages error as soon as it started. Huh? On a fresh install?

I had to run dpkg --configure -a TWICE

the original image contained the usual stuff like Firefox, Thunderbird, and OpenOffice. After installing and trying to update, it added Epiphany, Evolution, and LibreOffice (which apparently replaced OpenOffice). Now, call me old-fashioned but would it not have made more sense to have those packages there by default at installation time? (I realize that I am installing months after it was released, but still...)

Conclusion:

I haven't come to one yet...

So, fellow users, what are your thoughts about, and experiences with, the latest LMDE?

---

### Post by XubuRoxMySox on 2011-04-13
Further proof of what I said in the other thread ("Closer to Debian") here. Debian is simply a more difficult base to build on than Ubuntu. 

Both LMDE and the latest Xfce edition are built on Debian instead of Ubuntu and have frustrated alot of users who were used to the Ubuntu base and assumed that a Debian base would be as easy and effortless as Mint's Ubuntu-based editions have been.

They're great if you don't mind investing abuncha time to reinvent the wheel in order to make Debian run as effortlessly as Ubuntu does.

-Robin

---

### Post by Rubi1200 on 2011-04-13
Thanks for sharing your thought on this Robin; it is appreciated.

---

### Post by BrokenKingpin on 2011-04-14
I have also tried LMDE a few times, and I really like the concept of the distro (Debian compatible and rolling release), but it always seems to fall a bit short for me.

Every time I tried it I have to fix my swap partition (as mentioned above) and the sleep/hibernate functions do not work on my netbook. I am a pretty experience Linux user, so I can work around these issues, but I shouldn't have to. Regardless of the distro and how "user friendly" it is supposed to be, the installer should function properly and basic operations around turning your computer off and on should work out of the box.

I have since moved away from LMDE, but I will continue to watch it closely because I really like where they are going with it... I just hope they can work out some of the issues with it.

---

### Post by Rubi1200 on 2011-04-14
I agree with your assessment BrokenKingpin. There are quite a few things that the Mint team have done that I really like. 

But, as you mentioned, it seems to somehow fall short on certain things.

I, like you, will also be keeping an eye on developments.

Thanks for sharing your experiences and thoughts about this.

---

### Post by bodhi.zazen on 2011-04-15
> **dixiedancer said:**
> Further proof of what I said in the other thread ("Closer to Debian") here. Debian is simply a more difficult base to build on than Ubuntu. 

Both LMDE and the latest Xfce edition are built on Debian instead of Ubuntu and have frustrated alot of users who were used to the Ubuntu base and assumed that a Debian base would be as easy and effortless as Mint's Ubuntu-based editions have been.

They're great if you don't mind investing abuncha time to reinvent the wheel in order to make Debian run as effortlessly as Ubuntu does.

-Robin

Depends on what version of Debian you are using and how close to a release your are.

Debian stable is known for, well stability.

If you use testing it is not too bad, but they call it Debian "unstable" for a reason.

The transition from Ubuntu -> Debian is about as easy as it is going to get, easier then Ubuntu -> Fedora or most any distro and much easier then Ubuntu -> Gentoo or LFS.

The reason why all the "mints" migrated to Debian was that Debian testing (now squeeze) was quite stable (more stable then Ubuntu) and close to a release.

Now that debian (squeeze) has been released, with the passage of time, they will almost certainly migrate back to Ubuntu because they have the same problem everyone has with Debian - stable = old (stale) packages and testing / unstable is a crap shoot. If you follow a release cycle 1-2 months after Ubuntu you will have a stable base + fresh packages.

The things they do to make "Mint" easy are, for the most part, agnostic of the base, so it should be easy to transition debian <--> Ubuntu. Heck the (debian) live build suite can build either distro and many developers now work in (contribute to) both communities.

---

### Post by krapp on 2011-04-20
> **dixiedancer said:**
> Further proof of what I said in the other thread ("Closer to Debian") here. Debian is simply a more difficult base to build on than Ubuntu. 

Both LMDE and the latest Xfce edition are built on Debian instead of Ubuntu and have frustrated alot of users who were used to the Ubuntu base and assumed that a Debian base would be as easy and effortless as Mint's Ubuntu-based editions have been.

They're great if you don't mind investing abuncha time to reinvent the wheel in order to make Debian run as effortlessly as Ubuntu does.

-Robin

Debian Stable runs as effortlessly as Ubuntu and on a broader range of hardware. Granted, it has less GUI help to set up non-free things, such as codecs and Flash and the like, but I don't see where the "reinventing the wheel" part comes in. If anything, that's what Ubuntu has been doing, in order to move away from the command line.

LMDE is more complicated than Ubuntu because it's built on a constantly updated Debian Unstable. LMDE is **Debian Testing** + media codecs and a few other goodies pre-installed and available in the Mint repos.

---

### Post by XubuRoxMySox on 2011-04-20
Suffice it to say that Debian is harder to *set up* than Ubuntu is, but* once that is done*, running Debian is as effortless as running Ubuntu.

-Robin

---

### Post by krapp on 2011-04-20
If by setting up you mean installing, then, no. Debian is as easy to install as Ubuntu.

If by setting up you mean adding non-free things that Debian does not deem integral to using the system itself, then yes, Debian is more difficult; that is, if you find reading the Debian Wiki and copy-pasting into the Terminal difficult.

I too, as an Ubuntu user, found the prospect of using Debian intimidating, but it's not all, and I'd like to challenge that assumption, so that prospective users won't shy away from giving Debian a try.

---

### Post by Rubi1200 on 2011-04-21
Just to be clear, I wasn't suggesting this is a difficult distro to install or maintain because it has a Debian base. 

I was actually very impressed with the job the Mint team had done with the first attempt.

My issue is with the fact that I had to run commands to fix package problems immediately after a fresh install. To me, that seems like poor implementation.

---

