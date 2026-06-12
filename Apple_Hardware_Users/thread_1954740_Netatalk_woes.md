---
title: "Netatalk woes"
date: 2012-04-08
forum: Apple Hardware Users
---

### Post by Mk32 on 2012-04-08
I have Ubuntu 9.10 installed. 

First I downloaded the Berkeley DB software and made it, installed it.

```
$ cd Desktop/
$ tar -zxf db-5.3.15.NC.tar.gz
$ cd db-5.3.15.NC
$ cd build_unix
$ ../dist/configure --disable-shared
$ make
$ sudo make install
```Next, the Netatalk source (kinda hard to use sudo apt-get netatalk when they killed off the support...:mad:)

```
$ cd ~/
$ cd Desktop/
$ tar -zxf netatalk-2.2.2.tar.gz
$ cd netatalk-2.2.2.tar.gz
$ ./configure
$ make
$ sudo make install

```It appears to install normally, but there is no directory "netatalk" in /etc/, neither in init.d. I can't even get started!

Here's what I'm trying to do: Connect this Ubuntu machine to a System 7.0.1 Mac (and 6.0.8...) and read/write file transfer both ways, preferably with guest access.

I have spent many hours doing this, reading, searching the web, and this forum. Nothing.

---

### Post by Paddy Landau on 2012-04-09
As I understand, you just want to link the computers via the network and use shared folders. Is that right?

If so, why use an unsupported third-party application? Just use the applications that come by default with Windows and Ubuntu. (Sorry, I don't know how to add Mac; but I would hope that it is compatible with Windows.)

First, in Ubuntu, install [system-config-samba]("apt:system-config-samba"). Samba makes Ubuntu look like a Windows machine (so that Windows can access it).

Run Samba to set any applicable settings. Ensure that workgroup names are the same on both Windows and Ubuntu. Ensure that the computer names are *not* the same. Reboot both Windows and Ubuntu.

Try to get Windows and Ubuntu to see each other. Post back if you cannot.

Once Windows and Ubuntu are working, it's time to add Mac into the equation; sorry, I won't be able to help you with that (but maybe someone else reading this can do so).

---

### Post by Lars Noodén on 2012-04-09
[netatalk](http://packages.ubuntu.com/search?keywords=netatalk&searchon=names&suite=all&section=all) is still available in the package repository.  Otherwise, as Paddy suggests, Samba might be an option.

---

### Post by Mk32 on 2012-04-09
The only Windows version that supports AFP is Win Server 2000 and 2003. 

I don't have either. Samba will NOT work with pre OS X systems. (Maybe A/UX, but that's outside my reach.)

The repositories won't work either. None of them are listed for 9.10 Karmic. 

Support ended awhile ago. (Why do they kill off repositories anyways? too much bandwidth? insufficient space on rack servers?) 

Besides I'd rather than I know how to compile it in source, based on what I'm doing. (Well...sort of.) I have to compile it in source because of what I just said earlier.

[There is this](https://launchpad.net/ubuntu/karmic/+package/netatalk) but it is very much outdated.

---

### Post by Lars Noodén on 2012-04-10
> **Mk32 said:**
> 
The repositories won't work either. None of them are listed for 9.10 Karmic. 

The web site won't list Karmic because it stopped being supported about a year ago.  The package should still be available in Karmic's repository at *old-releases.ubuntu.com*.   However, it would be much better to update to a supported version of Ubuntu.  If you don't want to be bothered with updating often, then one of the LTS versions should be used.  Starting with Precise, the LTS version will last you 5 years both on the server and on the desktop.

---

### Post by Mk32 on 2012-04-10
Would there be a specific reason for why compiling in source produced the non-working result I have?

Obviously someone who *has* to compile in source because there is no repository source at all to begin with might have the same issue I have.

EDIT: Tried adding old-releases.ubuntu.org to my /etc/apt/sources.list (read only funzies) and it registers the repository correctly, but doesn't load anything past that. 

I occurred to me that I could probably just $ sudo mv or cp everything, but how would I know where stuff is supposed to go? 

I don't really feel like using the new ones, I mean it would be fine if they let you use GNOME 2, but that is out because it...well, it's just not worth it to pull out GNOME 3 and replace it with GNOME 2. (I wonder what was wrong with the old interface? I like it just ...a lot, but I can't bear to use GNOME 3)

Not to mention, let's say ______ really likes 8.04. For some reason. Well since it's not supported anymore, everything has to be compiled from source. Support ended last year. It was released two years earlier. At that rate, even Windows XP has better support -- for that matter, even W2K. At least you can still *get* certain things that will work with W2K.

I'll try now putting 10.04 and making it look like 9.10.

---

