---
title: "[SOLVED] What About The Future Of Gutsy 7.10?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-29
I have a question about the future of Gutsy....

After trying the Hardy Live CD for a couple of days, and finding out that because I have an ATI graphics card in my laptop, I cannot run compiz-fusion, emerald, or Avant Window Navigator anymore, well, not if I install Hardy.

So, my question is this:  I have heard that support will stop for Gutsy next month.  Does that mean that programs will no longer be available on Gutsy repositories, and that I cannot install programs thru Synaptic anymore?

Or, just what does 'No support' actually mean?

Thanks.

---

### Post by Google Spider on 2008-03-29
"No Support" means no more security updates/patches. Reporistories will still be open. You can install any software you want.

---

### Post by Lord Illidan on 2008-03-29
> **FreewareFan said:**
> I have a question about the future of Gutsy....

After trying the Hardy Live CD for a couple of days, and finding out that because I have an ATI graphics card in my laptop, I cannot run compiz-fusion, emerald, or Avant Window Navigator anymore, well, not if I install Hardy.

So, my question is this:  I have heard that support will stop for Gutsy next month.  Does that mean that programs will no longer be available on Gutsy repositories, and that I cannot install programs thru Synaptic anymore?

Or, just what does 'No support' actually mean?

Thanks.

Why exactly can't you run the above programs with ATi graphics?

---

### Post by bumanie on 2008-03-29
No support means no more updates etc. However gutsy should be supported for another 12 months yet. All ubuntu releases are supported for 18 months, unless they are Long Term Support (LTS) releases which are supported for 3 years.

---

### Post by Google Spider on 2008-03-29
> **FreewareFan said:**
> 
After trying the Hardy Live CD for a couple of days, and finding out that because I have an ATI graphics card in my laptop, I cannot run compiz-fusion, emerald, or Avant Window Navigator anymore, well, not if I install Hardy.


No that's because you don't have Xgl installed on that live CD. Installing xgl should get these things work once you install Hardy on your HDD

[http://ubuntuforums.org/showpost.php?p=4461682&postcount=6](http://ubuntuforums.org/showpost.php?p=4461682&postcount=6)

---

### Post by Sef on 2008-03-29
> All ubuntu releases are supported for 18 months, unless they are Long Term Support (LTS) releases which are supported for 3 years.

The desktop is supported for 3 years.   Servers are supported for 5 years.

> "No Support" means no more security updates/patches. Reporistories will still be open. You can install any software you want.

Repositories will be closed.

---

### Post by Google Spider on 2008-03-29
Support for Gusty ends April 2009 

[http://www.ubuntu.com/news/ubuntu-7.10rc](http://www.ubuntu.com/news/ubuntu-7.10rc)

---

### Post by luceerose on 2008-03-29
I am running Hardy with onboard nvidia.
Very happily running compiz & enjoying the desktop cube.

And I really have to say despite being an 'unstable' release, I have had infinitely less trouble with Hardy than I had with Gutsy.
I rely on Hardy as my main OS and it hasn't let me down yet.

---

### Post by FreewareFan on 2008-03-29
> **Lord Illidan said:**
> Why exactly can't you run the above programs with ATi graphics?

The exact reason is because the developers have blacklisted ati graphic cards.  I can install compiz, and compiz manager just fine, but when I start it, it shuts back down when it checks and sees that I have an ati card...   Major bummer!

There is a work-around, a dirty hack if you will, of SKIP_CHECKS=yes ,  but when it's used, other parts of the graphic display really get messed up on my system..  It's really not a good option.

---

### Post by FreewareFan on 2008-03-29
> **Sef said:**
> The desktop is supported for 3 years.   Servers are supported for 5 years.

<Repositories will still be open>

Repositories will be closed.

Which statement is true?  Will they be open, or closed, and what date will that take effect?

---

### Post by Google Spider on 2008-03-29
> **FreewareFan said:**
> Which statement is true?  Will they be open, or closed, and what date will that take effect?

You can guess that by looking at the beans.:biggrin: Sef must be right (He's a staff member). Repos will close.  But not before [April 2009.]("https://wiki.ubuntu.com/Releases")

---

### Post by FreewareFan on 2008-03-29
> **Google Spider said:**
> No that's because you don't have Xgl installed on that live CD. Installing xgl should get these things work once you install Hardy on your HDD

[http://ubuntuforums.org/showpost.php?p=4461682&postcount=6](http://ubuntuforums.org/showpost.php?p=4461682&postcount=6)

The fglrx driver is very, very slow, and very bad of quality..  I will not run that driver.

---

### Post by bumanie on 2008-03-29
Sef's answers are correct, Gutsy supported for one more year, repositories closed after that. LTS - 3 years desktop support, 5 years server support.

---

### Post by FreewareFan on 2008-03-29
Cool, so I have at least another 12 months.  Maybe by then they will have the ati graphic card issue dealt with in Hardy..

---

### Post by Lord Illidan on 2008-03-29
What's the graphics card?

---

### Post by forrestcupp on 2008-03-29
> **FreewareFan said:**
> The fglrx driver is very, very slow, and very bad of quality..  I will not run that driver.

What driver are you running right now?  Whatever way you got things working in Gutsy will also work in Hardy.  If you are using the open source drivers now, you can use them in Hardy, too.  If you installed the drivers in the Restricted Drivers Manager, you *are* using fglrx, and Hardy just has a newer version of it.

If you got it working in Gutsy, then there's absolutely no reason you can't get it working in Hardy.

---

### Post by FreewareFan on 2008-03-29
> **Lord Illidan said:**
> What's the graphics card?

I have a Radeon IGP 330M/340M/350M graphics card.   As you can see from this thread [http://ubuntuforums.org/showthread.php?t=722943](http://ubuntuforums.org/showthread.php?t=722943)  the following quote:

debian/patches/036_blacklist_ati_on_laptop.patch:
- don't start compiz if using the ati or radeon driver
and using a laptop as mobility cards have issues (LP: #197135) 


And here is a quote from Amaranth, one of the Heron Developers:

"Basically the idea is that all r200 and older cards work and everything newer doesn't. Someone might say "but my X600 Mobility works fine!" but they are the exception. The problem is there are a bunch of pci ids to blacklist to block all the ones that are actually broken and we will most probably not be able to compile a complete list.

So, what to do when you have a bazillion chips that don't work and a slightly smaller group that do? The easiest approach is to just block them all as it is better to have it refuse to start on working chip than make X restart or lock up on a broken chip."


So, as you can see, the Developers have just blacklisted all ATI graphic cards across the board, if you use a laptop.

As I already said, they have come up with a couple of dirty ways around this, but the end result is not prime at all...... particularly when it comes to video playback.... Terrible quality

---

### Post by FreewareFan on 2008-03-29
> **forrestcupp said:**
> What driver are you running right now?  Whatever way you got things working in Gutsy will also work in Hardy.  If you are using the open source drivers now, you can use them in Hardy, too.  If you installed the drivers in the Restricted Drivers Manager, you *are* using fglrx, and Hardy just has a newer version of it.

If you got it working in Gutsy, then there's absolutely no reason you can't get it working in Hardy.

I use the ati driver in Gutsy, not the fglrx driver.  And there IS a reason it won't work in Hardy, see the above reference...   I truly wish I were wrong about this, but believe me, I've tried all the suggestions in the developers forum for this issue, and it's just not going to happen, not until they fix the kernal issue....  Who knows how long that will take...

---

### Post by forrestcupp on 2008-03-29
Well, that's the problem with ATI.  There *are* things you can do to get it working, especially with the proprietary drivers, but those are the things you don't want to do.  That's just how it works when you have an ATI chipset.

But if you were to use the new ATI proprietary drivers, it is possible to unblacklist it so Compiz will start.  These drivers don't require Xgl anymore, and they are a lot smoother and faster than they were 2 releases ago.  You can also use the X11 video output module to prevent the flickering effect when viewing videos with Compiz running.

But if you're happy with Gutsy, you have a year of support left, so it's ok for you to stick with it.

And you can always hope that since AMD released the specs for your chipset, the open source drivers will get a lot better.

---

### Post by FreewareFan on 2008-03-29
> **forrestcupp said:**
> 

But if you were to use the new ATI proprietary drivers, it is possible to unblacklist it so Compiz will start.  These drivers don't require Xgl anymore, and they are a lot smoother and faster than they were 2 releases ago.  You can also use the X11 video output module to prevent the flickering effect when viewing videos with Compiz running.



Well, I'd be happy to try that new driver you are talking about, if you wouldn't mind walking me through how/where to download it, and how to install it?  I would appreciate your efforts on this!

---

### Post by forrestcupp on 2008-03-29
Well, the thing is, the fglrx drivers in Hardy's Restricted Drivers Manager (RDM) *are* the new drivers that I'm talking about.  The ones in Gutsy's RDM are pretty old and they are before they got rid of the need for Xgl.  So if you actually tried Hardy and installed the drivers in Hardy's RDM and they didn't work for you, you're out of luck.  But it sounds like you only used Hardy's Live CD, and I don't know how effective it would be to install restricted drivers with a Live CD, since it installs it to RAM, and pretty much have to reboot to get them to work.  To get the full effect, you really need to have it installed.

If you want to try it out in Gutsy, the easiest way to install the latest drivers is to use [Envy](http://www.albertomilone.com/nvidia_scripts1.html).  Just download the proper deb and install it.  Then when you run Envy, it will automatically download the latest drivers and install them for you.  These drivers should work better than the ones you're used to.  But before you install these drivers, if you have Xgl installed, you need to uninstall it
```
sudo apt-get --purge remove xserver-xgl
```.
Then if you are using the drivers in the Restricted Drivers Manager (which it appears that you are not), open up the RDM and disable them.  Then you can use Envy to install the new drivers.

The only problem is that fglrx is blacklisted in Compiz even though the new drivers work without Xgl.  So one way around this is the skip_checks workaround.  I know you already tried this and had problems, but the problem wasn't with the skip_checks workaround, it was with the drivers you were using.  So you can make skip_checks permanent by opening a terminal and typing
```
sudo gedit /etc/xdg/compiz/compiz-manager
```
That will open the compiz-manager file (which may be empty).  At the end of the document, enter
```
SKIP_CHECKS=yes
```
and save it.  You should be good to go.

**Warning**, if you install the drivers with Envy, and it boots to a black screen, or it just won't boot to your desktop, you can boot to your recovery mode and type
```
envy --uninstall-all
exit
```
To undo what you did with envy, and it should boot to your desktop.

**Also**, if you *are* using Hardy, just use the RDM because right now it is using the latest ATI drivers.

---

### Post by FreewareFan on 2008-03-29
I'll print out those instructions, and if I ever do decide to install Heron, I'll give them a try.  Many thanks!

---

### Post by N1N31NCHN41L5 on 2008-03-30
> **FreewareFan said:**
> I have a question about the future of Gutsy....

After trying the Hardy Live CD for a couple of days, and finding out that because I have an ATI graphics card in my laptop, I cannot run compiz-fusion, emerald, or Avant Window Navigator anymore, well, not if I install Hardy.

So, my question is this:  I have heard that support will stop for Gutsy next month.  Does that mean that programs will no longer be available on Gutsy repositories, and that I cannot install programs thru Synaptic anymore?

Or, just what does 'No support' actually mean?

Thanks.

i have a ati radeon xpress 1100 graphics card and have never been able to get 3D to work. Until today, try installing envy. EVERYTHING works now.

---

