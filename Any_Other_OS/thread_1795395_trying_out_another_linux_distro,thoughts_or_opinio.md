---
title: "trying out another linux distro,thoughts or opinions ?"
date: 2011-07-02
forum: Any Other OS
---

### Post by whoopwhoopgod on 2011-07-02
hi guys :)


i'm thinking of using another distribution,ubuntu is nice but i dont feel like i'm learning much:( i wanted to try linux because of

1)stability
2)free stuff(admit it,its a factor)
3)to learn stuff about computers,its the way of the future :D
4)to be able to fix up my damn computer if there is a  error

i'm currently using ubuntu 11.04(classic mode) and i think i need to decide soon as i heard ubuntu will only offer unity in the future(its not my kind of thing)

i am thinking of using a rolling distro ? it appeals to me as i hate installing from a live cd as i always want to format my whole system again before installing or ugrading to the new version and i cant make the CD installer for some reason(please dont ask)

i'm thinking of either
1)openSUSE
2)Arch
3)Sabayon
4)Debian(is it a rolling distribution ?)

any opinions/suggestions/criticisms are appreciated

i'm having college soon so i'm thinking of installing a new one,maybe an easy one but when my holidays start i wont mind spending the time to get my system up and running the way i want it

---

### Post by whoopwhoopgod on 2011-07-02
hi guys :)


i'm thinking of using another distribution,ubuntu is nice but i dont feel like i'm learning much:( i wanted to try linux because of

1)stability
2)free stuff(admit it,its a factor)
3)to learn stuff about computers,its the way of the future :D
4)to be able to fix up my damn computer if there is a  error

i'm currently using ubuntu 11.04(classic mode) and i think i need to decide soon as i heard ubuntu will only offer unity in the future(its not my kind of thing)

i am thinking of using a rolling distro ? it appeals to me as i hate installing from a live cd as i always want to format my whole system again before installing or ugrading to the new version and i cant make the CD installer for some reason(please dont ask)

i'm thinking of either
1)openSUSE
2)Arch
3)Sabayon
4)Debian(is it a rolling distribution ?)

any opinions/suggestions/criticisms are appreciated

i'm having college soon so i'm thinking of installing a new one,maybe an easy one but when my holidays start i wont mind spending the time to get my system up and running the way i want it

please dont ban me,i'm just trying to put them in the right prefixes,i'm not trying to spam the boards or anything

---

### Post by mikewhatever on 2011-07-02
If you don't like Unity, but still want to use the latest release of *buntu, try Kubuntu, Xubuntu or Lubuntu, none of them have Unity. If you are not stuck on the latest release, use Ubuntu 10.04.
For a rolling distro, try PClinux or Arch. Debian is not a rolling release distro, unless you use the testing or unstable branch. Arch and Debian are a bit harder to use, especially if you are new to Linux. OpenSuse and Sabayon are nice, kind of similar to Ubuntu, but I don't know for how long they'll keep using Gnome2, in fact, that's true for all distros, since Gnome2 has been discontinued by the Gnome Foundation. Do you know if you like Gnome3 yet?

---

### Post by in-dust-rial on 2011-07-02
hey there,

lets work through your goals

1)stability
well, stability is relative: but i think a rolling release is always less stable than a stable (point) release. so maybe you dont want to use a rolling release?

2)free stuff(admit it,its a factor)
thats available in all distros you mentioned above

3)to learn stuff about computers,its the way of the future
to learn about the system is maybe tightly bound to mess with the system. maybe you want to install linux in a virtual machine (virtualbox) to test selveral distributions and how they work.
I think the most valuable way to learn is to built linux fram scratch (so build your own distribution). 

4)to be able to fix up my damn computer if there is a error
i think this ability comes with reading the source code of programs and the possibility to change the code and compile again. so that would be a plus for gentoo.
however, that might be very stressful and painful. 
debian is the next step coming from ubuntu i would say.
messing with the slightly more complex package dependencies is already quite a learning experience!

debian is available as testing(rolling release) and stable (point release). so debian has both aspects.

if i were you i would download a virtual machine and test some distributions which combine source and package trees. 
(some BSD and i think gentoo as well(?))
in this way you can learn about the traditional make-install way a bit and the more modern binary way.

when you found a distribution which is not too complex but still interesting install it to a partition of your system.
link your home folder to another partition (by 'fstab').
then you can easily install new distribution but keep all the settings (not the /etc/ settings... maybe link them too) and files unchanged.

so a new install is a matter of a view minutes...
and also u can use tools to make install from USB.
linux usb creater for example. linuxliveusb DOT com

good luck

---

### Post by wolfen69 on 2011-07-02
I hear Debian Testing is a rolling release. Don't let the name fool you, as it is pretty stable.

---

### Post by ckop64 on 2011-07-02
I'm a long time distrohopper so hopefully I can give you** my personal opinion** on the distros you asked about.

1. openSUSE - Ok, so the rolling release branch os SUSE (Tumbleweed) is still kind of immature, so I wouldn't advise you using that (if you are a linux rookie). Overall if your goal is to learn more about Linux and generally how computers work SUSE is definetely not the way to go since --just like Ubuntu-- it is more geared towards average desktop usage and GUI configuration "for dummies".

2. Arch - My absolute favorite distro, has a very well established community and a clear vision of simplicity (from the technical standpoint: see "The Arch way" -- Arch accomplishes on this behalf extremely well), although don't forget that Arch will probably never be as stable and polished like the mainstream distros out there, and the philosophy of including untested or barely tested software in the main repositories often result in an unusable, and/or unstable system, with lots of bleeding-edges. I also wanted to mention AUR as one of the most awesome things ever happened to arch. They have a decent package manager as well. The distro itself can teach you a lot about configuring and building your stuff manually.

3. Sabayon - I've tried it only once, and meh... I didn't like it. I mean it is definitely not bad, It's just not my style. One of the weakest points (again, in my opinion) is the package manager entropy, which is a quite crucial piece of software for a rolling release distribution. They are based on Gentoo, which means an additional level of speed, and they have every package precompiled in their repositories for convenience, so you don't have to spend hours (days?) with compiling KDE for example. If you truly want to learn something about how Linux/UN*X works please just go with Gentoo. It WILL be a pain int the b*tt, but the end result is definitely worth it.

4. Debian (Testing) - Debian is a rock solid, old and well supported distribution. Don't let the word 'testing' fool you, it is a lot more stable than most of the top distros out there thanks to the Debian team, who do a really good job at testing, packaging, integrating and fixing upstream software. There is really nothing too much to say, since it probably just works. If you want to learn about Linux, it is not the best choice though, since almost everything is preconfigured, and the install process itself is graphical, so once you get it running its kinda like a stripped down version of Ubuntu. When I tried the last couple times the testing images provided by Debian just didn't work, were broken or buggy, so probably the best experience is installing Linux Mint Debian edition, since it is basically the same exact distro, plus some added mint stuff (like the mintMenu, or the graphical package manager, which nobody cares about... :).

So that would be it, I hope that I could help you a bit deciding which one is the best for you. write me a pm or reply here if you have further questions.

Cheers, ckop64

---

### Post by whoopwhoopgod on 2011-07-02
@mike , i did try unity actually but it felt weird,it felt slower than just using the classic mode for me.i did try to use and like it honestly,i'm not just being a sheep and following what other people say

i've never actually tried gnome 3 but it looks abit like unity to me,i've watched quite a number of reviews on youtube and i have to say i'm not a big fan of the style of it so i'm thinking of swapping to something like arch where i can customise everything(or so they say)

@in-dust-rial

thanks,i think i will do what you said and try usinga virtual box.anyways i'm off to try and do the installations on virtual box

---

### Post by handy on 2011-07-03
My experience of Arch is that it IS stable. I've experienced very few problems in the life (well over 3 years old now) of my oldest installation & I've been using the git kernel & AMD/ATi driver stack for most of the last 21 months too.

Arch doesn't suit everyone, it is the opposite of Ubuntu, many people really don't like the way Arch does things.

The Arch wiki sets the standard, it is where you look first.

If you do install Arch follow the Beginners' Guide to the letter, don't be put off by the size of that guide, as is jumps you through to where you need to go next.

[https://wiki.archlinux.org/index.php/Beginners%27_Guide](https://wiki.archlinux.org/index.php/Beginners%27_Guide)

---

### Post by lisati on 2011-07-03
Threads merged. Please do not start multiple threads on the same question, it dilutes the community experience.

---

### Post by krapp on 2011-07-03
> **ckop64 said:**
> When I tried the last couple times the testing images provided by Debian just didn't work, were broken or buggy, so probably the best experience is installing Linux Mint Debian edition

I think it's generally recommended that you install Debian Stable, change your /etc/apt/sources.list to Testing and do a full-upgrade to Testing.

---

### Post by snowpine on 2011-07-03
I recommend Ubuntu Long Term Support 10.04. It is 1) very stable; 2) free; 3) a good learning distro; 4) easy to fix due to the excellent documentation on the Ubuntu wiki/help pages and also the wonderful support you'll find on these forums.

10.04 will support the "classic" Gnome 2.x desktop through April 2013. You will be able to easily "roll" to 12.04 (if you choose) when it is released next year.

"Rolling release" distros by definition are not stable and will not support "classic" Gnome 2.x. Rolling release is for users who always want the latest software (i.e. Gnome 3) and new software is generally buggier than older, well-tested, extensively patched software. Also I disagree with the notion that Ubuntu is not a good learning distro. While it's true Ubuntu is very easy for a beginner, it also offers all the standard tools for intermediate/advanced projects. You can learn compiling from source, system administration, networking, virtualization, etc. in Ubuntu without switching distros. :)

---

### Post by maryfrank58 on 2011-07-03
You could install Oracle Virtualbox 4.0 and try out any or all.  Don't forget to download " VirtualBox 4.0.10 Oracle VM VirtualBox Extension Pack" will give you USB support. It allows you to run any distro, windows and my friend even has Mac's os running on it.  It is free!

---

### Post by whoopwhoopgod on 2011-07-03
@snowpine ,i know what you mean but i have a problem burning the .iso file to a cd,so its difficult for me to install one that i want.thats kind of why i want a rolling distro.

---

### Post by snowpine on 2011-07-03
> **whoopwhoopgod said:**
> @snowpine ,i know what you mean but i have a problem burning the .iso file to a cd,so its difficult for me to install one that i want.thats kind of why i want a rolling distro.

If your CD drive is busted, you can install from USB.

Anyway you will also need some way to install from CD or USB if you want to switch distros.

---

### Post by handy on 2011-07-03
> **snowpine said:**
> 
...

"Rolling release" distros by definition are not stable 

I've found Arch to be far more stable & reliable than my experiences with any other of the numerous distros that I have tried, including plenty of Ubuntu.

> **snowpine said:**
> 
and will not support "classic" Gnome 2.x. 

Like Ubuntu does now (2nd choice) which finishes-up in October?

> **snowpine said:**
> 
Rolling release is for users who always want the latest software (i.e. Gnome 3) and new software is generally buggier than older, well-tested, extensively patched software. 

Many rolling release users (myself included) don't use same for that reason, we use it because we don't have to go through all of the hassles of 6 monthly upgrades that so often bring regressions & other troubles. As far as Arch is concerned we get to install just what we want on top of the "Core System" - no more & no less. This also adds to the stability & simplicity of the system.

> **snowpine said:**
> 
Also I disagree with the notion that Ubuntu is not a good learning distro. 

Ubuntu is a great learning distro, it is terrific for getting your feet wet & gaining enough confidence to then be able to go out & explore the other ways people make distros & the BSDs & such. Whilst doing so you grow in experience which gives you the ability to evaluate empirically just what you do & what you don't prefer (for what ever reasons) to be the way you like to interface with your computing life.

> **snowpine said:**
> 
While it's true Ubuntu is very easy for a beginner, it also offers all the standard tools for intermediate/advanced projects. You can learn compiling from source, system administration, networking, virtualization, etc. in Ubuntu without switching distros. :)

Variety is the spice of life, & it teaches us to look at things from different perspectives, which helps us appreciate the positives & negatives of things with a more open mind. :)

---

### Post by snowpine on 2011-07-03
> **handy said:**
> I've found Arch to be far more stable & reliable than my experiences with any other of the numerous distros that I have tried, including plenty of Ubuntu.


Hi Handy, I've been reading and enjoying your posts on these forums for years...

"Stable" to me means "constant, unchanging." A "rolling release" distro is in a continuous state of change, and therefore inherently unstable (by this definition), just a stone that is "rolling" down a hill is not "stable."

I like Arch :) and recommend trying it to anyone who's interested. I agree with you it can be "reliable" in the right hands. In fact I would argue that in certain cases, "unstable" distros can be *more* "reliable" because they get bug fixes, security patches, support for new hardware, etc. sooner than "stable" distros.

In short, I distinguish between "stable" and "reliable" (and don't mean "unstable" as derogatory). 

> **handy said:**
> Like Ubuntu does now (2nd choice) which finishes-up in October?

Ubuntu 10.04 LTS fully supports Gnome 2.x through April 2013, furthermore it is in a "stable" state (no major updates, only bug fixes and security patches).

> **handy said:**
> Many rolling release users (myself included) don't use same for that reason, we use it because we don't have to go through all of the hassles of 6 monthly upgrades that so often bring regressions & other troubles.

Ubuntu LTS is supported 36 months (and 60 months for servers).

> **handy said:**
> As far as Arch is concerned we get to install just what we want on top of the "Core System" - no more & no less. This also adds to the stability & simplicity of the system.

Ubuntu is a great learning distro, it is terrific for getting your feet wet & gaining enough confidence to then be able to go out & explore the other ways people make distros & the BSDs & such. Whilst doing so you grow in experience which gives you the ability to evaluate empirically just what you do & what you don't prefer (for what ever reasons) to be the way you like to interface with your computing life.

Variety is the spice of life, & it teaches us to look at things from different perspectives, which helps us appreciate the positives & negatives of things with a more open mind. :)

I agree 100% with the quoted, as I usually do with your posts. :)

---

### Post by handy on 2011-07-04
Problems arise from time to time in written communication (particularly in forums) as we can have different definitions for the meaning of words.

I still don't completely agree with what you said, but so what!? lol

Forgive the use of the word "crap" I was obviously not feeling particularly articulate at the time of writing. :) 

[edit:] I've edited the original. :oops:

---

### Post by snowpine on 2011-07-04
All is forgiven Handy, I edited my quote of your post too. :) I am primarily a Debian user, so "stable" and "unstable" have a specific, non-judgmental meaning to me. 

Like you, I'm in the situation where I don't use Ubuntu very often, yet here I am on Ubuntu Forums trying to give advice on various topics. Sometimes when the "which distro?" question comes up, I like to play "devil's advocate" and say "have you considered sticking with Ubuntu?" In my perception, these forums have taken a weird turn lately where it's become unpopular/controversial to say "I recommend Ubuntu," or "I like Unity," etc. ;)

---

### Post by handy on 2011-07-04
Cool, & thanks. :)

Well, personally, Ubuntu doesn't suit me, but I still like it, & those that don't can like it or lump it, as I'm pretty sure that Ubuntu has bought more people into the Linux desktop fold from the Windows world (in particular) than any other distro.

As far as Unity goes, that is other people's problem. I've never used it & won't ever use. I'm perfectly happy with Openbox. :)

I don't know, but I suspect that Unity could be part of a plan that works in cahoots with a hardware manufacturer or two re. Netbooks in the future. I think that Canonical is desperately trying to compete in the marketplace. The more funding they get the better off Ubuntu will be in the long run. The alternative is that if Canonical can't support itself, there is a limit to how far ten million dollars goes, which would eventually leave Ubuntu on its own financially.

---

### Post by snowpine on 2011-07-04
I took Unity for a test drive lately and actually quite liked it. It is an improvement over "classic" Gnome for my own personal style anyway. My favorite part was its keyboard-friendliness; it is very straight-forward to hit the Super (Windows) key and start typing the name of an app, much easier than using the mouse to scroll through endless menus and sub-menus!

I also am primarily an Openbox user (though lately experimenting with Ratpoison, fun stuff!) which brings up an interesting question. Most of the people I've heard say "Arch is super-reliable" prefer a minimalist desktop like Openbox, Fluxbox, etc. which of course have a very slow development cycle and few features. 

What about Arch users who prefer Gnome, KDE, etc.? Has the Gnome 2 to Gnome 3 transition gone smoothly, or are Arch Gnome users having similar "growing pains" to the Ubuntu's community switch to Unity?

---

### Post by sidzen on 2011-07-04
Recommend going to [this mirror link]("http://ftp.cc.uoc.gr/mirrors/linux/") and downloading a progression of distros to learn on, starting (as a suggestion) with MEPIS then antiX then more complicated ones like sabayon or salix.

Have fun!!

---

### Post by handy on 2011-07-05
> **snowpine said:**
> 
...

What about Arch users who prefer Gnome, KDE, etc.? Has the Gnome 2 to Gnome 3 transition gone smoothly, or are Arch Gnome users having similar "growing pains" to the Ubuntu's community switch to Unity?

I don't know the answer to that. I rarely have anything to do with the Arch forum these days, apart from my daily checking on Perry3D's AMD/ATi mega-thread to see how things are going on the development front. 

We host Perry's repo at spiralinear.org which at least gives me an opportunity to repay him some for all of the work that he has done for Arch users in particular that use whatever variations of the git kernel & AMD/ATi open-source driver stack.

---

