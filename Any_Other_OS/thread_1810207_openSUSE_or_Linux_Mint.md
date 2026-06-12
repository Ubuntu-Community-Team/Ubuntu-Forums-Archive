---
title: "openSUSE or Linux Mint?"
date: 2011-07-22
forum: Any Other OS
---

### Post by laplacian13 on 2011-07-22
I've been messing around with ubuntu for a while now and I've decided I want to give another distro a try. This is partially because my system is so cluttered that I'm tempted to reinstall ubuntu, so I figure if I'm doing that I might as well get some more experience with linux all around and just install a different one instead

I understand that mint is very much like ubuntu, but I do like some things about it - particularly gnome 2 instead of unity. I virtualbox'd it and it also seemed smoother and a little more polished than ubuntu, but I stress that I am by no means an expert.

I have also recently heard of openSUSE. I don't know much about it, but KDE looks interesting and I've heard openSUSE is a little more for experienced users than ubuntu, which I like, because I'm really trying to learn about linux.

I'm open to other possibilities as well, really just taking recommendations here to try some other stuff out and get some linux experience. I tried installing arch to a virtualbox to try it out but had a really hard time getting wireless internet to work and gave up, so I'm not sure if I'm ready for  a distro that intense. If anybody would be willing to give me some advice or a recommendation, that'd be great.

---

### Post by dreamer3kx on 2011-07-22
I can just comment on Linux Mint, haven't used Suse for a very long, Mint is awesome, I install maybe like two programs that I use after a Mint install and Im ready to go, its super simple and works right out the box, no messing around with anything, has been a very nice and stress free distro for me.

---

### Post by jeffathehutt on 2011-07-22
For learning purposes, I would say openSUSE just because it is slightly different than Ubuntu and you would get some experience with .rpm packages.  But for general use I personally recommend Mint instead, because most things just work out of the box.  You won't learn as much though, since it is very similar to Ubuntu.

They are both great operating systems, so you might want to eventually try both. :)

---

### Post by jramshu on 2011-07-22
Check out Arch too.

---

### Post by krapp on 2011-07-23
Which one's greener?




> **jramshu said:**
> Check out Arch too.

Really on-topic.

---

### Post by garvinrick4 on 2011-07-23
> I'm open to other possibilities as well, really just taking  recommendations here to try some other stuff out and get some linux  experience. I tried installing arch to a virtualbox to try it out but  had a really hard time getting wireless internet to work and gave up, so  I'm not sure if I'm ready for  a distro that intense. If anybody would  be willing to give me some advice or a recommendation, that'd be great.You have to just install read,study,google-search on your own. Each one takes its own
learning curve. Find a good post-installation guide is best. 
If it is not Debian base it most likely uses grub-legacy (grub) and will not work well with
Ubuntu's grub2 (grub-pc) DO NOT install their grub at install. Choose in anaconda installer
which they most use to not install grub at all. Go to Ubuntu after install and do a sudo update-grub and it will be put in grub config and as a menu entry and if you can boot
into it. grub and grub2 do not play together well at all. If you are going to mess with various distro's  and you are new to linux here is a valuable link to keep.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
##Check out your wifi card and graphics card and see if they are proprietary drivers
that have to be installed after install. If you have drivers that are already in linux kernel
then you are OK there. Every distro has different ideas on what drivers they will give you. As you found out in Arch. 
Study your cards, read all you can about them. Get to know your machine like the back of your hand. Good luck and enjoy Linux. 
Me I like Ubuntu and everyone has an opinion, that is mine.

---

### Post by k357k9 on 2011-07-23
> I understand that mint is very much like ubuntu
It is, or at least it was before Unity. However, they put the finishing touches on it and make it better. If you run Mint right after Ubuntu, it will become obvious.

---

### Post by AwesomeMoose on 2011-07-23
If you want to try out KDE I suggest that you look into Pardus and MEPIS as well as OpenSUSE. Pardus will give you a good taste of an independent distro, and it is also very slick and easy to use. Mint is great. I also highly recommend Salix for it's Xfce edition. It's Slackware based, which is quite different from Ubuntu. PCLinuxOS comes from the Mandriva family, Fedora from the Red Hat family and Sabayon from Gentoo. That should handle every major group exept for Arch. Chakra is based on Arch and provides KDE, but I am not very knowledgeable about it, it shouldn't be too hard. I advise you to do what I did, try everything until you find something you like, and then stick with it. You'll learn a lot from it too. Enjoy!

---

### Post by Alwimo on 2011-07-23
If you like Linux Mint and want to try KDE, you can get Linux Mint KDE.

---

### Post by laplacian13 on 2011-07-23
Thanks guys, what I'm getting here is basically what I've read on the internet... that each one really is different and they simply have to be tried.

That being said, I think I'll probably try both linux mint and openSUSE, but for now I'm going to install openSUSE just because it's most different. I have ubuntu installed with wubi right now, so I can uninstall wubi and then simply have the installer shrink my windows partition and create a new one for openSUSE on it's own, right?

I don't know much about partitioning and whenever I try to learn it I get worried that I'm about to mess up and lose all my stuff, so I've never put much effort into learning it ](*,)](*,)

---

### Post by k357k9 on 2011-07-23
> I get worried that I'm about to mess up and lose all my stuff
:P You gotta -- gotta -- gotta backup first! :P

---

### Post by jramshu on 2011-07-23
> **krapp said:**
> Which one's greener?







Really on-topic.

Wow, really nice man.

Mint is basically Ubuntu that lets you install all the extras when installing. It's not very different than Ubuntu, actually gets updates from a lot of Ubuntu repositories.

If you want something different then go with openSuse, else you won't be learning anything you probably don't already know.

On topic.

---

### Post by laplacian13 on 2011-07-23
Went with openSUSE - just burned the .iso to a DVD and installed it. Loving it.

---

### Post by IWantFroyo on 2011-07-23
Glad you're liking it! :)

I personally prefer openSUSE to LM (that's just me, though). My one problem with openSUSE is I get carried away in YAST and end up locking myself out of the system. :(  

Good luck!

---

### Post by krapp on 2011-07-24
> **jramshu said:**
> Wow, really nice man.

Mint is basically Ubuntu that lets you install all the extras when installing. It's not very different than Ubuntu, actually gets updates from a lot of Ubuntu repositories.

If you want something different then go with openSuse, else you won't be learning anything you probably don't already know.

On topic.

I know what Mint and OpenSUSE are.

I don't understand what Arch has to do with this thread.

---

### Post by BigSilly on 2011-07-24
I've become a big fan of openSUSE in the last couple of months. The forum can be a bit grumpy and unfriendly (not as nice a place as here!), but on balance I've had much less trouble using it than pretty much any other distro I've ever used. Though that's not to say it's perfect, it's impressive especially when you consider I'm running Gnome 3 on it too, trouble free.

I'd recommend it to anyone, but people still bang on about *that* infamous deal....

---

### Post by HermanAB on 2011-07-24
Hmm, ask two Linux users which distro to use and you'll get 13 suggestions.

My favourites are Fedora (LXDE) and Mint.  Suse is slow - I never managed to figure out why, but it is slow - well, for me anyway.

---

### Post by BigSilly on 2011-07-24
> **HermanAB said:**
> Hmm, ask two Linux users which distro to use and you'll get 13 suggestions.

Yes true. Fedora is slow for me, but many seem to love it. OpenSUSE has been one of the fastest I've used, but ymmv of course. It amazes me how different people's experiences can be.

---

### Post by jramshu on 2011-07-24
> **krapp said:**
> I know what Mint and OpenSUSE are.

I don't understand what Arch has to do with this thread.

I wasn't talking to you about the differences, I quoted you just to let you know I was on topic.

@OP,
I hope you enjoy it. I've played with it some in the live environment, but haven't actually installed it, yet. I have gone through a ton of distros but seemed to find myself coming back to Ubuntu. I prefer the Debian based distros for now. The support for Ubuntu is like no other. Don't be surprised if you find yourself on here getting help for other than Debian based OS problems.

---

### Post by chegarty on 2011-07-25
> **HermanAB said:**
> Hmm, ask two Linux users which distro to use and you'll get 13 suggestions.

I really like it this way. So much choice!

openSUSE and Mint have different audiences, it seems. Mint is extremely user-friendly but doesn't get the new fun things quite as quickly as Ubuntu because it releases on a delay from Ubuntu. Aw, man, it's pretty, though.

openSUSE is different. It uses RPM, which is interesting. I'd suggest using KDE with openSUSE, but I don't have more than cursory experience with openSUSE in general.

I could probably point out 11 more distros, but these are just my thoughts on openSUSE and Mint. :)

---

### Post by BrokenKingpin on 2011-07-27
OpenSuse over Mint. Mint is fine, but I find it does not offer a lot over Ubuntu. The current version is still on Gnome2, and the Xfce versions are too bloated. The Debian edition seems cool in principle, but it quite buggy from my experience.

openSUSE is a nice user friendly distro, and has some cool features.

---

### Post by BigSilly on 2011-07-28
> **BrokenKingpin said:**
> OpenSuse over Mint. Mint is fine, but I find it does not offer a lot over Ubuntu. **The current version is still on Gnome2**, and the Xfce versions are too bloated. The Debian edition seems cool in principle, but it quite buggy from my experience.

openSUSE is a nice user friendly distro, and has some cool features.

You need [this]("http://en.opensuse.org/openSUSE:GNOME_3.0"). :)  I've been running Gnome 3 on it for about 2-3 months, and it's been stellar. Benefits over Ubuntu (imho) are that it is just less buggy generally. I couldn't run Natty at all, and moving to openSUSE has proved a great choice for me. It's not hard to use, and though I don't find the package management as nice as Debian, it's been excellent for me.

---

### Post by YesWeCan on 2011-07-28
Mad but informative:
[http://www.youtube.com/watch?v=Yxprxgw7VIA&feature=related](http://www.youtube.com/watch?v=Yxprxgw7VIA&feature=related)
[http://www.youtube.com/watch?v=GGqYsevDd84](http://www.youtube.com/watch?v=GGqYsevDd84)

---

### Post by mystika1 on 2011-07-28
> **laplacian13 said:**
> 

I'm open to other possibilities as well, really just taking recommendations here to try some other stuff out and get some linux experience..

I started off with Kubuntu and when I was ready to try other distros for a learning curve I decided to try debian. Yes....It is the base of ubuntu but without all of the "hand holding." This made it nice because I already understood the apt-get packages. The documentation is great. You may like that option. 

I then progressed to aptosid which is a rolling release of debian sid. 

Chakra linux started off as an KDE version of arch which I used shortly but like you...I had hardware troubles that could not be worked out.

I have a huge stack of live cd's as I love trying them all. Just have fun with it. There are tons of distros to try.

HTH,

Penny

---

