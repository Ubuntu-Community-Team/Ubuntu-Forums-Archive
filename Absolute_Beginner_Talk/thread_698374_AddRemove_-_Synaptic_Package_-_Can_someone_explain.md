---
title: "Add/Remove - Synaptic Package - Can someone explain all this?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-16
Being just about a week old here with Linux.
Something I don't quite yet fully understand. The whole concept of where progs come from, where you SHOULD get them from, and the rights and wrongs.

As I see it. We have the ADD/REMOVE programs area, where you can (obviously) install and uninstall various programs.

This looks the prettiest? area, together with little write ups and star ratings on the programs on offer. Although from my experience it never seems to tell you what version of the software it is. (and often does not seem to be the latest one)


Then, you can go to SYSTEM/ADMINISTRATION and select the "Synaptic Package Manager" which (from a newbie point of view) appears to do much the same, but in a much more basic layout kinda way, although this often does tell you the version you are going to get.

So, before I go any further...........

Are these two places pulling the programs from the same place?
Or do they come from different areas on the net somewhere?

Do I also assume BOTH these programs contain versions that have been tested and compiled (if that's the right term?) to work under Ubuntu Linux?



With that out the way, I also of course understand you can go to the actual home page of the software in question and download the source code (which I have never done yet) and sometimes builds for your version of Linux and/or self installing packages.

Just after a general overview of all of this, as (from someone used to windows, where you just get the latest setup.exe file. this all seems very confusing.

Thanks.

---

### Post by LaRoza on 2008-02-16
The programs are in repositories. There are four repositories by default and they are not all enabled. 

The Add/Remove, Synaptic Package Manager, and the "apt-get" and "aptitude" commands get the packages from the same places.

The GUI's are just wrappers for apt-get.

Another way of getting sofware is too get a Debian installer, with the extension .deb. They are clickable installers, like you are used to in Windows. [http://getdeb.net/](http://getdeb.net/) has a lot of Ubuntu programs. 

(To test it out, you can always get Opera. Get the 9.50b release: [http://www.opera.com/download/linux/](http://www.opera.com/download/linux/))

Not all sites have .deb's ready, and the most recent builds usually don't. You can get the source and build it yourself. Usually, there is a read me file in the archive, or the site explains it.

Windows doesn't have anything like a repository, but you can get the source and compile it for many Windows programs if you wanted. (GNU software of course) Windows makes it difficult to compile, and doesn't have the tools easily available like Linux.

---

### Post by PiggiePaul on 2008-02-16
> **LaRoza said:**
> The programs are in repositories. There are four repositories by default and they are not all enabled. 

The Add/Remove, Synaptic Package Manager, and the "apt-get" and "aptitude" commands get the packages from the same places.

The GUI's are just wrappers for apt-get.

Thanks, so those places you mention just get their progs(downloads) from the same place, hence there is no benefit in picking either place.

Just that the Add/Remove is a more "Pretty" front end, with ratings ect of (I guess) the more popular programs?

So, as a actual example:

I'm looking at downloading K9copy.

I can see it in Add/Remove programs (with no version number)
I can also see it in Synaptic Package Manager (version 1.1.3)

Selecting either of these would in effect produce exactly download on my system. Yes?

Or I can go to the K9copy website:
[http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)

And I see they have Sources up to 1.2.2 (I assume the source code you would need to build yourself - something I'm a million miles away from doing yet!)

I've seen that SOME websites do actually have self installing builds they have made (which seem great)
But I suppose the versions that you get from the add/remove and package manager have been built and tested and are stable. Even if they may not be the latest versions?

Is this kinda right, or have I got some things wrong?

---

### Post by LaRoza on 2008-02-16
> **PiggiePaul said:**
> Thanks, so those places you mention just get their progs(downloads) from the same place, hence there is no benefit in picking either place.

Just that the Add/Remove is a more "Pretty" front end, with ratings ect of (I guess) the more popular programs?

So, as a actual example:

I'm looking at downloading K9copy.

I can see it in Add/Remove programs (with no version number)
I can also see it in Synaptic Package Manager (version 1.1.3)

Selecting either of these would in effect produce exactly download on my system. Yes?

Or I can go to the K9copy website:
[http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)

And I see they have Sources up to 1.2.2 (I assume the source code you would need to build yourself - something I'm a million miles away from doing yet!)

I've seen that SOME websites do actually have self installing builds they have made (which seem great)
But I suppose the versions that you get from the add/remove and package manager have been built and tested and are stable. Even if they may not be the latest versions?

Is this kinda right, or have I got some things wrong?

Installing through Synaptic or Add/Remove or with the command:

```

sudo aptitude install k9copy

```

Would get the same thing from the same place.

You should always use the repositories when they are there, they are usually tested for the system, and are safe. 

Building it your self is not hard, it is just a couple commands that you don't need to understand. You just follow the directions usually.

You have it right.

---

### Post by billgoldberg on 2008-02-16
Synaptic is better because not all programs from the repositories get displayed in add/remove.

Also let's say you installed epiphany from add/remove, you just have the webbrowser.

If you search for it in synaptic you'll see that there are other epiphany related downloads like extentions.

In synaptic you can also easily add repositories.

Add/remove and synaptic (idem for apt-get and aptitude) only have programs that are tested and 100% compatible with your ubuntu version.

Add/remove and synaptic are a godsend if you need to download software because it eliminates "untrusted sites" and bogus programs and unwanted spyware/viruses (not that there are any linux viruses or spyware, but still).

---

### Post by seventhc on 2008-02-16
If you've downloaded k9copy, then assuming you opened it with archive manager, open a terminal and cd to that directory. 

If you saved it to your desktop then...
* cd Desktop/k9copy-1.2.2*

If you saved ut to your home directory then
* cd k9copy-1.2.2*
Once you do that, type
```

./configure
make
sudo make install

```That should do it.

---

### Post by PiggiePaul on 2008-02-16
> **LaRoza said:**
> 
Another way of getting sofware is too get a Debian installer, with the extension .deb. They are clickable installers, like you are used to in Windows. [http://getdeb.net/](http://getdeb.net/) has a lot of Ubuntu programs.

Excellent.

Just taken a look at that site and it looks superb.

Up-To-Date versions too :)

Any reasons NOT to get stuff from there for Ubuntu?

---

### Post by roaldz on 2008-02-16
Yeah, you´re kinda right. I recommend you to use Synaptic for package management. You seem smart, and so is Synaptic:) 
Synaptic also uses .deb´s, but it keeps lists with versions. Just go through Synaptic´s Repositories, you can enable them all.
Some sites (like winehq.com) offer own repositories. If you add these, you can stay up to date with their versions.
Repositories are managed in the file /etc/apt/sources.list
You don´t have to manually open the file, but it can give you an idea about what´s goin on

Good luck with ubuntu!

---

### Post by LaRoza on 2008-02-16
> **PiggiePaul said:**
> 
Any reasons NOT to get stuff from there for Ubuntu?

Not really, that site is really good.

The only other apps I use that I didn't get in the repositories or that site are Opera 9.50b and VirtualBox.

---

### Post by roaldz on 2008-02-16
> **PiggiePaul said:**
> Excellent.

Just taken a look at that site and it looks superb.

Up-To-Date versions too :)

Any reasons NOT to get stuff from there for Ubuntu?

Maybe they only offer a 32-bit build, while you´re running 64-bit. Doesn´t happen much.

---

### Post by PiggiePaul on 2008-02-16
Just wanted to say a big thanks to you all for explaining this.

From a new users point of view, unless you have someone sitting next to you to explain the basics, you could go for ages without actually understanding all the (apparently) different ways/places to get programs from.

Coming form Windows it does feel a but confusing at first.

I've just downloaded and installed the very latest K9copy from the "GetDeb" site, and very pleased.

Excellent area.

Just to give you a little background. Yes, I am very much a Linux Noob. Having been on various flavours of the dreaded windoze for many years.

Though before that. I did make my way thru a selection of other machines.
(off the top of my head)

Binatone Black/white pong game from Woolworths!
Atari VCS
Atari 800 48K Computer with Floppy Drive (The computer cost £650 plus £300 for the 96K drive!)
Commodore 64
Spectrum (mainly bought so I could get onto Prestel!)
Amstrad 6128
Yamaha MSX Music Computer.
Acorn Achimedes
Commodore Amiga 500

Then my 1st PC (25Mhz 486sx)

Next built my own PC (Pentium 200) and I bought 32MB of memory (two 16MB simms) for £520 !!!!!!!!!!!!!!!!! And that was a cheap deal !!!!

that £520 was just for the memory by the way!

So I've been around a bit :)

Though, even I will admit, my mind has been dulled a LOT over the past years by using Windows.

---

### Post by PiggiePaul on 2008-02-16
Oh yes, one other question:

Normally, (using Linux - Ubuntu in this instance of course) is it good/recommended practice to uninstall applications (using add/remove or package manager) BEFORE you install a newer version of the same program.

Or in Linux don't you have to go this, and the later app will cleanly go over the top of the older app?

---

### Post by LaRoza on 2008-02-16
> **PiggiePaul said:**
> Oh yes, one other question:

Normally, (using Linux - Ubuntu in this instance of course) is it good/recommended practice to uninstall applications (using add/remove or package manager) BEFORE you install a newer version of the same program.

Or in Linux don't you have to go this, and the later app will cleanly go over the top of the older app?

It is best to uninstall first.

---

### Post by PiggiePaul on 2008-02-16
> **LaRoza said:**
> It is best to uninstall first.

Thanks. I thought it would be (well, it is in windows) but wanted to make sure. :)

Just one more thing (whilst on this subject)

In Linux when you remove programs, do they get removed properly. Or (like Windows) do you get little bits left over all over the place even after uninstalling them?

(One of the worst aspects of windows)

---

### Post by seventhc on 2008-02-16
I think for certain apps, if you don't uninstall first you might even end up with both versions, not sure if thats a good thing or a bad thing.
In certain cases (Python for example) I've needed an older version before. That was only b/c I had a python program that should have worked but was giving me errors, so to test it out I installed an older version and the program did run then.
But for normal programs you should probably uninstall the older versions and just run the newest ones.

---

### Post by roaldz on 2008-02-16
> **PiggiePaul said:**
> Thanks. I thought it would be (well, it is in windows) but wanted to make sure. :)

Just one more thing (whilst on this subject)

In Linux when you remove programs, do they get removed properly. Or (like Windows) do you get little bits left over all over the place even after uninstalling them?

(One of the worst aspects of windows)

Certain parts stay, but most of them are config files, stored in your home directory (/home/<username>/). These files can´t do any harm to you system, because they are small, and are only opened by the program it belongs to.
In synaptic there is an option to completely remove something. This will probably remove these config files too.

---

### Post by yknivag on 2008-02-16
> **PiggiePaul said:**
> Oh yes, one other question:

Normally, (using Linux - Ubuntu in this instance of course) is it good/recommended practice to uninstall applications (using add/remove or package manager) BEFORE you install a newer version of the same program.

Or in Linux don't you have to go this, and the later app will cleanly go over the top of the older app?

It depends how you installed it.

If you used the respositories then the upgrades to the newer versions will happen automatically as and when they are available and apt deals with what needs to be removed and what doesn't.

If you installed from a .deb file or from source then read the readme from the new version - it will usually tell you how to go about upgrading and how to preserve any user configuration settings.

---

