---
title: "a concern about shutting the Windows for good"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by APendragon on 2006-01-07
I recently installed Ubuntu (downloaded version) onto a partition of my HP Pavilion ze 2000 laptop.  Had to tweak to get the display working, but the wireless and dialup are both still down.  I got good info here on getting the modem going but haven't had the time--I'm not linux-savvy and have a busy schedule.  If something else screws up I will probably bag the whole project.

Supposing I get Ubuntu working, what's to prevent me from being stuck with a version of Linux that gets abandoned due to all versions becoming standardized?  I really want to quit using Windows--FOREVER, I HATE Windows--but I am a writer who needs certain programs to work the same on my editor's Windows machine--like Word for instance, which isn't a perfect match with OpenOffice.  It doesn't seem to me that Linux is really keeping up with Windows products, and much as I love the idea of open source, I'm too busy to continually switch back and forth between two operating systems.

Comments very much appreciated.

---

### Post by Puptentacle on 2006-01-07
Even though I'm a newbie when it comes to Linux, I have an opinion on this. 

Windows programs can be run in Linux using wine so there shouldn't be any issue running MS Office under Ubuntu. 

As far as being stranded in a Linux OS...

I don't think you are in any danger of being left stranded by Ubuntu. The way the project and the people involved seem to be in it for the long haul. Even if Ubuntu were to dry up tomorrow the Linux kernel will still exist. The learning curve for a different Linux OS (once you have learned basic Linux operations) is rather small, certainly no worse than learning a new version of Winders. The basics are the same. 

That having been said I still haven't gone full Linux myself yet. I'm planning to in the future but I'm still so comfortable in Winders in comparison to Linux that I'm not quite ready to make a full switch yet. That day is coming, however.

---

### Post by Jammy_Stuff on 2006-01-07
What I'm doing when I get my new laptop on Monday night is have Ubuntu set up on it and then have Windows on a VM inside it. Set up host only networking and I'm good to go.

---

### Post by LoclynGrey on 2006-01-07
If you really hate windows then stop using it.
Start using Linux 100%, if you have trouble finding an windows equilvant then search 1st then ask on this forum or google it.
The only way to really learn the Linux OS way is to just use it.
Good luck, you are not alone hope to see your posts and new posts still going strong in 6 months time.:)

---

### Post by rubinstein on 2006-01-07
[QUOTE=APendragon][...]
Supposing I get Ubuntu working, what's to prevent me from being stuck with a version of Linux that gets abandoned due to all versions becoming standardized?  I really want to quit using Windows--FOREVER, I HATE Windows--but I am a writer who needs certain programs to work the same on my editor's Windows machine--like Word for instance, which isn't a perfect match with OpenOffice.  It doesn't seem to me that Linux is really keeping up with Windows products, and much as I love the idea of open source, I'm too busy to continually switch back and forth between two operating systems.
[/QUOTE]
Ubuntu is here for the long run, also the programs don't change; if you ever have the need to switch distributions, it's not that hard. But we hope you will stay with Ubuntu :-) .

If you REALLY need Windows programs to run under Ubuntu, you have some (commercial) choices.
If you only need Microsoft Office and a few other programs, then you can try wine [http://www.winehq.com/](http://www.winehq.com/) which is free software. You can look at the application database [http://appdb.winehq.org/](http://appdb.winehq.org/) to find out how good the program you want to run is supported. There is a commercial wine distribution which is called CrossOver Office at [http://www.codeweavers.com/](http://www.codeweavers.com/) . This is a supported version of wine which is more convenient and already configured to work best with the supported programs.

Another option is VMware [http://www.vmware.com/](http://www.vmware.com/) (which I use), which is a complete Windows System running on top of Linux/Ubuntu. It is rather expensive, but I can run almost every Windows application I need.


And another option is you change your workflow to OpenOffice.org (Have you read the documentation at [http://documentation.openoffice.org/manuals/index.html](http://documentation.openoffice.org/manuals/index.html) ? There is a full free book on Writer you can download) and your editor installs the Windows version of OpenOffice.org (which is also free). Even if he doesn't want to do it, OpenOffice.org has a very good compatibility with Word, so maybe that's good enough.

Remember: You don't have to make a fast switch.

Good luck and I hope this posting helps you a little bit...

---

### Post by newuser111 on 2006-01-07
[QUOTE=APendragon]I recently installed Ubuntu (downloaded version) onto a partition of my HP Pavilion ze 2000 laptop.  Had to tweak to get the display working, but the wireless and dialup are both still down.  I got good info here on getting the modem going but haven't had the time--I'm not linux-savvy and have a busy schedule.  If something else screws up I will probably bag the whole project.

Supposing I get Ubuntu working, what's to prevent me from being stuck with a version of Linux that gets abandoned due to all versions becoming standardized?  I really want to quit using Windows--FOREVER, I HATE Windows--but I am a writer who needs certain programs to work the same on my editor's Windows machine--like Word for instance, which isn't a perfect match with OpenOffice.  It doesn't seem to me that Linux is really keeping up with Windows products, and much as I love the idea of open source, I'm too busy to continually switch back and forth between two operating systems.

Comments very much appreciated.[/QUOTE]

I've noticed abiword is better at reading MS word documents than openoffice

or just install microsoft word in wine, i believe it should work

---

### Post by kairu0 on 2006-01-07
[QUOTE=APendragon]Supposing I get Ubuntu working, what's to prevent me from being stuck with a version of Linux that gets abandoned due to all versions becoming standardized?[/QUOTE]

I'm going to partially plagarize Richard Stallman by saying that your concern is backward-oriented. Rather than fearing that Linux is abandoned by becoming standarized, fear that the Windows version is the one that will get abandoned. Open source is here, it is strong, and the beauty of it is that it is open.

When one developer stops developing or one format stops being supported, others can pick up the torch by using their open code. In the Windows world, when X program gets abandoned and Y program that was providing a software compatible with X files goes out of business, you are out of luck.

With Microsoft's exodus from the old-school .DOC format to XML, for example, the Microsoft team demonstrates itself that open source is not being abandoned but rather gathering speed.

---

### Post by Lord Illidan on 2006-01-07
[quote=newuser111]I've noticed abiword is better at reading MS word documents than openoffice

or just install microsoft word in wine, i believe it should work[/quote]

Or use Crossover Office. I have installed the trial version and I am impressed with MS Office 2003's support! Seems excellent.

---

### Post by APendragon on 2006-01-07
All these replies (except "just use it") were helpful.  One other question:  if ubuntu overhauls itself, even comes out in a new version, which I understand is on the way, then will it be possible to install without losing the old data?  Thx

---

### Post by Estariel on 2006-01-07
yes!
updating from one ubuntu version to its successor is very easy, won't touch your data and won't (as opposed to windows upgrades between major versions) mess up your system.

All you do is edit the file /etc/apt/sources.list and exchange all appearances of the word "breezy" with "dapper"
Then do a dist-upgrade (e.g. with synaptic) and you are done. apt is such a nice tool :)

Edit: Don't do that NOW! Dapper is not yet ready for use on a end-user machine. I keep it around on a second box to play with it, but twice a week something breaks... And you probably don't want that...

---

### Post by aysiu on 2006-01-07
[QUOTE=APendragon]All these replies (except "just use it") were helpful.  One other question:  if ubuntu overhauls itself, even comes out in a new version, which I understand is on the way, then will it be possible to install without losing the old data?  Thx[/QUOTE] If you have a separate /home partition, yes.

---

### Post by Estariel on 2006-01-07
[QUOTE=APendragon](...) It doesn't seem to me that Linux is really keeping up with Windows products (...)[/QUOTE]

I disagree. In my opinion, the only problem is that most people keep looking at the world through Microsoft's eyes...
Let's take a word processor (like MS WORD) as an example. You probably use it, since you haven't used anything else. As a professional writer, you have probably noticed that Word tends to badly mess up complex documents. The largest thing I tried to write using Word was my thesis at the end of highschool (we have such a thing in germany...) and Word kept messing up my enumeration and my styles. It was a real mess. 
In undergrad school, I started using Linux, and learned about Latex (which is a professional typesetting program). I have written all protocols, essays, papers, etc. using LyX (which is a nice front-end to Latex). It is available in the repositories, so try it out.

Of course there is still the problem that your editor expects a Word document, and Latex won't produce anything like that. This is of course a problem, but I wanted to point out that there exist great programs in the open source world, for which Microsoft doesn't have any equivalent.

I use 100% linux, and I am a lot more productive on this system than on a Windows box. It would take a lot of time and effort to get all the tools I need to run on Windows (but it would probably be possible. Just as it is possible to run Word on Linux by using WINE).

---

### Post by Estariel on 2006-01-07
[QUOTE=aysiu]If you have a separate /home partition, yes.[/QUOTE]
Why would he need a separate home partition? All he needs is a dist-upgrade... ?!

---

### Post by yustabeme on 2006-01-07
[QUOTE=rubinstein]
Another option is VMware [http://www.vmware.com/](http://www.vmware.com/) (which I use), which is a complete Windows System running on top of Linux/Ubuntu. It is rather expensive, but I can run almost every Windows application I need.
[/QUOTE]

vmplayer is now free.

[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

I've used the trial version of VMware workstation to create a WinXP-pro vm in Kubuntu, as well as a Win98 Se vm.

[http://www.vmware.com/download/ws/eval.html](http://www.vmware.com/download/ws/eval.html)

After the trial period (30 days) the vm will work with the free player. Also, there are a few third party efforts afoot for creating vm's without the need for purchasing anything, and VMware seems to be actively
encouraging this. Here are a few links:

[http://hackaday.com/entry/1234000153064739/](http://hackaday.com/entry/1234000153064739/)

[http://petruska.stardock.net/software/Vmware/index.html](http://petruska.stardock.net/software/Vmware/index.html) parrticularly the VMX Builder at the bottom looks promising, but I'll have to boot to  XP to give it a try...

[http://fabrice.bellard.free.fr/qemu/download.html](http://fabrice.bellard.free.fr/qemu/download.html)

---

### Post by aysiu on 2006-01-07
[QUOTE=Estariel]Why would he need a separate home partition? All he needs is a dist-upgrade... ?![/QUOTE] This part of the original post made me think the OP was concerned about some kind of major change in Ubuntu beyond just the regular six-month releases: > Supposing I get Ubuntu working, what's to prevent me from being stuck with a version of Linux that gets abandoned due to all versions becoming standardized? Regardless, dist-upgrades do not always work (sadly), so sometimes a fresh re-install is the only way to go, in which case, a separate /home partition comes in handy.

---

