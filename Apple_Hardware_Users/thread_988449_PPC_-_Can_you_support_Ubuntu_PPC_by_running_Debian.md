---
title: "PPC - Can you support Ubuntu PPC by running Debian? - Yes"
date: 2008-11-20
forum: Apple Hardware Users
---

### Post by stream303 on 2008-11-20
Since Debian-ppc is the upstream source for Ubuntu's ppc release, it behooves us to support that project *as well.*  What follows is a quick intro on how to get started.

Using Debian does not mean that you are abandoning Ubuntu or it's great community.  Nor should it involve any sort of cheerleading - it is merely a way to help the downstream Ubuntu project survive.  Since this is an Ubuntu Apple forum, I won't go into great detail, nor profess to know "which one is best".

Where to start?
Obviously the home page is recommended:
[http://www.debian.org/](http://www.debian.org/)

Quick jump to the download instructions:
[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

Bittorent, jigdo downloads etc are recommended to be mindful of bandwidth, although the standard download obviously works.

If you do decide to download the POWERPC version, note that there is a warning not to just try and use a normal browser, since many have no way of restarting a failed download from where they left off.  But, if you KNOW you have a good connection, it can be done - make your decision wisely.

Which release - stable (4.0r5) or testing (Lenny)?
That's up to you.  Stable is very good for low-spec boxes, and is still getting updates.  It has support for G5's and newer hardware as well.

Lenny-Testing is great for seeing how the about-to-be-released Lenny will turn out.

Do I need to download all the CD's?  **NO!**  
All you need is the first one.  Downloading all the CD's would be like using synaptic to download every piece of software available.  All you need is the first one to provide a standard Gnome experience.

What about KDE, XFCE, or Net-Install?
If you scroll down the page, you'll see images for the KDE desktop version, the XFCE4 version, and my favorite - Net-Install, which only contains enough to boot the machine basically and grab the rest from the net:

[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

Some related notes:
These images should be similar to you as what the Ubuntu "alternate" text-based installers are.  Debian uses both root and user passwords instead of relying too much on sudo.  For G5's, be sure to use "install64" at the second-stage yaboot boot: prompt. (hit TAB to stop the automatic countdown)  Afterwards, you may want to make sure your keyboard is set to Macintosh. Debian allows you to set up your firewire port for ethernet - be careful as this is not likely what you want to do when presented with that dialog box.  Firefox is IceWeasel.

Fonts: fonts in Etch can sometimes be improved by just saying "NO" to "bitmapped fonts" at the last prompt of the fontconfig dialog.

```
dpkg-reconfigure fontconfig-config
```

CPU Frequency Scaling:
This isn't installed by default.  Of course you could install powernowd, but my favorite happens to be cpudyn.  You can download either one afterwards and it will install itself.  I've never had a problem with cpudyn and some report that it has lower-latency than powernowd, which could be useful for audio/video editing, etc.  

How to contribute?
The easiest way is to just stand up and be counted by allowing the "popularity-contest" feature be enabled during install.  This collects data on the packages you install on a weekly basis, and provides feedback to the Debian devs on how many people are actually using the release.  It is off by default.  If you miss it during install, you can enable it afterwards with

```
dpkg-reconfigure popularity-contest
```

I've always disliked this name, as I doesn't really reflect any sort of "contest" between distros or communities.  It is just a tally, really.  To see the data being used:

[http://popcon.debian.org/](http://popcon.debian.org/)

The other usual way is to help out your fellow user, be it Debian or Ubuntu since we have common problems and common solutions.  You can apply much of what you read in the Ubuntu PPC Faqs to your Debian install.  You can get even more involved with bug-reports, mailing lists, etc.

The thing to remember is that by helping Debian as the source, you are also helping your neighbor who may choose to run solely Ubuntu ppc.  There should be no contention between us.  Each has their merits.

If you do decide to get more involved with the Debian community, the same rules apply as they do here for best results:  Know your machine, try what is listed in the faqs or mailing lists, and then if all else fails, ask for help.

Get to know your machine:
There are a few good resources out there.  One of my favs is:

[http://www.everymac.com/](http://www.everymac.com/)

There are others, so find what suits you best.  If something in the Ubuntu ppc faqs doesn't seem to work right off the bat, be sure to look at the Debian mailing list archives:

[http://lists.debian.org/debian-powerpc/](http://lists.debian.org/debian-powerpc/)

Hopefully, by providing support for the parent project, we can indirectly help our beloved downstream Ubuntu release and it's community members.

---

### Post by mkvnmtr on 2008-11-20
I never thought that I might use Debian for Power pc. K feel it is important for me to dual boot and I think I am having a virus or adware problem on my Mac system. I don't trust it for doing things that involve money any longer. I guees I should look into Debian. Thank you for the idea.

---

### Post by Leslie Viljoen on 2008-11-21
Thanks for this. I was under the impression that Ubuntu basically was Debian, except with faster releases and a bit prettier. So I thought any problems in Ubuntu would also be in Debian. Is this not true? Where can you find the differences between the two?

While we are about pooling PPC resources, perhaps it's a massive crying shame that there's both Ubuntu and Debian still going on. Do the projects have different goals, or just different management?

---

### Post by oswaldkelso on 2008-11-21
My 2bits on Debian, 
Ubuntu and PPC


[http://www.debian.org/intro/about](http://www.debian.org/intro/about)

[http://www.debian.org/social_contract](http://www.debian.org/social_contract)

[http://en.wikipedia.org/wiki/Debian](http://en.wikipedia.org/wiki/Debian)

[http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions#Architecture_support](http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions#Architecture_support)



As you can see Debian "The Universal Operation System" has quite  a different set of goals to most other Linux distributions. It aims to support as many architectures as it can, and offer its users as much choice as it can. Whilst remaining "free". That said, these supported architectures are petty much, all getting pure not really considered a special case. Debian. This means there is a reluctance to create arch specific part of the forum (We tried). The fact that 90% of desktop pc's are 32 bit and Debian does not  really consider 64 bit and ppc a special case, does not aid ppc. Debian is an Operating System first and a Desktop distribution 2nd. Because there are many professional and power users. The Debian forums though friendly can be a shock to new users migrating from Ubuntu etc. New users that demand an answer get short shrift. The forums at first look can appear intimidating. You are  expected to do some homework via the search or google first. Answers to most common questions is nearly always to be found already answered. Obvious lost souls are normally taken by the hand. I have also noticed that the geeks come out the woodwork for genuine and really tricky stuff.



A post from the Debian forums that sums up the differing Debian offerings quite well.



PostPosted: 2008-11-14 00:29   by Bio tube

Debian is a beast in four (five) parts:



Experimental: Where SVN-pulls and other works in progress go. Packages in here might be extremely dangerous.



Unstable(permantly "Sid): When a new version of a package(or a new package all together) gets uploaded, it usually goes here. Sid machines can be highly volatile(giving birth to the saying "If it breaks, you get to keep both halves"), although it's calmed down in recent years thanks to experimental.



Testing(currently "Lenny", about to be "Squeeze"): After a while, a package in Sid with no really bad bugs gets moved here(the exact time depends on the urgency of the update). For this reason, it's much more stable than Sid. Since packages are updated fairly quickly, it's recommended for desktop users(don't let the name fool you - testing can be more stable than some distros'(especially the-one-that-cannot-be-named) releases).



Stable(currently "Etch", soon to be "Lenny"): Every once in a blue moon, the Debian release team puts testing in what's know as "The Big Freeze". During this time, nothing but bugfixes may be moved to testing. Once all release-critical(RC) bugs are gone, testing becomes stable and a new testing branch is opened. Since only bugfixes are allowed in stable, the packages tend to get dated rapidly.



Oldstable(currently "Sarge", soon to be "etch"): Where stable goes when it gets replaced. oldstable is supported for a year after the next release.



Lenny's currently in The Big Freeze, so it's fairly safe to move even servers to.





Lenny being in freeze means its going stable (150 odd bugs to go) this make its packages a little old. Once Lenny is stable, users running testing and sid will have packages of the a similar spec or newer than Ubuntu 8.10. A warning about sid  [http://wooledge.org/~greg/sidfaq.html](http://wooledge.org/~greg/sidfaq.html) though alittle old a good insight. Out of the box Debian is a little plain, you are expected to make it "yours" I went to Debian when Ubuntu dropped official ppc support. Great move for me and my ppc machines. The only thing I've  missed has been the easy going forums here, probably as I'm no geek, no interest in being one, just wanted to run a "free OS".
 That said, in the Debian forums there is not a day goes by when I don't read/learn some interesting little snippet. But even in off-topic things have to be vaguely computer related. I guess it's felt you have the rest of the internet to chat on, or what ever. And only if your a regular does this get much lea-way. 


Ubuntu aims can be summed up by "Bug no 1" i.e. it wants to replace Windows as No 1 (be the most common  place desktop). I suspect ppc was just a casualty on the road there.  Ubuntu takes a&#8221;snapshot&#8221; of Debian sid and tries to stabilize, tweak and polish it etc. Every 6 months it repeats this. Apart from LTS which is tweaked every 3 years?  Ubuntu tries to hand hold a lot so adds or creates many features to add this. The forums here are part of that, geared to noobs, and getting people up and running

---

### Post by stream303 on 2008-11-21
I couldn't have said it better myself.  Good stuff.

The big advantage that Ubuntu-PPC used to have, was that a dedicated forum easily facilitated the hand-holding crowd.  I was one who needed that myself and have wanted to repay that assistance to users like yourself and others over time.  With a combined forum, things are a bit more difficult - and the last thing a ppc-er needs is just one more hurdle. :)

---

### Post by Leslie Viljoen on 2008-11-21
Well I couldn't find a local mirror for Lenny so I got Etch.5. Now parted won't resize my Ubuntu partition because it says there are incompatible features enabled - I guess the resize_inode feature. The tune2fs with Etch won't touch that feature so I am trying to change it with Ubuntu. 

We'll see if my triple-boot works!

---

### Post by tiresia on 2008-11-21
To download Debian Lenny
[http://www.debian.org/devel/debian-installer/index.en.html](http://www.debian.org/devel/debian-installer/index.en.html)

---

### Post by Leslie Viljoen on 2008-11-21
Yeah, but I coulnd't find a local mirror of the Lenny CD image. Just the packages. So I'll install Etch and upgrade to Lenny.

Even after turning off the resize_inode feature, parted still won't resize my Ubuntu partition, so I deleted it. Debian in 3 hours!

---

### Post by Leslie Viljoen on 2008-11-22
Ok, got Etch.5 running. Next time I would spend the time to get Lenny directly rather than going through Etch, because the update is 800MB! I expected around 300MB. But you guys did say I should get Lenny so: live and learn! 

For now, Tuxpaint is working again, wireless is broken again. Back to the Gutsy days!

---

### Post by Leslie Viljoen on 2008-11-22
Another thing: I got Gnome by default because I chose "standard desktop" or somesuch. Next time I'll install no desktop and then install XFCE directly.

---

### Post by stream303 on 2008-11-22
> **tiresia said:**
> To download Debian Lenny
[http://www.debian.org/devel/debian-installer/index.en.html](http://www.debian.org/devel/debian-installer/index.en.html)

The only problem that may arise with this, is that it is a live-installer, and may not run if the user has minimal memory on an older machine.  Thus, the text-based, or standard Debian installer might be the best bet.  It is also a release-candidate of the live installer, so there might be problems there.  However I'm sure they'd welcome feedback from ppc'ers that do have the necessary ram (and can get past possible xorg.conf issues right off the bat)

Gotta' score one for Ubuntu-PPC for their live-desktop installers! :)

---

### Post by stream303 on 2008-11-22
> **Leslie Viljoen said:**
> Ok, got Etch.5 running. Next time I would spend the time to get Lenny directly rather than going through Etch, because the update is 800MB! I expected around 300MB. But you guys did say I should get Lenny so: live and learn!

I did notice that a full selection of images were available for bittorrent, so that might be the best option.  Perhaps the CD images are getting regenerated as I notice a pretty big update as well.

Like Ubuntu, we can install any other desktop environment that isn't part of the standard image, but be sure to look for the KDE or XFCE4 specific install images to make it a bit easier next time right from the start.

(I can't tell you how many times I have installed/reinstalled Ubuntu or Debian over the years.  I'm amazed my power switch has held up.)

Since I don't do wireless, I can't really guide you there, but you may want to search the Debian list archives to see if the lack of this could be a show-stopper for you.  I'm pretty sure that the B43xxx firmware cutter isn't looked upon very highly.

However, the gist here isn't to duplicate an Ubuntu environment, but to provide support for the upstream Debian project to feed back down to Ubuntu-PPC, so perhaps certain things can be overlooked, or worked around with say a free-source usb wireless stick...  It should be much easier once kernel 2.6.27 comes along.

---

### Post by mfox on 2008-11-22
Nice post, stream303.  I was already a Ubuntu user who switched to Debian Lenny on my PowerBook G4 when Debian fixed Mac-on-Linux. (Ubuntu still hasn't; there is a post about this in this forum.)  Before installing it on my PowerBook, I tried Debian in virtualization on my Mac mini.  Debian has a reputation of being more difficult for novice users, but perhaps as a result of my Ubuntu experience, I didn't find it difficult at all.  Having Ubuntu on other Macs, I find working with Debian to be complementary; when I learn something about one it often applies to both.

One thing that really impressed me about the Debian forums is that you can actually talk to the Debain programmers on them.  (This might be true in Ubuntu as well; I just don't know who the Ubuntu programmers are.)  In this case, it was about Mac-on-Linux (MOL).  I was frustrated that it didn't work on Hardy when I knew that it worked on openSUSE 11 (which is also installed on my PowerBook for that reason).  I searched the net and came across some communication between two Debian developers about fixing MOL on Lenny.  I followed this for a month, at which point there was talk of a patch and getting it upstream in Lenny.  I emailed the developer to ask if this was done yet and heard immediately back from him in the affirmative.  I then installed Lenny, but couldn't get MOL to work.  So I went to the forums, posted a query about this, and lo and behold, the same two developers who were communicating about it in the earlier note, responded to my query with a simple fix.  (It worked.)

The biggest difference I notice between Lenny and Ubuntu (8.04, 8.10) is in branding - Debian doesn't put its brand on the gnome menu and it uses an unbranded browser (Iceweasel) instead of Firefox.  I was surprised to find that even Debian makes it easy to obtain non-free add-ons like codecs you need to play music files; just like Ubuntu.  Getting AirPort wireless to work on Lenny took one extra step relative to Ubuntu, but it was easy.

---

### Post by stream303 on 2008-11-22
> **mfox said:**
> Debian has a reputation of being more difficult for novice users, but perhaps as a result of my Ubuntu experience, I didn't find it difficult at all.  Having Ubuntu on other Macs, I find working with Debian to be complementary; when I learn something about one it often applies to both.

You got that right!  That's an old reputation that no longer applies, especially for Ubuntu PPC users that use the "alternate" installer.  When the live DI installer gets polished, it will be even easier, provided the ppc user has enough ram - but even then we'll still have to manually edit some things.  Thus, the community lines become gray areas where we all benefit from each other's knowledge.

> One thing that really impressed me about the Debian forums is that you can actually talk to the Debain programmers on them.

This is very true, but you did your homework up front.  Busy guys, these devs. :)  While we all wish they were chained to their cubicles and fed nothing but pizza and cola to work on ppc, I suspect they support other architectures mainly. :)  That makes their contributions to PPC even more valuable.

> The biggest difference I notice between Lenny and Ubuntu (8.04, 8.10) is in branding - Debian doesn't put its brand on the gnome menu and it uses an unbranded browser (Iceweasel) instead of Firefox.  I was surprised to find that even Debian makes it easy to obtain non-free add-ons like codecs you need to play music files; just like Ubuntu.  Getting AirPort wireless to work on Lenny took one extra step relative to Ubuntu, but it was easy.

Now we're stepping into gNewSense FSF territory. (also recommended!, but no ppc as of yet)  Much of it depends on how involved one gets when determining the difference between open-source and free-software, but that's a different thread. :)

I heartily recommend Gnome's Epiphany-Browser especially for lower-spec Macs.  Firefox / Iceweasel are great, but sometimes even that is too much for a 128mb box.

I'd also like to compile IceCat for PPC.  Like IceWeasel, but it may have some additional security features worth looking into, and possibly a nice intro to free vs open software.  I don't want to get too heavily into that in this thread, but here's a handy link:

[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)

In the end, we all have more in common than not, and Ubuntu's PPC forum served a great purpose by providing a hand-holding area that didn't annoy the other users not interested in that architecture.

---

### Post by ubuntubrian on 2008-11-22
Hey Mfox, thanks for the post. I saw your other post that you refer to and stumbled upon this one by accident.
I want to keep using my 2 powerbooks, a G3 Lombard and a TiBook G4, usable as long as possible. Waste not, want not, you know!
I have enough room on both to triple boot the TiBook and dual boot the G3. Are you able to write a How To? That would be very helpful.
Are you able to watch flash content? Does gnash work, or swfdec? How about importing photos with F-Spot or Gthumb?
these are all things that have worked at some point in my journey from Warty to Intrepid and I'm getting tired of fixing things-makes me miss OS X, almost....

---

### Post by Leslie Viljoen on 2008-11-23
Ok, Lenny is installed after a day of downloading. Unfortunately, it may be worse than Intrepid. Like Fedora and Intrepid, SDL seems incomptible with directfb on these releases and so NO SDL programs work, they all crash, completely logging me out of my X session. It could be related to this problem here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=342053](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=342053)

Though those reports are three years old. Pure OpenGL programs seem to work. Wireless doesn't work - I'll start reading up on that again but in Intrepid it was detected and sorted out automatically.

Thunar and XFDesktop do not crash, so that's a small improvement, but at this point I wish I'd stayed on Etch-and-a-half (though wireless would probably not work there).
I struggled so much with wireless before Intrepid though that I ran cables in the roof - so I can live without that. 

:(

---

### Post by Leslie Viljoen on 2008-11-23
Bug reported, after much work:
[https://bugs.launchpad.net/ubuntu/+source/directfb/+bug/301278](https://bugs.launchpad.net/ubuntu/+source/directfb/+bug/301278)

I don't have much faith in it being read though, if you look at the list of bugs I have ever reported. Should I try reporting it at Debian too, or would they see it in Launchpad?

---

### Post by Leslie Viljoen on 2008-11-23
How's this for irony: MOL works in Lenny and Tuxpaint runs reasonably well in there.

---

### Post by mfox on 2008-11-23
> **ubuntubrian said:**
> Hey Mfox, thanks for the post. ....
I have enough room on both to triple boot the TiBook and dual boot the G3. Are you able to write a How To? That would be very helpful.
Unfortunately, I didn't document everything I did in the many distros I tried on my PowerBook, so I can't write a how-to.  What I do remember about installing Lenny was that it wasn't difficult at all, and that I had to get wireless working right after the installation.  There were simple instructions on the Debian site, and it worked right away.  (FYI, I never could get Etch to run my AirPort wireless very well, although the r4 version may have fixed that.)

> **ubuntubrian said:**
> Are you able to watch flash content? Does gnash work, or swfdec? How about importing photos with F-Spot or Gthumb?
I think this is a sore spot in any Linux PPC installation; I know of no way to get Adobe Flash installed on Debian or any other, and I've searched and tried.  I did install gnash and swfdec, and this gave me some functionality.  I can watch YouTube videos, but they stutter and aren't all that pleasant.  Using Safari on MOL gives a slight improvement, but it's still not the smooth video you see on Mac or Windows with Flash installed.  Good reason to leave MacOSX as a dual boot, even if you use Linux as your default system on a PPC.

> **ubuntubrian said:**
> these are all things that have worked at some point in my journey from Warty to Intrepid and I'm getting tired of fixing things-makes me miss OS X, almost....
I hear you!  OS X may not be free, but it just works, and although Linux distros are getting better and better, they will probably never accomplish the ease of operation inherent in the Mac OS.  That doesn't stop me from being interested in Linux; I'm more comfortable with its basic philosophy and I'm getting less comfortable all the time with the restricted hardware choices Apple gives me.  And PPC is a special case where Linux works less smoothly than it does on Intel/AMD hardware.  But my PowerBook is perfectly operational and I don't feel the need to buy another laptop as of yet.  And by and large, Lenny is pretty functional on it and hasn't been hard for a relative novice like me to set up.  (I would say the same about Ubuntu Hardy, but I really wanted MOL and it doesn't do it.)

I can't speak about the functionality and ease of use of either Lenny or Hardy on G3 hardware.  I once tried installing Ubuntu on an "old world" G3 - a beige.  I couldn't get Gutsy to work; I had to go back to 6.06 LTS.

---

### Post by Leslie Viljoen on 2008-11-23
> **ubuntubrian said:**
> Are you able to watch flash content? Does gnash work, or swfdec? How about importing photos with F-Spot or Gthumb?
these are all things that have worked at some point in my journey from Warty to Intrepid and I'm getting tired of fixing things-makes me miss OS X, almost....

Not sure if you saw my other post: you can get around the Flash requirement for watching Youtube videos if you just download them and watch them from your harddrive with VLC. To do this, install Firefox/Iceweasel's "fast video download" plugin.

---

### Post by mfox on 2008-11-23
> **Leslie Viljoen said:**
> Ok, Lenny is installed after a day of downloading. Unfortunately, it may be worse than Intrepid. Like Fedora and Intrepid, SDL seems incomptible with directfb on these releases and so NO SDL programs work, they all crash, completely logging me out of my X session. It could be related to this problem here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=342053](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=342053)

Though those reports are three years old. Pure OpenGL programs seem to work. Wireless doesn't work - I'll start reading up on that again but in Intrepid it was detected and sorted out automatically.

Thunar and XFDesktop do not crash, so that's a small improvement, but at this point I wish I'd stayed on Etch-and-a-half (though wireless would probably not work there).
I struggled so much with wireless before Intrepid though that I ran cables in the roof - so I can live without that. 
:(
I had a similar dilemma with Etch and Lenny.  When I first tried them, wireless wouldn't work properly on Etch and Mac-on-Linux (MOL) wouldn't work on Lenny.  So I went to openSUSE 11, and both worked, except I couldn't get my favourite music player (Rhythmbox) to play mp4's I had in iTunes.  Eventually, Lenny was updated and MOL worked on it, so I installed it alongside of openSUSE.  But as I just found out in response to ubuntubrian's query, Adobe flash can't be installed on any of them (there is no PPC version and no way I know of to compile it from source), and neither swf or gnash give equivalent functionality to watch videos on a browser.  PPC Linux is one big compromise.  So if you want to have OS X-equivalent functionality, you're best off to set up your PPC as dual boot.

---

### Post by mfox on 2008-11-23
> **Leslie Viljoen said:**
> Not sure if you saw my other post: you can get around the Flash requirement for watching Youtube videos if you just download them and watch them from your harddrive with VLC. To do this, install Firefox/Iceweasel's "fast video download" plugin.

Thanks; I didn't know that.  Sorry if this is a stupid question, but how do you download a YouTube video?  I don't see that option on the YouTube site; only uploading.

---

### Post by Leslie Viljoen on 2008-11-23
> **mfox said:**
> Thanks; I didn't know that.  Sorry if this is a stupid question, but how do you download a YouTube video?  I don't see that option on the YouTube site; only uploading.

As I said: install the [fast video download]("https://addons.mozilla.org/en-US/firefox/addon/3590") add-on.

---

### Post by ubuntubrian on 2008-11-23
So onward!
I can watch Youtube vids by downloading them, if Firefox doesn't crash, which it is doing at a very annoying rate since upgrading to Intrepid. this doesn't help watching other flash content on many sites but i know that gnash is working on that. What is frustrating is that I will have the gnash plugin working and then after an update I lose it again!
With the upgrade I have lost several apps working. I loved Banshee as I could listen and write audio CD's from MP3's. Now Banshee won't run at all with an sqlite error. Must be connected to this when I run the UpdateManager:
```
Setting up postgresql-8.3 (8.3.4-2.2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                     * Starting PostgreSQL 8.3 database server                                                                   * The PostgreSQL server failed to start. Please check the log output:
2008-11-23 09:57:18 MST FATAL:  unsafe permissions on private key file "server.key"
2008-11-23 09:57:18 MST DETAIL:  File must be owned by the database user or root, must have no write permission for "group", and must have no permissions for "other".
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):

```

when I check the permissions on "server.key" they are as required in the error output. Same the file that it links to, /etc/ssl/private/ssl-cert-snakeoil.key.
any ideas on that one? this happened after the upgrade to Intrepid. Also all of these:
```
dpkg: error processing bzr (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bzrtools:
 bzrtools depends on bzr (>= 1.6~); however:
  Package bzr is not configured yet.
 bzrtools depends on bzr (<< 1.7~); however:
  Package bzr is not configured yet.
dpkg: error processing bzrtools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bzr-builddeb:
 bzr-builddeb depends on bzr (>= 1.2~); however:
  Package bzr is not configured yet.
 bzr-builddeb depends on bzrtools (>= 1.2); however:
  Package bzrtools is not configured yet.
dpkg: error processing bzr-builddeb (--configure):
 dependency problems - leaving unconfigured

```

So perhaps this is too much for this thread?

What is so frustrating is that most everything worked in Dapper, except the gnash plugin (tho it did a couple of times) and all the way to Hardy things seemed to be getting better. Now there seems to be an increase in problems.KDE apps can't upgrade and the issues above.some apps no longer run at all. Ahhh.......
sorry about the rant!

---

### Post by Leslie Viljoen on 2008-11-23
> **ubuntubrian said:**
> when I check the permissions on "server.key" they are as required in the error output. Same the file that it links to, /etc/ssl/private/ssl-cert-snakeoil.key.
any ideas on that one? this happened after the upgrade to Intrepid.


What are the permissions for the file? Are you sure there's not another "server.key" somewhere else on your system? 

> 
 Also all of these:
```
dpkg: error processing bzr (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bzrtools:

```


Just looks like the install didn't complete. Normally "apt-get -f install" fixes that sort of thing. But perhaps you need to fix the server.key problem first?

---

### Post by ubuntubrian on 2008-11-23
thanks for the prompt reply Leslie!
In checking the properties with nautilus I get the server.key permissions as Root-read and write
Group-read only
Others-none
However, in terminal I get this:
lrwxrwxrwx 1 root     root       38 2008-07-31 23:07 server.key -> /etc/ssl/priv

Which appears to grant read-write to all. I'm not good with permissions in the command line so if anyone can help here I'd appreciate it. The permissions for the linked to file in Nautilus are the same as above but in terminal are:
-rwxr-x--x 1 root ssl-cert 891 2006-04-25 13:08 ssl-cert-snakeoil.key
which appears to be correct.

As far as running "apt-get -f install", I have done that repeatedly to no effect and actually get the exact same errors as I reported previously. Maybe getting the server.key permissions correct will solve this.

Oh, and there are lots of issues around importing photos eitherin F-Spot or gthumb. Since the upgrade.....
thanks again.
I will say that our community support is stellar and we are all trying to figure this stuff out. I am starting to be concerned with the amount of time it takes for me, however.

---

### Post by Leslie Viljoen on 2008-11-23
Ok, you need "chmod 640 ssl-cert-snakeoil.key". The message stipulates "no permissions for other", and you have "x" permission (execute). 

BTW: You are right about putting these things in new threads because I think this one is losing the plot!

---

### Post by ubuntubrian on 2008-11-23
thanks again Leslie! that fixed the permissions issue and postgresql started.
The other apt-get errors still exist but no need to go into that here, as you say.
I may install Lenny on the G3 as a dual boot with Intrepid though I have a Broadcom wireless card that is a pain, having to use the Broadcom cutter fix. It took quite some time in Hardy and Intrepid the 2 times I did it and I'm not looking forward to that.
Judging from your Lenny experience (which seems much worse than Mfox's) I may just hold off. I had some luck with Fedora a while backso maybe that.
I'm hoping that there are some fixes for we PPC users soon for Debian and Ubuntu use. 
Thanks again and see you on the Forums!!:popcorn:

---

### Post by Leslie Viljoen on 2008-11-23
No problemo. Looks like you should have bzr 1.5 at least. That should make everything happy. 

[This]("http://packages.ubuntu.com/search?keywords=bzr&searchon=names&suite=intrepid&section=all") says you should have 1.6.

**dpkg -l bzr** would perhaps shed light on the mystery.

---

### Post by oswaldkelso on 2008-11-23
> **Leslie Viljoen said:**
> As I said: install the [fast video download]("https://addons.mozilla.org/en-US/firefox/addon/3590") add-on.

I find gnash not quite there for all sites on ppc so for you-tube use "clive". Its in the Debian repos, so is tested and "free". I haven't installed flash even on my new non ppc net-book. I still use clive. A little how to below.
  
[http://forums.debian.net/viewtopic.php?t=25187](http://forums.debian.net/viewtopic.php?t=25187)

In its most basic form, highlight the youtube url, open a terminal, type. clive  paste url and hit return. Repeat in new tabs for more videos.

---

### Post by ubuntubrian on 2008-11-23
thanks again Leslie! I moved my bzr issue to: [http://ubuntuforums.org/newthread.php?do=newthread&f=328](http://ubuntuforums.org/newthread.php?do=newthread&f=328)
I'm also adding a Banshee thread as I have had no luck resolving that issue either (it's not the postgresql problem I was having)
that thread is here:
[http://ubuntuforums.org/showthread.php?p=6238016#post6238016](http://ubuntuforums.org/showthread.php?p=6238016#post6238016)

I will check out Clive too!

---

### Post by ubuntubrian on 2008-11-23
Sorry-the bzr thread is: [http://ubuntuforums.org/showthread.php?p=6238028#post6238028](http://ubuntuforums.org/showthread.php?p=6238028#post6238028)

---

### Post by ubuntubrian on 2008-11-23
solved the bzr issues. Yeah!

---

### Post by mfox on 2008-11-23
Looks like we're all making progress, bit by bit.  ubuntubrian, I'm surprised you've had such difficulty installing the broadcom wireless firmware in the past.  Any time I've tried it, the fix is either quick and straightforward, as in Unbuntu Gutsy and Hardy, Debian Lenny and openSUSE 11, or it didn't work at all (as in Debian Etch and believe it or not, Yellow Dog 6).  In each case, I've been able to follow cookbook instructions posted in a forum.  Could it be because your AirPort card isn't AirPort extreme?

You want difficult - try getting Rhythmbox to play mp4's in KDE or openSUSE gnome.  I've wasted more time downloading codecs to make that work than I can count.  :confused:

---

### Post by ubuntubrian on 2008-11-24
Actually, I am just complaining about the broadcom issue. I can just copy the broadcom patches and install them. I use the broadcom directions and it's not too hard to copy and paste.
BTW, I ran "aptitude autoclean" and all of those broken and weird KDE apps got repaired or dumped. I may even try to install Kubuntu desktop to get Amarok and others back.
What app in gnome will catalog, play and burn audio CD's from MP3s and other formats besides Banshee?
Onward and upward! "Engage".

---

### Post by mfox on 2008-11-24
> **ubuntubrian said:**
> What app in gnome will catalog, play and burn audio CD's from MP3s and other formats besides Banshee?

Rhythmbox will catalog and play, but I don't think it will burn.  It's very attractive and iTunes-like; my favourite.

---

### Post by Leslie Viljoen on 2008-11-24
> **mfox said:**
> I had a similar dilemma with Etch and Lenny.  When I first tried them, wireless wouldn't work properly on Etch and Mac-on-Linux (MOL) wouldn't work on Lenny.  So I went to openSUSE 11, and both worked, except I couldn't get my favourite music player (Rhythmbox) to play mp4's I had in iTunes.  Eventually, Lenny was updated and MOL worked on it, so I installed it alongside of openSUSE.  But as I just found out in response to ubuntubrian's query, Adobe flash can't be installed on any of them (there is no PPC version and no way I know of to compile it from source), and neither swf or gnash give equivalent functionality to watch videos on a browser.  PPC Linux is one big compromise.  So if you want to have OS X-equivalent functionality, you're best off to set up your PPC as dual boot.

Hehe, I got wireless working in Lenny! I went [here]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware") and followed the directions under "You are using the b43 driver from linux-2.6.25 or newer".

I rebooted but it still didn't seem to work. Then this morning I tried and it was working fine.
Now if I can get directfb (and SDL) fixed, I think I'll have a properly working system!

---

### Post by bishnuroy on 2008-11-24
**:guitar:**Do online data entry job more then 50 International companies directly on their working server. Offer available worldwide. Work in the comfort of your home. A genuine Typing job from worlds best home based business provider. Work free before you register. earn a guaranteed $5000 p.m Payment proof available. 
For more details Visit Us at [http://www.geocities.com/meet_multi](http://www.geocities.com/meet_multi)   or
[http://www.fullfill.webs.com](http://www.fullfill.webs.com)  
E-Mail us at [email]info@365jobs4u.com[/email]
call us at +91-9377944133/9898583959.

---

### Post by ubuntubrian on 2008-11-24
Yeah, that's why I liked Banshee. It did it all. I've used Rhythmbox but I liked the Banshee features. turns out that this is probably a PPC issue that I'm having in any case. I'm trying a workaround of sorts from my post on the Banshee forums.

---

### Post by ubuntubrian on 2008-11-24
Glad you're getting somewhere Leslie.
I made some progress too. Now I can run amarok (after running aptitude autoclean, update, dist-upgrade, it became installable) and with the proper codecs can burn audio cd's from mp3's via K3b. Banshee used to do it all but this is pretty seamless, though unattractive! KDE not my favorite but it works great!!

---

### Post by tealio on 2008-11-24
mfox - i'm currently running Ubuntu on my iBook G4 1.42Ghz.  I chose Ubuntu because, like so many others, i just got sick of the bulky OS, restrictive software, etc, etc, etc... also i was able to find more info about getting the Airport Extreme to work... I actually prefer Debian, just because i know it better.

What steps did you take to get Airport Extreme to work under Debian?  the b43 fwcutter package? i guess just add the right repository to /etc/apt/sources.list?

more info on this would be greatly appreciated.

***Edit: i quit reading too soon... i'm checking out the instructions above...

---

### Post by mfox on 2008-11-24
> **tealio said:**
> ...What steps did you take to get Airport Extreme to work under Debian?  the b43 fwcutter package? i guess just add the right repository to /etc/apt/sources.list?

***Edit: i quit reading too soon... i'm checking out the instructions above...
Yep, the 'ol b43 fwcutter package, for Lenny.  I can't remember what steps I tried in Etch, but it took something earlier than b43.  I never got it to work properly in Etch.

---

### Post by mfox on 2008-11-24
> **ubuntubrian said:**
> Yeah, that's why I liked Banshee. It did it all. I've used Rhythmbox but I liked the Banshee features. turns out that this is probably a PPC issue that I'm having in any case. I'm trying a workaround of sorts from my post on the Banshee forums.
Funny how different our experiences can be.  I like the look of Banshee, but I could never figure out how to play mp4's on it.  Since my music is imported from iTunes, inability to play mp4's makes it useless to me.  With Rhythmbox, I've had trouble figuring out the codecs for playing mp4's in openSUSE and any distro running KDE.  Amarok is the easiest to configure across Gnome and KDE in any distro I've tried.  But I don't care for the way Amarok is organized so I don't use it unless I can't get Rhythmbox to work.

---

### Post by Leslie Viljoen on 2008-11-25
Getting back to the Debian issue: I have contacted the original Debian maintainer of a package I reported a bug in almost a year back (wajig). He hadn't seen the bug in launchpad yet, which makes me think that perhaps launchpad is not the best place to report bugs unless they are bugs specific to Ubuntu (ie. packaging bugs). Advice from some MOTU's was to report directly upstream if you know the bug is in the original software. 

There is apparently no queue for bugs to be handled, they are handled ad-hoc by people interested in them. I don't think bug reporters realise this, and it could be quite frustrating for them.

Since I think I can contribute best by helping find and fix original-software bugs, I may just move to Debian on all my machines and so any fixes will trickle down to Ubuntu. But I may become a MOTU too so I can help streamline fixes: launchpad seems completely overwhelmed.

---

### Post by stream303 on 2008-11-25
> **Leslie Viljoen said:**
> Getting back to the Debian issue: I have contacted the original Debian maintainer of a package I reported a bug in almost a year back (wajig). He hadn't seen the bug in launchpad yet, which makes me think that perhaps launchpad is not the best place to report bugs unless they are bugs specific to Ubuntu (ie. packaging bugs). Advice from some MOTU's was to report directly upstream if you know the bug is in the original software.

Most definitely! 

In many cases once a bug has been identified in LaunchPad for Ubuntu PPC, it may take a LONG time for it to be even looked at and actually verified as an Ubuntu bug.  And then, it *might* get turned over to Debian as an upstream issue, even though there are a few devs that are involved with both Debian and Ubuntu at the same time.  It can be a long wait, and then the process starts again from the Debian side to actually verify that it is truly a bug of theirs!

Case in point - the nv video driver for PPC starting with Hardy has a slight shift to the right on a 20" iMac screen.  Maybe a quarter-inch.  Not a showstopper, but it turns out that not only is it not an Ubuntu bug, nor even a Debian bug - it comes all the way upstream from freedesktop.org.  (it has been reported and verified by all parties, but to date, no action has been taken since it might be a regression to fix a bug seen by a larger majority of Intel users.)

One tip for reporting PPC bugs is to find the ones that are truly unique, and not just a rehash of the ones that are known issues that cannot be fixed unless the manufacturers release the specs to the devs. Knowing these is an art unto itself and requires involvement in the mailing list communities, etc.  Putting an emphasis on getting a black screen bug fixed on your Pismo might take a back seat to another issue on a more recent machine. :)  I'm not saying don't report a bug, but it is vitally important time-wise to search out for duplicate bugs and get a handle on what are show-stoppers, and which are legacy bugs that can be fixed by manual configuration editing.

One example of an Ubuntu-specific bug is that during installation on certain G5's the fan runs at full speed during install, and only calms down after the first reboot - whereas with Debian the fans are under control during install.  This is just a general annoyance, so that's why I'm not going crazy over it getting fixed - I'd rather try to dig out other show-stoppers first.

Intrepid 8.10's show-stopper need for *modprobe ide-scsi* to get your cdrom recognized out of the gate is certainly Ubuntu-specific.  Unfortunately, we can't find these when ppc is beta or RC'ed so late in the release cycle.  And even if they are found, it is so late that nothing can be done about it.  Debian doesn't have this problem, so some bugs could be fixed if Canonical would release to us early like the rest - provided they actually put some resources into it after the report!  At this stage however, it seems that some bugs are mainly about not allowing for time on non-commercial architectural support to concentrate solely on those that are.  It's just a matter of resources and timing.

This kind of cdrom-detection bug out of the gate is showing up more and more during the past several RC releases even when they do become available!  Not only are the RC's late in the cycle for us, but it makes it even harder for us to test it when we can't get past step one, and spend much of our time hunting down some sort of workaround - and then again it's too late to do anything about it.  By then, many possible ppc users just go on to other things.  Sorry - got on a rant-tangent again. :)

There are also devs in Debian that might have the faster track on getting bugs fixed in the ppc kernel too.

So there is the side-benefit of running Debian - if the bug also appears there as well as in Ubuntu, you can help fast-track it by getting it upstream faster.  And then hopefully it trickles down.

---

### Post by Leslie Viljoen on 2008-11-25
My question is: why run Ubuntu on PPC? The whole advantage of Ubuntu is that it is pretty, well-polished and convenient to use. There is amazing support. But on PPC only the forum applies. Ubuntu PPC should be dropped completely and the forum continue as a Debian forum - the half-baked PPC release actually disadvantages everyone because:

1. Users waste time and bandwidth trying a severely broken distro
2. Users get disappointed because they expect what they've been getting on x86
3. Users may drop Linux because they may be used to Ubuntu being the easiest
4. Bugs go to launchpad and are not looked at much, clogging up launchpad further
5. Devs need to search more bug trackers
6. Ubuntu devs waste time building broken ISO's

Like my Mom said: if you're going to do something, do it well.

---

### Post by Leslie Viljoen on 2008-11-25
q

---

### Post by stream303 on 2008-11-25
> **Leslie Viljoen said:**
> Like my Mom said: if you're going to do something, do it well.

Without any real access to the ones who develop it, they may be doing the best they can. :)  Or is it just auto-builds on auto-pilot?  Who knows?

But more to the point - with the recent emphasis on becoming more OSX-Like, and with commercial sustainability with the likes of paid-for codecs, who would pour money and resources into Apple boxes that have had their ppc architecture dropped years ago - possibly to the detriment of the others?  As much as we'd like it, that wouldn't be very "ubuntu" on the whole when the majority is considered.

I'm really amazed that there was life beyond Hardy. With the upcoming emphasis on becoming OSX-like, unless there is an outpouring of Linux love from Cupertino with docs for our hardware for the devs, it may be very hard and possibly risk a black-eye to make PPC very OSX-Like, considering the the problems mentioned above.

This may be one reason to de-emphasize ppc, if that is actually what is going on.  The first comparison anyone is going to make when the OSX-like goodness really takes off, might be stymied if the natural comparison is made about how hard it is to install on a ppc box which used to run OSX natively - the users aren't aware that the devs just don't get the love from Cupertino. :)

To do PPC right today, we'd have to rewrite the installer scripts to detect the specific machine, and apply database techniques to write out the various configs to overwrite the defaults that don't work due to the hardware quirks.  (Not a bad project for anyone into shell scripting btw! - perhaps a post-install script based on lspci and /proc/cpuinfo ?)

To my amazement, Canonical still releases a PPC port, so I guess we'll just have to make the best of it.  Ubuntu's PPC demise has been predicted so many times before I don't even want to speculate.

I think the smart thing to do is what we're doing now - run Debian in addition to Ubuntu.  It is an easy transition for the most part, so Ubuntu-ppc'ers shouldn't worry *that much* :)

---

### Post by ubuntubrian on 2008-11-25
Like Tim the T-Rex said, "I don't want to go extinct!"

If anyone is game I'm up for triple booting my TiBook with OS X, Ubuntu and Debian. I'm running the first 2 already but I need help in setting up a triple boot. What I've found on line isn't helpful for me.
I want Ubuntu to work. I like it and I'm used to it. I've run Debian on my other Powerbook and it's OK but I admit that i am shallow and like some glitz in my OS.:)

---

### Post by oswaldkelso on 2008-11-26
> **ubuntubrian said:**
> Like Tim the T-Rex said, "I don't want to go extinct!"

If anyone is game I'm up for triple booting my TiBook with OS X, Ubuntu and Debian. I'm running the first 2 already but I need help in setting up a triple boot. What I've found on line isn't helpful for me.
I want Ubuntu to work. I like it and I'm used to it. I've run Debian on my other Powerbook and it's OK but I admit that i am shallow and like some glitz in my OS.:)

My experiences multi booting

[http://www.my2bits.org/?p=49](http://www.my2bits.org/?p=49)

Thats a little old but my experiences of 8.10 on ppc has been poor. Two disks both failed to install. Ubuntu including non-free on the disk does nothing to educate new users as to the importance of "why non-free is bad for Gnu/Linux" It turns it self into the bast-ard son of Osx. A free core with slaveware ontop. (I digress) 8.04 on my imac 333mhz was so slow it was painful. 8.10 wouldn't install. Lenny xfce, blackbox with rox-filer, lxde all install and run fine. Even e17 from experimental complete with animated desktop runs at a usable but slower pace. the only down side was I did need to tweak xorg to get X. Ubuntu's only saving grace on ppc is its live cd (8.04). It rocks, does everything alive CD should. I use one as a rescue disk, come diagnostic, partition resize tool, on my G4 at least. A real pity its become such a hog and gone after the up'n coming markets, intel-macs and arm etc. Neglecting older machines, one of the gnu/Linux strengths.  

Everyone laughs at Debian as they always miss their release date. Everyone says it's old. Debian users don't care. "It's ready when it's ready" is the mantra and it's only during the "freeze" that Debian testing actually gets old. Thats only for a few months every couple of years. In short, the devs try to fix the bugs before it's released, not rely on the users afterwards.

Another thing I like is the fact that I can run kernel-libre and it doesn't break anything it just works without the binary blobs (probably doesn't use them anyway but it was the principle for me.I could remove them so I should). It also seems to recognize that mono applications, though free, are not as equal under Debian than Novel. No mono application on a default Debian install. Also it does not support just the latest and greatest. So long as 5 devs (if my memory is right?) can maintain an arch in accordance with the Debian rules its in. No mater how old, irrelevant, or unsexy it is to the majority of other users.

I apologize. I'm a ppc user with no-ware ppc specific to go. The ppc forum here used to be that place. It probably still is **the** place where most new users come. But were not wanted. Just squatters. 

I've also just realized theres no two ways about it.I've defiantly become a Debian fan-boy. Even though they don't see ppc as a special case. A real pitty as there is a need for a ppc place somewhere.

---

### Post by Leslie Viljoen on 2008-11-26
> **oswaldkelso said:**
> Ubuntu including non-free on the disk does nothing to educate new users as to the importance of "why non-free is bad for Gnu/Linux" It turns it self into the bast-ard son of Osx.

Perhaps the codec installer and the proprietary device installer should have a big clear button which you can press on with the title "WHY NON-FREE IS SO BAD". This can then open this awesome site:
[http://www.getgnulinux.org](http://www.getgnulinux.org)

The goal of Ubuntu is to beat Windows on the desktop, it has to make some "pragmatism not idealism" choices to do that. I think. But it seems more successful at this than other distros, so although it's an Open Source rather than a Free Software approach, perhaps once a critical mass is reached it can be leveraged to educate people. 

Richard Stallman talks about this here:
[http://www.fsfeurope.org/documents/rms-fs-2006-03-09.en.html#we-urgently-need-people-to-work-on-stage-2](http://www.fsfeurope.org/documents/rms-fs-2006-03-09.en.html#we-urgently-need-people-to-work-on-stage-2)

I don't know if he's right or not. But almost everyone I have spoken to about this is uninterested in philosophy, happy to be spied on and pirate anything they want. They even don't care about viruses since they just reinstall. So when I recommend Linux they ask if it's better than Windows, and by 'better' they mean: can run *everything* Windows can, use *all* devices Windows can and then also has some other benefit, like not having to run cracks to "activate". They certainly don't notice they are slaves, even when I point out that they don't really know what their programs are doing and that their data is in formats that only one program/service can decode. 

I think we need both: philosophers who appreciate freedom and ignoramuses who don't, but once they have experienced enough of it they might feel pain when it is taken away, wake up and become philosophers. Without the compromise we get no support from most people, and no support from most hardware manufacturers. So I work on phase 1 and phase 2 at the same time.

> Everyone laughs at Debian as they always miss their release date. Everyone says it's old. Debian users don't care. "It's ready when it's ready" is the mantra and it's only during the "freeze" that Debian testing actually gets old. Thats only for a few months every couple of years. In short, the devs try to fix the bugs before it's released, not rely on the users afterwards.

Hehe! Since you can stay on Testing, it doesn't really get old, and you can put your servers on a stable version. My problem is that I want even my servers on the very latest because very often I am using very new technology. Like I make a Rails app and I need sqlite3. So I'd always stay on Lenny or upgrade Ubuntu every 6 months.

> Another thing I like is the fact that I can run kernel-libre and it doesn't break anything it just works without the binary blobs (probably doesn't use them anyway but it was the principle for me.I could remove them so I should). It also seems to recognize that mono applications, though free, are not as equal under Debian than Novel. No mono application on a default Debian install. 

Yes, I hate Mono. MS will find a way to hurt people using Mono, and it seems to be a resource hog. We do need a RAD programming language though, with an integrated visual designer. NetBeans is closest to that at the moment, for Java, and when Matisse gets Ruby support I hope the problem will be solved.

> I apologize. I'm a ppc user with no-ware ppc specific to go. The ppc forum here used to be that place. It probably still is **the** place where most new users come. But were not wanted. Just squatters. 

We are not squatters! We still get support here. No-one's telling us to go.

> I've also just realized theres no two ways about it.I've defiantly become a Debian fan-boy. Even though they don't see ppc as a special case. A real pitty as there is a need for a ppc place somewhere.

Maybe I should start a website: Linux PPC world! I just don't think I'm going to have time or perhaps money. My existing website is so far behind.
I have to merge [http://www.lesismore.co.za](http://www.lesismore.co.za) and [http://www.freewebs.com/lesliev](http://www.freewebs.com/lesliev) and get a paid host.

I don't really think this forum is too bad though, you just need to use the PPC tags. And lots of people come here.

The thing I really don't like about the current state of affairs is that Ubuntu's ISO's are typically too broken to install properly, and people don't know before they download. And once packages are fixed, there's no way to get the ISO rebuilt so people can have hassle free installations after that. So I recommend that PPC people use Lenny from the start, and I'd like that to be a sticky at the top of this forum. If the install is OK, at least we can fix other problems later.

---

### Post by mfox on 2008-11-26
All very interesting; I'm glad we have this space to talk about such things and I'm glad we have this thread.  I'm not a fanboy for any particular distro, and while I like the GNU FSF philosophies, I'll do what I have to to make my computer functional in the ways I have come to expect it to be.  I don't expect any distro of Linux to be as user-friendly as MacOS X (never mind Windows), but I do expect to be able to operate the same range of software, even if it's more trouble to set up.  If this means using non-free codecs when appropriate free ones aren't available, I'll use non-free codecs.  If I have to compile them, no big deal, but I'm not going to be happy doing without.  The case of flash player for the PPC is borderline for me.  I can view web videos without it (thanks to Leslie and oswaldkelso), but the way to do it is more cumbersome.  If I had to do that a lot for things like music playing or work operations I do often, I would stop experimenting with Linux and just live with OSX and all that implies for software and hardware.  Fortunately, this doesn't seem to be the case, even with PPC hardware.

Debian vs Ubuntu - I don't really care which one I use.  Both are enjoyable, both are customizable, both are Linux, and best of all, I am now familiar enough with both to be able to work with them smoothly (as a relatively experienced beginner, anyway).  Ubuntu makes it slightly easier to get what I want on an Intel machine, so I tend to experiment with it.  Debian Lenny works better for me on a PPC, so I use it there.  The branding stuff I don't care about one way or another.  I don't need the newest version of every OS either, and Lenny is new enough for me.  I have one vm of Ubuntu 8.10 going, but I would be reluctant to put it on my one PC - a netbook running Ubuntu 8.04.1 with Netbook Remix.  The latter just works and the remix setup is perfect for a small screen laptop.

With Black Friday and Boxing Day sales around the corner, I'm thinking seriously of replacing my PowerBook G4 with a MacBook or MacBook Pro.  That would solve some Linux PPC problems, but then I couldn't run MOL (which I can even use to run OS9 software that no longer works on an Intel Mac).  Decisions, decisions.

---

### Post by stream303 on 2008-11-26
The funny thing is that with PPC, we are already very close to FSF guidelines by default. No flash, no 3D, no proprietary partner repositories since nobody compiles for ppc, and possibly no blobs used in the kernel even if they are there.  (I haven't confirmed that one yet..)  And openfirmware is a lot better than the typical proprietary bios of x86 machines.

What is left are branding issues, and one can avoid that if other browsers such as Epiphany-browser and others like Iceweasel, or gnu's IceCat will do the job.

I think the ultimate freedom is that once you know the difference between free and open source, just choose what makes you comfortable, and where do you draw the line?  PPC users should feel very comfortable with gNewSense on their X86 boxes.  I did, but chose Debian later because I can follow fsf guidelines on my own, and build libre-kernels if I want. (thanks Oswaldkelso!)

I like to think of it this way - every time you purchase new hardware, be it from Apple or anywhere else, as soon as you have laid your money on the counter, you are supporting a closed-source corporation - even if the first thing you do is run over to an ac outlet and install Linux before leaving the store.  The deed has already been done.  So until there is FSF hardware that it entirely free-as-in-freedom, one must temper their ideals with that thought when making a purchase in the first place. :)

I guess we're getting off track, but despite it all, I just say follow your own path.

---

### Post by mkvnmtr on 2008-11-26
In reading the posts of the other ppc users It looks like my problems are smaller than yours. I have  G4 Ibook that just won't break so I have to keep using it. My 8.04 installed ok but 8.10 looks like a lost cause. That is why I have become so interested in this thread. Looks like I need a distro for another 5 years or so. My 8.04 does every thing I need it to and I am not interested in glitz but I like to have at least two systems. I am always doing something to mess one up and have to go to the other to get help. I have cut down my mac partition and reinstalled 8.04 in a larger partition. I have the old 8.04 on a 15 g partition and in the next week I think I better install debian. I hope you folks will help me triple boot. I still haven't found a method that works to reconfigure yaboot. I will search for a couple of more days and then post a thread after I install.

---

### Post by mfox on 2008-11-26
mkvnmtr, triple boot is a snap with Grub.  I started with OS X.  Then every time I installed a distro, the Grub menu automatically put all the relevant ones on it, as long as Ubuntu or Debian was the last one installed.  Even when I wiped out one and installed the other, Grub picked it up without any work on my part.  So if you're installing Ubuntu and Debian for your triple boot, it doesn't matter which one goes first.

In my case, I have OS X, openSUSE and Debian with Debian the last one installed.  My grub menu first gives a choice between Linux and OS X.  It chooses Linux by default or by hitting the "L" key.  Then I get a second choice, the choice of Linux distros.  Default is the last installed (Debian).  If I hit a tab, it lists the choice.  To get openSUSE, I must type in "hda6-openSUSE", as that's the way Debian installed it on Grub.  I can change the menu if I want but I think Debian (or Ubuntu before I removed it) makes a pretty rational choice on the Grub menu structure.

---

### Post by ubuntubrian on 2008-11-26
I am pretty sure that PPC cannot use Grub but uses Yaboot, which is not too easy to set up. I've screwed up my booting plenty editing yaboot.conf file.

---

### Post by mkvnmtr on 2008-11-26
Yes ppc uses yaboot. In my searching it looks like indeed it will be a chalange.

---

### Post by stream303 on 2008-11-27
For complicated yaboot setups, you may want to look into the *yabootconfig* utility.  Man yabootconfig for more details.

Previously, yabootconfig only worked on G4's and lower, but with the new yaboot perhaps it will also work with G5's?  I haven't tested this utility so I can't say.

---

### Post by Leslie Viljoen on 2008-11-27
> **stream303 said:**
> The funny thing is that with PPC, we are already very close to FSF guidelines by default. No flash, no 3D, no proprietary partner repositories since nobody compiles for ppc, and possibly no blobs used in the kernel even if they are there.  (I haven't confirmed that one yet..)  And openfirmware is a lot better than the typical proprietary bios of x86 machines.

Interesting point: so I ran VRMS on my Mac Mini (running Lenny) and I saw that only the mol-drivers and GCC documentation are non-free.

Oh the irony: Virtual Richard Stallman regards real Richard Stallman's documentation license as non-free! It just makes me want to uninstall those docs in disgust!

---

### Post by oswaldkelso on 2008-11-27
> Perhaps the codec installer and the proprietary device installer should have a big clear button which you can press on with the title "WHY NON-FREE IS SO BAD". This can then open this awesome site:
[http://www.getgnulinux.org](http://www.getgnulinux.org)

The goal of Ubuntu is to beat Windows on the desktop, it has to make some "pragmatism not idealism" choices to do that. I think. But it seems more successful at this than other distros, so although it's an Open Source rather than a Free Software approach, perhaps once a critical mass is reached it can be leveraged to educate people.

Richard Stallman talks about this here:
[http://www.fsfeurope.org/documents/r...ork-on-stage-2](http://www.fsfeurope.org/documents/r...ork-on-stage-2)

I don't know if he's right or not. But almost everyone I have spoken to about this is uninterested in philosophy, happy to be spied on and pirate anything they want. They even don't care about viruses since they just reinstall. So when I recommend Linux they ask if it's better than Windows, and by 'better' they mean: can run *everything* Windows can, use *all* devices Windows can and then also has some other benefit, like not having to run cracks to "activate". They certainly don't notice they are slaves, even when I point out that they don't really know what their programs are doing and that their data is in formats that only one program/service can decode.

I think we need both: philosophers who appreciate freedom and ignoramuses who don't, but once they have experienced enough of it they might feel pain when it is taken away, wake up and become philosophers. Without the compromise we get no support from most people, and no support from most hardware manufacturers. So I work on phase 1 and phase 2 at the same time.

Thanks, I have those links very good too. I guess I feel that the pursuit of bums on seats, any bums, is a bad idea. That why IMO bug No1 is harmful to Gnu/Linux. Uneducated bums, bringing old windows habits. I feel getting across the reasons why things don't work and why flash and skype etc do nothing for the community are important before you try and get people to switch, other wise they become the enemy within. You just replace M$ with Ubuntu remix [put your trendy name here]. So long as you can get open standards the number of B.O.S is irrelevant.

> 
 Hehe! Since you can stay on Testing, it doesn't really get old, and you can put your servers on a stable version. My problem is that I want even my servers on the very latest because very often I am using very new technology. Like I make a Rails app and I need sqlite3. So I'd always stay on Lenny or upgrade Ubuntu every 6 months. 

Here's a guide on apt-pining I think this is what you require.
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)


Ref: [http://en.wikipedia.org/wiki/Mono_(software](http://en.wikipedia.org/wiki/Mono_(software))
> On November 2, 2006, Microsoft and Novell announced a joint agreement whereby Microsoft agreed to not sue Novell’s customers for patent infringement.[7] According to Mono project leader Miguel de Icaza,[8] this agreement extends to Mono but only for Novell developers and customers. It was criticized by some members of the free software community because it violates the principles of giving equal rights to all users of a particular program (see Novell and their Patent Agreement with Microsoft).

This is the reason I dislike mono, it is free but divisive. 
#to see how much mono is on your system
dpkg -l | grep mono

> We are not squatters! We still get support here. No-one's telling us to go.

> I don't really think this forum is too bad though, you just need to use the PPC tags. And lots of people come here.

True, but they did not listen when we all complained about ppc being merged with intel-mac. Neither group wanted to be joined at the hip. A merger with the aim of irradiating ppc if I were to trust my instincts. Whether that is true we may never no. But it certainly felt like it. That said this still is the most popular place for ppc discussion. Simply because of the popularity of Ubuntu. 


I've just reread  and I sound more negative than I wanted to, water under the bridge and all that, but I'm tired and can't be bothered to tone it down. Sorry.

mkvnmtr

You missed the yaboot link. Just search "yaboot" here and you'll find the archives 

> My experiences multi booting

[http://www.my2bits.org/?p=49](http://www.my2bits.org/?p=49)

---

### Post by stream303 on 2008-11-27
> **oswaldkelso said:**
> True, but they did not listen when we all complained about ppc being merged with intel-mac. Neither group wanted to be joined at the hip.

To my knowledge, no community member was ever asked, nor any polls taken before making this move - something I consider very UN-ubuntu.

When I first started out with Warty, I was excited mainly by the fresh new outlook on community-building, in addition to the release itself.  No other place really accepted very low-level handholding, and even dissent as long as it was constructive or non-personal.

The fact that this thread here hasn't been banned shows that some of the original spirit still lives on.

Lately however, I am confused by the joined-forum without any sort of community input - since it seems obvious that it is not building a community of Apple users, but is helping to break it down on both sides.

When I first started with Ubuntu, almost everyone I knew was interested in what it meant, and wanted to know more than just the "humanity towards others" keyphrase.  They looked it up, read it, and applied much of it to other aspects of their lives as well.

Today, I'm not sure that any newcomer is really interested in what it means, as Ubuntu to me has just become a brand-name -- just another Linux distro you download and install.  At least that's how the combined forum issue makes me feel anyway.

Hopefully it won't for others.  It is still a most valuable forum filled with a great community on both sides.  I just wish that somebody would reconsider without having to feel like they are "losing face", or that "we won" if it were to be separated again.

THAT would restore my faith in the real meaning of what Ubuntu actually means - building communities along with a distro release.

---

### Post by oswaldkelso on 2008-11-27
After my above post I went to down load lottalinuxlinks podcast as per usual.

Dave Yates had a link to the very same issue discussed in my previous post. Made me smile, but also realise I'm not the only one with these concerns.   

[http://lottalinuxlinks.com/podcast/ogg.html](http://lottalinuxlinks.com/podcast/ogg.html)

 
[http://www.linuxplanet.com/linuxplanet/opinions/6596/1/](http://www.linuxplanet.com/linuxplanet/opinions/6596/1/)

Free as in Freedom, Not Free as in Freeloader
Ask Not What Linux Can Do For You-- Ask What You Can Do For Linux

Good article IMO Carla Schroder lays it out much better than I could. Enjoy.

---

### Post by mfox on 2008-11-27
> **mkvnmtr said:**
> Yes ppc uses yaboot. In my searching it looks like indeed it will be a chalange.
I stand corrected, the PPC uses yaboot, not grub.  But that doesn't change anything else about my experience.  Getting a triple boot going with either Ubuntu or Debian as the last distro installed was a no-brainer.  The installer did all of the work.  All I had to do was confirm that I was happy with it near the end of the installation. 

I don't think this is true with all distros.  As I recall, when I tried Yellow Dog and it was the last one installed, the other distro on there at the time (Ubuntu 7.10 or 8.04) wasn't on the bootup menu.

---

### Post by mkvnmtr on 2008-11-27
With the help of a link or two posted above I think I have it figured out. I am going fishing for a few days so the first of next week I will give it a try. I will post a thread but it looks like it will be a success.

---

### Post by tiresia on 2008-11-27
> **mkvnmtr said:**
>  I still haven't found a method that works to reconfigure yaboot. I will search for a couple of more days and then post a thread after I install.

I posted a short yaboot-how-to here:
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)
It is just a compendium of the important files to boot a LinuxOS

---

### Post by tealio on 2008-11-27
> **mfox said:**
> Yep, the 'ol b43 fwcutter package, for Lenny.  I can't remember what steps I tried in Etch, but it took something earlier than b43.  I never got it to work properly in Etch.

mfox... ok i had trouble compiling the b43fwcutter... i think i may be missing some major libs for c... got errors for stdio.h (or o maybe) ... anyhow... i can probably figure out what libs i'm missing and get em i hope, but what's the line in */etc/apt/sources.list* to add the repositories? i tried adding the same lines i had in ubuntu, and either i got em wrong, or they didn't work... apt-get and aptitude gave me a ton of error messages saying basically that it couldn't find the correct filess... i'll clarify that if need be, but i'm not near the machine debian's on... 

so to sum up, i need to know what the */etc/apt/sources* line is, and also if you happen to know the libs necessary for compiling...

oh... and debian's kernel is pretty outdated... would it be worth upgrading the kernel to the latest? and what libs are necessary for that?  i tried compiling the newest stable kernel with *make defconfig* with similar errors to the ones i got trying to compile b43-fwcutter...

---

### Post by Leslie Viljoen on 2008-11-27
> **tealio said:**
> mfox... ok i had trouble compiling the b43fwcutter... i think i may be missing some major libs for c... got errors for stdio.h (or o maybe) ... anyhow... i can probably figure out what libs i'm missing and get em i hope, but what's the line in */etc/apt/sources.list* to add the repositories? i tried adding the same lines i had in ubuntu, and either i got em wrong, or they didn't work... apt-get and aptitude gave me a ton of error messages saying basically that it couldn't find the correct filess... i'll clarify that if need be, but i'm not near the machine debian's on... 

so to sum up, i need to know what the */etc/apt/sources* line is, and also if you happen to know the libs necessary for compiling...

oh... and debian's kernel is pretty outdated... would it be worth upgrading the kernel to the latest? and what libs are necessary for that?  i tried compiling the newest stable kernel with *make defconfig* with similar errors to the ones i got trying to compile b43-fwcutter...

If you want to do some compiling you almost always install build-essential.
You shouldn't need to change your sources.

Are you running Lenny? I try to avoid compiling kernels myself.

---

### Post by tealio on 2008-11-27
i'm running Etch 4.0r5... whatever the latest stable is... i'll try the build-essentials package if it's not already there... 

What is involved in upgrading to Lenny?  is the b43fwcutter package in Lenny and not Etch?  would it be easier to just build the cutter and stick with etch?  

I have never compiled a kernel which is why i'd like to try... are there any tremendous benefits to upgrading the kernel?  and significant risks?

---

### Post by mfox on 2008-11-27
tealio, when I tried to install the wireless firmware on Etch 4.0r3, I had all kinds of trouble.  The instructions I found called for a slightly different version of the fwcutter than b43; the name escapes me at the moment.  I tried several times.  At one point I had the firmware installed, but it worked very poorly and wouldn't connect at all to my home router.  So I dumped Etch on my PowerBook and tried Lenny instead.  b43 installed flawlessly and I never had connection trouble with it.  Subsequently, I dumped Lenny because Mac-on-Linux didn't work on it at the time, but a month or so later I put it back on when MOL was patched.  Again, installation of the firmware with b43 proceeded flawlessly and it works well.

If you have the option, I would recommend installing Lenny from scratch rather than upgrading.  I'm not sure how you would upgrade anyway, given that Lenny isn't "released" yet.  Also, while Debian isn't Ubuntu, there were a lot of postings on Ubuntu forums from individuals that had problems upgrading their 8.04 installations to 8.10 when it came out.

---

### Post by Leslie Viljoen on 2008-11-27
> **stream303 said:**
> The fact that this thread here hasn't been banned shows that some of the original spirit still lives on.

I have seen what I think is a little defensiveness here and there, but I always just drop the issue because people are working hard, in their spare time, on something they are passionate about. It's pretty similar to church. Those conditions will always produce real high-strung emotions, and they are not worth splitting up over. 

> Lately however, I am confused by the joined-forum without any sort of community input - since it seems obvious that it is not building a community of Apple users, but is helping to break it down on both sides.

I am understanding more now, since I never knew there was once a separate forum. Perhaps we Linux PPC people need a whole knowledge-base, repository, wiki AND forum, all PPC specific. Then we don't put architecture common stuff up there, just PPC specific stuff. I for one would really have appreciated knowing a whole lot of things I now know before I spent days downloading and installing. I read a lot before I tried to pick the best distro for my Mac and still chose wrong several times.

So I'm negotiating to see if I can afford a new website. Maybe I could start something for all of us? Would people appreciate that?

And would more than 20 people appreciate that? Since only about 20 have downloaded my fixed PPC Thunar/xfdesktop packages!

---

### Post by mkvnmtr on 2008-11-27
Leslie I for one would be grateful. And maybe for any distro someone cared to use on ppc. I am not unhappy with this forum but is only for Ubuntu.

---

### Post by stream303 on 2008-11-27
> **Leslie Viljoen said:**
> So I'm negotiating to see if I can afford a new website. Maybe I could start something for all of us? Would people appreciate that?

And would more than 20 people appreciate that? Since only about 20 have downloaded my fixed PPC Thunar/xfdesktop packages!

That would be wonderful!  A few of us have discussed this before, but like anything else, we want to be mindful of how much time one could actually devote to the project - in my case depending on life/work conditions, I can be active for a few months, drop out for a few, and then come back.

The immediacy and popularity of web-forums can't be understated.  I have often looked at

[http://www.phpbb.com/](http://www.phpbb.com/)

and wondered about bringing it to fruition.  But, I had to be honest about how much time I could devote to it - I didn't want to leave it hanging when other aspects of life came up.  Someone with more time may be able to pull it off - and not just financially as one could always solicit donations to help defray the cost of hosting.

An important thing to think about is always what happens "after the revolution".  Many projects fail because they can get initially started, but have no plan for dealing with its own success. :)

So would it be just a big general ppc-forum, or could it be even grander - like separate sections for other distros even?  While we all have things in common, we've seen that Ubuntu has more install-quirks than does Debian.  Obviously there is Gentoo with its own special needs along with PPC versions of Fedora, OpenSuse, and yep -even all the BSD's!  Would you clump that all together, or provide distro-specific forums?

One thing that can be taken with us is the original spirit of Ubuntu - as I've said in the past is that you don't have to run or even like Ubuntu to agree with its principles and apply it to your own projects.

Some might see concentrating on PPC foolish, but if you apply the sense of community-building along with it, that never goes out of style. :)

---

### Post by Leslie Viljoen on 2008-11-27
> **stream303 said:**
> That would be wonderful!  A few of us have discussed this before, but like anything else, we want to be mindful of how much time one could actually devote to the project - in my case depending on life/work conditions, I can be active for a few months, drop out for a few, and then come back.

I surely have the least time of all. I jump in here and there and everywhere when I get a gap, and have two "private" programming projects I must finish before the end of December.

> and wondered about bringing it to fruition.  But, I had to be honest about how much time I could devote to it - I didn't want to leave it hanging when other aspects of life came up.  Someone with more time may be able to pull it off - and not just financially as one could always solicit donations to help defray the cost of hosting.

I guess you could try to get donations. I was thinking perhaps getting a virtual server and running three low-usage websites off the same instance. Since I really don't think a PPC information site would generate a lot of traffic unless I host rebuilt ISO's or something.

> An important thing to think about is always what happens "after the revolution".  Many projects fail because they can get initially started, but have no plan for dealing with its own success. :)

So would it be just a big general ppc-forum, or could it be even grander - like separate sections for other distros even?  While we all have things in common, we've seen that Ubuntu has more install-quirks than does Debian.  Obviously there is Gentoo with its own special needs along with PPC versions of Fedora, OpenSuse, and yep -even all the BSD's!  Would you clump that all together, or provide distro-specific forums?

Before we jump off the cliff, I have in mind something that I would hardly have to maintain: a wiki mostly, for everyone to put up whatever useful info they discover. So you wouldn't have to search all around for PPC/Linux, you'd have one place for it all. But it would be run by public interest or not at all. I wouldn't mind if no-one used it, that would just mean it's not needed and I'd eventually take it down. 

We could try to get the wiki to have a well sorted framework before information starts getting added so that there are general places for general info and specific places for specific info.

My first thought was just to install a Redmine instance. Redmine is a development project tracker like Trac, but in Rails. It has a simple Wiki, a Forum, News and other bits baked in. Like this:
[http://www.redmine.org/projects/show/redmine](http://www.redmine.org/projects/show/redmine)

Sections that don't fit can be disabled and then enabled if we find a use for them. I don't have time for graphic design right now - maybe over time in the new year. But I don't think we need much more than consolidated information.

---

### Post by stream303 on 2008-11-28
Check this out:

[http://www.123macmini.com/forums/](http://www.123macmini.com/forums/)

Seems like these guys have some nice community going with some ppc-specific threads and have some interesting things to say about all the major ppc players.

I guess it shows that you can specialize, in their case just a particular model series, and survive! :)

---

### Post by Leslie Viljoen on 2008-11-28
Ok, I'll see if I can get a prototype up on the weekend that we can all mess around with.

---

### Post by mfox on 2008-11-28
> **stream303 said:**
> Check this out:

[http://www.123macmini.com/forums/](http://www.123macmini.com/forums/)

Seems like these guys have some nice community going with some ppc-specific threads and have some interesting things to say about all the major ppc players.

I guess it shows that you can specialize, in their case just a particular model series, and survive! :)
I'm a regular on 123macmini and yes, this community has really thrived.  The site opeerators are very amenable to change as new community interests have arisen, a recent example being the netbooks (small form factors or SFF forum). There's even a small, but active Linux group in the community.  We post Linux-related items under the Boot Camp forum.  I'm sure if we asked for a separate forum, we would get one but the way it is working now is just fine.

Where the example breaks down is that there is no separate forum in 123macmini for PPC mini owners.  The reason for that is that there aren't many topics that are exclusive to PPC or Intel minis.  (Exception: items that fall into the Boot Camp forum, which are exclusively Intel mini - PPC mini users probably don't check that forum.)

I do agree that PPC owners running different Linux distros have more topics of mutual interest with each other than individuals running the same distro on a PPC do with those running Intel/AMD  computers.  If there was a PPC Linux forum site, I would check it regularly.  Even if there isn't the energy to run one, a PPC Linux wiki with howtos and tips and tricks would be very useful.

---

### Post by Leslie Viljoen on 2008-11-28
Ok, so Redmine-wise we could start with News, Wiki and Forum sections.

For the wiki, I am open to suggestions on how to organise things. Perhaps we could start by just throwing information in there and then after we have some articles we can start making index pages that point to them, sorting them into different sections. It's pretty easy to make links in a wiki.

Who wants to help with initial content or play with the site's options? Email me off-list and I'll give you admin access when I get things rolling.

You can email me at Google's online mail service, using address "leslieviljoen".

---

### Post by stream303 on 2008-11-28
Sounds good to do a little brainstorming.  Who knows, maybe it will also help here.

I only have two problems with faqs and wikis:

Faqs - unless they are *locked*, they turn into another general purpose thread and make it hard to get the info you need by having to wade through 60 other issues.  Also, the author needs to prevent it from becoming stale as solutions evolve as releases change.

Wikis - another great resource - The same thing applies, as I see that even though well-intentioned, some solutions are presented as being global, when they are very model-specific or visca-versca.  Sometimes the author doesn't realize this, and you may have a G3 owner frustrated by a supposedly global solution that doesn't work for her.  Obviously you don't want to lock a wiki, but there could be control issues to deal with.

Don't worry - I'm still in the dark ages when it comes to editing wikis. :)  I can handle doing my own web-pages by hand, I just haven't taken the time to get into wiki authorship.  Hmmmm....

---

### Post by Leslie Viljoen on 2008-11-28
> **stream303 said:**
> Sounds good to do a little brainstorming.  Who knows, maybe it will also help here.

I only have two problems with faqs and wikis:

Faqs - unless they are *locked*, they turn into another general purpose thread and make it hard to get the info you need by having to wade through 60 other issues.  Also, the author needs to prevent it from becoming stale as solutions evolve as releases change.

Wikis - another great resource - The same thing applies, as I see that even though well-intentioned, some solutions are presented as being global, when they are very model-specific or visca-versca.  Sometimes the author doesn't realize this, and you may have a G3 owner frustrated by a supposedly global solution that doesn't work for her.  Obviously you don't want to lock a wiki, but there could be control issues to deal with.

Don't worry - I'm still in the dark ages when it comes to editing wikis. :)  I can handle doing my own web-pages by hand, I just haven't taken the time to get into wiki authorship.  Hmmmm....

Well OK, lets try to deal with those problems when we come to them. The first problem would be getting enough information and participation for people to actually use the site. Then we have to rely on people pointing out "hey, this solution is G4 specific, it doesn't work on mine" because I'm sure few people have a wide range of PPC machines.

I am going to try and admin the site in the few free minutes I have, and keep it from getting chaotic. So people are going to have to accept me chopping and changing what they put up as I see fit. But if anyone has opinions about the site, I promise to listen to everyone's suggestions without feeling slighted at all.

Can you access the site yet?

---

### Post by Leslie Viljoen on 2008-11-28
I have redirected [http://www.lesismore.co.za](http://www.lesismore.co.za) to the new site so people can sign up and give it a try.

I haven't configured emailing yet so I have to approve anyone who logs on, but please sign up and I'll approve you. If the site doesn't work, please let me know because I can't test it fully from inside the network here.

---

### Post by Leslie Viljoen on 2008-11-28
Ok, I tested and it's working from outside my network. So sign up guys! Start sharing all this wonderful PPC specific knowledge that everyone is dying to hear!

I have put in what I have learned about Debian so far, I'll add some stuff about Intrepid soon. BTW: I think I'm going to try and register maclin.org.za or maclin.co.za eventually for the site. Does the name sound ok to you guys?

---

### Post by tiresia on 2008-11-28
> **Leslie Viljoen said:**
> I think I'm going to try and register maclin.org.za or maclin.co.za eventually for the site. Does the name sound ok to you guys?

Well, maybe, the name should more connect **linux** and **powerpc** - not 'mac' 
Anyway, thanks a lot for your efforts - I registered already :)

---

### Post by boydrice on 2008-11-28
I agree with tiresia. The name of the site should really link powerpc and linux.  A mac linux name would draw people with intel macs looking for info.  Just my two cents.

Boyd

---

### Post by Leslie Viljoen on 2008-11-28
> **tiresia said:**
> Well, maybe, the name should more connect **linux** and **powerpc** - not 'mac' 
Anyway, thanks a lot for your efforts - I registered already :)

I see you are making changes: goooood!

About Maclin: you are right.

I was thinking 'maclin' because it sounds cool - I couldn't come up with any PowerPC contraction that sounded as nice. PPCLIN? Powerlin? PowerLine?
I'm a bit wary of horrible sounding names, they seem to be Linux's speciality. Linpus anyone? GNewSense?

---

### Post by oswaldkelso on 2008-11-28
I will buy ppclinux.co.uk for "the community" now  before I go to work. Ya or nay people

---

### Post by Leslie Viljoen on 2008-11-28
> **oswaldkelso said:**
> I will buy ppclinux.co.uk for "the community" now  before I go to work. Ya or nay people

I vote "ya", if this is a democracy. But I still think "maclin" sounds cooler. Over to you guys.

---

### Post by mfox on 2008-11-28
ppclinux may not be cool, but I think it will bring the right audience to it.  I seem to recall that there once was a ppclinux site, but it was not very active.

---

### Post by pxwpxw on 2008-11-28
I registerd. the wiki is a good start, I like it already.
I think take your time about the name - ppclinux or maclin not so good if you google,
and we need our friend google.
ppclinuxwiki  or ppclinuxusers works but sounds terrible.

---

### Post by Leslie Viljoen on 2008-11-29
Great, lets have more ideas, and if we can, move the discussion here:
[http://www.lesismore.co.za/projects/maclin/boards/show/11](http://www.lesismore.co.za/projects/maclin/boards/show/11)

So far I think Oswald's name is the most relevant.

On the site I have activated these users so far: 
mfox, pxwpxw, stream303, tiresia

Thanks for contributing!

---

### Post by tealio on 2008-11-29
okok... the build-essentials package did the trick... i actually looked at that package before, but the description made it seem more geared toward building .deb packages... anyhow it did the trick... 

i've got the firmware installed, according to the b43legacy instructions, and i tried setting up */etc/network/interfaces* similarly to my ethernet adapter, but no joy... i didn't figure it would work, but sometimes i get lucky.

according to the main b43 website, the b43legacy driver is what i needed... there is another driver in the kernel though... i get messages about it when i boot up, and it ends with a message telling me that the radio is turned off or somehting of that nature...

so what are the next steps after installing the firmware?  

i'm still interested in upgrading the kernel, because as i understand there is a more recent driver built into the newer kernels... that true? is b43legacy just as good?  

my newest trouble with the kernel build is trying to build with *make defconfig*.  I am promptly told there is no file *arch/config/ppc_defconfig* (or something very similar).  if i need to give specifics, let me know.  there are several different files in the dir that the error message points to, apparently different types of ppc chips?  i'm just not sure what category a G4 falls under... and if i was i don't know how to point to a specific 'defconfig' file....

so basically i have the same problems i had, minus the compiling issue... that was just plain bone-headed on my part... 

what steps do i take after installing the firmware? would i benefit from better drivers with a newer kernel? i've heard that older drivers (and maybe the newest ones) will only connect at 802.11b speeds... that's ok for my laptop, but i've also been told that one 'b' device slows the entire network, and there are 5 computers in the house... and if i would benefit, how can i determine the correct defconfig file and point make to it?

---

### Post by oswaldkelso on 2008-11-29
ppclinux.co.uk and ppclinux.info are ours :)

---

### Post by Leslie Viljoen on 2008-11-29
> **oswaldkelso said:**
> ppclinux.co.uk and ppclinux.info are ours :)

:) 

Ok, email me directly or sign up at the site!

---

### Post by tiresia on 2008-11-29
ppclinux.info - I like it
thanks!

---

### Post by mfox on 2008-11-29
I've registered and added my PowerBook to the new list of PowerPC machines and what distro they're running.  Don't forget to add yours to the list.

---

### Post by tealio on 2008-11-30
> **tealio said:**
> okok... the build-essentials package did the trick... i actually looked at that package before, but the description made it seem more geared toward building .deb packages... anyhow it did the trick... 

i've got the firmware installed, according to the b43legacy instructions, and i tried setting up */etc/network/interfaces* similarly to my ethernet adapter, but no joy... i didn't figure it would work, but sometimes i get lucky.

according to the main b43 website, the b43legacy driver is what i needed... there is another driver in the kernel though... i get messages about it when i boot up, and it ends with a message telling me that the radio is turned off or somehting of that nature...

so what are the next steps after installing the firmware?  

i'm still interested in upgrading the kernel, because as i understand there is a more recent driver built into the newer kernels... that true? is b43legacy just as good?  

my newest trouble with the kernel build is trying to build with *make defconfig*.  I am promptly told there is no file *arch/config/ppc_defconfig* (or something very similar).  if i need to give specifics, let me know.  there are several different files in the dir that the error message points to, apparently different types of ppc chips?  i'm just not sure what category a G4 falls under... and if i was i don't know how to point to a specific 'defconfig' file....

so basically i have the same problems i had, minus the compiling issue... that was just plain bone-headed on my part... 

what steps do i take after installing the firmware? would i benefit from better drivers with a newer kernel? i've heard that older drivers (and maybe the newest ones) will only connect at 802.11b speeds... that's ok for my laptop, but i've also been told that one 'b' device slows the entire network, and there are 5 computers in the house... and if i would benefit, how can i determine the correct defconfig file and point make to it?

...

---

### Post by Leslie Viljoen on 2008-12-03
> **tealio said:**
> ...

I don't think AirForce One wireless will work in Etch no matter what you do. Take a look at our "known issue matrix" at [www.ppclinux.info:](www.ppclinux.info:) 

[http://www.ppclinux.info/wiki/maclin/Known_Issue_Matrix](http://www.ppclinux.info/wiki/maclin/Known_Issue_Matrix)

Perhaps by installing a new kernel you'll get it working, I just don't know, and I'm sure not many people have tried that.

Wireless worked straight off in Intrepid (it detects the card and does the firmware programming for you, no intervention required), and you can get it going with the manual process in Lenny, but I haven't seen it in Etch, and if it's the same problem that Gutsy had you may be trying for the next six months (I did). 

Once the driver is working, nm-applet normally connects as soon as it gets the right WEP key. If you have no wireless icon on your panel, you'll need to follow the directions to run nm-applet:

[http://www.ppclinux.info/wiki/1/Cross-distribution_issues](http://www.ppclinux.info/wiki/1/Cross-distribution_issues)

The symptom of the driver not working is that nm-applet won't be able to connect no matter what you try.

---

### Post by eraker on 2008-12-12
> **stream303 said:**
> Most definitely! 
Intrepid 8.10's show-stopper need for *modprobe ide-scsi* to get your cdrom recognized out of the gate is certainly Ubuntu-specific.  Unfortunately, we can't find these when ppc is beta or RC'ed so late in the release cycle.  And even if they are found, it is so late that nothing can be done about it.  Debian doesn't have this problem, so some bugs could be fixed if Canonical would release to us early like the rest - provided they actually put some resources into it after the report!  At this stage however, it seems that some bugs are mainly about not allowing for time on non-commercial architectural support to concentrate solely on those that are.  It's just a matter of resources and timing.

This kind of cdrom-detection bug out of the gate is showing up more and more during the past several RC releases even when they do become available!  Not only are the RC's late in the cycle for us, but it makes it even harder for us to test it when we can't get past step one, and spend much of our time hunting down some sort of workaround - and then again it's too late to do anything about it.  By then, many possible ppc users just go on to other things.  Sorry - got on a rant-tangent again. :)


Oh, so that's why installer couldn't find /dev/cdrom?? That seemed to me like a ridiculous problem and my immediate response was, "I'm going back to debian since ubuntu apparently doesn't want ppc users anymore." I was able to do apt-get upgrade/dist-upgrade (but it broke xfce4 (because apparently there is no xfwm anymore, only metacity?) so I switched to gnome for expedience). 

It also took me way too long to figure out why the repositories for ppc weren't working anymore. I guess the point is that I should read stuff like this more often.

I have to second the encouragement to move to debian. I've always been more comfortable with my iBook clamshell on debian because it never installs a whole lot of crap on the system that I will never use.

---

### Post by Leslie Viljoen on 2008-12-13
> **eraker said:**
> Oh, so that's why installer couldn't find /dev/cdrom?? That seemed to me like a ridiculous problem and my immediate response was, "I'm going back to debian since ubuntu apparently doesn't want ppc users anymore." I was able to do apt-get upgrade/dist-upgrade (but it broke xfce4 (because apparently there is no xfwm anymore, only metacity?) so I switched to gnome for expedience). 

It also took me way too long to figure out why the repositories for ppc weren't working anymore. I guess the point is that I should read stuff like this more often.

I have to second the encouragement to move to debian. I've always been more comfortable with my iBook clamshell on debian because it never installs a whole lot of crap on the system that I will never use.

This comes from the dropping of an architecture! Ubuntu said "community: TAKE OVER", but the problem is, how? Who do we talk to? How do we get ISO releases delayed until the betas have been adequately tested? We need a howto that will list all the gaps that need to be filled and how to fill them. 

In my opinion the current Intrepid ISO's for PPC should still be in beta, or at least should have been in beta until at least the XFCE packages were fixed and the modprobe ide-scsi problem was fixed. But then the XFCE packages are still not fixed, and I built working ones a few weeks back. I'm just not sure how to do more than I have already done.

Ubuntu should either drop PPC entirely, or as a rule have delayed releases for unsupported architectures, making full use of the community to sort out issues before release. Perhaps if Ubuntu dropped PPC entirely, all the users and developers working on PPC would revert to Debian... but I'm not entirely sure of that. I have never experienced "tough love" from Debian but I get the feeling that the general perception of Debian is one in which "tough love" is all you'll get. So new people are afraid of Debian.

---

### Post by stream303 on 2008-12-13
> **Leslie Viljoen said:**
> I have never experienced "tough love" from Debian but I get the feeling that the general perception of Debian is one in which "tough love" is all you'll get. So new people are afraid of Debian.

Which is a shame, since the distro is actually very user friendly - it is one of the most ironic secrets out there. :)  Most of the tough-love is a total act, and once you get to know a few people, they will really help you out - as long as you've told them what you've already tried....

Any Ubuntu ppc'er who is reconfiguring xorg.conf, yaboot.conf, using rescue-shells etc via the commandline is already PRE-QUALIFIED to use Debian! :)

---

### Post by Leslie Viljoen on 2008-12-13
Go here: [http://forums.debian.net/viewtopic.php?t=33609](http://forums.debian.net/viewtopic.php?t=33609)
Type ctrl-f, enter "stupid".

Now the guy had a legitimate, intelligent question. I think Ubuntu is friendlier because this is where a huge amount of first-timers come, and everyone is used to that and are very nice indeed. It's something everyone here can be really proud of.

I'm sure every forum has it's good and bad, but I started reading Debian's forum today, and that post was in the second thread I tried. I love Debian and Ubuntu both, but that makes the whole of Debian look just a little different in my eyes.

---

### Post by stream303 on 2008-12-13
> **Leslie Viljoen said:**
> I'm sure every forum has it's good and bad, but I started reading Debian's forum today, and that post was in the second thread I tried. I love Debian and Ubuntu both, but that makes the whole of Debian look just a little different in my eyes.

Don't sweat it - like any human endeavour, we all have our good and bad days. :)

One always has alternatives if it bugs them.  Use other forums, books, magazines, etc, so the user-support issues shouldn't really reflect on the distro itself.  No forum, not even this one, is really the sole determination of character - that only comes from within.

In fact, if one wanted an Ubuntu-like friendly atmosphere for Debian, it's right here in the "Other OS" forums.  There are many others, not to mention the fact that one could just do as we did with a niche forum of our own.

I guess "interoperability" might be the keyword to focus on no matter what forum one finds themselves in.

Enough of my romanticism - I just hate to see users jumping ship over the opinions of the vocal minority.  Is it any wonder that devs don't have the time to even step foot inside forums for the most part? :)

---

### Post by cyberdork33 on 2008-12-13
> **Leslie Viljoen said:**
> Go here: [http://forums.debian.net/viewtopic.php?t=33609](http://forums.debian.net/viewtopic.php?t=33609)
Type ctrl-f, enter "stupid".

Now the guy had a legitimate, intelligent question. I think Ubuntu is friendlier because this is where a huge amount of first-timers come, and everyone is used to that and are very nice indeed. It's something everyone here can be really proud of.

I'm sure every forum has it's good and bad, but I started reading Debian's forum today, and that post was in the second thread I tried. I love Debian and Ubuntu both, but that makes the whole of Debian look just a little different in my eyes.

Yea, I think there is a bit more of the "read the f***ing manual" types there imo.

---

### Post by eraker on 2008-12-14
I always think of that RTFM-type stuff as more of an old-linux community way of thinking and responding. Ubuntu fora, in my opinion, have been the exception and not the rule.

With that said, I've had great responses from people reading fora and working in the debian community. I had someone walk me through all the debian steps for a custom kernel build. That kind of advanced knowledge and patience is very rare all around, however.

---

### Post by Leslie Viljoen on 2008-12-14
That's bad for Linux. Imagine if support staff at Apple or Microsoft said that to someone looking for help. They may say "you need to pay us before we speak to you" but at least they are not rude.

---

### Post by stream303 on 2008-12-15
I was having some discussions elsewhere about Ubuntu PPC, and I forgot why I do this in the first place.  When Ubuntu first started, I adopted the spirit of the name, even though today I don't run it as my primary ppc distro.

In the past, I had taken some heat about adopting the Ubuntu spirit, and was told so many times that it is nothing more than a self-righteous hypocritical marketing gimmick.

I think it was said so much that I too have forgotten that Ubuntu is more than just a distribution brand-name, and even started to believe it sub-consciously.

I guess all I can say regarding any forum, is that no matter what they say, or even what the leaders or others may do (or forget), nothing prevents *me* from expressing the Ubuntu spirit with other distro users.  I just forget it all too often.

---

### Post by cyberdork33 on 2008-12-15
> **stream303 said:**
> I guess all I can say regarding any forum, is that no matter what they say, or even what the leaders or others may do (or forget), nothing prevents *me* from expressing the Ubuntu spirit with other distro users.  I just forget it all too often.

:)

---

### Post by Leslie Viljoen on 2008-12-16
> **stream303 said:**
> 
I guess all I can say regarding any forum, is that no matter what they say, or even what the leaders or others may do (or forget), nothing prevents *me* from expressing the Ubuntu spirit with other distro users.  I just forget it all too often.

Awesome. You are very right.

---

