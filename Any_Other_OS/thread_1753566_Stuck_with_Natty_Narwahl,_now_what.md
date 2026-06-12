---
title: "Stuck with Natty Narwahl, now what?"
date: 2011-05-09
forum: Any Other OS
---

### Post by azupan on 2011-05-09
Here's my story: I've been using Windows for more than 15 years. A little more than 6 months ago, I bought a new PC, and dedicated an empty disk partition to Ubuntu, to try it out. About 3 months ago, I started to learn PHP, and decided to do LAMP stuff on Ubuntu. I had no mentionable problems installing and configuring it, until about 2 weeks ago. The window inviting me to install 11.4 popped up all of the sudden, and I said "Yeah, OK, why not", and clicked 'Yes'".
 

I think Unity is a good idea, and I like it enough to cope with small annoyances which always come with new versions. After tinkering with Compiz cube & stuff for a while I got back to work, and discovered, that dragging a Netbeans menu, window, or pane breaks the desktop. Things return to normal only after I exit Netbeans and Firefox ([http://ubuntuforums.org/showthread.php?t=1753180](http://ubuntuforums.org/showthread.php?t=1753180)). Since it's pretty much impossible to get anything done this way, I'm forced to consider other options:[LIST=1]
[*]Using "Classic Ubuntu" hoping that Netbeans issues will be eventually fixed. I'm not sure what Canonical's current plans are, though.
[*]Switching to another distro, maybe Debian or something.
[*]Switching back to Windows, from LAMP to WAMP.
[/LIST]I'd be very grateful for any advice. Before all, I'd like to know what Canonical's strategy is. If they target the mass market, they might need to dumb down things a little bit, make them less configurable, and more average user friendly. Developer usability might become a permanent collateral damage in the process. If this is the case, I'll have to switch to another distro or back to Windows, the sooner the better. If that PHP project I started to play with ever becomes a bit more serious, I can't afford to waste time tinkering with OS. I need something to set up, configure, get used to, and forget about it.

---

### Post by mikewhatever on 2011-05-09
There are some insights on the future of Unity in this interview: [http://www.omgubuntu.co.uk/2011/05/mark-shuttleworth-talks-windicators-changes-for-unity-in-oneiric-and-whole-lot-more/](http://www.omgubuntu.co.uk/2011/05/mark-shuttleworth-talks-windicators-changes-for-unity-in-oneiric-and-whole-lot-more/).

Generally, if you want your development environment to be stable, I would discourage any "Yeah, OK, why not", and clicked 'Yes'" kind of changes. With Ubuntu, a Long Term Support release (if it works for you) is the best bet for a development environment.

---

### Post by azupan on 2011-05-09
> **mikewhatever said:**
> Generally, if you want your development environment to be stable, I would discourage any "Yeah, OK, why not", and clicked 'Yes'" kind of changes.Yeah, I noticed that :redface:
 
I'm a beginner in PHP & Linux, and the project I'm working on is still well in the "let's see" phase". For the time being, making risky "yeah why not" moves is reasonable, because it's the best way to gain some experience. So far, I was able to tweak every problem i got with Ubuntu out of existence. I simply wasn't expecting something as serious as aforementioned Netbeans problem. It's pretty much a showstopper. The last time I've seen application interfering with desktop that bad was in Windows 3.11. Things like this just shouldn't happen.
 
As far as I know, there is no easy way of rolling back to 10.10. The amount of trouble is about the same as with switching the distros, which means I might as well try that.

---

### Post by SoFl W on 2011-05-09
Turn off "Release updates" in the update manager settings.

---

### Post by azupan on 2011-05-09
> **SoFl W said:**
> Turn off "Release updates" in the update manager settings.I will, thanxx- if I keep Ubuntu.
 
Guess I'll use "Classic" until -say- the end of the week, and then... if I shrink my Windows partition a little bit, get rid of pretty much useless D: disk... , maybe I could squeeze Debian or Mint in there, have a triple boot instead of dual boot, so to speak. Grub should be able to handle that, I hope. I'm a bit worried about that, though, because I could trash entire disk, Ubuntu **and** Windows installation that is. :shock:
 
Another solution would be to copy the whole Ubuntu partition on external disk, to put it on ice, so to speak, and try out another distro until the Netbeans issue is fixed. After that, I can make informed decision about what to use in the future. It's just the idea, though, I've never done such a thing.

---

### Post by cvielma on 2011-05-09
I agree with MikeWhatever, you should stick to a LTS version :S

But, just to give a shot, can you try to add this line to /etc/environment?

AWT_TOOLKIT=MToolkit

(open a terminal -> sudo gedit /etc/environment -> add the line, save and restart).

See if that could solve the problem with Netbeans/Unity, if it doesn't another thing i would recommend is to disable the visual effects.

Hope it helps

Best regards,

---

### Post by akand074 on 2011-05-09
Netbeans works flawlessly here running Unity :S. But yeah if stability is important stick to 10.04 LTS. By 12.04 LTS Unity should be perfect. That's the plan anyways.

---

### Post by azupan on 2011-05-10
> **akand074 said:**
> Netbeans works flawlessly here running Unity :S.Have you tried to drag toolbars and docked windows around? Watch what happens with launcher! It's pretty subtle, but very annoying. Even if you don't rearrange the Netbeans windows all the time like I do, you can still accidentaly drag toolbar a little when you click the button. When you do that, launcher refuses to move out of the way until you close Netbeans. If you have been debugging PHP, you have to close all Firefox windows too.
 
My guess is, that Netbeans doesn't free or release something the way Unity expects it to. Something sits in the Java garbage collector holding some resources that are supposed to be released immediatelly.
 
It's not necessarily Unity's fault, could also be Nvidia drivers, but the final outcome is: For the time being, I can't use Netbeans on Unity.
 
 
> **akand074 said:**
> But yeah if stability is important stick to 10.04 LTS.IMHE 10.10 worked a bit better than 10.04
 
> **akand074 said:**
> By 12.04 LTS Unity should be perfect. That's the plan anyways.I certainly hope so. I was just beginning to like it, when this Netbeans problem appeared.
 
 
 
BTW, regarding Debian: I rearranged my disk partitions the way they should be (thank Chinese geeks for Easeus), but the goddamed thing refuses to install alongside Windows 7 and Ubuntu. It says it has no permission to write on disk :confused:. How considerate!
 
The reason I'm writing this is that I found the probable reason for this problem while playing with disk partitions:
 
[http://ubuntuforums.org/showthread.php?t=1750332](http://ubuntuforums.org/showthread.php?t=1750332)
 
During the upgrade from 10.10 to 11.4, /dev/... partition names were changed. Link to swap partition is broken, and no swap means no hibernation.

---

### Post by akand074 on 2011-05-10
> **azupan said:**
> Have you tried to drag toolbars and docked windows around? Watch what happens with launcher! It's pretty subtle, but very annoying. Even if you don't rearrange the Netbeans windows all the time like I do, you can still accidentaly drag toolbar a little when you click the button. When you do that, launcher refuses to move out of the way until you close Netbeans. If you have been debugging PHP, you have to close all Firefox windows too.

What do you mean by "drag toolbars and docked windows?" I'm grabbing the net beans icon and moving it around the bar. Throwing everything around and moving my window. The launcher still moves out of the way. Everything works perfectly as always. Are you using the Netbeans from the Ubuntu software center? (i.e not downloaded from anywhere else or added as a software source?). Otherwise if you'd like you can give me a general step by step test case to try to see if I get what you get. If not it could just be your install and a clean install might fix it?

---

### Post by azupan on 2011-05-10
> **akand074 said:**
> What do you mean by "drag toolbars and docked windows?" I'm grabbing the net beans icon and moving it around the bar. Throwing everything around and moving my window. The launcher still moves out of the way. Everything works perfectly as always. Are you using the Netbeans from the Ubuntu software center? (i.e not downloaded from anywhere else or added as a software source?). Otherwise if you'd like you can give me a general step by step test case to try to see if I get what you get. If not it could just be your install and a clean install might fix it?I use Netbeans 7.0 downloaded from netbeans.org, **not** from the Ubuntu software center. I use Netbeans 7.0 because it's much better for PHP development than 6.0.

"Toolbars and docked windows" are marked on the left screenshot.

Since I'm only beginning to learn PHP & Drupal, I do a lot of side by side editing. So, when I drag one of the docked widows on the side, Unity launcher pops on the screen, and stays on top, until Netbeans is restarted (see the right screenshot).

During writing of this post, I had to go away from computer for about an hour. When I came back, launcher was behaving normally again. I imagine Netbeans's Java garbage collector activated itself in the meantime.

Netbeans 7.0 works OK in "Classic Ubuntu", though, which means Natty is, for the time being, still useful for the purpose. If there is a reasonable chance Unity will be fixed in the foreseeable future, I guess I can wait. With Netbeans & such working, global menu out of the way when applications with hidden menu or without menu (like Chromium) are on the top, and a bit more configurability, Unity would be ideal desktop, as far as I'm concerned. I especially like Unity MT Grab Handles. An excellent idea. I've always hated that pesky mouse hunting for the window edge. I've already mapped them on Alt key.

---

### Post by akand074 on 2011-05-10
Ohhh I understand now what you're talking about. Yeah I use Netbeans 6.9 from the repositories. I officially reproduced your bug. All I had to do was drag one of my java windows and boom Unity came out and I can't get rid of it. Did you file a bug report? If not it might be a good idea to. It works fine after restarting Netbeans but that is super annoying! I think this will definitely be fixed in Unity by 12.04 if not 11.10. Unity is a lot to ask for in just 6 months it's got plenty of bugs that I believe most will be fixed by 11.10.

---

### Post by azupan on 2011-05-10
> **akand074 said:**
> Did you file a bug report? If not it might be a good idea to.I don't know how to do it, I'm totally new here.

---

### Post by el_koraco on 2011-05-10
alt+f2 

```
ubuntu-bug unity
```

hit enter. the rest is self-explanatory.

---

### Post by azupan on 2011-05-10
> **el_koraco said:**
> alt+f2 

```
ubuntu-bug unity
```hit enter. the rest is self-explanatory.
Done.

---

### Post by akand074 on 2011-05-10
> **azupan said:**
> Done.

I was doing some work outside I was actually in the middle of filing the report before I saw this post. I'll confirm the bug in your report!

---

### Post by azupan on 2011-05-11
I got a triple boot machine now! :biggrin: Just managed to install Mint besides Windows 7 & Ubuntu.

Now how do I get rid of that ugly mint grub screen? Ubuntu's much better, and I'd like to have it back!

---

### Post by akand074 on 2011-05-11
> **azupan said:**
> I got a triple boot machine now! :biggrin: Just managed to install Mint besides Windows 7 & Ubuntu.

Now how do I get rid of that ugly mint grub screen? Ubuntu's much better, and I'd like to have it back!

Boot into your Ubuntu Live CD and [reinstall]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") it.

---

### Post by azupan on 2011-05-12
> **akand074 said:**
> Boot into your Ubuntu Live CD and [reinstall]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") it.I tried that, but it didn't work. Got some funny error messages, googled them, and found them somewhere listed as bug. Anyway, it's just an aestethic thing, nothing urgent. I still have some problems with hibernation, but I'll try to solve that on my own.

My 1st impression of Mint: Very similar to Ubuntu a couple of releases ago, except color scheme, which was probably modelled on[ Hyla arborea]("http://en.wikipedia.org/wiki/European_tree_frog"). Desktop's usability is decent enough. With Cairo dock on the side it doesn't matter anyway, it's almost like Unity. In all: It serves the purpose. If need be, I can mount Ubuntu's file system, and migrate my stuff in no time.

So... I guess this pretty much solves my problem. Thanks for all your help and hints! 
:)

---

### Post by el_koraco on 2011-05-12
Try Docky. It's faster than Cairo.

---

### Post by azupan on 2011-06-03
My experience with other distros, in case anybody is interested.

**Debian:** Will not install on RAID. At least not simply or safely.

**Mint:** Looks nice enough at the 1st glance, very useful main menu. Alas, it's bug compatible with Ubuntu. Julia had exactly the same shortcomings 10.04 has, and upgrades are pretty painful. Upgrade from Julia to Katya deleted MySql databases, and trashed Apache settings. Katya is bug compatible with Natty, Compizconfig does exactly the same strange things when Cube is enabled.

So, rather than restoring the databases from backup and setting Apache again, I reverted to my original Ubuntu installation, and converted it to Kubuntu. Had some trouble with Nvidia driver. This solution works, however:

[http://ubuntuforums.org/showthread.php?t=1748642](http://ubuntuforums.org/showthread.php?t=1748642)

Kubuntu works good enough, looks good as well, and I'm beginning to like that "Activities" thingy. Reconfiguring the desktop with a couple of mouse clicks is something I've always wanted, so... I might as well keep Kubuntu, even after (and if) Canonical gets Unity in order. I just hope they won't trash Compiz too much in the process. At it's current state, it works under Kubuntu as well. IMHO it's much better than KDE's cube.

---

