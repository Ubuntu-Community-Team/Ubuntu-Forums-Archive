---
title: "Ubuntu on apple computers needs your help!"
date: 2008-07-29
forum: Apple Hardware Users
---

### Post by kdb424 on 2008-07-29
Ok. I realize that this issue has been brought up many times. What are the 2 first questions that people ask on these forums? Usually "Will Ubuntu run on a Mac?" and "Where do I find drivers?". I know some people that love Ubuntu on a desktop, but would never attempt it on a mac, because of all of the extra crap that they have to go through. Trackpad drivers, wifi, and other things. I propose that we change that. Apple drivers, like the hardware, is pretty much like other hardware. So what does that mean? Apple drivers will work with non apple computers because they work the same.

I think that the mac installer should have a Mac/PC option in the installer. It would automatically select a mac version of any keyboard that they pick, if available, install the wifi drivers, if they have wireless, and set up the trackpad.

One of my issues, is my house has run out of the 3 ethernet ports, and this being a laptop, is wireless. If it was a wireless desktop, that would be worse. I have to get an ethernet port off of another computer, and plug it in, possibly having to get feet of cable if it was a desktop located farther away. Some routers are wireless only. What would they do?

My point is that we need some increased support for Apple computers. Others argue that it won't increase apple users to come to linux, but most people are afraid that they have to install a ton of junk, and do all kinds of special things. If full apple support was added, people could use bootcamp, or manually partition knowing that it will be as easy as windows.

Please support this idea! I am glad that I triplebooted, and want others to know it's as easy as a PC!

[http://brainstorm.ubuntu.com/idea/11357/](http://brainstorm.ubuntu.com/idea/11357/)

---

### Post by cyberdork33 on 2008-07-29
> **kdb424 said:**
> Ok. I realize that this issue has been brought up many times. What are the 2 first questions that people ask on these forums? Usually "Will Ubuntu run on a Mac?" and "Where do I find drivers?". I know some people that love Ubuntu on a desktop, but would never attempt it on a mac, because of all of the extra crap that they have to go through. Trackpad drivers, wifi, and other things. I propose that we change that. Apple drivers, like the hardware, is pretty much like other hardware. So what does that mean? Apple drivers will work with non apple computers because they work the same.

I think that the mac installer should have a Mac/PC option in the installer. It would automatically select a mac version of any keyboard that they pick, if available, install the wifi drivers, if they have wireless, and set up the trackpad.

While I really like what you are saying and I am all for promoting and improving Ubuntu on the Mac, there are a few problems. 

At the end of your first paragraph, generally it is the case that (now) Apple hardware is the same as other PC hardware, but Apple tends to customize firmware and do little things different here and there so that often a driver made for the hardware on a PC does not completely work on a Mac the same way. Take for example the sound hardware on Macbook Pros. This is a standard chipset, but requires special code (which was patched onto the original driver to be compatible with the Mac) to map things correctly which is activating by passing an option to the kernel when the module is loaded. Something like this would be easy to "fix" if you knew you were only distributing to mactel machines.

Secondly, the idea of the installer is to cover as many bases as possible. One installer can work on a multitude of PCs, including Macs. If they could create the base Ubuntu system to be better compatible with Macs, then they would (In fact, you can see how this has already been done. Initially Linux on Intel Macs was a nightmare. Now, a Mac Mini can pretty much work out of the box.) It just takes time. This improvement is made by users contributing patches, making suggestions for new packages, and developing tools and drivers for new hardware. It takes time, but these have been making it into Ubuntu.

> **kdb424 said:**
> One of my issues, is my house has run out of the 3 ethernet ports, and this being a laptop, is wireless. If it was a wireless desktop, that would be worse. I have to get an ethernet port off of another computer, and plug it in, possibly having to get feet of cable if it was a desktop located farther away. Some routers are wireless only. What would they do? The WiFi issue with Macs is a WiFi issue for all of Ubuntu. You will have this same problem with PCs using the same hardware. The current madwifi driver does not yet support the chipsets in the Macs, and we all know that Broadcom has never been linux friendly, and that pretty much ANY broadcom WiFi card on any PC requires some kind of download (firmware or Windows drivers) to get working under linux. Atheros support is coming, eventually. We can get the cards working with a development snapshot, but they would not include such a thing in Ubuntu because it is not a stable release. Broadcom may never be supported out of the box due to legal issues.

> **kdb424 said:**
> My point is that we need some increased support for Apple computers. Others argue that it won't increase apple users to come to linux, but most people are afraid that they have to install a ton of junk, and do all kinds of special things. If full apple support was added, people could use bootcamp, or manually partition knowing that it will be as easy as windows.

Please support this idea! I am glad that I triplebooted, and want others to know it's as easy as a PC!

[http://brainstorm.ubuntu.com/idea/11357/](http://brainstorm.ubuntu.com/idea/11357/)

As you can see your idea has already been proposed. In fact, several people work everyday on increasing support for Apple hardware in Ubuntu. It also doesn't help that most of the typical Linux users shun Apple Users, but there are many Apple-friendly developers and Linux-users out there. Ubuntu is actually one of the most Apple-friendly distributions likely due to the hard work of the large community of Apple-Users here.

One of the easiest things that you can do to better Apple Hardware support is to file bugs and help developers fix issues. For Ubuntu, this is done in Launchpad. If there is a specific problem that you have with Ubuntu, file a bug and state your experience / solution. Be sure to search for an existing bug first!

You might also like to join the [mactel-support community]("https://launchpad.net/%7Emactel-support-community"), if you have programming expertise, the [mactel-support]("https://launchpad.net/%7Emactel-support") team.

Your other option is to start with gobuntu or something, and start your own branch of Ubuntu with better support for Apple hardware... However, you will still be limited on including certain proprietary drivers on the install.

---

### Post by stream303 on 2008-07-29
> **cyberdork33 said:**
> It also doesn't help that most of the typical Linux users shun Apple Users, but there are many Apple-friendly developers and Linux-users out there.

I agree with you there.  Small rant ahead, and is not aimed at anyone here:

I'm sad to see that a lot of the FUD concerning a user's choice of using Apple hardware comes from within our own Linux community.  They don't seem to be happy that we are using Linux in any fashion, unless it conforms to their own open-source marketing (yes, marketing!) agenda.  Ok, ppc has gone somewhat specialized, but even with Intel-Macs, it seems that architecture has nothing to do with the FUD.

The key issue is to stay focused on support, and not get easily sidelined with Apple marketing/politics issues.

The reason I use an Apple, whether it is purchased new, used, or received as a gift, is my own business.  Politics has nothing to do with it.

I read too many FUD threads about Apple users, and ironically the very same complaints about elitism are mirrored right back on the poster trying to foster isolation and calling into question a person's financial status.  It is immaterial.

Sure I wish I could afford the latest and greatest, but I buy used when I need to - still immaterial really when it comes to support.

Sorry - had to get that off my chest in the hopes that we can break the alarming trend of non-apple users trying to isolate us into us-and-them.  Fortunately, that isn't happening here.

---

### Post by cyberdork33 on 2008-07-29
> **stream303 said:**
> I'm sad to see that a lot of the FUD concerning a user's choice of using Apple hardware comes from within our own Linux community.  
...
I read too many FUD threads about Apple users, and ironically the very same complaints about elitism are mirrored right back on the poster trying to foster isolation and calling into question a person's financial status.  It is immaterial.

Basic responses:

[LIST=1]
[*]Nobody with a Mac wants to / is able to run Linux. (i.e. low priority)
[*]Macs are expensive. (IDK why that matters, whether it is true or not)
[*]Mac users are elitist / egocentric / complain too much
[*]OSX already has GCC / X11 / other *nix tools
[/LIST]
Thanks Linux community!

---

### Post by kdb424 on 2008-07-29
I do agree with everything that was said. When I said 2 installers, I wasn't asking for two different downloads, but one that would give you the option to choose at the beginning, that would help choose better drivers, and tweak things like the trackpad. I do understand these issues, and I realize that a lot of the apple community is big on, "Oh Mac is way better!", but I've gotten many people around here to install Ubuntu, 2 of the computers Apple. The things that I think should be included when you choose mac in the installer is any drivers that we currently have, or have mac specific tweaks, and things like the apple remote support, motion sensors, iSight camera, things like pommed, and the sound tweaks if needed. This would make the overall experience even better, and all of the information is available on the wiki, so why can't we put this in the installer under a mac option? Ubuntu is my favorite distro of linux. I am running an Ubuntu server right now, and have an Ubuntu PC, and an Ubuntu install in this Mac I'm on now. I will do m best to support it however I can, and as soon as the cash starts flowing, I'll be donating right to Ubuntu.

---

### Post by cyberdork33 on 2008-07-29
apple remote support - already included (for many systems anyway), 
motion sensors - part of the kernel already, 
iSight camera - cannot include propritary firmware from OSX, 
pommed - already in the repos

> This would make the overall experience even better, and all of the information is available on the wiki, so why can't we put this in the installer under a mac option?
If you start having custom installs for Macs, then you have to custom install for other hardware types as well.

Tweaking the touchpad is not the same for your Mac as another, and defintely not the same as for a Dell. A basic setup is included and that is the default for ALL touchpads. Everyone wants to tweak it for their machine. 

However, creating a "package" that someone could install that would apply many fixes at once would be possible.

---

### Post by hanzomon4 on 2008-07-29
I support the basic idea. I love my Macbook Pro and Ubuntu rocks on it... but it trips and falls hard. No sound after resume from suspend/hibernate or total lockups, losing wireless... For a laptop these issues are show stoppers. Slowly it does get better and I can wait. When I can install Ubuntu on any hardware and not have to follow howtos to get basic things to work or tragic things to stop working will be a great day.

---

### Post by stream303 on 2008-07-29
Is there such a thing as DSDT tables for the Intel Macs?  Makes me wonder if some of the acpi stuff needs to be told it is windows and not linux, etc??

I'm not a hardware guy, so I have no idea if this is even applicable to Intel Macs..

---

### Post by cyberdork33 on 2008-07-29
> **stream303 said:**
> Is there such a thing as DSDT tables for the Intel Macs?  Makes me wonder if some of the acpi stuff needs to be told it is windows and not linux, etc??

I'm not a hardware guy, so I have no idea if this is even applicable to Intel Macs..
Yea, although we do not have a literal BIOS...

I checked mine out. Suprisingly, it compiles with absolutely no errors or warnings whatsoever. There was one if statement that did something for "Darwin" and something else for "Linux". It didn't look suspicious. But if the Kernel reports itself as Windows to ACPI then that wouldn't matter anyway.

There are several modules that do not reload properly after suspend currently. I think that they are just bugs, or something weird that Macs do a bit differently. This is definitely something that needs attention though. There are a couple of bug reports that have zero action on them.

Also, for wireless, the ath9k driver was recently released. This is the new open source atheros driver (that atheros has been helping develop) and should support the AR5008 cards that these Macs have.

---

### Post by DarchAengel on 2008-07-29
Just throwing my change at the idea...I would like to try that.  I have a dual hard drive G4 and I built a PC for my gf with Ubuntu.  I'm more comp savvy than she is but but since I don't know her comp that well it makes for difficult troubleshooting.  If I were able to install and delete different distros I could play around and be able to understand more what it is I gave her.  But it would have to either be a partition on my main drive or be able to install on my second drive since I can't afford to give up OSX.

---

