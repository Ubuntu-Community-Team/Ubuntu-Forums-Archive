---
title: "Kde and Firefox woes"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-12-18
Hi all, 

Using KDE and Firefox latest build the browser just...crawls..I could probably sometimes run faster in the expressway then its moving...I disabled all my addons and only am running the Blue Ice Theme, it was never this bad in gnome, but I like KDE more..

Does anyone know which swiftfox to download for a Celeron intel processor?  I keep getting only the documentation when ive tried and is this a normal behavior for KDE?  It seems wierd to me but I dunno...

---

### Post by mmb1 on 2007-12-18
I always had trouble installing swiftfox, but there is an open source version-swiftweasel that is available through synaptic, I'm not sure about adept though.

Your speed issue could come from the fact that you're using an unstable build, or are you running stable?

---

### Post by p_quarles on 2007-12-18
> **mmb1 said:**
> I always had trouble installing swiftfox, but there is an open source version-swiftweasel that is available through synaptic, I'm not sure about adept though.

Your speed issue could come from the fact that you're using an unstable build, or are you running stable?
Swiftweasel isn't available in the repositories. If you have it installed already, it will show up in Synaptic, but that's a different story.

Anyway, there are a couple different builds of Swiftfox/Swiftweasel for Celerons -- can you identify your exact processor?

Also, this is a good guide to speeding up Firefox and integrating it with KDE:
[http://darkox-weblog.blogspot.com/2007/09/speed-up-and-integrate-firefox.html](http://darkox-weblog.blogspot.com/2007/09/speed-up-and-integrate-firefox.html)

---

### Post by sports fan Matt on 2007-12-18
Hey MMB,

Yeah im running 2.0.0.11 the latest stable one.  I have heard of swiftweasel, but like you im unaware if it runs in KDE..Also tried opera but it seems like opera (I had installed it and  is locked--when i go to synmaptic it says "it looks like another opera instance is using the same configuration directory because its lock file is active: /home/office/.opera/lock, do you want to start it anyway"? I could use Opera, if i could get it unlocked...

---

### Post by mmb1 on 2007-12-18
Does Konqueror still work normally?

---

### Post by sports fan Matt on 2007-12-18
p_q,

The name of the processor is a Coppermine as far as I can tell :  PS: I'll look at that link as well...

---

### Post by sports fan Matt on 2007-12-18
Konqueror Works except it keeps telling me in yahoo mail "to use a more recent browser" and some things arent there like the tabs in the mail preview...etc

---

### Post by p_quarles on 2007-12-18
> **sox fan Matt said:**
> p_q,

The name of the processor is a Coppermine as far as I can tell :  PS: I'll look at that link as well...
The pentium3 version is the best for the Celeron Coppermine processor. I'd recommend Swiftweasel over Swiftfox. Here's a link to the .deb:
[http://downloads.sourceforge.net/swiftweasel/swiftweasel-2.0.0.11_pentium-3_ubuntu-i386.deb?modtime=1196597814&big_mirror=0](http://downloads.sourceforge.net/swiftweasel/swiftweasel-2.0.0.11_pentium-3_ubuntu-i386.deb?modtime=1196597814&big_mirror=0)

---

### Post by mmb1 on 2007-12-18
Most definitely, swiftweasel is faster and open-source!

(not to hate on firefox, I love it too.)

---

### Post by p_quarles on 2007-12-18
> **mmb1 said:**
> Most definitely, swiftweasel is faster and open-source!

(not to hate on firefox, I love it too.)
Nah, no hate for Firefox: it's open-source as well. It's just Swiftfox that isn't. The Mozilla Public License allows for proprietary forks, which is exactly what the Swiftfox project is.

Of course, if you just compiled the Firefox source code yourself, you would essentially get the same thing that Swiftfox/Swiftweasel offers -- but that's a lot more work. ;)

---

### Post by sports fan Matt on 2007-12-19
Why wont Konqueror play nicely with Yahoo Mail?  I keep getting this: Why miss out?
 To see all the new Yahoo! home page has to offer, please upgrade to a more recent browser. 

*Sigh* I just cant seem to win sometimes LOL....I hope Firefox Gran Paradiso will be better

---

### Post by p_quarles on 2007-12-19
> **sox fan Matt said:**
> Why wont Konqueror play nicely with Yahoo Mail?  I keep getting this: Why miss out?
 To see all the new Yahoo! home page has to offer, please upgrade to a more recent browser. 

*Sigh* I just cant seem to win sometimes LOL....I hope Firefox Gran Paradiso will be better
Did you give Swiftweasel a shot?

Anyway, Konqueror comes with a built-in agent switcher. You can use this by clicking on "Tools," selecting "Browser Identification" and changing it to something widely supported (Firefox, Explorer, Opera). This will work with just about every web site that isn't MSIE-only.

---

### Post by sports fan Matt on 2007-12-19
p_q or anyone can jump in:
 
I downlosded swiftweasel, but need to know which debian binary to use?  I got firefox running last night, so its not a huge concern, just want to try swiftweasel, as it may be a tad faster but unsure what binary to use (control, debian, or tar giz).  I must say these are minor issues im experirncing, the linux transition isnt all hard, just takes patience and a willingness to learn, experiment and know "its only a computer, its easy to fix with great help from the forums"

---

### Post by p_quarles on 2007-12-19
The link I gave you earlier goes straight to the .deb file for the version that works with the Celeron Coppermine processor. Once it's downloaded, you can install the package by double-clicking on the .deb file.

.deb files, by the way, are what you get in the Ubuntu repositories: the only difference here is that you're installing something that isn't in the repos, but it's the same kind of package. 

Again, for either Swiftfox or Swiftweasel, you'll want the Pentium 3 version of the .deb file.

---

