---
title: "Problem after upgrade to 3.8"
date: 2013-04-26
forum: Any Other OS
---

### Post by kevdog on 2013-04-26
Arch linux decision to upgrade from 3.6 to 3.8 really through me for a loop.  It destroyed use of the cinnamon desktop, it wouldn't boot (likely because of certain installed packages from the AUR), and to the best of my knowledge the new gdm (Gnome display manager for 3.8) is still broken.  This all happened when pacman asked me to upgrade libsoup and I said yes -- I had no idea this was going to pull down the new version of Gnome.  Suffice to say, despite trying to spend hours rolling back the installation of packages, I couldn't get the system to startx.  I later installed SLIM and then later installed LXDE and then later KDE.   Despite not wanting to, I basically deleted all the cinnamon settings and such, and totally uninstalled gnome and removed as many libraries as I could.  I then reinstalled gnome, and finally the system booted. Needless to say the Arch forums were not too friendly offering assistance, despite the numerous threads that were similar to mine.  A few users through their posts point me in the correct direction.  

Needless to say, I got Gnome3 finally booted and running, however in the process I discovered how good KDE was -- one desktop I haven't used in years (like 6-7 years).  It's come a long way since 2007 -- a long way.  After seeing the generic Gnome3, I think I might just stick with KDE and running the plasmoids for awhile.  Wasn't so totally blown out of the water by LXDE, but in truth I used to run an open box setup years ago, and I'm aware OpenBox needs a lot of luv by the indivdual user before you could call it home.

I see posts asking whether the next release of Ubuntu (13.10) should run Gnome 3.8 vs 3.6.  After seeing 3.8, I'd have to vote with just sticking with 3.6 and let the kinks be worked out.

---

### Post by kevinmchapman on 2013-04-27
So, in short, Arch's decision to upgrade Gnome from 3.6 to 3.8 broke a third party desktop (Cinnamon). You couldn't boot "likely because of certain installed packages from the AUR" (unsupported packages that you installed), and therefore you conclude that Ubuntu should not include 3.8?

Interesting "logic".

In the interest of balance, vanilla Gnome 3.8 and GDM working fine here.

---

### Post by kevdog on 2013-04-27
Must be response from arch forum member. Cinnamon aside does Gnome 3.8 really work for you? Its extremely laggy and gdm for me is still broke. I'm still using slim here. And if you discount my experience, there are many other similar posts made by various other users that report similar and other such issues. I'm glad it works great for you, however discounting other users problems just because it works for you is rather petulant don't you think?  I'm still looking for performance solutions which are slowly trickling in on the arch forum website.  Arch is a bleeding edge distro so I'm describing some of the problems associated with this type of installation. Ubuntu isn't quite so bleeding edge. I could only imagine if something similar were to effect Ubuntu users. These forums would be even more chaotic.

---

### Post by kevinmchapman on 2013-04-27
> **kevdog said:**
> discounting other users problems just because it works for you is rather petulant don't you think?

I dismissed your problems because, in your own post, you suggest Cinnamon and AUR were at fault.

> **kevdog said:**
> Needless to say, I got Gnome3 finally booted and running, however in the process I discovered how good KDE was -- one desktop I haven't used in years (like 6-7 years). It's come a long way since 2007 -- a long way. After seeing the generic Gnome3, I think I might just stick with KDE and running the plasmoids for awhile. Wasn't so totally blown out of the water by LXDE, but in truth I used to run an open box setup years ago, and I'm aware OpenBox needs a lot of luv by the indivdual user before you could call it home.

At no point do you state that the re-installed Gnome is not working, just that you dislike it.

I have certainly seen some posts on the Arch forums, so 3.8 is not without issue. For me, both GDM and Gnome work as well as ever, except for the usual requirement to increment version numbers in extensions and the ever-present memory leak which sees memory usage gradually increase (no practical impact, but visible if I open a task manager).

---

### Post by kevdog on 2013-04-27
So just to some up -- if you had to tell all Ubuntu users to manually increment version numbers in gnome 3 extensions -- that would be a problem.  A memory link is always a problem eventually. Hopefully they will fix gnome3 since I'm a gnome user (although I really am liking the kde stuff right now). As far as the AUR -- I've got mixed feelings about the AUR.  They are unsupported packages -- so they are unsupported.  The problem however is that at least for me, I have to install a lot of packages that are in the AUR b/c they aren't in the main repositories.  AUR packages can lead to breakage with updates as just witnessed, so its a lot of manual labor keeping track of things.  This is definitely the arch way, however I'm not sure this is the Ubuntu way.  I guess Ubuntu has much the same problem with ppa's, but in my experience the ppas don't seem to cause as many potential problems.  Maybe other users experiences are different.  So to some it up, I'm still of the opinion 3.6 should be the default gnome3 install version for Saucy Salamander.  Things will definitely change in the next 6 months, so I'll probably change my opinion sometime in the future.

---

### Post by mips on 2013-04-27
> **kevdog said:**
> AUR packages can lead to breakage with updates as just witnessed, so its a lot of manual labor keeping track of things.  This is definitely the arch way, however I'm not sure this is the Ubuntu way.  I guess Ubuntu has much the same problem with ppa's, but in my experience the ppas don't seem to cause as many potential problems.

PPA a dev can build a package for Ubuntu 12.10 for example and it should remain stable as long as 12.10 is around.
AUR packages have to be continually updated to keep up with the rolling nature of Arch.

Two different beasts.

---

### Post by kevinmchapman on 2013-04-27
To sum up from my end :) you believe that Gome 3.6 should be the default in future Ubuntu releases, and you have some issues with Cinnamon and AUR, neither of which are present in Ubuntu, and I'm struggling to see a connection...

---

### Post by kevdog on 2013-04-27
You should be a lawyer since you like to miscontrue statements that others make -- go back and re-read the original post.  There is a debate about including either 3.6 or 3.8 with the next Ubuntu release.  I stated I feel they should stick with 3.6 for the next release SS.  And as far as statements with some issues with Cinnamon and the AUR -- yes I have them, however I (and many others) have issues with the currently supported 3.8 Gnome release from the officially supported repository as well.

---

### Post by kevinmchapman on 2013-04-28
In two paragraphs of the original post, I filtered out the following pertinent surmisal.

> **kevdog said:**
> to the best of my knowledge the new gdm (Gnome display manager for 3.8) is still broken. 

On that basis, then, 3.8 is not ready for use in the future? I'm not interested in the defensive statements, just the facts

---

### Post by trent.josephsen on 2013-04-28
You seem to be under the impression that problems with 3.8 on Arch will be problems with 3.8 on Ubuntu. That, to me, seems to be a completely unwarranted assumption without which your argument falls completely apart. Yes, they come from the same upstream, but Arch brings in the upstream essentially vanilla, whereas Ubuntu does more thorough integration testing and patching to make sure it works with every other package. Even just the compilation options can make a big difference.

If it was crashing regularly, or running the CPU to 100% while idle, or something like that, and it was a bug that was clearly in upstream and not related to any unsupported packages you installed on the side, that might be one thing; but it seems to me all your issues might be fixed by better integration testing and a few minor patches. Which might even be *less* work than what's necessary to stay on 3.6; I don't know.

---

### Post by mamamia88 on 2013-04-28
The AUR is a user repository that has packages that aren't maintained by the main arch developers.  Cinnamon is an offshoot of gnome and has a crap load of stuff that is interconnected to gnome.    If gnome got updated and cinnamon hasn't caught up yet then yeah your are bound to have problems.   I'm sorry but it's more of a dependency getting updated prior to the dependent package catching up.  There really is nobody to blame in this case.    The arch devs don't care if an official update breaks an unsupported package.

---

### Post by codingman on 2013-04-28
Hey kevdog, try using CDM, I had a problem with using i3 after the upgrade to 3.8 GNOME, so I quit using GDM and am now using CDM without disruption between my WM's. I don't think that this is due to packages in the AUR, as I have plenty of AUR packages installed. 

@kevin , why do you need to "sum things up"? It rather sums things down for everyone focused on the content.

---

### Post by trent.josephsen on 2013-04-28
I think OP's point was that the package is itself broken, not just that it breaks AUR packages. Although I don't have enough information to determine whether kevdog's issues were caused by his configuration or a buggy package, it would not surprise me to find that Arch's 3.8 package is not all that stable; that just goes back to what I was saying about integration testing. Arch is bleeding edge and breakages happen from time to time. Most such problems are fixed long before they make it into mainstream distros like Ubuntu. (It's possible to reduce the risk by avoiding AUR packages, but it does still happen. I wasn't affected by the recent update because I use XFCE without a display manager, but I see other problems pop up occasionally; usually they're minor and I ignore them until the next update fixes them. In a similar situation to the OP it's likely I would have just switched to openbox for a while.)

---

