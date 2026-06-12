---
title: "login root"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by X-Tek on 2006-06-10
anyone know how to log into root?  when i installed dapper drake, it never asked me to set up a root access and when i tried to create one, it was already in existance.  only problem is, i don't have the password.  so hmm..  i need to login so i can access my /etc/apt to get updates and install the new GCC and MPlayer.  

if anyone knows how to do this w/o having to have permissing to access the /etc/apt/source.list -- i'm all eyes*.

i've done:

cd /ect/apt
sudo apt-get update

list of updates were shown

MPlayer packages were not listed so I have to edit the sources.list (which requires root login).  Or the other way I can do it is to manually install it but first, I have to install my GCC v3.4.6.  I have yet to be successful in installation.  it's saying that i need to set the environment or some sh*t.

damn it.  all i wanna do is watch Underworld Evolution on my Linux PC!  IS THAT TOO MUCH TO ASK????   ](*,)

---

### Post by asimon on 2006-06-11
> **X-Tek]anyone know how to log into root?  when i installed dapper drake, it never asked me to set up a root access and when i tried to create one, it was already in existance.  only problem is, i don't have the password.  so hmm..  i need to login so i can access my /etc/apt to get updates and install the new GCC and MPlayer.[/quote]
Ubuntu by default has the root account disabled and expects that you use sudo for administrative tasks. See this wiki page for some information about sudo: [RootSudo](https://wiki.ubuntu.com/RootSudo).

[QUOTE=X-Tek]
if anyone knows how to do this w/o having to have permissing to access the /etc/apt/source.list -- i'm all eyes*.

i've done:

cd /ect/apt
sudo apt-get update

list of updates were shown

MPlayer packages were not listed so I have to edit the sources.list (which requires root login). [/quote]
Yes, use sudo to change the sources.list.  said:**
> AddingRepositoriesHowto[/url].

[QUOTE=X-Tek]
Or the other way I can do it is to manually install it but first, I have to install my GCC v3.4.6.  I have yet to be successful in installation.  it's saying that i need to set the environment or some sh*t.

No need to do this as mplayer is already packaged for Ubuntu. BTW, if you want to compile stuff your own "build-essential" is a good candidate to install, it contains not only gcc, but also some other stuff you will need like make.

[QUOTE=X-Tek]
damn it.  all i wanna do is watch Underworld Evolution on my Linux PC!  IS THAT TOO MUCH TO ASK????   ](*,)[/QUOTE]
As we see, there is still a lot of room for improvements to make Ubuntu more user friendly. ;-)

There exists also the [Automatix](http://www.getautomatix.com) project which aims to make it easier for people to install multimedia and some other propritary stuff. I never used it but it seems to be quite popular. There is a [thread about Automatix](http://ubuntuforums.org/showthread.php?t=190025).

If you prefer to install multimedia stuff without Automatix the wikipage [RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) is a good place to look for what to install.

Have fun with Underworld Evolution. :-)

---

