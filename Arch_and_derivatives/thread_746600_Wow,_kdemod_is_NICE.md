---
title: "Wow, kdemod is NICE"
date: 2008-04-05
forum: Arch and derivatives
---

### Post by TheOrangePeanut on 2008-04-05
I switched to Arch this weekend and decided to go with kdemod instead of gnome, which I ran when I was using Ubuntu, and wow is it nice.  It's very, very modulare (there's nothing on here application wise that I don't want), it's very fast, and it looks great and is easy to theme.  I don't know why anyone would go with a full KDE instead of kdemod if they're running Arch.  I hope the kdemod team ends up doing this for kde4 eventually.

---

### Post by Whiffle on 2008-04-05
Isn't it though?  I've been running it for 2 weeks now and havn't even had the desire to change the default theme, which says alot because I usually change themes anytime I get bored.

---

### Post by finferflu on 2008-04-06
I've heard there is already a KDEmod for KDE4, but I'm not sure about how to get it. So just double-check on their website, and see if you have a better eye sight than me :P

---

### Post by K.Mandla on 2008-04-06
Yes, KDEmod is very smooth. It hasn't torn me away from Openbox, but it could if I let it.

---

### Post by Whiffle on 2008-04-06
Yeah they're working on KDEmod4.  Its available in unstable.  Its in unstable for a reason though... I tried it the other day and it wasn't quite there yet.

---

### Post by ch_123 on 2008-04-07
I read on their website that they wont be making as extensive modifications to KDE4 as they did to KDE3.5, and that they're waiting for a more stable version of KDE4 to come out before they release a stable package.

---

### Post by Ajay Chahar on 2008-04-20
Even if KDE4 comes out stable I think I am going to stick to KDE 3.X. My poor lappy needs some air to breathe! Though the KDE devs claim that KDE4 consumes less memory, it lags on my lappy! :S

---

### Post by Whiffle on 2008-04-20
> **Ajay Chahar said:**
> Even if KDE4 comes out stable I think I am going to stick to KDE 3.X. My poor lappy needs some air to breathe! Though the KDE devs claim that KDE4 consumes less memory, it lags on my lappy! :S

I have a strong feelling this will improve.  I tried KDE4 on my desktop and it lags too, mostly because of the NVIDIA card.  I think once it hits 4.1 it'll be pretty usable.

---

### Post by houms on 2008-08-18
Yeah The arch team has done a fantastic job. KDEmod4 is awesome. feel free to give it a try. If you need help let me know. And as far as kde4 lagging. Not sure which version you were running but 4.1 does seem to be a bit snappier than kde3. Not sure if this is the great work of Funkyou, Dunkelstern and company or if kde4 really is more efficient, or a combo of both, but its noticeable. Obviously there are still some apps that have not been ported to kde4, but all in do time, and you can always use kde3 apps in kdemod4 if you just cant wait. Either way Arch is great.

---

### Post by ch_123 on 2008-08-19
I tried it out on my laptop, but I found it too different to KDEmod 3.5 so I reverted to the older version... that said, I need to reinstall Arch on my desktop. Might give it a proper try there.

---

### Post by mips on 2008-08-20
> **houms said:**
> And as far as kde4 lagging. Not sure which version you were running but 4.1 does seem to be a bit snappier than kde3. 

KDEmod4.1 feels sluggish on my laptop (desktop effects turned off), where 3.5.9 felt fast (Celeron 1.4Ghz, 1.256GB ram). Wondering why this is?

On my desktop however it runs like a dream.

---

### Post by handy on 2008-08-20
> **mips said:**
> KDEmod4.1 feels sluggish on my laptop (desktop effects turned off), where 3.5.9 felt fast (Celeron 1.4Ghz, 1.256GB ram). Wondering why this is?

On my desktop however it runs like a dream.

So what is your recommendation mips?

Should I install KDEmod3.5 or 4.1, or just wait a while until the bugs are ironed out of 4.1?

By the way I put the photo's on my drive yesterday, do you want me to bring them down in size to suit computer screen viewing or should I just send the chosen as is (about 4 - 5 megapixels from memory)?

---

### Post by houms on 2008-08-20
> **mips said:**
> KDEmod4.1 feels sluggish on my laptop (desktop effects turned off), where 3.5.9 felt fast (Celeron 1.4Ghz, 1.256GB ram). Wondering why this is?

On my desktop however it runs like a dream.

You may want to refer back to the wiki and setup the appropriate laptop tools. like cpu-governer, cpufreq-utils. Just have a look at the beginners guide on the wiki page. They got lots of great info there. It may help to improve the performance. are you using generic video drivers? also what is the output of 
cpufreq-info?

@handy
if you want my opinion, it depends. If your looking to hit the ground running, just install kdemod3, its slick, its stable, and is the kde you know and love with an arch twist, but if you want to learn the new kde4 then go with kdemod4. I say learn because they are different in a sense. Yes some of your favorite apps are not there yet so you will have a choice to make. For example, I like to use amarok. so in kdemod3 you can use amarok 1.4.10, however amarok2 (which is slated for kde4) is still in alpha, so while you could compile amarok2 on kdemod4, it may not be desirable to use it on a regular basis if this is your primary machine. But I will also add that you can always just install amarok 1.4.10 in kdemod4, but the catch is that you must install kdelibs3 and qt3, which FOR ME, that was not desirable. But you can also use some alternatives. For example a lot of posts I have read, users complain about the lack of knetworkmanager in kde4, but I find wicd not only acceptable but much better app for handling my wired/wireless connections.
If your feeling really adventurous, I do believe you can install both side-by-side, but the catch is you should use a different user for the different sessions.

---

### Post by mips on 2008-08-20
> **handy said:**
> So what is your recommendation mips?

Should I install KDEmod3.5 4.1 or wait a while until the bugs are ironed out of 4.1?

I myself would go with KDEmod4.1. It's not perfect but MUCH better than 4.0. I do the updates as they come along.

My laptop is a funny one. It experiences a lot of disk access (and it's not using swap) and the cpu fan is runnig way to much even after I removed KDEmod4.1 (about 10min ago) and trying out LXDE (which is nice). I think I'm going to reprep my laptop though as something just does not feel right about the way it is behaving.

> **handy said:**
> 
By the way I put the photo's on my drive yesterday, do you want me to bring them down in size to suit computer screen viewing or should I just send the chosen as is (about 4 - 5 megapixels from memory)?

Up to you my friend although it would be nice if the images dont exceed say 500kB each. Thanks, looking forward to them.

---

### Post by handy on 2008-08-20
> **houms said:**
> 
@handy
if you want my opinion, it depends. If your looking to hit the ground running, just install kdemod3, its slick, its stable, and is the kde you know and love with an arch twist, but if you want to learn the new kde4 then go with kdemod4. I say learn because they are different in a sense. Yes some of your favorite apps are not there yet so you will have a choice to make. For example, I like to use amarok. so in kdemod3 you can use amarok 1.4.10, however amarok2 (which is slated for kde4) is still in alpha, so while you could compile amarok2 on kdemod4, it may not be desirable to use it on a regular basis if this is your primary machine. But I will also add that you can always just install amarok 1.4.10 in kdemod4, but the catch is that you must install kdelibs3 and qt3, which FOR ME, that was not desirable. But you can also use some alternatives. For example a lot of posts I have read, users complain about the lack of knetworkmanager in kde4, but I find wicd not only acceptable but much better app for handling my wired/wireless connections.
If your feeling really adventurous, I do believe you can install both side-by-side, but the catch is you should use a different user for the different sessions.

Personally, I rarely like KDE.  I am a refugee from 10 years of being a Windows tech'.  I have usually found KDE reminiscent of Windows, which obviously does not please me, or you I'm sure.

The thing I have appreciated about Gnome is the simplicity that did NOT exist in Windows.

These days I use Arch with Openbox.  Does it get any simpler with a window manager than Openbox? At this point, in my experience I don't know.

I *expect* that KDEmod is a simplified (less Windows like) interface.  Therefore I am interested, as I would sometimes like a few more GUI options than are available to me in Openbox.

In the future I will try KDEmod, hopefully I pick the right time with regard to its development so I don't waste my time.

---

### Post by mips on 2008-08-20
> **houms said:**
> You may want to refer back to the wiki and setup the appropriate laptop tools. like cpu-governer, cpufreq-utils. Just have a look at the beginners guide on the wiki page. They got lots of great info there. It may help to improve the performance. are you using generic video drivers? also what is the output of 
cpufreq-info?

Yeah, I actually think I might just start from scratch doing a re-install.

cpufreq-info returns "no or unknown cpufre driver is active on this CPU" which basically tells me it is not setup correctly.
I'm also using XFS on this laptop which I think I'm going to change to something a bit less cpu intensive if I could call it that.

> **houms said:**
> 
@handy
if you want my opinion, it depends. If your looking to hit the ground running, just install kdemod3, its slick, its stable, and is the kde you know and love with an arch twist, but if you want to learn the new kde4 then go with kdemod4. I say learn because they are different in a sense. Yes some of your favorite apps are not there yet so you will have a choice to make. For example, I like to use amarok. so in kdemod3 you can use amarok 1.4.10, however amarok2 (which is slated for kde4) is still in alpha, so while you could compile amarok2 on kdemod4, it may not be desirable to use it on a regular basis if this is your primary machine. But I will also add that you can always just install amarok 1.4.10 in kdemod4, but the catch is that you must install kdelibs3 and qt3, which FOR ME, that was not desirable. 

I used amarok from the kdemod-extragear repos (v1.86 I think). So far I have only had one crash with it and amarok is permanently running on my pc. There is also the -svn version in AUR which I have not tried yet.

Something else I like about 4.1 is the cleaner look it has over 3.5. It really does look nice, in my eyes anyway :)

---

### Post by houms on 2008-08-20
> **handy said:**
> Personally, I rarely like KDE.  I am a refugee from 10 years of being a Windows tech'.  I have usually found KDE reminiscent of Windows, which obviously does not please me, or you I'm sure.

The thing I have appreciated about Gnome is the simplicity that did NOT exist in Windows.

These days I use Arch with Openbox.  Does it get any simpler with a window manager than Openbox? At this point, in my experience I don't know.

I *expect* that KDEmod is a simplified (less Windows like) interface.  Therefore I am interested, as I would sometimes like a few more GUI options than are available to me in Openbox.

In the future I will try KDEmod, hopefully I pick the right time with regard to its development so I don't waste my time.

I can respect your opinion on KDE, though I have never felt like its windows-like. But thats the great thing about FOSS, one mans trash is another man's treasure. Personally my kde looks more liek OS X than windows. At least thats what friends keep telling me everytime they see my laptop.
Now i will say I really dislike gnome for its lack of features, though I again respect that you like its "simplicity".
Openbox is a no-brainer when it comes to simplicity.
It sounds like you are a minimalist kind of fellow, which openbox is perfect for really. I'm sure your aware of other window managers that would suffice as well. The question I would ask is what does openbox really lack that you would like to see? You don't sound like you would enjoy xfce all that much as it may be too gui rich for your liking. You could also try LXDE which mips mentioned earlier. All-in-all though I don't think you would like kdemod as it is kde at the end of the day and kdemod still uses kwin. the base version of it really comes with nothing, allowing you to add just what you want. Kinda of like the overall arch philosophy. But not in a flukbox,openbox, or any other box, sort of way. I would say since Arch is a rolling release, its always the "right" time to give it a try. Just what DE/WM you go with would be the only issue.

---

### Post by mips on 2008-08-20
> **handy said:**
> Personally, I rarely like KDE.  I am a refugee from 10 years of being a Windows tech'.  I have usually found KDE reminiscent of Windows, which obviously does not please me, or you I'm sure.


I suspect you would be better off with gnome but would like to encourage you to at least give kdemod4.1 a spin sometime. You can always uninstall it just as easily as you installed it.

---

### Post by houms on 2008-08-20
> **mips said:**
> Yeah, I actually think I might just start from scratch doing a re-install.

cpufreq-info returns "no or unknown cpufre driver is active on this CPU" which basically tells me it is not setup correctly.
I'm also using XFS on this laptop which I think I'm going to change to something a bit less cpu intensive if I could call it that.



I used amarok from the kdemod-extragear repos (v1.86 I think). So far I have only had one crash with it and amarok is permanently running on my pc. There is also the -svn version in AUR which I have not tried yet.

Something else I like about 4.1 is the cleaner look it has over 3.5. It really does look nice, in my eyes anyway :)

Yeah I would stick with ext3 and see how that goes. are you also using xfs on the desktop?If so, what are the desktop specs?
Yeah I had some issues with getting my cpu setup right. that may also be a contributing factor to the "sluggishness" your feeling on the laptop.
Yeah I'm thinking about building amarok using the svn version. Can you tell me what version you are running? I have the extragear repo enabled, but I do not have amarok available. is it only available using 
[http://kdemod.iskrembilen.com/repo/extragear/i686](http://kdemod.iskrembilen.com/repo/extragear/i686)

my repo is pointing to 
[http://kdemod.ath.cx/repo/extragear/i686](http://kdemod.ath.cx/repo/extragear/i686)
I only have amarok 1.4.9 from the extra repos?

Its definitely a cleaner look. I mean both kdemod version are pretty damn polished, both are much cleaner looking than vanilla kde, but kdemod4 definitely looks better than even kdemod3 did.


EDIT: Mips, are you running kdemod4.1 exclusively? if so, do you know how to install kdemod3 and 4 side by side?

---

### Post by handy on 2008-08-20
> **houms said:**
> I can respect your opinion on KDE, though I have never felt like its windows-like. But thats the great thing about FOSS, one mans trash is another man's treasure. Personally my kde looks more liek OS X than windows. At least thats what friends keep telling me everytime they see my laptop.
Now i will say I really dislike gnome for its lack of features, though I again respect that you like its "simplicity".
Openbox is a no-brainer when it comes to simplicity.
It sounds like you are a minimalist kind of fellow, which openbox is perfect for really. I'm sure your aware of other window managers that would suffice as well. The question I would ask is what does openbox really lack that you would like to see? You don't sound like you would enjoy xfce all that much as it may be too gui rich for your liking. You could also try LXDE which mips mentioned earlier. All-in-all though I don't think you would like kdemod as it is kde at the end of the day and kdemod still uses kwin. the base version of it really comes with nothing, allowing you to add just what you want. Kinda of like the overall arch philosophy. But not in a flukbox,openbox, or any other box, sort of way. I would say since Arch is a rolling release, its always the "right" time to give it a try. Just what DE/WM you go with would be the only issue.

Thanks for your logical reply, you held the crux of the biscuit all the way (as Frank Zappa once said). :)

The bottom line for me IS, can I have a more fully featured desktop than Openbox, that is still fast & simple?

Don't get me wrong, I really like Openbox, it just comes down to compromise (as usual).

---

### Post by handy on 2008-08-20
> **mips said:**
> I suspect you would be better off with gnome but would like to encourage you to at least give kdemod4.1 a spin sometime. You can always uninstall it just as easily as you installed it.

I use Openbox, which I much prefer to Gnome.  I don't like the too much of KDE, I am hoping that KDEmod is somewhat more streamlined & hopefully is easily configurable being modular & all?

---

### Post by houms on 2008-08-20
> **handy said:**
> Thanks for your logical reply, you held the crux of the biscuit all the way (as Frank Zappa once said). :)

The bottom line for me IS, can I have a more fully featured desktop than Openbox, that is still fast & simple?

Don't get me wrong, I really like Openbox, it just comes down to compromise (as usual).

It sounds like kde,gnome,xfce, are not going to meet your needs as they are too full-fledged DE's. e17 will never be finished so that is also out.lol 
You sound like your looking for a WM with tweakability. 
I would suggest any of the following though you seem like you've done your homework, and may already have what some consider the best WM so the answer to your bottom line may be no, so this may be useless to you. but
blackbox, icewm, fvwm, fluxbox, dwm, ion, stump, ratpoison, wmii, are all options and I think they all should be available in arch. I'm sure I left some out, so to all the WM zealots, I'm sorry.
Compromise is the human way of living.

---

### Post by mips on 2008-08-20
> **houms said:**
> Yeah I would stick with ext3 and see how that goes. are you also using xfs on the desktop?If so, what are the desktop specs?

Desktop is Q6600 2.4GHz cpu, 4GB ram, nvidia6600 gpu. HD is running ext2 for /boot, reiserfs for /var and xfs on all other partitions. XFS works fine on my desktop and I have been using xfs for a long time now. I have not noticed a significant change using reiserfs on /var though.


> **houms said:**
> 
Yeah I had some issues with getting my cpu setup right. that may also be a contributing factor to the "sluggishness" your feeling on the laptop.

I follow the beginners guide step for step everytime. I though maybe it was an oversight on my side this time but I have redeemed myself with a quick google search. It seem to be a kernel issue in 2.6.25, [http://bbs.archlinux.org/viewtopic.php?id=50380](http://bbs.archlinux.org/viewtopic.php?id=50380)
Busy updating now, hopefully all works well again :)


> **houms said:**
> 
Yeah I'm thinking about building amarok using the svn version. Can you tell me what version you are running? I have the extragear repo enabled, but I do not have amarok available. is it only available using 
[http://kdemod.iskrembilen.com/repo/extragear/i686](http://kdemod.iskrembilen.com/repo/extragear/i686)

my repo is pointing to 
[http://kdemod.ath.cx/repo/extragear/i686](http://kdemod.ath.cx/repo/extragear/i686)
I only have amarok 1.4.9 from the extra repos?

Your repo [(http://kdemod.ath.cx/repo/extragear/i686]("http://kdemod.ath.cx/repo/extragear/i686")) is correct for i686, I verified this with my laptop.
I have x86_64 on my destop and there seems to be more extragear packages for x86_64 where Amarok 1.86 is available.

Aparently (from what I have read) the SVN version is pretty stable so maybe give it a go.

Maybe also look around in:
*[kdemod-playground]*  -> for any unstable extra apps and stuff for KDE 4
*[kdemod-unstable]*      -> for unstable KDE 4 (pre)releases



> **houms said:**
> 
Its definitely a cleaner look. I mean both kdemod version are pretty damn polished, both are much cleaner looking than vanilla kde, but kdemod4 definitely looks better than even kdemod3 did.

Yeah, much cleaner would be safe to say I think. I tried OSX the other day and actually think  kdemod4.1 is cleaner than OSX. It really is a nice look. Bitstream Vera Sans fonts make it even better ;)


> **houms said:**
> 
EDIT: Mips, are you running kdemod4.1 exclusively? if so, do you know how to install kdemod3 and 4 side by side?

Exclusively running 4.1. When 4 was still beta/rc I ran it side by side but back then they did not share the same folders.

Edit:
[http://kdemod.ath.cx/bbs/viewtopic.php?id=892](http://kdemod.ath.cx/bbs/viewtopic.php?id=892)
> **CHANGES AND "WHAT YOU SHOULD KNOW":**
- All packages are now renamed to kdemod3-$PACKAGE
- [COLOR=Red]KDEmod 3.5.9 does now conflict with KDE 4.1, so there is no side-by-side installation possible anymore[/COLOR]The rest of the thread has a bit more on the issue of side-by-side installs.

Edit2:
> [http://kdemod.ath.cx/bbs/viewtopic.php?id=892&p=2](http://kdemod.ath.cx/bbs/viewtopic.php?id=892&p=2)
after a (too long) marathon tonight, we seem to have fixed the kde3/kde4 interfering problem. the pkgs will come soon. **please be patient**. thank you very much. soooooo tired 
.oO0(zZzZzZz)So it does seem possible after all. Best to go and ask in that thread maybe.

---

### Post by mips on 2008-08-20
> **handy said:**
>  I don't like the too much of KDE, I am hoping that KDEmod is somewhat more streamlined & hopefully is easily configurable being modular & all?

Streamlined compared to KDE, yes. Modular, very, with v4 they took it a few steps further and modularised the hell out of it. There is not much to configure if anything at all. Theming these days is a breeze, the settings gui links straight to kde-look website, just click what you like and bobs your uncle.

---

### Post by houms on 2008-08-20
handy 
i will agree and say that kde4 is much more modular.

---

### Post by houms on 2008-08-20
> **mips said:**
> Desktop is Q6600 2.4GHz cpu, 4GB ram, nvidia6600 gpu. HD is running ext2 for /boot, reiserfs for /var and xfs on all other partitions. XFS works fine on my desktop and I have been using xfs for a long time now. I have not noticed a significant change using reiserfs on /var though.
That is a beast of a machine if i can just say. even vista may run on that thing.:lolflag:




> I follow the beginners guide step for step everytime. I though maybe it was an oversight on my side this time but I have redeemed myself with a quick google search. It seem to be a kernel issue in 2.6.25, [http://bbs.archlinux.org/viewtopic.php?id=50380](http://bbs.archlinux.org/viewtopic.php?id=50380)
Busy updating now, hopefully all works well again :)

that looks like it may be your issue. I am running 2.6.26



> Your repo [(http://kdemod.ath.cx/repo/extragear/i686]("http://kdemod.ath.cx/repo/extragear/i686")) is correct for i686, I verified this with my laptop.
I have x86_64 on my destop and there seems to be more extragear packages for x86_64 where Amarok 1.86 is available.

Now I see, cause I have heard people keep saying go to extragear repo for amarok but thats a no go, I didnt realize that x86_64 had it.. seems kinda bass ackwards to have 64 packages before 32bit, but what the hell. all in due time.

> Aparently (from what I have read) the SVN version is pretty stable so maybe give it a go.

I think i may give it a go, my only concern is what to do when amarok 2 is released in the official repo? is it just uninstall svn build and reinstall via pacman? gotta love arch.

> Maybe also look around in:
*[kdemod-playground]*  -> for any unstable extra apps and stuff for KDE 4
*[kdemod-unstable]*      -> for unstable KDE 4 (pre)releases

will look and let you know


> Yeah, much cleaner would be safe to say I think. I tried OSX the other day and actually think  kdemod4.1 is cleaner than OSX. It really is a nice look. Bitstream Vera Sans fonts make it even better ;)

really? thats impressive, bitstream vera sans is not by default right?do i just set that in the system settings?



Exclusively running 4.1. When 4 was still beta/rc I ran it side by side but back then they did not share the same folders.

Edit:
[http://kdemod.ath.cx/bbs/viewtopic.php?id=892](http://kdemod.ath.cx/bbs/viewtopic.php?id=892)
The rest of the thread has a bit more on the issue of side-by-side installs.

Edit2:
So it does seem possible after all. Best to go and ask in that thread maybe.[/QUOTE]


Thanks mips, I really have had some conflicting answers on that issue, let me ask you though, do you have kdelibs3 and qt3 installed? are you running any native kde3 apps in kde4? I want to avoid it if possible.

---

### Post by mips on 2008-08-20
> **houms said:**
> That is a beast of a machine if i can just say. even vista may run on that thing.:lolflag:
I doubt it. If I bring a Vista cd close to the cd-rom tray the computer would keel over and die in disgust :)


> **houms said:**
> 
I think i may give it a go, my only concern is what to do when amarok 2 is released in the official repo? is it just uninstall svn build and reinstall via pacman? gotta love arch.

**yaourt -S kdemod4-extragear-amarok2-svn**
there is also a amarok2-svn version I see. Check AUR web page for the details.

to remove it later is as simple as 
**yaourt -Rcs kdemod4-extragear-amarok2-svn**


> **houms said:**
> 
really? thats impressive, bitstream vera sans is not by default right?do i just set that in the system settings?

Thats how much I like it, things in OSX are not even consistant all the time either.

No, bitstream vera sans is not the default. Install the font (ttf-bitstream-vera) and then just select it in System Settings-Appearance->Fonts
Dejavu Sans is also worth having a look at.


> **houms said:**
> 
Thanks mips, I really have had some conflicting answers on that issue, let me ask you though, do you have kdelibs3 and qt3 installed? are you running any native kde3 apps in kde4? I want to avoid it if possible.

Yes, I do have kdelibs3 & qt3 installed as there are a few kde3 apps I installed that required those. But browsing throught the repos now I see that some of them are available as SVNs for kdemod4 so I might look at starting to prune them out.

---

### Post by handy on 2008-08-21
I've done a little research on KDEmod, & am now very interested, BUT, I think I will wait a month or two & let the dev's squash more bugs before I leap in.

On a side note: Mips, have you received any worthwhile invitations yet?  As I have very recently directed two your way...

---

### Post by mips on 2008-08-21
> **houms said:**
> 
Thanks mips, I really have had some conflicting answers on that issue, let me ask you though, do you have kdelibs3 and qt3 installed? are you running any native kde3 apps in kde4? I want to avoid it if possible.

> **mips said:**
> 
Yes, I do have kdelibs3 & qt3 installed as there are a few kde3 apps I installed that required those. But browsing throught the repos now I see that some of them are available as SVNs for kdemod4 so I might look at starting to prune them out.

I actually realised today that I only have one kde3 app that requires the above and that is k3b. If I remove k3b and it's dependancies kdelibs3&qt3 get uninstalled as well.

There is a kdemod4-extragear-k3b-svn available but when I try to install it with yaourt I get a complaint "Error: kdemod4-kdebase-runtime not found in AUR. "

I'm trying to sort this out, [http://aur.archlinux.org/packages.php?ID=18255](http://aur.archlinux.org/packages.php?ID=18255)

---

### Post by mips on 2008-08-21
> **handy said:**
> 
On a side note: Mips, have you received any worthwhile invitations yet?  As I have very recently directed two your way...

Yes, thank you very much I received one. I've already registered :)

---

### Post by handy on 2008-08-21
> **mips said:**
> Yes, thank you very much I received one. I've already registered :)

Very good, that number did not last long, I'm so glad you made it. :-)

You are now (in that regard) off my to do list. :lolflag: Whether you got there sooner or later matters not to me at this point.  If you know what I mean? :-)

---

### Post by mips on 2008-08-21
> **handy said:**
> 
You are now (in that regard) off my to do list. :lolflag: Whether you got there sooner or later matters not to me at this point.  If you know what I mean? :-)

Lol, yip, you are of the hook now :) I understand ;)

---

### Post by handy on 2008-08-21
> **mips said:**
> Lol, yip, you are of the hook now :) I understand ;)

:cool:

---

### Post by mips on 2008-08-26
> **houms said:**
> 
Yeah I'm thinking about building amarok using the svn version. Can you tell me what version you are running? I have the extragear repo enabled, but I do not have amarok available. is it only available using 
[http://kdemod.iskrembilen.com/repo/extragear/i686](http://kdemod.iskrembilen.com/repo/extragear/i686)

my repo is pointing to 
[http://kdemod.ath.cx/repo/extragear/i686](http://kdemod.ath.cx/repo/extragear/i686)
I only have amarok 1.4.9 from the extra repos?




Now running Amarok v2.0-svn. It's available for i686 so try:

```
yaourt -S kdemod4-extragear-amarok2-svn
```
Edit1: I just tired this and it has a libmtp=>0.3.0 dependancy which I cannot find.

I still cannot get K3b(x86_64) to build but not giving up.
Edit2: For i686 a simple pacman -S kdemod-playground-k3b-svn will install k3b for you.

---

### Post by mips on 2008-08-27
> **mips said:**
> 
I still cannot get K3b(x86_64) to build but not giving up.
Edit2: For i686 a simple pacman -S kdemod-playground-k3b-svn will install k3b for you.

yaourt -S k3b-svn will install k3b for x86_64

---

