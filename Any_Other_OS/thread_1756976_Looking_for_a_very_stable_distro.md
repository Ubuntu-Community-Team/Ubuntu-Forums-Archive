---
title: "Looking for a very stable distro"
date: 2011-05-12
forum: Any Other OS
---

### Post by racie on 2011-05-12
Hey guys.  First of all, let me say that Ubuntu has been great to me.  After updating to 11.04, I have some massive freezing issues (similar to the fellow [here](http://ubuntuforums.org/showthread.php?t=1751800) if you're interested).  Now, rather than searching everywhere for an answer, I've decided that I don't really want to have to play with the bugs and hope they will resolve any more.  

I'm looking to try out some of the least buggy distros you can think of.  I guess I'm trying to say that I'm looking for more stable and thoroughly-tested distros, rather than more bleeding-edge distributions.

Although I could install Windows XP on this PC, I would rather chose a Linux distro first because I feel like it could take better advantage of my hardware.

So... I've heard Debian may be what I'm looking for, but how do other major distributions do in comparison?  Linux Mint?  OpenSUSE?  Arch?  Slackware?

*edit* Oh and the freezing issue isn't the sole reason for my wanting to try out other distros... it was more of a buildup to this point.

---

### Post by snowpine on 2011-05-12
I think it's worth putting in a little time to investigate the freezing issue. If the freeze is being caused by a particular version of the kernel, Xorg, a hardware driver, etc. then you might have the same problem with other distros that share the same version. 

To answer your specific question, the most stable distros that I've personally had the pleasure of using include Debian, CentOS, Slackware, and of course, Ubuntu Long-Term-Support.

---

### Post by boydrice on 2011-05-12
Slackware, FreeBSD, OpenBSD, NetBSD, Debian, Scientific Linux, CentOS, and Ubuntu LTS.  Basically you want to stick with enterprise quality distributions/projects that have fixed release cycles and numerous QA/testing cycles and good security support.

---

### Post by jerrrys on 2011-05-12
pick an LTS.  stability is what there all about.

---

### Post by racie on 2011-05-12
> **snowpine said:**
> I think it's worth putting in a little time to investigate the freezing issue. If the freeze is being caused by a particular version of the kernel, Xorg, a hardware driver, etc. then you might have the same problem with other distros that share the same version.

True.  And I'm not blaming Ubuntu for the problem... it just reminded me of the other major issues I've had.

Hmm... so far Debian and Ubuntu LTS are my top choices.  In fact, I think I'll try a dual-boot with Debian this weekend.

---

### Post by Spice Weasel on 2011-05-13
Debian, Scientific Linux, Slackware. All really stable, all good choices.

---

### Post by tnmarktx on 2011-05-13
I think that Lubuntu 11.04 is excellent, if LXDE has all the features that you need.  Salix OS a slackware based distro is also very excellent.  XFCE is the desktop for the main edition for Salix.

---

### Post by cgroza on 2011-05-13
Arch, it may take some time to set up tho.

---

### Post by malspa on 2011-05-13
Another one: Mepis.

---

### Post by exploder on 2011-05-13
My suggestion would be to try PCLinuxOS. My reasoning is here.

[http://ubuntuforums.org/showthread.php?t=1757274](http://ubuntuforums.org/showthread.php?t=1757274)

---

### Post by kn0w-b1nary on 2011-05-13
Debian Squeeze w/ XFCE 4.

Tinycore. Very minimalist, however, very fast and customizable. Just plan to take a day to set it up.

---

### Post by krapp on 2011-05-13
> **cgroza said:**
> Arch, it may take some time to set up tho.

He said very stable.

---

### Post by NormanFLinux on 2011-05-13
OZ Unity is worth looking into. Based on Ubuntu 10.04 LTS, its stable and fast and sports a default netbook remix interface - the pre-Unity version.

I also run PCLOS KDE. Its a solid newbie-friendly RPM distro with apt-get and Synaptic.

In both distros, multimedia codecs are pre-installed and everything works out of the box.

They're both aimed at people who are intimated by Linux but want an easy to use and stable OS system.

---

### Post by kelvin spratt on 2011-05-13
Salix is rock solid slackware made easy peasy that just works!

---

### Post by racie on 2011-05-14
Hmm... sadly, Debian stable is a no-go.  My wireless card is not supported.

Salix, huh?  I've never heard of this one.

Right now I'm looking at PCLinuxOS, Slackware/Salix, and Ubuntu LTS.

But what do you guys think of OpenSUSE?  It's a major distro, but none of you have said anything about it.

---

### Post by krapp on 2011-05-14
> **racie said:**
> Hmm... sadly, Debian stable is a no-go.  My wireless card is not supported.

You mean it's not supported out of the box because there isn't a free driver for it?

---

### Post by snowpine on 2011-05-14
> **racie said:**
> Hmm... sadly, Debian stable is a no-go.  My wireless card is not supported.

What kind of wireless card do you have? If your card requires a "nonfree" firmware, then most distros will require you to install it. 

For example I have a Broadcom wireless card. Debian cannot support this card "out of the box" but all I need to do is follow the instructions on the wiki: [http://wiki.debian.org/bcm43xx](http://wiki.debian.org/bcm43xx)

---

### Post by ilovelinux33467 on 2011-05-14
> **racie said:**
> But what do you guys think of OpenSUSE?  It's a major distro, but none of you have said anything about it.

openSUSE is an excellent distro and I find it very stable.

---

### Post by screaminj3sus on 2011-05-14
> **racie said:**
> Hmm... sadly, Debian stable is a no-go.  My wireless card is not supported.

Salix, huh?  I've never heard of this one.

Right now I'm looking at PCLinuxOS, Slackware/Salix, and Ubuntu LTS.

But what do you guys think of OpenSUSE?  It's a major distro, but none of you have said anything about it.

Opensuse 11.4 is a great distro.

---

### Post by racie on 2011-05-14
> **krapp said:**
> You mean it's not supported out of the box because there isn't a free driver for it?

> **snowpine said:**
> What kind of wireless card do you have? If your card requires a "nonfree" firmware, then most distros will require you to install it. 

For example I have a Broadcom wireless card. Debian cannot support this card "out of the box" but all I need to do is follow the instructions on the wiki: [http://wiki.debian.org/bcm43xx](http://wiki.debian.org/bcm43xx)

Yes, it requires a nonfree driver.

Long story short: the installation tries to detect the driver located on my USB drive(s) and fails and Debian needs to update if I want to install it manually.  Sadly, I cannot update without the internet.

Don't worry, I'm not just giving up right away.  I've joined the Debian forums and searched for solutions, but I've yet to get my answer.

Still distro hopping atm.  :)

---

### Post by NightwishFan on 2011-05-14
I would not give up on Debian, once you get it running it will work great. :)

More info: [http://wiki.debian.org/WiFi](http://wiki.debian.org/WiFi)

---

### Post by krapp on 2011-05-14
Ugh that sucks. Perhaps there's a non-free CD or DVD that has it (not live images), if you wanna check there. Some people at the Debian forums know the contents of those .iso's pretty well, so maybe they could let you know.

---

### Post by snowpine on 2011-05-15
Just plug into a wired ethernet connection temporarily and fix your wifi, it should be easy. If you want to tell us which wifi card you have, maybe one of us can help you. :)

It's a shame to limit yourself to "distros that support non-free hardware out-of-the-box" because that basically means 1) distros that operate out of foreign countries with weak software patent laws; or 2) distros that are so small/unpopular that they "fly under the radar." Most of the reputable top distros (Ubuntu, Debian, Fedora, Red Hat, etc.) take free vs. non-free software seriously, as they should. :)

---

### Post by racie on 2011-05-15
> **snowpine said:**
> Just plug into a wired ethernet connection temporarily and fix your wifi, it should be easy. If you want to tell us which wifi card you have, maybe one of us can help you. :)

It's a shame to limit yourself to "distros that support non-free hardware out-of-the-box" because that basically means 1) distros that operate out of foreign countries with weak software patent laws; or 2) distros that are so small/unpopular that they "fly under the radar." Most of the reputable top distros (Ubuntu, Debian, Fedora, Red Hat, etc.) take free vs. non-free software seriously, as they should. :)

I can't use a wired connection.  The router is in the basement and I really don't want to lug the computer down there.

I'm not limiting myself... didn't you see my response?  I am currently looking for help in the Debian forums.

---

### Post by kopilo on 2011-05-17
Linux Mint is liable to have your drivers,
but personally I have found arch and openSuse to be the most stable.

I think the main reason I have found arch so stable is that I just keep with xinit rather than install something like gdm.

---

### Post by kaldor on 2011-05-17
Scientific 6.0

Developed by CERN and FermiLab, based on Red Hat Enterprise Linux. Solid, stable GNOME desktop. Includes some extra blobs for wireless too :)

It's excellent. Compatible with Fedora (RHEL based on Fedora 12/13).

Highly recommended if you need stability for some years.

---

### Post by krapp on 2011-05-17
> **kopilo said:**
> Linux Mint is liable to have your drivers,
but personally I have found arch and openSuse to be the most stable.

I think the main reason I have found arch so stable is that I just keep with xinit rather than install something like gdm.

:roll:

I don't get why Arch fanatics have to make claims for Arch beyond what even Arch claims for itself (which is a whole lot).

---

### Post by J. Sloan on 2011-05-17
> **racie said:**
> Hey guys.  First of all, let me say that Ubuntu has been great to me.  After updating to 11.04, I have some massive freezing issues (similar to the fellow [here](http://ubuntuforums.org/showthread.php?t=1751800) if you're interested).  Now, rather than searching everywhere for an answer, I've decided that I don't really want to have to play with the bugs and hope they will resolve any more.  

I'm looking to try out some of the least buggy distros you can think of.  I guess I'm trying to say that I'm looking for more stable and thoroughly-tested distros, rather than more bleeding-edge distributions.

Although I could install Windows XP on this PC, I would rather chose a Linux distro first because I feel like it could take better advantage of my hardware.

So... I've heard Debian may be what I'm looking for, but how do other major distributions do in comparison?  Linux Mint?  OpenSUSE?  Arch?  Slackware?

*edit* Oh and the freezing issue isn't the sole reason for my wanting to try out other distros... it was more of a buildup to this point.

I use Arch Linux (with Fluxbox), and it is a rolling distro which means that it is bleeding edge (in a sense). I have not had any major issues with Arch at all. I started out on Linux Slackware which is a good, stable distribution, imho. Also, both Arch and Slackware are/can be minimal distributions which I think affords the user a stable/configurable distro. If you are a Ubuntu user, then Debian would be a good, stable distro that you would be familiar with since Ubuntu is basically based off of Debian.   Good luck!

By the way, I have played around with Ubuntu and have had more breakage issues with Ubuntu in package upgrades than with Arch. Don't misunderstand Arch's philosophy here where "stable" doesn't necessarily mean an unchanged system, but Arch means something much different by "stable":

Q) Is Arch Linux a stable distro? Will I get frequent breakage?

[I]A) The long and short answer is: It is largely as stable as you make it.

You assemble your own Arch system, atop the simple base environment, and you control system upgrades. (Obviously, a larger, more complicated system incorporating multitudes of packages, multiple toolkits and desktop environments would be more likely to experience configuration issues due to upstream changes than a slimmer, more simple system would.) Arch is targeted at capable, proactive users. General UNIX competence and good system maintenance and upgrade practices also play a large role in system stability. Also recall that Arch packages are predominantly unpatched, so most application issues are inherently upstream.

Therefore, it is the user who is ultimately responsible for the stability of his own rolling release system. The user decides when to upgrade, and merges necessary changes when required. If the user reaches out to the community for help, it is often provided in a timely manner. The difference between Arch and other distributions in this regard is that Arch is truly a 'do-it-yourself' distro; complaints of breakage are misguided and unproductive, since upstream changes are not the responsibility of Arch devs. [/I]

Source:  [https://wiki.archlinux.org/index.php/FAQ#Q.29_Is_Arch_Linux_a_stable_distro.3F_Will_I_get_frequent_breakage.3F](https://wiki.archlinux.org/index.php/FAQ#Q.29_Is_Arch_Linux_a_stable_distro.3F_Will_I_get_frequent_breakage.3F)

---

### Post by el_koraco on 2011-05-17
> **J. Sloan said:**
> I use Arch Linux (with Fluxbox)

Of course. 

Debian stable, Slackware, Scientific Linux, or if you wanna go down the build it from the ground up and roll on road, one of the *BSD's.

---

### Post by snowpine on 2011-05-17
Ubuntu can also be very stable if you use Fluxbox instead of Unity. :)

---

### Post by krapp on 2011-05-17
> **J. Sloan said:**
> I use Arch Linux (with Fluxbox), and it is a rolling distro which means that it is bleeding edge (in a sense). I have not had any major issues with Arch at all. I started out on Linux Slackware which is a good, stable distribution, imho. Also, both Arch and Slackware are/can be minimal distributions which I think affords the user a stable/configurable distro. If you are a Ubuntu user, then Debian would be a good, stable distro that you would be familiar with since Ubuntu is basically based off of Debian.   Good luck!

By the way, I have played around with Ubuntu and have had more breakage issues with Ubuntu in package upgrades than with Arch. Don't misunderstand Arch's philosophy here where "stable" doesn't necessarily mean an unchanged system, but Arch means something much different by "stable":

Q) Is Arch Linux a stable distro? Will I get frequent breakage?

[I]A) The long and short answer is: It is largely as stable as you make it.

You assemble your own Arch system, atop the simple base environment, and you control system upgrades. (Obviously, a larger, more complicated system incorporating multitudes of packages, multiple toolkits and desktop environments would be more likely to experience configuration issues due to upstream changes than a slimmer, more simple system would.) Arch is targeted at capable, proactive users. General UNIX competence and good system maintenance and upgrade practices also play a large role in system stability. Also recall that Arch packages are predominantly unpatched, so most application issues are inherently upstream.

Therefore, it is the user who is ultimately responsible for the stability of his own rolling release system. The user decides when to upgrade, and merges necessary changes when required. If the user reaches out to the community for help, it is often provided in a timely manner. The difference between Arch and other distributions in this regard is that Arch is truly a 'do-it-yourself' distro; complaints of breakage are misguided and unproductive, since upstream changes are not the responsibility of Arch devs. [/I]

Source:  [https://wiki.archlinux.org/index.php/FAQ#Q.29_Is_Arch_Linux_a_stable_distro.3F_Will_I_get_frequent_breakage.3F](https://wiki.archlinux.org/index.php/FAQ#Q.29_Is_Arch_Linux_a_stable_distro.3F_Will_I_get_frequent_breakage.3F)

Seriously? You see a thread titled "Looking for a very stable distro" and you enter to talk about Arch?! And save us the KISS dear God. "The long and short answer is: It is largely as stable as you make it." Wow. I suppose making a Windows box stable by not connecting it to the internet is close to what the OP was looking for, too, right?

---

### Post by snowpine on 2011-05-17
> **krapp said:**
> Seriously? You see a thread titled "Looking for a very stable distro" and you enter to talk about Arch?! And save us the KISS dear God. "The long and short answer is: It is largely as stable as you make it." Wow. I suppose making a Windows box stable by not connecting it to the internet is close to what the OP was looking for, too, right?

Do I remember correctly from another thread that you've never used Arch? :)

---

### Post by krapp on 2011-05-17
> **snowpine said:**
> Do I remember correctly from another thread that you've never used Arch? :)

Yes, an Arch thread. Wherein the OP asked for our strong feelings, not our dispassionate observations, cited and referenced.

What's your point?

---

### Post by snowpine on 2011-05-17
> **krapp said:**
> Yes, an Arch thread. Wherein the OP asked for our strong feelings, not our dispassionate observations, cited and referenced.

What's your point?

How can you say Arch is not stable if you've never tried it? 

Or, more to the point, how can you say J. Sloan's Arch+Fluxbox install is not stable for him/her? :)

---

### Post by NormanFLinux on 2011-05-17
Open SUSE is good... I just never could stand the YAST installer.

I have nothing against an RPM based distro but I like apt-get so PCLinuxOS works for me.

---

### Post by J. Sloan on 2011-05-17
> **krapp said:**
> Seriously? You see a thread titled "Looking for a very stable distro" and you enter to talk about Arch?! And save us the KISS dear God. "The long and short answer is: It is largely as stable as you make it." Wow. I suppose making a Windows box stable by not connecting it to the internet is close to what the OP was looking for, too, right?

Hey, I signed up in 2008 and I waited three years to post my first post, so cut me some slack!  Seriously though, if you'll go back and read what I wrote, I did not enter this thread to talk about Arch.  I mentioned that while Arch is a rolling distro, I found it to be stable.  I also mentioned Slackware and Debian to the original poster.  

I edited my post after reading your comments to add that I think some people misunderstand the Arch philosophy, and that perhaps what you mean by "stable" and what others may mean, can be two different things.  With Arch, you can have a stable system, and believe it or not, some people like being in control of that.  

You obviously have some strong opinions, which is fine, but like snowpine correctly pointed out, you haven't even used Arch so how can you say what you're saying?  

By the way, thanks for your insightful comments, snowpine!

---

### Post by krapp on 2011-05-17
> **snowpine said:**
> How can you say Arch is not stable if you've never tried it? 

Or, more to the point, how can you say J. Sloan's Arch+Fluxbox install is not stable for him/her? :)

I'm sure you think your little rhetorical turn is quite ingenious, and it might have been, were it not so tired (YMMV blahblah), and, more importantly, wholly unbelieved by you. You know very well rolling distributions shipping new software are not stable distributions stuck with old software. Don't try to make them out to be the same thing in the proverbial some-other-user's experience, whose years sitting under a tree meditating upon the Arch Way made Arch just work for him.

---

### Post by krapp on 2011-05-17
> **J. Sloan said:**
> Hey, I signed up in 2008 and I waited three years to post my first post, so cut me some slack!  Seriously though, if you'll go back and read what I wrote, I did not enter this thread to talk about Arch.  I mentioned that while Arch is a rolling distro, I found it to be stable.  I also mentioned Slackware and Debian to the original poster.  

I edited my post after reading your comments to add that I think some people misunderstand the Arch philosophy, and that perhaps what you mean by "stable" and what others may mean, can be two different things.  With Arch, you can have a stable system, and believe it or not, some people like being in control of that.  

You obviously have some strong opinions, which is fine, but like snowpine correctly pointed out, you haven't even used Arch so how can you say what you're saying?  

By the way, thanks for your insightful comments, snowpine!

ArchFans deserve zero slack seeing as they've nearly monopolized the channels of communication in the FLOSS community.

In what land except ArchLand is Arch the answer to: "I'm looking to try out some of the least buggy distros you can think of. I guess I'm trying to say that I'm looking for more stable and thoroughly-tested distros, rather than more bleeding-edge distributions."

---

### Post by snowpine on 2011-05-17
> **krapp said:**
> ArchFans deserve zero slack seeing as they've nearly monopolized the channels of communication in the FLOSS community.

In what land except ArchLand is Arch the answer to: "I'm looking to try out some of the least buggy distros you can think of. I guess I'm trying to say that I'm looking for more stable and thoroughly-tested distros, rather than more bleeding-edge distributions."

Please re-read the original post:

> So... I've heard Debian may be what I'm looking for, but how do other major distributions do in comparison? Linux Mint? OpenSUSE? **Arch?** Slackware?

(emphasis added)

---

### Post by krapp on 2011-05-17
> **snowpine said:**
> Please re-read the original post:



(emphasis added)

LOL, the OP sets the topic, but he doesn't get to redefine truth values.

That the OP asked for "the least buggy distros" and took a half-step toward answering his own question doesn't mean he was taking the right step. If anything it is the divinely enlightened Arch user's responsibility to correct this falsehood.

---

### Post by manzdagratiano on 2011-05-17
Arch... Anybody who says it is not rock solid stable is lying.

My corroboration? I have been regulary using it on my two machines for more than a year, and I have **never** has a **single** problem.

Their wiki is excellent. It is like writings on the wall.

Almost all the packages you can dream of - certainly **all** of what I have dreamed of - it has supported; if not in the main repo, then in the AUR.

It only takes some amount of common sense to not go with dangerous updates - though I have never actually had to bother with such a thing. If you want to be cautious, just click the forums or their website to gaze at the news before hitting pacman -Syu.

Once it is set up, which does not take that long, you barely notice it is Arch you are running. As simple to deal with as Ubuntu.

In fact, I am typing from Arch right now.

---

### Post by SynonM on 2011-05-17
Try Ubuntu Netbook 10.10 & maybe wait till Natty Narwhal becomes more stable.

---

### Post by manzdagratiano on 2011-05-17
Also, I love Debian, Slackware and Gentoo as well, and I use them constantly with Ubuntu and Arch, but I would not recommend them as the single distro to have, for the following reasons:

Debian - hard to have everything configured to work as perfectly as Ubuntu to this date, since the niceness you get with Ubuntu is not enabled by default. Also, even Debian Sid is far from bleeding edge.

Slackware - it is very easy to install and maintain, but a majority of packages needed every day are not in the repos, so you get them from, say, Slackbuilds.org. Therefore, bigger packages take a long time to compile.

Gentoo - difficult to set up with all kernel options configured correctly, though after a few times you know that like the back of your hand. Compiles **all** packages, which means installations/updates take a long time.

All of these distros are exteremely stable, and stability is the last issue to not recommend these - it's only the ease of installation of new packages/upgrades.

I use a quintuple boot since I love all of them.

---

### Post by snowpine on 2011-05-17
> **krapp said:**
> LOL, the OP sets the topic, but he doesn't get to redefine truth values.

That the OP asked for "the least buggy distros" and took a half-step toward answering his own question doesn't mean he was taking the right step. If anything it is the divinely enlightened Arch user's responsibility to correct this falsehood.

Please "correct this falsehood" by offering a *positive* recommendation, based on your own personal experience, of which distribution you would recommend and why.

---

### Post by krapp on 2011-05-17
> **manzdagratiano said:**
> Arch... Anybody who says it is not rock solid stable is lying.

My corroboration? I have been regulary using it on my two machines for more than a year, and I have **never** has a **single** problem.

Their wiki is excellent. It is like writings on the wall.

Almost all the packages you can dream of - certainly **all** of what I have dreamed of - it has supported; if not in the main repo, then in the AUR.

It only takes some amount of common sense to not go with dangerous updates - though I have never actually had to bother with such a thing. If you want to be cautious, just click the forums or their website to gaze at the news before hitting pacman -Syu.

Once it is set up, which does not take that long, you barely notice it is Arch you are running. As simple to deal with as Ubuntu.

In fact, I am typing from Arch right now.

Google doesn't lie about broken systems: [http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=site%3Abbs.archlinux.org+broke](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=site%3Abbs.archlinux.org+broke)

I still fail to see how the user at all, whether he can or can't read your holy writ wikis, has anything to do with making a bug free, thoroughly tested distro stable.

---

### Post by krapp on 2011-05-17
> **snowpine said:**
> Please "correct this falsehood" by offering a *positive* recommendation, based on your own personal experience, of which distribution you would recommend and why.

Common sense (as most people in this thread seem to have) dictates that the least bug ridden system will be 1) the most tested one 2) where the installed software is old enough to know that it plays nice with the rest of the system.

If I say Debian, Red Hat, etc., I will be repeating what others have said. For what it's worth I use Debian Testing apt-pinning the Unstable/Experimental repos now, and I don't have any illusions as to its stability facing Stable proper.

---

### Post by snowpine on 2011-05-18
> **krapp said:**
> Common sense (as most people in this thread seem to have) dictates that the least bug ridden system will be 1) the most tested one 2) where the installed software is old enough to know that it plays nice with the rest of the system.

If I say Debian, Red Hat, etc., I will be repeating what others have said. For what it's worth I use Debian Testing apt-pinning the Unstable/Experimental repos now, and I don't have any illusions as to its stability facing Stable proper.

I would tend to agree with your Debian and Red Hat recommendations (see my post #2) and your assertion that using older software is one possible path to "stability." 

However if your hardware is not supported by older kernels/drivers or your favorite applciation has an annoying glitch that's fixed it its latest version, then you might indeed find Debian Stable/Red Hat to be an "unstable" experience indeed!

As an example from my personal experience, when I installed CentOS (a very "stable" distribution) on my netbook, it had suspend/hibernate issues that frustrated me to no end. The more recent distributions I've tried (such as Arch) do not suffer from this "instability."

---

### Post by kk0sse54 on 2011-05-18
> **manzdagratiano said:**
> Arch... Anybody who says it is not rock solid stable is lying.

My corroboration? I have been regulary using it on my two machines for more than a year, and I have **never** has a **single** problem.


"Works For Me" (TM) :roll:

---

### Post by J. Sloan on 2011-05-18
> **krapp said:**
> ArchFans deserve zero slack seeing as they've nearly monopolized the channels of communication in the FLOSS community.

In what land except ArchLand is Arch the answer to: "I'm looking to try out some of the least buggy distros you can think of. I guess I'm trying to say that I'm looking for more stable and thoroughly-tested distros, rather than more bleeding-edge distributions."

I'm not sure where you got the idea that a rolling distro can't be, or rather equates to, not being stable. Testing goes into the packages before they are added to the repos, so "bleeding-edge" does not mean "unstable". Rather, it means that the packages are available quicker. Arch is as stable as the user wants it to be, simply put. It's a polite way of saying that Arch is idiot-proof. You may not agree with that or even like it, but I have yet to see you point to any relevant facts that dispute it (hint: your rants don't count as relevant facts).  Arch is very explicit about it's philosophy which gives the user the freedom to design the system they want; as Arch says, it is *code-correctness* over (user) convenience.  

I find stability in minimalism and elegance, and yes, with Arch, the user is greatly responsible for that.  I would recommend Arch to anyone looking to learn a bit more about the Linux OS and who really wants to get down and dirty and have a system that is both stable and fast, as well as up to date.  Others disagree and that's fine.  The great thing about Linux is that there are many different distros which user's can enjoy.  

By the way, your google search for  **site:bbs.archlinux.org broke** netted "About 31,700 results (0.09 seconds)"

A search for **site:ubuntuforums.org broke** netted "About 272,000 results (0.06 seconds)"

All kinds of issues with Unity, upgrades, xfce, etc (also, look how many of the issues were solved in the search results for Arch). Arch pwns Ubuntu again! :) Just joking of course. Certainly breakage isn't just privy to rolling distros!  Good day, I've lurked here for three years and I shall resume lurking mode again. :)

---

### Post by NightwishFan on 2011-05-18
> **J. Sloan said:**
> I'm not sure where you got the idea that a rolling distro can't be, or rather equates to, not being stable.

[QUOTE="Dictionary"]Stable: Resistant to change of position or condition; not easily moved or disturbed[/QUOTE]

ie: Not Arch... ):P

---

### Post by krapp on 2011-05-18
Re. the inherent instability of rolling releases, I give up. Nearly every other post by an Arch partisan quotes the Arch Way in full, no matter it usually implies, as it does here, exactly the opposite of what the Arch partisan wishes to argue. I'll drop this now so as to not hear the words Linux and simple and elegant and vanilla and pure near other again.

I turned to Google because the Arch forums search function sucks; the search itself was a response to a comment above, "Arch... Anybody who says it is not rock solid stable is lying."

I don't run Ubuntu, nor do I claim Ubuntu to be stable, nor bug free, so I'm not sure what you're trying to accomplish there.

Edit: From the newly published (I think!) [Arch Way 2.0]("https://wiki.archlinux.org/index.php/The_Arch_Way_v2.0"):

> Elegant combining simplicity, power, effectiveness, a quality of neatness and **an ingenious grace of design**
The French aviator, adventurer, and author Antoine de Saint-Exupéry gave us perhaps the best definition of engineering elegance when he said “A designer knows he has achieved **perfection** not when there is nothing left to add, but when there is nothing left to take away.”
It is slightly **more important to be simple than elegant**.


Just threw up in my mouth/thought I was reading an advertisement for a tacky watch.

---

### Post by J. Sloan on 2011-05-18
> **krapp said:**
> 
Just threw up in my mouth/thought I was reading an advertisement for a tacky watch.

You have failed to provide any relevant facts that would support the idea or claim that Arch is not stable.  None.  I get that you don't like Arch, your comments reveal that much. Obviously, some Arch user pissed in your Wheaties at some point in your life. But aside from your personal distaste, I find it incredulous on your part to make any claims about Arch since your  opinions lack any experiential data/facts to take what you are saying, seriously.  As mentioned, packages go through plenty of testing before they are released to the repos so the confusion of "bleeding edge" and "unstable" are your confusions.

---

### Post by krapp on 2011-05-18
Well you could begin by recognizing that I never said Arch was not stable. Rather I objected most immediately to its being brought up in a thread requesting suggestions for the most bug-free and stable distro, and more generally to the attitude that Arch is the answer to everything, even when what you're looking for (i.e. well patched software far downstream) is exactly what Arch seeks to avoid providing. The answers were obvious enough that this thread wouldn't have gotten past the 3rd page if it hadn't been veered off track by the recital of Arch mantras. And I find it laughable that you should call attention to my lack evidence when the burden is on you to disjoin a connection that's pretty well seared in everyone else's mind. Must be the Arch Way or something.

---

### Post by SynonM on 2011-05-18
This forum is for Ubuntu right? ;)

It says so at the top in your address bar.

---

### Post by el_koraco on 2011-05-18
Fedora is also rock solid, especially with Rawhide enabled. You just need to set it up good. Also, one can suggest openSUSE Tumbleweeds with Factory repos for kicks.

---

### Post by NightwishFan on 2011-05-18
Debian Experimental:
> Warning: This package is from the experimental distribution. That means it is likely unstable or buggy, and it may even cause data loss.

= Less up to date than Arch. :P

---

### Post by J. Sloan on 2011-05-18
> **SynonM said:**
> This forum is for Ubuntu right? ;)

It says so at the top in your address bar.

This is the **Other OS/Distro Talk** part of the forum. ;)

---

### Post by J. Sloan on 2011-05-18
> **krapp said:**
> Well you could begin by recognizing that I never said Arch was not stable. Rather I objected most immediately to its being brought up in a thread requesting suggestions for the most bug-free and stable distro, and more generally to the attitude that Arch is the answer to everything, even when what you're looking for (i.e. well patched software far downstream) is exactly what Arch seeks to avoid providing. The answers were obvious enough that this thread wouldn't have gotten past the 3rd page if it hadn't been veered off track by the recital of Arch mantras. And I find it laughable that you should call attention to my lack evidence when the burden is on you to disjoin a connection that's pretty well seared in everyone else's mind. Must be the Arch Way or something.

You have very strongly implied that Arch is not stable, here are some of your words:

*He said very stable.*

*I don't get why Arch fanatics have to make claims for Arch beyond what even Arch claims for itself (which is a whole lot).*
[I]
You know very well rolling distributions shipping new software are not stable distributions stuck with old software. Don't try to make them out to be the same thing in the proverbial some-other-user's experience, whose years sitting under a tree meditating upon the Arch Way made Arch just work for him.[/I]

*That the OP asked for "the least buggy distros" and took a half-step toward answering his own question doesn't mean he was taking the right step. If anything it is the divinely enlightened Arch user's responsibility to correct this falsehood.*

[I]
Google doesn't lie about broken systems: [http://www.google.com/search?sourcei...inux.org+broke](http://www.google.com/search?sourcei...inux.org+broke)

I still fail to see how the user at all, whether he can or can't read your holy writ wikis, has anything to do with making a bug free, thoroughly tested distro stable.[/I]

The implications of your statements are very clear, and there is no need to read between the lines.  Contrary to what you are claiming about who has the onus of the burden of proof here, it is the positive claimant that does.  You are the one making these claims, and contrary to your claims there are the masses of Arch users who have experiential evidence to support the claim that Arch is stable.  The only thing that you have proffered is a google link and in your words, *Common sense (as most people in this thread seem to have) dictates that the least bug ridden system will be 1) the most tested one 2) where the installed software is old enough to know that it plays nice with the rest of the system.*

I'm still waiting for one piece of fact that you can provide that would support the rhetoric that you keep typing on your keyboard.  So far, you are lacking, and for a guy who hasn't even used Arch, your rhetoric is laughable.  I have used Arch and Ubuntu and Debian, and Slackware, and lot's of others.  I can tell you that Arch has been just as stable as any of them so long as you set up your system to be stable.  Again, before packages are added to the repos, they get plenty of testing.  Arch would not be so big if it were a bleeding edge "buggy" OS. It's user's have found it to be as stable as anything out there.

---

### Post by J. Sloan on 2011-05-18
> **NightwishFan said:**
> Debian Experimental:


= Less up to date than Arch. :P

Less up to date is not the same as "less" tested.  Debian Experimental is much different than Arch in that respect.  You guys should at least understand a little about other distros before you make claims about them. ;)

---

### Post by krapp on 2011-05-18
> **J. Sloan said:**
> The implications of your statements are very clear, and there is no need to read between the lines.

By definition implications are always between the lines, but that is neither here nor there as I made my working distinctions clear from my first posts. Unless you recognize the nature of my objection (I wouldn't have made it so forcefully if it wasn't as obvious as it was: in sum, nobody would run Arch on a computer which requires absolutely stable bug-free software) I end this exchange here. I'm acquainted with some of the bizarre household truths held in ArchLand, but not this understanding of debate where it is my responsibility to rigorously disprove the outlandish beliefs of what is clearly a minority. After all it was you who set out to enlighten us all about the novel way in which Arch understands "stable." If Arch were stable in the way Solaris, the BSDs, Debian and Red Hat have understood it for decades it wouldn't need to resort to such formulations as "it's as stable as you make it." This is akin to making the disclaimer often heard in connection with Debian Unstable ("you break it, you get to keep the pieces") into a virtue.

---

### Post by krapp on 2011-05-18
> **el_koraco said:**
> Fedora is also rock solid, especially with Rawhide enabled. You just need to set it up good. Also, one can suggest openSUSE Tumbleweeds with Factory repos for kicks.

:lolflag:

---

### Post by snowpine on 2011-05-18
This is a very frequent debate that comes around every month or so. It all comes down to a question of semantics...

"Stable" has a specific meaning within the Linux world. A "stable release" is one that will have no major changes after its release date, only bug fixes and security patches. 80-90% of distros fall into this category (also referred to as "fixed release" or "time-based release"), including Ubuntu, Debian, Fedora, Red Hat, etc. and Krapp is absolutely correct that Arch cannot be considered "stable" by this definition.

However in layman's terms "stable" has a different meaning that I think we all understand: reliable, dependable, well-engineered, secure, bug-free, and not prone to crashes, freezes, or loss of data. 

Now when someone like the OP asks "which distro is more stable?" it's pretty clear to see the second definition is implied. If you wrongly assume the first definition, the question becomes meaningless, because "stable release" is a binary state--Red Hat and Fedora are "equally stable" because both use the same fixed release model--and you end up with the circular argument that "rolling release is not stable because it is constantly rolling."

But if you use the second definition of "stable"--an operating system that makes you feel confident and relaxed because you know it will reliably meet your needs over time--then I would argue there are two different paths to achieve that. Think of the concept of yin and yang if you will, or static and dynamic. The static path is to freeze something in time and test, patch, poke, and prod until it is "perfect." The dynamic path is to have faith that software generally gets better over time, an evolutionary process that creates a "better monkey" with each iteration.

Certainly the testimonials I have read, based on posters' personal experience, suggest that each path has its happy travelers.

---

### Post by krapp on 2011-05-18
> **snowpine said:**
> This is a very frequent debate that comes around every month or so. It all comes down to a question of semantics...

"Stable" has a specific meaning within the Linux world. A "stable release" is one that will have no major changes after its release date, only bug fixes and security patches. 80-90% of distros fall into this category (also referred to as "fixed release" or "time-based release"), including Ubuntu, Debian, Fedora, Red Hat, etc. and Krapp is absolutely correct that Arch cannot be considered "stable" by this definition.

However in layman's terms "stable" has a different meaning that I think we all understand: reliable, dependable, well-engineered, secure, bug-free, and not prone to crashes, freezes, or loss of data. 

Distributions used on servers wouldn't promote themselves as appropriate for servers if they didn't think of themselves in your "layman's terms" as well.

---

### Post by el_koraco on 2011-05-18
> **snowpine said:**
> circular argument "rolling release is not stable because it is constantly rolling."


I don't see anybody making that kind of argument. User experiences suggest that a rolling release model in the Linux world is less stable, because it constantly brings in new packages that can't be tested to the same degree as those in the fixed releases. I say the rolling release model in the Linux world, because the nature of development is much different in the BSD world. It's not yin and yang, if the rolling release model was more stable, Red Hat and Novell would be using it in their enterprise versions. And I'm pretty sure the guys at CERN don't dabble in pop psychology when building their distribution of Linux.

---

### Post by fuduntu on 2011-05-18
> **snowpine said:**
> Just plug into a wired ethernet connection temporarily and fix your wifi, it should be easy. If you want to tell us which wifi card you have, maybe one of us can help you. :)

It's a shame to limit yourself to "distros that support non-free hardware out-of-the-box" because that basically means 1) distros that operate out of foreign countries with weak software patent laws; or 2) distros that are so small/unpopular that they "fly under the radar." Most of the reputable top distros (Ubuntu, Debian, Fedora, Red Hat, etc.) take free vs. non-free software seriously, as they should. :)

This isn't true, many of the non-free packages are free to distribute legally.  Sometimes it means the source isn't available, and sometimes it means that one must go get a distribution license.  It doesn't though mean that they "operate out of foreign countries".

---

### Post by SynonM on 2011-05-18
> **J. Sloan said:**
> This is the **Other OS/Distro Talk** part of the forum. ;)

right 
opps...

:popcorn:

Anybody here try Haiku ? I was looking at it, is it good...?

---

### Post by krapp on 2011-05-18
Start a new thread SynonM here. There's a few Haiku ones from not too far back if you want to do a few searches.

---

### Post by snowpine on 2011-05-18
> **el_koraco said:**
> I don't see anybody making that kind of argument. User experiences suggest that a rolling release model in the Linux world is less stable, because it constantly brings in new packages that can't be tested to the same degree as those in the fixed releases. I say the rolling release model in the Linux world, because the nature of development is much different in the BSD world. It's not yin and yang, if the rolling release model was more stable, Red Hat and Novell would be using it in their enterprise versions. And I'm pretty sure the guys at CERN don't dabble in pop psychology when building their distribution of Linux.

I definitely agree with you (I am primarily a Debian Stable user, and if you look at my post #2, my personal recommendations were Debian, Ubuntu LTS, Slackware, or CentOS) however there is a strong counter-argument that "rolling release is the shortest path to upstream improvements, bug fixes, and security patches." 

Certainly I have read enough "Arch has been very stable for me" testimonials (verified by my own experience) to see the merit of both paths.

---

### Post by snowpine on 2011-05-18
> **fuduntu said:**
> This isn't true, many of the non-free packages are free to distribute legally.  Sometimes it means the source isn't available, and sometimes it means that one must go get a distribution license.  It doesn't though mean that they "operate out of foreign countries".

You're right--my claim was pretty much baseless--just a personal observation that the US-based distros I've used seem "stricter" about the free/nonfree issue than the European-based. Could just be coincidence... (and veering quite off-topic)

What I meant to say was, it's a shame to pass up an otherwise ideal, stable distro because of an easily-remedied hardware issue.

---

### Post by fuduntu on 2011-05-18
> **snowpine said:**
> You're right--my claim was pretty much baseless--just a personal observation that the US-based distros I've used seem "stricter" about the free/nonfree issue than the European-based. Could just be coincidence...

It is more of a philosophy issue than a legal or technical issue.  In most cases it's pretty straightforward and simple to get the licences.

I have several of them for Fuduntu.

---

### Post by el_koraco on 2011-05-18
> **snowpine said:**
> there is a strong counter-argument that "rolling release is the shortest path to upstream improvements, bug fixes, and security patches." 


Doesn't the most amount of bug fixes and security patches come from paid developers from Red Hat, Novell, and volunteers from Debian, which are sent back upstream?

---

### Post by snowpine on 2011-05-18
> **el_koraco said:**
> Doesn't the most amount of bug fixes and security patches come from paid developers from Red Hat, Novell, and volunteers from Debian, which are sent back upstream?

I assume that is a rhetorical question, because I certainly don't know the answer. :) As I mentioned several times, I'm primarily a Debian user, so obviously I am incredibly grateful to the Debian volunteers who make it possible.

I think however that's a separate question from whether or not Distro X is stable for the end user. As a thought experiment, it's easy to imagine a stable and well-engineered distro whose community happens to be selfish about sharing their discoveries.

---

### Post by snowpine on 2011-05-18
> **fuduntu said:**
> It is more of a philosophy issue than a legal or technical issue.  In most cases it's pretty straightforward and simple to get the licences.

I have several of them for Fuduntu.

Cool, thanks for clarifying from somebody "in the know." I keep meaning to try Fuduntu one of these days, I like the concept. :)

---

### Post by fuduntu on 2011-05-18
> **snowpine said:**
> Cool, thanks for clarifying from somebody "in the know." I keep meaning to try Fuduntu one of these days, I like the concept. :)

Once you try Fuduntu you'll never want .. uhh Windows? /joke

:D

---

### Post by deadalus.globalnode on 2011-05-18
Putting "looking for a <type> of linux distro" is probably one of the best ways to get a reply :) . Any way, I highly recommend Slackware, CentOS, or freeBSD. While freeBSD is not linux and is a bit more advanced than many other distros, It is very very stable. At the same time it is quite fast to.

---

### Post by el_koraco on 2011-05-18
> **snowpine said:**
> I think however that's a separate question from whether or not Distro X is stable for the end user.

Well, the reason Red Hat and Novell, even Cannonical at times, put such efforts into fixing bugs upstream is so that their respective distributions can benefit from those fixes. Running a rolling distribution, or even a stable release, but bleeding edge one, doesn't mean you're closer to the source of bug fixes, but closer to the source of new bugs :D

I mean, that's well understood, and the only reason we're even having this discussion is that a few guys here had the need to make the claim that Arch, as a bleeding edge rolling distro, is something to recommend to people who want high grade stability.

---

### Post by snowpine on 2011-05-18
> **el_koraco said:**
> I mean, that's well understood, and the only reason we're even having this discussion is that a few guys here had the need to make the claim that Arch, as a bleeding edge rolling distro, is something to recommend to people who want high grade stability.

I respect that opinion. :)

---

### Post by J. Sloan on 2011-05-18
> **krapp said:**
> By definition implications are always between the lines, but that is neither here nor there as I made my working distinctions clear from my first posts. Unless you recognize the nature of my objection (I wouldn't have made it so forcefully if it wasn't as obvious as it was: in sum, nobody would run Arch on a computer which requires absolutely stable bug-free software) I end this exchange here. I'm acquainted with some of the bizarre household truths held in ArchLand, but not this understanding of debate where it is my responsibility to rigorously disprove the outlandish beliefs of what is clearly a minority. After all it was you who set out to enlighten us all about the novel way in which Arch understands "stable." If Arch were stable in the way Solaris, the BSDs, Debian and Red Hat have understood it for decades it wouldn't need to resort to such formulations as "it's as stable as you make it." This is akin to making the disclaimer often heard in connection with Debian Unstable ("you break it, you get to keep the pieces") into a virtue.

Once again, you are missing the point of the Arch philosophy and abusing terms here.  First, stability is definable in various ways.  Does a user want a desktop enviroment, a server, or something else?  The answer to that question will invariably play into what we mean by stable so obviously asking what distros are stable is a loaded question open to various answers. Secondly, I have provided reasons why Arch is stable.  There is both the user experiences and the fact that with Arch, the user can make the system as stable as they like.  Arch explains this very well:

[I]A) The long and short answer is: It is largely as stable as you make it.

You assemble your own Arch system, atop the simple base environment, and you control system upgrades. (Obviously, a larger, more complicated system incorporating multitudes of packages, multiple toolkits and desktop environments would be more likely to experience configuration issues due to upstream changes than a slimmer, more simple system would.) Arch is targeted at capable, proactive users. General UNIX competence and good system maintenance and upgrade practices also play a large role in system stability. Also recall that Arch packages are predominantly unpatched, so most application issues are inherently upstream.

Therefore, it is the user who is ultimately responsible for the stability of his own rolling release system. The user decides when to upgrade, and merges necessary changes when required. If the user reaches out to the community for help, it is often provided in a timely manner. The difference between Arch and other distributions in this regard is that Arch is truly a 'do-it-yourself' distro; complaints of breakage are misguided and unproductive, since upstream changes are not the responsibility of Arch devs. [/I]

Also, see here:

[https://wiki.archlinux.org/index.php/Enhancing_Arch_Linux_Stability]("https://wiki.archlinux.org/index.php/Enhancing_Arch_Linux_Stability")

[I]However, Arch is inherently stable due to its commitment to simplicity in configuration, coupled with a rapid bug-report/bug-fix cycle, and the use of unpatched upstream source code. Thus, by following the advice below on setting up and maintaining Arch, the user should be able enjoy a very stable system. Furthermore, advice is included that will ease system repair in the event of a major malfunction.

How stable can Arch Linux really be? There are numerous reports in the Arch forums of skilled system administrators successfully using Arch for production servers. Archlinux.org is one such example. On the desktop, a properly configured and maintained Arch installation can offer excellent stability. [/I]

Furthermore, ArchServer is offered as a more stable distro designed for server use.

This idea that you have been implying that Arch is somehow inferior in regards to stability is nonsense.  And furthermore, you've yet to offer any factual data to account for claims which makes them nothing other than rhetoric. All the more so (being polite) given that you have no experience with Arch and are basing your opinion on your limited and constrained view of what is entailed by stability.

---

### Post by NightwishFan on 2011-05-18
We like Arch here.. Personally I just do not see why it has to be the subject of so many fairy tales though. It is just another distribution. (Though a good one I am sure)

---

### Post by manzdagratiano on 2011-05-18
> **J. Sloan said:**
> Once again, you are missing the point of the Arch philosophy and abusing terms here.  First, stability is definable in various ways.  Does a user want a desktop enviroment, a server, or something else?  The answer to that question will invariably play into what we mean by stable so obviously asking what distros are stable is a loaded question open to various answers. Secondly, I have provided reasons why Arch is stable.  There is both the user experiences and the fact that with Arch, the user can make the system as stable as they like.  Arch explains this very well:

[I]A) The long and short answer is: It is largely as stable as you make it.

You assemble your own Arch system, atop the simple base environment, and you control system upgrades. (Obviously, a larger, more complicated system incorporating multitudes of packages, multiple toolkits and desktop environments would be more likely to experience configuration issues due to upstream changes than a slimmer, more simple system would.) Arch is targeted at capable, proactive users. General UNIX competence and good system maintenance and upgrade practices also play a large role in system stability. Also recall that Arch packages are predominantly unpatched, so most application issues are inherently upstream.

Therefore, it is the user who is ultimately responsible for the stability of his own rolling release system. The user decides when to upgrade, and merges necessary changes when required. If the user reaches out to the community for help, it is often provided in a timely manner. The difference between Arch and other distributions in this regard is that Arch is truly a 'do-it-yourself' distro; complaints of breakage are misguided and unproductive, since upstream changes are not the responsibility of Arch devs. [/I]

Also, see here:

[https://wiki.archlinux.org/index.php/Enhancing_Arch_Linux_Stability](https://wiki.archlinux.org/index.php/Enhancing_Arch_Linux_Stability)

[I]However, Arch is inherently stable due to its commitment to simplicity in configuration, coupled with a rapid bug-report/bug-fix cycle, and the use of unpatched upstream source code. Thus, by following the advice below on setting up and maintaining Arch, the user should be able enjoy a very stable system. Furthermore, advice is included that will ease system repair in the event of a major malfunction.

How stable can Arch Linux really be? There are numerous reports in the Arch forums of skilled system administrators successfully using Arch for production servers. Archlinux.org is one such example. On the desktop, a properly configured and maintained Arch installation can offer excellent stability. [/I]

Furthermore, ArchServer is offered as a more stable distro designed for server use.

This idea that you have been implying that Arch is somehow inferior in regards to stability is nonsense.  And furthermore, you've yet to offer any factual data to account for claims which makes them nothing other than rhetoric. All the more so (being polite) given that you have no experience with Arch and are basing your opinion on your limited and constrained view of what is entailed by stability.

+10 =D>

Indeed, I would go so far as to say that ***any*** distro, aside from release-critical bugs, is as stable as you want it to be. Ubuntu usually never makes releases with release-critical bugs either - all such bugs - the ones that are known prior to a release - are either fixed before the release or the offending packages are shipped at an earlier version. Arch itself never has any critical bugs filter down from their testing repo into the mainstream one. If the word ``stable" is to be abused as ``remain stagnant", then what distro cannot be made stable?

One could indeed install Debian Stable, and stick to it, or Ubuntu Lucid Lynx, and stick to that... and there people have the epitome of stability. I have thought about that myself. However, I like to experience new features when they come out, which is the reason I upgrade Ubuntu, as well as stick to Arch, as well as run Debian Sid. Upgrades can indeed break your system, but never if you have a watchful eye - just wander to the forums, and see what is up with the new upgrade; if problematic, just don't! - at least until things settle down, and not even the most unstable of distros would break! Debian Sid, by ***very definition*** **unstable**, has never broken down on me, thanks to `apt-listbugs'. Arch has never broken down, since I always take a look at the news before I upgrade, and there I have two very stable systems.

And yet, I am the same person who broke Ubuntu Jaunty a little less than two years ago, because I mixed Karmic sources to pull in newer packages - be foolhardy, and even Debian stable will break for you and you will get to keep all the pieces.

I **must **reiterate - anybody who does not use Arch and states ``*it is rolling ergo unstable*", is plainly and simply, **lying**. In fact, in my personal opinion, it is probably the one distro of choice I would recommend to people who do not want headaches with bugs; more so than Slackware, because no matter how much I love Slackware, installing packages with their dependencies can become a headache for n00bs - of course one may use `slapt-get', but that's not what real Slackers do is it? And Gentoo, though it has an excellent package manager, it just takes too friggin' long to update. Arch brings the perfect balance of a stable system with almost-bleeding-edge updates.

As a matter of fact, I am contemplating replacing Ubuntu on my Fiancee's netbook - rather than upgrade it from Maverick to Natty - with Arch at this moment - she cannot be bothered with the few bugs that remain, and very much likes to use the ``latest and the greatest" - and more brownie points for me if I can demonstrate to her that her GNU/Linux install is better than her Windows install, which she already half-believes with Ubuntu. Arch, as far as I use it and I use it for a **lot** of things, has **none** off the top of my head.

---

### Post by boydrice on 2011-05-18
> **manzdagratiano said:**
> 

I **must **reiterate - anybody who does not use Arch and states ``*it is rolling ergo unstable*", is plainly and simply, **lying**. In fact, in my personal opinion, it is probably the one distro of choice I would recommend to people who do not want headaches with bugs; more so than Slackware, because no matter how much I love Slackware, installing packages with their dependencies can become a headache for n00bs - of course one may use `slapt-get', but that's not what real Slackers do is it? And Gentoo, though it has an excellent package manager, it just takes too friggin' long to update. Arch brings the perfect balance of a stable system with almost-bleeding-edge updates.
.
I like Arch quite a bit, it is a great distro however I have to disagree with this statement.  Arch has more breakage than Slackware, period.  Arch has lessened the frequency of breakage significantly from the earlier days but there is still breakage. Slackware has a reputation as one of the most stable distributions around and a nearly 2 decade old track record to back it up.  I also think the whole dependency issue is very overblown.  A full install of Slackware contains most deps you will need and if you use Slackbuilds.org all the deps are called out in each readme.  Unless the user just installs random packages off the net then of course they will end up in trouble, just like if an Arch user blindly runs pacman -Syu everyday.  

There is a method to the madness why most sysadmins want a system with the least amount of change possible.  Change introduces a greater possibility of breakage or error.  Now can change be navigated safely by an experienced admin, sure, but change introduces risk to a functioning system.

Again not saying is bad it is not but you won't find it powering a stock exchange, or a fortune 500 company's webserver and there is a reason for that.

---

### Post by manzdagratiano on 2011-05-19
I never disputed the issue that there is breakage - of course there is breakage, and more so in Arch than in Slackware, which is certainly rock-solid stable.

I install stuff from the Slackbuilds.org repository all the time, using sbopkg. This however does not change the fact that all packages are compiled, and it may take a very long time depending on what is being installed, and the everyday ``power" user (whatever that really means) may not have stomach for that.

Also, even though Slackbuilds.org lists all the dependencies of a package, the trouble is with **recursive dependencies** of those dependencies, which of course the main package does not list, while the respective dependency packages of course do. This leads you in a tree down to the last one - try installing the main package - if it has a dependency, try installing that. If that in turn has a dependency, try installing that, and so on till the one whose dependencies are satisfied. This does not have to be done manually, but significantly more work than what ``apt-get" or ``pacman" ask from the user (even ``yaourt", which does compile packages, takes care of all dependencies recursively)

Slackware has worked great for me, and one could argue that since you compile all the packages **not** in the main repo from source, it is as bleeding edge as it gets. However, the long compile times for these packages needed for every day use, and there are many that are not in the main tree, keep me from using it as my primary OS out of all five. It has usually been Ubuntu that I use most of the time, though these days I have been mainly using Arch at work.

I personally think it is plain ignorance that is leading to Arch not powering some well-known limelight cluster, but it is just a matter of time. Debian stable has been the best thing one can do to a server, and Arch is quite up there to give it competition. Moreover, the archlinux.org server is itself powered by Arch, and that boasts of something.

---

### Post by wolfen69 on 2011-05-19
Debian command line install. ;)

---

