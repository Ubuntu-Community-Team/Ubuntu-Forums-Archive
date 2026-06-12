---
title: "How to maintain a current sytem without breaking everything"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by sddfdds on 2006-10-28
I suppose this isn't the best time for a question like this, with Edgy Eft having just released with, among other things, Firefox 2.0 and Gaim 2.0.0b3.1.

Basically my question is, how do you keep up-to-date with current general-use software that won't necessarily get put into packages.  In many cases, your only option would be upgrading to Feisty Fawn or compiling yourself, both of which can be dangerous for a novice.

I don't want to ramble on giving 1000 examples, but one example to work off of: Gaim.  Currently, you can get beta3.1.  But what if I want beta4.  Or beta5 when it comes out.  Or 2.0.0 final?

Or something like Azureus, when it updates.  Maybe there aren't any security-critical fixes that warrant a new official package, but maybe there are new features that users may want but can't get because they don't want to break their system by going outside the default method of apt-getting their current release's repos.

Thanks for any input.

---

### Post by MethodOne on 2006-10-29
For Azureus upgrades, you can try downloading the jar file from [http://azureus.sourceforge.net](http://azureus.sourceforge.net), saving it to your home directory,  and running the following command in the terminal:

```
sudo cp Azureus(version you downloaded).jar /usr/share/java/Azureus2.jar
```

For Gaim 2.0 beta 4, you can find it [here](http://www.ubuntuforums.org/showthread.php?t=280739&highlight=GAIM)

---

### Post by thk on 2006-10-29
Dual boot Ubuntu. Keep you last best setup in one partition and upgrade the other. Keep /home on a separate partition. I learned this from running Gentoo which breaks constantly. When your new setup becomes stable switch to upgrading your old stable partition.

---

### Post by bsussman on 2006-10-29
> **thk said:**
> Keep /home on a separate partition. I learned this from running Gentoo which breaks constantly. 

Generally a great way to use multiple versions.

BUT

As I am finding out with firefox 1.5 versus 2.0, this method can lead to some interesting difficulties - when I go back to my 6.06 system, the state of extensions that ff determined to be incompatible in 2.0 get screwed up!

Some minor kde breakagew occurred as well.

Be careful - flipping back and forth can cause small annoyances (and probably some big ones too :mrgreen:).

---

### Post by CatKiller on 2006-10-29
You could always ask the backports project people to backport later versions of the software you use. That **is** what they do, as I understand it.

---

### Post by sddfdds on 2006-10-31
Thanks for the replies.  These are all good suggestions, but I guess more what I am wondering is, why isn't it easier?  I don't want to start a slippery slope of unreasonable expectations, but it seems like one thing you'd expect from a desktop system is current software.  I hate to make this comparison, but take Windows for example.  My 3 examples, Azureus, Firefox, and Gaim, their current versions can very easily be downloaded and had for Windows.

---

### Post by CatKiller on 2006-10-31
> **sddfdds said:**
> I hate to make this comparison, but take Windows for example.  My 3 examples, Azureus, Firefox, and Gaim, their current versions can very easily be downloaded and had for Windows.

Since we're making crazy comparisons, how easy will it be to install IE7 in Windows 2000? All of the examples you gave can be downloaded and had for Dapper. And for any open-source project, you can use the compiler that came on the cd to make it for your platform, which is far more than you can say for Windows, which only works at all on one platform. And if you want to compile it from source, you can use checkinstall to integrate your new software with your package management system, to easily handle updates. How do you do that in Windows, again?

---

### Post by sddfdds on 2006-11-02
People don't want to compile their own software, that's my point.  They just want to download the exe (apt-get the deb/use synaptic) and run it and be done with it.

Also re: IE7, yes it isn't available for Win2K, because it's "old."  XP is considered the "current version" (Edgy) and then Vista is in beta (Feisty).  Though I wouldn't necessarily put dapper in the same boat as win2k because of the whole LTS thing.  Either way though, anyone using dapper cannot easily get Firefox 2.0 if they wanted it.

As far as edgy goes, it's current now because it's new, but what happens when theres a Firefox 2.1, or an Azureus 2.5.0.2, or a Gaim 2.0final or a 2.0.1 update after that?

---

### Post by CatKiller on 2006-11-02
> **sddfdds said:**
> People don't want to compile their own software, that's my point.  They just want to download the exe (apt-get the deb/use synaptic) and run it and be done with it.

Says who? That's not what I want. It's not even what my elderly mother wants. So how can you possibly be speaking for "people"?

People will get security updates and bug-fixes for the software that comes with their distribution. This will be supported for several years. If they **choose** to install **new** software then they have a number of different methods by which to do so. **Someone** has to compile any piece of software, but it doesn't have to be the user. They could ask a friend to do it or, if their platform is popular enough, the developers may do it for them. Some kind soul may host a repository for the project, as is the case with Wine. How is any of this Ubuntu's problem, again? Hell, if you think that "the people" are so desperate for bleeding edge rather than support, you are perfectly free to make your own distribution based on Ubuntu but with the latest and greatest packages available. Anyone is, and some already have.

> Also re: IE7, yes it isn't available for Win2K, because it's "old."  XP is considered the "current version" (Edgy) and then Vista is in beta (Feisty).  Though I wouldn't necessarily put dapper in the same boat as win2k because of the whole LTS thing.

As I said, we're making crazy comparisons. Any way, the current version isn't really Edgy. Edgy is for people that want new software for the sake of having new software. Which is you, apparently. Feisty is for those who want to help the community by beta testing software.

> Either way though, anyone using dapper cannot easily get Firefox 2.0 if they wanted it.

That is simply not true. There's even a script that will automatically download the latest source, compile it and install it for you. How many steps does that save you compared to your Windows-using brethren?

> As far as edgy goes, it's current now because it's new, but what happens when theres a Firefox 2.1, or an Azureus 2.5.0.2, or a Gaim 2.0final or a 2.0.1 update after that?

If these versions contain security or bug fixes, these fixes will be made available automatically. Otherwise, the user is perfectly free to install the software themselves. I'm really not sure what the problem with this is.

---

### Post by arsenik on 2006-11-02
I understand his point. I'm new to ubuntu and it's not easy to install new software.  This whole compiling thing has me baffled.  So how would i compile the new firefox on dapper if i wanted to?

---

### Post by CatKiller on 2006-11-02
> **arsenik said:**
> I understand his point. I'm new to ubuntu and it's not easy to install new software.  This whole compiling thing has me baffled.  So how would i compile the new firefox on dapper if i wanted to?

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by thk on 2006-11-22
> **bsussman said:**
> Generally a great way to use multiple versions.

BUT

As I am finding out with firefox 1.5 versus 2.0, this method can lead to some interesting difficulties - when I go back to my 6.06 system, the state of extensions that ff determined to be incompatible in 2.0 get screwed up!

Some minor kde breakagew occurred as well.

Be careful - flipping back and forth can cause small annoyances (and probably some big ones too :mrgreen:).

I've run into these issue as well. You can keep separate /home directories only for config information and keep your non-config files on a separate partition eg. /myfiles

---

### Post by bodhi.zazen on 2006-11-22
> **thk said:**
> I've run into these issue as well. You can keep separate /home directories only for config information and keep your non-config files on a separate partition eg. /myfiles

[Data partition](http://ubuntuforums.org/showthread.php?t=300246) See Posts # 10 and 13

Here is how I stay current:

I have two partitions, testing and production.

Each has it's own /home for configuration files as thk is asking.

Now install and configure Ubuntu the way you like in the Production partition.

Next boot the [Gparted CD](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828) and copy the production partition to the testing partition.

Add an entry for testing in /boot/grub/menu.lst

Boot and update testing to your hearts content. If you break it, oh well, just re-copy from the Gpatrted live CD.

But if you like it, boot the Gparted cd and copy testing to production.

---

### Post by mgmiller on 2006-11-22
I think we may all be missing his point.  He is trying to keep installing newer versions of software.  You don't really have to.  Once it's installed through apt, any bug fixes or security updates are handled automatically.  Since the entire operating system updates every 6 months or so, this is where you pick up the newest versions of software.  Unless, as others have noted earlier, you want to install newer versions ahead of time, (like Firefox 2.0)  I personally didn't bother, my Dapper 6.06 updated to the latest FF 1.5.0.8 for security purposes and then when I updated to Edgy, I got the newest 2.0 version.  The lag between availability and my using it in Edgy was about a month, and I waited about 3 weeks after the release date to update.  Slow down and take the time to smell the flowers, you are getting a whole new OS every 6 months or so. For free.  Enjoy it.

PS:
I know some folks just have to be "bleeding edge" with their software, if that's the case, with minimal work, you can usually do  so, as many of the previous posters pointed out.

---

### Post by JPMaximilian on 2007-01-06
> **arsenik said:**
> I understand his point. I'm new to ubuntu and it's not easy to install new software.  This whole compiling thing has me baffled.  So how would i compile the new firefox on dapper if i wanted to?

I think that installed new software is *easier* in Ubuntu than in XP, or even OS X as long as the app is in synaptic.  If there is a .deb. installing the app is about the same as XP, OS X, if not though, it is harder.

---

