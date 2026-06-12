---
title: "Trying out Arch - two weeks now"
date: 2008-07-31
forum: Arch and derivatives
---

### Post by rsambuca on 2008-07-31
Just starting out with Arch, and I must say, I am enjoying it so far.  I have a feeling this may take over as my #1 distro.  I guess time will tell.  I'll have to see if there is any blips after package updates/upgrades in the future.

---

### Post by Barrucadu on 2008-07-31
Once you go Arch you can never go back :D

---

### Post by Dr Small on 2008-07-31
It's too late. You have already joined us, and there is no turning back! :D

---

### Post by chucky chuckaluck on 2008-07-31
> **Barrucadu said:**
> Once you go Arch you can never go back :D

i tried to go back, but failed (happily so).

---

### Post by floke on 2008-07-31
You don't want to give up the only distro with post-apocalypseability.

[http://wiki.archlinux.org/index.php/Apocalypse](http://wiki.archlinux.org/index.php/Apocalypse)

---

### Post by K.Mandla on 2008-07-31
Oh, did I ever lol at that ... :biggrin:

---

### Post by beavenburt on 2008-07-31
You're now in Archs power forever. Really, nothing else compares.
I'm running with the beautiful KDEMod, nothing is moving this sucker from my machine.

---

### Post by mips on 2008-07-31
> **rsambuca said:**
> Just starting out with Arch, and I must say, I am enjoying it so far.  I have a feeling this may take over as my #1 distro. 

Another addict!

Repeat after me, "Hi, my name is rsambuca and I'm an Archaholic"

---

### Post by MONODA on 2008-07-31
has anyone tried arch and not fallen in love with it??? :P I heart arch linux :D

---

### Post by rsambuca on 2008-07-31
Well, I don't quite think I am an addict.  Yet anyways.

Question:  Is there a reason why my Arch installation is so much bigger than all of my other ones?  For instance, this Arch install is up to 5.5 GB, whereas my Ubuntu Hardy partition is at 3.1 GB.  Not a big deal for my desktop, but I was thinking of putting Arch on my eee PC 900, and it will definitely make a difference there.

---

### Post by cardinals_fan on 2008-07-31
> **MONODA said:**
> has anyone tried arch and not fallen in love with it??? :P I heart arch linux :D
I tried Arch and left.  Then I returned.  And this time, I'm not leaving :)

---

### Post by sub2007 on 2008-07-31
> **Barrucadu said:**
> Once you go Arch you can never go back :D

I think I've recently found that as well! I switched to Arch about two weeks ago and I think it's amazing, In two weeks (probably faster actually) it's become my favourite distro, Ubuntu is the only distro I could stand to keep on my box for longer than a week until I found Arch. I can't think of anything I don't like about it and I definitely couldn't leave now. I'm also finding that now it's set up (which was actually much less painless than I thought it would be) it's so much easier to maintain and rolling release really clinches it for me, I really like bleeding edge and having something new available every day is a big bonus for me.

I love the fact there's a lot of Arch users here as well, in fact if it wasn't for reading all the positive things said about Arch here I don't think I would ever have tried it.

---

### Post by YodaMstr on 2008-07-31
> **rsambuca said:**
> Well, I don't quite think I am an addict.  Yet anyways.

Question:  Is there a reason why my Arch installation is so much bigger than all of my other ones?  For instance, this Arch install is up to 5.5 GB, whereas my Ubuntu Hardy partition is at 3.1 GB.  Not a big deal for my desktop, but I was thinking of putting Arch on my eee PC 900, and it will definitely make a difference there.

The most probable cause is that you left the installed packages in your cache.  Go to /var/cache/packman/pkg and you'll most-probably find a list of .pkg.tar.gz files.  These are packages that you've installed on your computer, easily accessible if you need to reinstall or roll back.  Chances are, that path is taking up quite a bit of space.  If you want to clean that cache out, run pacman -Scc.  As for your Eee woes, they're unfounded.  I run Arch on my Eee 701 just fine (I had all my applications and such installed at a total of 1.8gb) , so your 900 will be fine.

---

### Post by wolfvorkian1 on 2008-08-01
> **rsambuca said:**
> Just starting out with Arch, and I must say, I am enjoying it so far.  I have a feeling this may take over as my #1 distro.  I guess time will tell.  I'll have to see if there is any blips after package updates/upgrades in the future.

Same concern here but after a couple months, no problems. I've also noticed like you mentioned in a later post - I haven't installed much in Arch yet it is larger than my pretty much stock Xubuntu setup on another hard drive and it is not the cache which is cleaned after each download. 

I like the concept of the rolling upgrades, I believe they call it. That is as long as they don't break things constantly. I really don't like to fiddle that much and if that starts happening I'll use something like Etch or Xubuntu Hardy as my main distro. 

The acid test of course is time. If upgrades don't start hosing my setup, I'll probably never change. Why bother? Linux is Linux. From what I've seen, they're all pretty much the same.

---

### Post by will1911a1 on 2008-08-01
> **YodaMstr said:**
>  space.  If you want to clean that cache out, run pacman -Scc.

I didn't know this and it cleared up a good deal of space for me.  Thanks!

---

### Post by Dr Small on 2008-08-01
I have the space, so I save all my pacman cache, incase something breaks. But then again, there is always ABS ;)

---

### Post by beavenburt on 2008-08-01
> **will1911a1 said:**
> I didn't know this and it cleared up a good deal of space for me.  Thanks!

I didn't know that either. Good tip.

---

### Post by blazercist on 2008-08-01
Since I have all you Arch users captive in this thread lemme ask you... 

Tell me a little bit about Arch, its debian right? so whats the difference ? is it just attractive because you start out with a base and only install the packages you want?  Like build your own distro?

---

### Post by YodaMstr on 2008-08-01
> **blazercist said:**
> Since I have all you Arch users captive in this thread lemme ask you... 

Tell me a little bit about Arch, its debian right? so whats the difference ? is it just attractive because you start out with a base and only install the packages you want?  Like build your own distro?

No, Arch isn't Debian.  Arch uses a rolling release (packages are available for upgrade shortly after they come out) compared to Debian's timed release, which offers the upgrades en masse.  Arch packages are packaged as .pkg.tar.gz compared to Debian's .deb (a technicality, but still).  Arch aims at offering full control over how your system is setup, and leaves everything open to the user by minimizing the GUI (the reasoning behind this is that a GUI may complicate and obscure or altogether remove an option); compare this to Debian's goal of strict adherence to the UNIX and free software philosophies.

Yes, Arch did appeal to me for the "build your own distro" aspect.  It allowed me to have only the packages I wanted, cutting out bloat.  Several other distros offer this, but the compiling of Gentoo didn't appeal to me, and I have no interest in copy/pasting LFS.

---

### Post by blazercist on 2008-08-01
so the pkg.tar.gz files work like debs with "pacman" correct?

You get a basic cli system with an internet connection from the install and you install your own DE or WM ontop of it if you want right?

When you talk of removing the "bloat" does that mean that you aren't wasting harddrive space on apps that you don't use and you get to install the tools that you prefer like say opera instead of firefox? Or does it mean that you actually reduce your memory footprint and CPU usage?

I think I get the "rolling release" thing, its basically just all the packages that have incrementally changed get updated, instead of the ubuntu one where they only change a few packages at a time when they need serious bug fixes or security fixes.  I like this idea that even the little things that I don't pay attention to are updated.

I also like the "build your own distro" idea, I'm contemplating trying Arch out, I'm just worried that it'll be Gentoo-ish and I'll spend the next 2 months compiling junk from source and trying to satisfy dependencies.  What are the repos like? Do they compare in size and variety to say Ubuntu? or will I be searching for, downloading and compiling source from around the web?

Finally, I'm not completely clueless when it comes to linux and the cli, but things like what programs run at startup I do at the GUI and I'm worried that I'll be editing text files constantly whenever I want to make a change.

Can anyone comment on my fear/understanding of these concepts?

---

### Post by YodaMstr on 2008-08-01
> **blazercist said:**
> so the pkg.tar.gz files work like debs with "pacman" correct?

You get a basic cli system with an internet connection from the install and you install your own DE or WM ontop of it if you want right?

When you talk of removing the "bloat" does that mean that you aren't wasting harddrive space on apps that you don't use and you get to install the tools that you prefer like say opera instead of firefox? Or does it mean that you actually reduce your memory footprint and CPU usage?

I think I get the "rolling release" thing, its basically just all the packages that have incrementally changed get updated, instead of the ubuntu one where they only change a few packages at a time when they need serious bug fixes or security fixes.  I like this idea that even the little things that I don't pay attention to are updated.

I also like the "build your own distro" idea, I'm contemplating trying Arch out, I'm just worried that it'll be Gentoo-ish and I'll spend the next 2 months compiling junk from source and trying to satisfy dependencies.

Finally, I'm not completely clueless when it comes to linux and the cli, but things like what programs run at startup I do at the GUI and I'm worried that I'll be editing text files constantly whenever I want to make a change.

Can anyone comment on my fear/understanding of these concepts?

Yes, the installation leaves you with the command line and lets you piece it together from there.

When I talk about removing bloat, it's a little bit of both.  Firefox on Arch isn't going to just magically have a smaller footprint, but, for the most part, I determine what runs when (which generally means smaller footprints compared to pre-built distros).  You can take an install like Debian and "reverse" it down to only what you want to run, but it's the satisfaction of being sure you have it all juuuuust right.  In addition, Arch's packages are optimized for i686 use, so it does strip a bit of size out of installs by removing other architecture information.

Gentoo's compile-from-source installation wasn't much my thing either.  However, you won't have to worry about compiling, as Arch's packages are binary.  If you do decide you want to compile something from source, Arch uses something called ABS (the Arch Build System).  This allows it to compile into a binary.  You get the custom-tailored install of a source install, but the tidiness and ease-of-removal of a package-managed-install.

Startup programs I determine with a GUI as well, so have no fear over things like that.  It doesn't restrict you from using the GUI, it just fosters CLI configuration.  The only thing that you'll edit with a text file in relation to "startup" is which modules to load, in which order, and how.

---

### Post by rsambuca on 2008-08-01
> **YodaMstr said:**
> The most probable cause is that you left the installed packages in your cache.  Go to /var/cache/packman/pkg and you'll most-probably find a list of .pkg.tar.gz files.  These are packages that you've installed on your computer, easily accessible if you need to reinstall or roll back.  Chances are, that path is taking up quite a bit of space.  If you want to clean that cache out, run pacman -Scc.  As for your Eee woes, they're unfounded.  I run Arch on my Eee 701 just fine (I had all my applications and such installed at a total of 1.8gb) , so your 900 will be fine.

Thanks for that.  I should have known to investigate that further.  That certainly accounts for the majority of the overhead I was seeing (but not all).

---

### Post by K2712 on 2008-08-01
I use both arch and ubuntu, and I agree with everyone else that arch is awesome.  I love being able to customize my installation from the ground up, and after having pacman and the AUR, it's hard to use anything else.

---

### Post by mips on 2008-08-01
pacman -Scc will clear the cache for you and free up space.

Sometimes it is nice to hang onto the cache though. the other day I installed kdemod4.1. i played around with it, did my usual updates and then all of a sudden I had some sig*^&^& error from konqueror that closed the app. Instead of trying to fix it I simply did a yaourt -S kdemod which reinstalled everything from cache and the problem dissapeared.

---

### Post by kpkeerthi on 2008-08-02
Arch with Pacman + ABS + AUR + Rolling Updates simply won me over other distros.

---

### Post by mips on 2008-08-02
> **blazercist said:**
> so the pkg.tar.gz files work like debs with "pacman" correct?

Yes, same thing just slightly different. Pacman is probably easier to use & faster than apt-get.

To update/sync your repos do a: **pacman -Sy**
To search a repo for firefox simply do a: **pacman -Ss fire** which will list all packages with 'fire' in the name or you can be more specific.
To install firefox simply do a: **pacman -S firefox**
To upgrade your entire sytem do a: **pacman -Syu**
Also look into Yaourt which gives you options to access AUR besides the normal repos.


> **blazercist said:**
> 
You get a basic cli system with an internet connection from the install and you install your own DE or WM ontop of it if you want right?

Correct. Next you will install Xorg & Alsa followed by a DE/WM of your choice.


> **blazercist said:**
> 
When you talk of removing the "bloat" does that mean that you aren't wasting harddrive space on apps that you don't use and you get to install the tools that you prefer like say opera instead of firefox? Or does it mean that you actually reduce your memory footprint and CPU usage?

Correct on the first question. You install what YOU want and not what the system decides like other distros do.
As for the memory footprint & CPU usage I would say it is less. Why? Because you decide what daemons & services you are running and not the distro. Furthermore it is i686 optimised which removes a bit of stuff for older cpus. There is also a pure 64bit version available, x86_64.


> **blazercist said:**
> 
I think I get the "rolling release" thing, its basically just all the packages that have incrementally changed get updated, instead of the ubuntu one where they only change a few packages at a time when they need serious bug fixes or security fixes.  I like this idea that even the little things that I don't pay attention to are updated.

Correct. As the devs update the packages they move from unstable->testing->current. So you do not get unstable stuff but the latest stable versions unlike other distros where you have to wait for the next release version of the distro before you see the updates of the packages.


> **blazercist said:**
> 
I also like the "build your own distro" idea, I'm contemplating trying Arch out, I'm just worried that it'll be Gentoo-ish and I'll spend the next 2 months compiling junk from source and trying to satisfy dependencies.  What are the repos like? Do they compare in size and variety to say Ubuntu? or will I be searching for, downloading and compiling source from around the web?

The repos are binary so there is no need to compile if you don't want to unless have a very specific need. You also have access to AUR and ABS so you can compile if you want to. To date I have not used ABS. I use AUR but for that I simply use Yaourt and it uses the same command syntax as Pacman. So Yaourt -S Package_Name will do everything for you, no need to worry.


> **blazercist said:**
> 
Finally, I'm not completely clueless when it comes to linux and the cli, but things like what programs run at startup I do at the GUI and I'm worried that I'll be editing text files constantly whenever I want to make a change.

You can carry on using your GUI just like you have been used to.


> **blazercist said:**
> 
Can anyone comment on my fear/understanding of these concepts?

Hope the above helps.

I still say that if you can read and follow the Beginners Guide wiki step by step you will end up just fine. Most people feel intimidated when they see the wiki but once they have gone through it they all proclaim that it was not hard and they were overly worried.

if you need a hand just shout and someone here will help.

Go on, give it a try and you will not look back ;)

---

### Post by Rumor on 2008-08-02
> **blazercist said:**
> 
I think I get the "rolling release" thing, its basically just all the packages that have incrementally changed get updated, instead of the ubuntu one where they only change a few packages at a time when they need serious bug fixes or security fixes.  I like this idea that even the little things that I don't pay attention to are updated.

I also like the "build your own distro" idea, I'm contemplating trying Arch out, I'm just worried that it'll be Gentoo-ish and I'll spend the next 2 months compiling junk from source and trying to satisfy dependencies.  What are the repos like? Do they compare in size and variety to say Ubuntu? or will I be searching for, downloading and compiling source from around the web?

Finally, I'm not completely clueless when it comes to linux and the cli, but things like what programs run at startup I do at the GUI and I'm worried that I'll be editing text files constantly whenever I want to make a change.

Can anyone comment on my fear/understanding of these concepts?

Hey there neighbor to the south!

Mips has already answered your questions quite well. I thought I'd add a couple little things.

To use a poor illustration, using Ubuntu is like going to a Ford dealership and buying a red F150 pickup. You get the features that are already preinstalled at the factory. Using Arch is like going to the factory and choosing your options as the truck rolls down the assembly line. Either way, in the end you have a truck you can drive. With Arch, your truck has what you wanted in it and nothing you don't want.

With the rolling release, your packages are updated as they hit the Arch repos. For instance, let's say you use Gnome and a new version is released. With Ubuntu, you have to wait for the next year model truck to come out. With Arch, you simply install it and go on without the need for waiting.

As to the size of the repos, they are quite sufficient for most users, I should think. The AUR contains a lot of user created content which, as Mips noted can be installed using the pacman wrapper yaourt. Most every package I have ever needed / wanted has been in either the standard repos or in the AUR. On the two occassions I simply could not find what I was looking for, the ABS (Arch build System) is dead simple for making your own package. the neat thing about it is that you then install the package and pacman keeps it current for you.

The text files that you will have to edit during install are very well commented and the beginner's guide gives even more detail as to what you'll be doing during the install process.

The initial base system install takes 10-15 minutes, longer depending on your hardware. From that point to a GUI desktop can be done in another twenty minutes to an hour.

---

### Post by PurposeOfReason on 2008-08-02
> **will1911a1 said:**
> I didn't know this and it cleared up a good deal of space for me.  Thanks!

> **beavenburt said:**
> I didn't know that either. Good tip.
Did you guys not pay attention during the install where is specifically says "Would you like to keep these packages in the pacman cache? It can be cleared later with pacman -Scc"? lol

---

### Post by rsambuca on 2008-08-02
> **PurposeOfReason said:**
> Did you guys not pay attention during the install where is specifically says "Would you like to keep these packages in the pacman cache? It can be cleared later with pacman -Scc"? lol

Obviously we didn't, but laughing at us isn't appropriate.  Sometimes when I am trying to install an unfamiliar system I don't recall everything verbatim from the wiki.  Thanks for the comment, though.

---

### Post by PurposeOfReason on 2008-08-02
Glad to know people ITT can take a joke.

---

### Post by rsambuca on 2008-08-02
Seemed more like making fun as opposed to making a joke, but whatever makes you feel better about yourself.

---

### Post by mips on 2008-08-02
Relax people, if you dont like a post just ignore it :)

Me, I do recall that part of the install and I followed it the first time but no more ;)

---

### Post by Barrucadu on 2008-08-02
I used to obsessively clear my cache - then I lost my entire package database by playing with ramfs and realised just how nice having one can be. I now keep the cache, sometimes clearing out cached packages I no longer have installed, but still keeping one or two versions of packages I do have installed.

---

### Post by basenvironment on 2008-08-02
Any way in Arch to clear only the old packages from the cache?

---

### Post by RedSquirrel on 2008-08-03
> **rsambuca said:**
> Just starting out with Arch, and I must say, I am enjoying it so far.  I have a feeling this may take over as my #1 distro.  I guess time will tell.  I'll have to see if there is any blips after package updates/upgrades in the future.

Just out of curiosity, what is your current #1 distro? (I saw in another thread you wrote that you have about seven distros installed.) Arch has some good features, but Gentoo is my current #1.

---

### Post by RedSquirrel on 2008-08-03
> **cardinals_fan said:**
> I tried Arch and left.  Then I returned.  And this time, I'm not leaving :)
So much for your love affair with Xubuntu. :p :D

---

### Post by rsambuca on 2008-08-03
> **RedSquirrel said:**
> Just out of curiosity, what is your current #1 distro? (I saw in another thread you wrote that you have about seven distros installed.) Arch has some good features, but Gentoo is my current #1.

I always seem to come back to Ubuntu as my primary, but I haven't touched it since I installed Arch.

---

### Post by cardinals_fan on 2008-08-03
> **RedSquirrel said:**
> So much for your love affair with Xubuntu. :p :D
I liked it right up until I saw how many processes it was using :)

Anyway, it felt weird using a non-rolling OS.

---

### Post by fwojciec on 2008-08-04
> **basenvironment said:**
> Any way in Arch to clear only the old packages from the cache?

Yes: pacman -Sc cleans only the packages that are no longer installed on the system (i.e. old packages), pacman -Scc cleans all.

---

### Post by fwojciec on 2008-08-04
> **rsambuca said:**
> That certainly accounts for the majority of the overhead I was seeing (but not all).

Another thing I noticed can eat up a lot of disk space is log files -- some apps, it seems, produce massive logs with default configurations (slim, moblock, and some others) so it's a good idea to keep an eye on that.

Other than that all I can suggest is to use something like "du -shc /*" (as root) on both Arch and Ubuntu systems and compare the results to figure out what it is that makes Arch take up more space.

---

### Post by monstermudder78 on 2008-08-04
> **rsambuca said:**
> Just strung out with Arch, and I must say, I am enjoying it... Fixed.

---

### Post by wolfvorkian1 on 2008-08-04
> **fwojciec said:**
> Another thing I noticed can eat up a lot of disk space is log files -- some apps, it seems, produce massive logs with default configurations (slim, moblock, and some others) so it's a good idea to keep an eye on that.

Other than that all I can suggest is to use something like "du -shc /*" (as root) on both Arch and Ubuntu systems and compare the results to figure out what it is that makes Arch take up more space.

Thanks, that figured out for me where the overhead was. /var besides having a gob of logs I also had nearly half a gig of an iso in /var/temp/recorder that the little  cd/dvd application called 'recorder' had put there. Obviously after using Recorder you have to manually clean out the temporary directory, which I didn't know. 

Now things look more realistic. I knew I hadn't downloaded enough software to have 'more' than a total Xubuntu installation does. 

I should forget about all these burners and just use the command line. I don't make that many discs and what I do make isn't anything exotic anyhow. The couple times I have used a terminal, the results have been just fine.

---

### Post by andrek on 2008-08-05
I've finally convinced myself to try Arch and.. I LOVE IT! I had to apply some font ubuntu patches from AUR ( which is suberb, btw ) and now it looks and works awesome.
One thing - I have too much sound modules in my rc.conf :
```
ac97_bus snd-mixer-oss snd-pcm-oss snd-seq-oss snd-seq-device snd-seq-midi-event snd-seq snd-page-alloc snd-pcm snd-rawmidi snd-timer snd snd-mpu401-uart snd-mpu401 snd-ac97-codec snd-via82xx soundcore
```
I think the only needed from above is snd-via82xx for me, alsaconf used this to configure itself. Can I remove the rest?

And oh, "Loading UDev uevent" takes 7 seconds - is it related to the list of modules?

---

### Post by YodaMstr on 2008-08-05
You could try prefixing the sound modules with a bang (!) and then rebooting; if sound doesn't work properly, narrow down which ones are required and which ones can be deleted.  For reference, here are the sound modules in my array.

```
snd-mixer-oss snd-pcm-oss snd-hwdep snd-page-alloc snd-pcm 
snd-timer snd snd-hda-intel soundcore 
```

I haven't thought about trying to narrow these down any, so you could probably get by with even fewer than that.  Also, keep in mind that we almost assuredly have different types of sound cards, so there will most likely be some difference between ours.

---

### Post by handy on 2008-08-05
*Sorry, I posted a new thread rather than hijack this one.*

---

### Post by rsambuca on 2008-08-06
> **fwojciec said:**
> Another thing I noticed can eat up a lot of disk space is log files -- some apps, it seems, produce massive logs with default configurations (slim, moblock, and some others) so it's a good idea to keep an eye on that.

Other than that all I can suggest is to use something like "du -shc /*" (as root) on both Arch and Ubuntu systems and compare the results to figure out what it is that makes Arch take up more space.

Ahhh... thanks for the du command.  I had forgotten about that one.  I another 600 MB of stuff I don't think I need - in my home folder no less.  Seems when I installed a couple of programs manually (gcompris and tuxpaint), all the unpacked stuff stuck around and took up a bunch of space.

---

### Post by rsambuca on 2008-08-14
Hmmm...  Potential deal-breaker here for Arch on my PC.  We stuck in the kid's Little Einsteins DVD this morning.  It plays, but is virtually unwatchable due to stuttering.  It doesn't matter what player I use.

After a bit of research, it appears to be a problem with my DVD drive, DMA, and the current kernel.  Until the new kernel is out, looks like I'll be trying something else.  Perhaps Foresight this time - I am kinda keen on a Rolling Release distro.

---

### Post by flick on 2008-08-14
Why not just reinstall the previous kernel from your pacman cache, if dvds played fine when that kernel was installed?

---

### Post by rsambuca on 2008-08-14
I have only had one kernel so far.  I just haven't used the DVD player until now.

---

### Post by Dr Small on 2008-08-14
> **rsambuca said:**
> I have only had one kernel so far.  I just haven't used the DVD player until now.
You can still build an older kernel from ABS.

---

### Post by rsambuca on 2008-08-14
> **Dr Small said:**
> You can still build an older kernel from ABS.

Yeah, I know.  I can also compile the newer -26 kernel, which has apparently fixed the problems.  However, these are the types of things I want to avoid.

---

### Post by Barrucadu on 2008-08-15
Compiling a kernel isn't really that bad - it's just that you have to recompile any modules you use as well which is more of a hassle really.
That said, I did like the feeling of running on 'my' Arch box that was unique because it had 'my' kernel - so I might try it again some time.

---

### Post by rsambuca on 2008-08-15
> **Barrucadu said:**
> Compiling a kernel isn't really that bad - it's just that you have to recompile any modules you use as well which is more of a hassle really.
That said, I did like the feeling of running on 'my' Arch box that was unique because it had 'my' kernel - so I might try it again some time.

Yeah, I know it isn't that bad - I have done it before.  I just find it a pain in the ..., especially when there are a billion other distros, most of which don't have that problem with my rig.

---

### Post by rsambuca on 2008-08-16
Hmmm...  Apparently the new kernel was out a few days ago.  It wasn't installing when I updated because of a conflict with linux-uvc-svn (which I found out was built into the new kernel).

Question:  Is there a way to find out what packages are supposed to be installed in the update?  When I did the "pacman -Syu", it always started and then just said something about a conflict with linux-uvc-svn.  I just kept waiting, assuming it would clear it self out.  After I found out I had to remove the uvc package, there a bunch of updates along with the kernel.  If I had seen all of those updates, I would have investigated things sooner, but I had no idea what was supposed to be installed.

---

### Post by Barrucadu on 2008-08-16
Other than looking at the updated packages on the Arch website, or subscribing to the RSS feed, I don't think so.

---

### Post by fwojciec on 2008-08-16
> **rsambuca said:**
> Hmmm...  Apparently the new kernel was out a few days ago.  It wasn't installing when I updated because of a conflict with linux-uvc-svn (which I found out was built into the new kernel).

Question:  Is there a way to find out what packages are supposed to be installed in the update?  When I did the "pacman -Syu", it always started and then just said something about a conflict with linux-uvc-svn.  I just kept waiting, assuming it would clear it self out.  After I found out I had to remove the uvc package, there a bunch of updates along with the kernel.  If I had seen all of those updates, I would have investigated things sooner, but I had no idea what was supposed to be installed.

Pacman -Qu displays info about available updates, but I don't know if it gives any more info than regular pacman -Syu.  It's useful if you want to write a script that displays info about available upgrades (combined with "pacman -Syuw --noconfirm" cronjob, for example, to download packages automatically without installing them)...

Rule of thumb -- warnings don't necessarily resolve themselves automatically in Arch, they usually indicate that something needs to be done/decided by the user.

---

### Post by rsambuca on 2008-08-29
Well, it has been a little more than a couple of weeks now, and I feel I have had ample time to really test out Arch.

One thing that is really annoying me is the numerous problems I am having with file permissions.  For instance...  install the flash plugin, but it doesn't work.  After a lot of messing around and research, I discovered it was because of improper file permissions on the /usr/lib/mozilla folder.  I can't browse through some folders with nautilus because of permissions, and doing gksu nautilus doesn't do anything.  Tried changing my gnome menu - it won't let me because I don't have permission.

Coming from Ubuntu, I have been used to sudo, and thus installed it on Arch.  Is this causing my problems?  If you go through their wiki, it simply says to do the "pacman -S flashplugin".  Nowhere is anything mentioned about changing folder permissions.

---

### Post by Barrucadu on 2008-08-29
You shouldn't need to change any permissions, that definitely sounds like something has gone wrong.

---

### Post by rsambuca on 2008-08-29
Yes, it is very strange.  I am not alone with these problems though.  I am also (almost) positive that it has something to do with 'sudo', but I don't understand enough to narrow it down further.

---

### Post by wolfvorkian1 on 2008-08-29
> **rsambuca said:**
> Yes, it is very strange.  I am not alone with these problems though.  I am also (almost) positive that it has something to do with 'sudo', but I don't understand enough to narrow it down further.

I use sudo and don't have any problems like you speak of. I do empathize though, I despise permission problems.

---

### Post by handy on 2008-08-29
> **rsambuca said:**
> Yes, it is very strange.  I am not alone with these problems though.  I am also (almost) positive that it has something to do with 'sudo', but I don't understand enough to narrow it down further.

I take it you followed the [***_Arch wiki guide_***]("http://wiki.archlinux.org/index.php/Sudo") for setting up sudo?

I can't see how sudo can be responsible, unless you have accidentally changed your group settings.

This page will enable you to check & change your group settings where necessary:

***_[http://wiki.archlinux.org/index.php/Groups](http://wiki.archlinux.org/index.php/Groups)_***

I hope that helps you, it is a pain when permission settings obstruct us, I know. Not that I have experienced it with Arch, but I have experienced it.

---

### Post by rsambuca on 2008-08-29
Thanks for the info (and epmathy) guys.  I'll keep looking into it.  Strange thing is, these problems are only on my laptop, my Desktop has never had these problems.

What is really strange is that when I do "ls -la" in my home folder, I notice that some of my config files aren't owned by me (and in fact I have no permissions on some of them at all).  Clearly something is borked.  I can obviously chown/chmod the entire folder, but I kinda want to know why this has happened first!

---

### Post by Barrucadu on 2008-08-30
Did you edit any files in your home folder as root? That would explain it. There isn't (shouldn't) be any harm in fixing the permissions on your home folder yourself, so go for it.

---

### Post by hessiess on 2008-08-31
> What is really strange is that when I do "ls -la" in my home folder, I notice that some of my config files aren't owned by me (and in fact I have no permissions on some of them at all). Clearly something is borked. I can obviously chown/chmod the entire folder, but I kinda want to know why this has happened first!
do you sync your computer with anouther using unison/ rsync or something? I use unison, and anoytingly the fileowner keeps getting changed to root.

---

### Post by rsambuca on 2008-08-31
> **hessiess said:**
> do you sync your computer with anouther using unison/ rsync or something? I use unison, and anoytingly the fileowner keeps getting changed to root.

Nope.  I am starting to think that this may have been caused when I ran my laptop battery dry and the system didn't shut down properly.  Upon the next boot, there were some errors which were fixed by fsck, but I didn't really pay much attention to it.  Is it possible that the permissions were changed then?

---

### Post by chris4585 on 2008-09-21
I'm looking at installing arch on my laptop just for the fun of it, and I was curious whats the difference from installing KDE 4.1 from `pacman -S kde' and the kdemod I've heard so much about?

---

### Post by mips on 2008-09-21
> **chris4585 said:**
> I'm looking at installing arch on my laptop just for the fun of it, and I was curious whats the difference from installing KDE 4.1 from `pacman -S kde' and the kdemod I've heard so much about?

kdemod is VERY modular. They took KDE and split it up into small components.  So instead of installing a meta package you can choose to only install parts of the meta package in kdemod.

Example, normal KDE4 has a meta package called **kdegraphics** which installs several packages whether you like it or not.

KDEmod4 on the other hand splits the **kdegraphics** package up into it's individual components as listed below:

kdemod-core/kdemod-kdegraphics-common 4.1.1-1
kdemod-core/kdemod-kdegraphics-doc 4.1.1-1
kdemod-core/kdemod-kdegraphics-gwenview 4.1.1-1
kdemod-core/kdemod-kdegraphics-kamera 4.1.1-1
kdemod-core/kdemod-kdegraphics-kcolorchooser 4.1.1-1
kdemod-core/kdemod-kdegraphics-kolourpaint 4.1.1-1
kdemod-core/kdemod-kdegraphics-kruler 4.1.1-1
kdemod-core/kdemod-kdegraphics-ksnapshot 4.1.1-1
kdemod-core/kdemod-kdegraphics-okular 4.1.1-1

This allows you to only select the actual kdegraphics packages you want instead of installing all of them in normal KDE.

This is the MAIN difference.

The other slight difference is they applied about 3 patches to kdemod and these are purely cosmetic and it's basically to identify it as kdemod instead of kde. The old kdemod3.5 had plenty of patches applied but they are not going down that road again.

Hope this makes sense.

---

### Post by chris4585 on 2008-09-21
Yep thanks!

---

### Post by rsambuca on 2008-09-21
Thanks mips.  I'll definitely have to look into this kdemod thing.  I like one or two of the games from kdegames, but it ticks me off that I basically have to install the entire kde just to play kbounce.  Not a big deal on my desktop, but on my little eeepc...

---

### Post by chris4585 on 2008-09-21
So I got arch setup with kdemod, I like it, its pretty stable, I have openbox and gnome on it aswell and it runs very smooth

---

### Post by mips on 2008-09-22
> **chris4585 said:**
> So I got arch setup with kdemod, I like it, its pretty stable,

KDE4/KDEmod4 is not quite there yet but it is usable. 4.1 is a big improvement over 4.0 though.

Yes, I use 4.1.

---

### Post by mips on 2008-09-22
> **rsambuca said:**
> Thanks mips.  I'll definitely have to look into this kdemod thing.  I like one or two of the games from kdegames, but it ticks me off that I basically have to install the entire kde just to play kbounce.  Not a big deal on my desktop, but on my little eeepc...

I agree with you 100%, I don't see why one should install an entire meta package when you just want one of it's single packages. KDEmod is what got me into Arch in the first place, I hated installing stuff I did not want.

KDEmod is what normal KDE should be if you ask me, modular.

---

### Post by handy on 2008-09-22
> **mips said:**
> i agree with you 100%, i don't see why one should install an entire meta package when you just want one of it's single packages. Kdemod is what got me into arch in the first place, i hated installing stuff i did not want.

Kdemod is what normal kde should be if you ask me, modular.

+1 on the modular.

---

### Post by basenvironment on 2008-09-25
> **mips said:**
> ... I don't see why one should install an entire meta package when you just want one of it's single packages.
Uh, does something force you to install the whole meta-package?

If someone wants a easy to install meta-package then I am glad there is one. In fact, I like that in debian there is a few different meta packages for kde depending on how much you want bundled up. I am still always free to pick and choose pieces though.

---

### Post by mips on 2008-09-25
> **basenvironment said:**
> Uh, does something force you to install the whole meta-package?


:roll:

---

### Post by basenvironment on 2008-09-25
[-X

I find it funny people talk about how great it is to pick and choose what you want yet nothing stops you from doing the same on most distros AND you still have some great meta-packages in case you do not want to bother picking and choosing. Best of both worlds IMO.

---

### Post by rsambuca on 2008-09-25
> **basenvironment said:**
> Uh, does something force you to install the whole meta-package?

If someone wants a easy to install meta-package then I am glad there is one. In fact, I like that in debian there is a few different meta packages for kde depending on how much you want bundled up. I am still always free to pick and choose pieces though.

We kind of all agree here.  There is nothing wrong with meta-packages at all.  No one has said otherwise.  It is when meta-packages and bundles are the only choice that it becomes a nuisance to some.  It is not a distro thing, in this case it is a KDE thing.  For instance, if I want to install kbounce (one of the kde-games packages), with regular kde, you can't just install kbounce without installing the entire kde-desktop to your computer.  So now I have an entire Desktop Environment on my rig that I will never use, just because I like kbounce.

---

### Post by basenvironment on 2008-09-25
> ... you can't just install kbounce without installing the entire kde-desktop to your computer.
huh, sure you can....

Obviously you need kdelibs,libarts, qt, and other kdecrapola for kbounce but certainly not the whole kde-desktop. It is a distro/packager thing if they are bundling too much with a app. At worst a distro may recommend too much but should never depend/require more packages than what the software needs to fully function.

Looks okay to me...
[http://packages.debian.org/lenny/kbounce](http://packages.debian.org/lenny/kbounce)

---

### Post by MisfitI38 on 2008-09-26
Don't feed the troll.

---

### Post by basenvironment on 2008-09-27
If you can add something to the discussion then please feel free. Nothing stops you from picking/choosing pieces on any OS - it is free software afterall. Any kde app is going to require parts of kde since that is why they call it a kde app. But if a packager has bundled too many depends with his package then file a bug report and/or use dpkg-repack to repack it and edit the depends file yourself. easy peasy

---

### Post by Louis de Broglie on 2008-09-28
I like "the arch way". So i decided to try it( though i am linux a noob ). But i managed to install xorg and kde without any problem. :lolflag:

But i have not got working sound yet. I have read the alsa wiki. I checked the configs and according to wiki they are ok. Then i am stuck in unmute section . I don't understand what these means 

for example IEC958 Center/LFE
IEC958 Front, analog front etc. :confused:

I randomly did tweaking in kmix and now getting really weird sound:lolflag:

Can anybody help me understand what these means and fix them by "the arch way" ?:)

---

### Post by mips on 2008-09-28
> **Louis de Broglie said:**
> 
But i have not got working sound yet. I have read the alsa wiki. I checked the configs and according to wiki they are ok. Then i am stuck in unmute section . I don't understand what these means 

for example IEC958 Center/LFE
IEC958 Front, analog front etc. :confused:


Those describe all your output channles. Front Center, Front Left, Front Right, Rear Right, Rear Left, Mic(rophone) etc

You need to unmute the ones you are using and bump the volume up to about 90%.

---

### Post by MisfitI38 on 2008-09-28
> **basenvironment said:**
> If you can add something to the discussion then please feel free.
I took the liberty and added it already.

---

### Post by basenvironment on 2008-09-28
> **MisfitI38 said:**
> I took the liberty and added it already.
I meant add to the discussion relating to installing pieces instead of meta-packages. What would the difference be to, for example, install kbounce in arch and install kbounce in debian?

---

### Post by rsambuca on 2008-09-28
I was mistaken.  You don't need to add the entire kde-desktop to get kbounce!  When I have a chance I'll go through my pacman logs to find out when I added kde.  I certainly don't remember doing it.  Apparently I need to upgrade the RAM in my noggin.

---

### Post by doorknob60 on 2008-09-29
Yay, I installed Arch+KDEmod and I love it :-D I really like the AUR (combined with yaourt, which half the time i spell wrong...) and I like how I don't have to mess around with -dev packages :-P Anyways, it's fast and works well.

---

