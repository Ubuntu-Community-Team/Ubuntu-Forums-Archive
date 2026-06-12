---
title: "[SOLVED] Gnome + KDE = problems"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-02-19
I've read on the forums about being able to have KDE installed with Gnome on Ubuntu and being able to select which I want via "options" and "session" at login.  So, since my Ubuntu 7.04 seems about as good as it's going to get for now, I decided to also install the KDE desktop - at least that's what I THOUGHT I was doing.

I did:

sudo apt-get install kde-desktop

After waiting for it all to download and install, I logged off my Gnome session and logged into a KDE session - worked fine.  However, now when I boot I get the splash screen for kubuntu, and when I try to login to a KDE session straight from the boot, desktop initialization aborts, wireless doesn't work, sometimes even locks up my keyboard.  Note that if I reboot but login to a Gnome session first, I can then logout and login to a KDE session with no problem.  I'd like to be able to boot and log straight into a KDE session if possible.

So, again I'm back with something that I've probably done something wrong with.

Any ideas?? 

Thanks in advance!  :)

---

### Post by timbounceback on 2008-02-19
Strange... I assume you mean kubuntu-desktop, not kde-desktop?

---

### Post by luisromangz on 2008-02-19
If you install kubuntu-desktop, you are installing kubuntu, with all its default configs, replacing those of ubuntu. If you just wanted to install kde, you only need to install the kde packages.

---

### Post by anewguy on 2008-02-19
Oops.... so you're saying I installed kubuntu?  Any ideas why I have the problems logging straight into KDE from boot, but not if I login to Gnome first, logout, then login to KDE?

:)

---

### Post by anewguy on 2008-02-19
bump

---

### Post by anewguy on 2008-02-20
bump

---

### Post by philinux on 2008-02-20
Looking through my synaptic there is no kde-desktop package. There is kubuntu-desktop though.

Anyway click the psychocats link below and scroll down to the gnome/kde links.

I would go back to pure gnome if things aren't working out.

---

### Post by anewguy on 2008-02-28
I believe the package I installed was indeed kubuntu-desktop.

I just upgraded from Feisty to Gutsy to see if this would make any difference.  It made some, but still not solved:

When I boot Ubuntu, if my FIRST login is to KDE, sometimes the startup aborts in some process in "Desktop", other times not.  In all cases, wireless networking shows my various available networks but refuses to connect to any of them.  Logging out and going to a Gnome session no longer helps.  I *MUST* login to Gnome as the FIRST login after a boot, then it asks for my keyring password (apparently I lost pam in the upgrade) - which is something it does not do in KDE.  Then it will connect to the network.  I can then logout and login to KDE and all appears fine with the world.

Why do I have to login to Gnome FIRST after a boot if I expect anything to work?  Seems to me that I should be able to just login to KDE.

Why am I asked for the keyring password in Gnome but not KDE?

I have found I prefer KDE lately, and would like to make it my default for now.  These problems are preventing me from doing so.  I don't want to have to download a kubuntu LiveCD and reinstall.

Thanks :)

---

### Post by sayakb on 2008-02-28
> **anewguy said:**
> I believe the package I installed was indeed kubuntu-desktop.

I just upgraded from Feisty to Gutsy to see if this would make any difference.  It made some, but still not solved:

When I boot Ubuntu, if my FIRST login is to KDE, sometimes the startup aborts in some process in "Desktop", other times not.  In all cases, wireless networking shows my various available networks but refuses to connect to any of them.  Logging out and going to a Gnome session no longer helps.  I *MUST* login to Gnome as the FIRST login after a boot, then it asks for my keyring password (apparently I lost pam in the upgrade) - which is something it does not do in KDE.  Then it will connect to the network.  I can then logout and login to KDE and all appears fine with the world.

Why do I have to login to Gnome FIRST after a boot if I expect anything to work?  Seems to me that I should be able to just login to KDE.

Why am I asked for the keyring password in Gnome but not KDE?

I have found I prefer KDE lately, and would like to make it my default for now.  These problems are preventing me from doing so.  I don't want to have to download a kubuntu LiveCD and reinstall.

Thanks :)

If you like KDE, try the KDE4 desktop also. Works fine for me w/o any problems:

```
sudo apt-get install kde4
```

---

### Post by harold4 on 2008-02-28
Make sure you actually installed kubuntu-desktop

```
sudo apt-get install kubuntu-desktop
```

If so, 

```

sudo apt-get clean && sudo apt-get autoclean
sudo apt-get install --reinstall kubuntu-desktop

```

Current issues aside, [kmenu gnome]("http://www.kde-apps.org/content/show.php/K+Menu+Gnome+(source)?content=31025") will keep your menus clean having gnome and kde installed

---

### Post by aysiu on 2008-02-28
The keyring is the Gnome Keyring Manager, which stores passwords for Gnome applications. I believe KDE has a similar program called KWallet, which stores passwords for KDE applications.

Gnome uses Network Manager for internet connections. I don't remember what KDE uses, but I'm sure you can run Network Manager in KDE, too, if that's what works for you:
Alt-F2 ```
nm-applet --sm-disable
```

---

### Post by harold4 on 2008-02-28
knetworkmanager should be running when you load into KDE, so the gnome applet should be irrelevant.

---

### Post by anewguy on 2008-02-28
Tried the re-install of kubuntu-desktop.  That didn't help either.  There must be a solution of some sort out there -  does KDE for some reason handle a USB network adaptor differently than Gnome?  If I left click on the network icon while in KDE, is says no device defined.  But it does show the wireless networks, and my router indicates it is trying to connect (fails each time at 57% done - something with retrieving address).  In addition, I don't remember what I exactly was looking at, but it did show eth0 for the hardwire connector and showed eth1 as the wireless and working.

I really could use a solution here!  :)

---

### Post by harold4 on 2008-02-28
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bck 
```

reboot

---

### Post by anewguy on 2008-02-28
I found the problem - feel a little stupid.  In KDE, the network connection manager was defaulting to a passphrase, when I used a password and different bit length.  Once I found that and got KDE Wallet to accept it also, things work as they should with one exception:

Gnome or KDE either one:  I have pam installed, yet it isn't doing anything on either desktop.  My password was set to my logon password so I was getting automatically connected until I did the upgrade to Gutsy.  Perhaps I need to delete the keyring files and start anew since the upgrade.

At any rate, at least now I can connect to the net in KDE right after a boot, and my desktop seems fine now as well.  So, I'll mark this as closed.

The lesson here:  watch conflicting defaults in the network connection manager in KDE versus Gnome.:)

---

