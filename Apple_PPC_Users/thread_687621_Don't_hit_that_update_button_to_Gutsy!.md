---
title: "Don't hit that update button to Gutsy!"
date: 2008-02-04
forum: Apple PPC Users
---

### Post by VCF on 2008-02-04
I'm totally new to Linux but I've been able to get Feisty running on my totally standard iMac G3/500 (1gb memory, no wi-fi, just internal CDRW and 128gb HD).  After the Feisty install and full update (which I did the usual X11 config fix and works just fine after that), I tried to upgrade to Gutsy.  My odyssey is as follows:

1: busybox bust, fixed with the usual fix including doing the sudo update thingy which then gets me to:

2: login screen (with the drum sound)  all fine here but then this happens.

3: a very very long wait while some of the gnome screen comes up which includes the borders for some error message (which doesn't display any text) and much disk activity which never seems to stop.

4: I've waited several hours to see if anything else happens but no luck.  I can drop into a command box cntrl+option+F1 so I'm ready for some fun console commands!

Is there some way I can show a log of start-up activity so I can watch and save what is happening during boot-up (other linuxes I've used have many screens of start-up messages, very fun to watch!).

I've checked all the posts and can see no problem exactly like this, should I just give up and use Feisty or is there some magic bullet I can use?

thanx!

---

### Post by Cannaregio on 2008-02-04
If you can use a terminal then have a look at the error messages:

```
dmesg
```
or
```
dmesg | less
```
or 
```
dmesg | grep "problem"
```

using whatever problem you think you have as filter, for instance
```
dmesg | grep BIOS
```

Could be a module or a graphic problem, in your case.

---

### Post by stream303 on 2008-02-04
> **VCF said:**
> 2: login screen (with the drum sound)  all fine here but then this happens.

3: a very very long wait while some of the gnome screen comes up which includes the borders for some error message (which doesn't display any text) and much disk activity which never seems to stop.

4: I've waited several hours to see if anything else happens but no luck.  I can drop into a command box cntrl+option+F1 so I'm ready for some fun console commands!

Any chance that this is a date-bug?  I had the same symptoms on my G4 iBook.  Unfortunately I didn't even have a virtual terminal so I had to type in the blind.  Nah, this bug couldn't apply to my modern ibook with good battery!  See this:

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

bingo.  At least for me.  Luckily you've got the luxury of a terminal!

---

### Post by VCF on 2008-02-04
Thanks all for the help so far!
I didn't notice that the clock had reset from previous Feisty to Gutsy installs, ie. the clock would be right when it got back to a running Feisty.  

However, I will try both the date and dmesg commands when I get back to my iMac tonight and report back with the results.

---

### Post by VCF on 2008-02-05
Tried out the date bug thing last night, it wasn't that as the date command came back just fine.  Ah well, too bad it wasn't so easy as that!

As for the dmesg | more command, the log gave back many many messages, none seeming very ominious except for (I quote anything that looked graphics oriented here, I'm writing from what I wrote down so all the spaces and text may not be exactly as I saw it)

aty128fb: Invalid ROM signature 8181 should be 0x aa55
aty128fb: BIOS not located, guessing timings
aty128fb: Rage128 TR Ultra AGP [chiprev 0x4] 16M 128bit SDR SGRAM (1:1)

fb0: ATY Rage128 frame buffer device on Rage128 TR Ultra AGP

agpgart: Detected Apple Unitnorth/Pangea chipset
agpgart: configuring for size idx: 8
agpgart: AGP aperture is 32M @ 0x0
agpgart: Couldn't find an AGP VGA controller
agpgart: Putting AGP V2 device at 0000:00:0b.0 into 0x mode
agpgart: Putting AGP V2 device at 0000:00:10.0 into 0x mode

I RE-INSERTED IN THE HD THAT HAD FEISTY ON IT AND LOOKED AT THE LOG AND IT HAD THESE SAME MESSAGES AS GUTSY!  The Feisty log did go a lot farther into such things as bluetooth and the like.  

BTW the Gutsy log seemed very happy with the ethernet controller chip and many other things.

STUMPED AGAIN!  Any thoughts?

Thanks!

---

### Post by stream303 on 2008-02-05
At this stage I'd be tempted to just do a full reinstall with the ALternate cd of Gutsy burnt at a very low speed on good media.  Call me chicken. :)

If you've got a copy of your working Feisty /etc/X11/xorg.conf, I'd keep that handy. :)

Sorry, guess I'm getting lazy today..

---

### Post by VCF on 2008-02-06
Yup, I tried the alternate install a couple of times with about the same results as the upgrade.  I'm going to go back to the logs for both versions and see where Gutsy stopped and Feisty continued on (I'm hoping that they keep loading stuff until something breaks like in Windows).
  
However, I'm rapidly coming to the conclusion that Gutsy is fundamentally broken on certain models and that with no proper beta testing except for poor suckers like me, you just go to the last working version and wait until a new version sorts it out but make darn sure you have one hard drive to play on while keeping the production drive out of sight of bad updates.  That's why I'm keeping the case apart indefinitely.

Is there anybody else out there using an iMac G3/500 with Gutsy?  It's not that it'is a rare model.

---

### Post by Yochanan on 2008-02-08
I've got Gutsy PPC Alternative on mine, maybe I should start over with Feisty. See my thread [here](http://ubuntuforums.org/showthread.php?p=4265800)

---

### Post by VCF on 2008-02-08
Yup, I've been watching your thread and picked up some good ideas...

 I had even made sure the ESD was checked off in Feisty before I hit the upgrade button.  I'm assuming that the upgrades don't mess around with config files so I presume the ESD bug was a red herring for my situation.

I've even experimented with the Hardy Heron alternate install and things are even worse, it doesn't even detect the ide controller for the HD which I think is a problem for Gutsy as well.  The whole modprobe ide-core thing doesn't work either.  I need to find out what controller my iMac uses as Hardy presents a whole long list of them to get to the next stage.

---

### Post by VCF on 2008-02-15
Ok!
I think I do have the esd problem because I finally could see the GNOME setting daemon error after  NetworkManager.  Now the Gnome screen is just really slow but I still can't bring up menus.  Yes I checked all the drivers as per the FAQ.

Now here is the rub:

1. I type killall esd in terminal and it says no process to kill
2. When I get back to GNOME i can't bring up the settings menu because I the screen is way too slow.

Is there a way to change that setting in terminal in some sort of config file?

---

### Post by stream303 on 2008-02-16
I'd go into a virtual terminal, CTRL-ALT-F1, and run TOP to see if there is a process hogging the cpu.  Network Manager was a big proglem on one of my iBooks.  If so, there is a workaround...

---

### Post by VCF on 2008-02-16
> **stream303 said:**
> I'd go into a virtual terminal, CTRL-ALT-F1, and run TOP to see if there is a process hogging the cpu.  Network Manager was a big proglem on one of my iBooks.  If so, there is a workaround...


Yup, did exactly that!  Disable network manager as per the bug report.  Now top doesn't show any cycle hogging processes at all.

Now I need to edit the gnome config in command mode to stop esd from running (which is the other bug in Gutsy that brings up the panel message) as per my previous message

---

### Post by stream303 on 2008-02-16
Now that the gui is working at a normal speed, can you go into your sound prefs, and just uncheck esd?  That should esd from restarting - I think.

---

### Post by stream303 on 2008-02-16
Aha - looks like we can nail esd in a terminal right at the start by editing /etc/esound/esd.conf

I'm not a sound guy, :) so I'll have to dig through the docs to see...

Got the hint from here:

[http://ubuntuforums.org/showthread.php?t=160871](http://ubuntuforums.org/showthread.php?t=160871)

---

### Post by VCF on 2008-02-17
Nothing seems to help, that's it I'm done.

---

### Post by VCF on 2008-02-17
> **VCF said:**
> Nothing seems to help, that's it I'm done.

I'm going to stick with 7.04 until Hardy gets fixed up enough that I can install it (no luck so far on that front)

Thanks for the suggestions y'all

---

### Post by ubuntubrian on 2008-02-19
I've followed and posted on several of these threads. I'm on a TiBook, massively upgraded hardware and am loathe to abandon my beloved laptop to a life of dust collecting! those Toshibas and Acers are looking pretty good at sub $600 prices though!
I have stuck with version 6.06 and added as much functionality as I can with FireFox 2.0, thunderbird, gnash, etc but I am not going to fight the Gutsy battle anymore. does anyone know if Hardy development will even attempt to address these myriad issues? Or will we just be typing "live-nosplash, blah, blah, modprobe yaddah, yaddah" forever?
If Hardy fixes these issues for my TiBook then I'll just copy my home directory and install Hardy but if not then I'll keep using Dapper and probably break down and get the toshiba or something.
Too bad Apple's MacBooks are so expensive!

---

### Post by VCF on 2008-02-19
> **ubuntubrian said:**
> I've followed and posted on several of these threads. I'm on a TiBook, massively upgraded hardware and am loathe to abandon my beloved laptop to a life of dust collecting! those Toshibas and Acers are looking pretty good at sub $600 prices though!
I have stuck with version 6.06 and added as much functionality as I can with FireFox 2.0, thunderbird, gnash, etc but I am not going to fight the Gutsy battle anymore. does anyone know if Hardy development will even attempt to address these myriad issues? Or will we just be typing "live-nosplash, blah, blah, modprobe yaddah, yaddah" forever?
If Hardy fixes these issues for my TiBook then I'll just copy my home directory and install Hardy but if not then I'll keep using Dapper and probably break down and get the toshiba or something.
Too bad Apple's MacBooks are so expensive!

Yup, since PPC isn't supported by Canonical any more, I think things will just get much worse for PPC in the future.  I needed to go to Feisty to get the most current support for QEMU and found things totally painless in upgrading from Dapper to Edgy to Feisty 
HOWEVER, I have my machine taken apart for easy swapping of disk drives (I have four going right now) to test out Gutsy and Hardy.  It's a lot harder to take laptop apart so do a full backup before upgrading (if you see fit) <grin>

---

### Post by stream303 on 2008-02-19
Hopefully installation issues will become easier, but remember that PPC support consists of making the latest Ubuntu available from developers, but the fine-tuning and basically end-user support for unseen issues rests largely upon us.

Since hardware specs/code from proprietary manufacturers doesn't seem to be forthcoming, the PPC devs and users just try to make the best of it.

What you "buy into" when you go Ubuntu PPC is a fantastic forum support community.  I've learned so much from others here over the years.

A new laptop is not guaranteed to be fault-free either - you may just face a different set of plus's and minus' :)  One thing won't change - great Ubuntu community support.

---

### Post by ubuntubrian on 2008-02-20
I will and heartily agree that the community support is fantastic and I have benefited from it immensely over the years since first installing Hoary on this same TiBook. I'm not complaining at all but I do worry that some upgrade will either just not work, like the sound issue, or I'll lose my customized Dapper OS, which has almost everything from flash and other video working to the huge amount of work I put into building Firefox (god that mozilla compiling is a bugger!) and other apps. I can backup completely,and I do, and I can even swap hd's which I have done but i still weigh the efforts of continuing with a probably dying breed, the ppc.
I know there are issues anyway and that has stopped me from going AMD or x86 so far.
I have been able to get Gutsy live cd to boot but have no sound so I'm reluctant to upgrade even to Feisty which had the same issue. the earlier versions just worked so easily, even when I screwed them up!
I love Ubuntu and i love the community and never say thanks enough so...
THANKS
:popcorn:

---

### Post by stream303 on 2008-02-21
> **ubuntubrian said:**
> I can backup completely,and I do, and I can even swap hd's which I have done but i still weigh the efforts of continuing with a probably dying breed, the ppc.

From the sound of it (pun intended), I'd say stick with what works until you find something that forces your hand.  Since manufacturers aren't releasing any specs on their ppc video / audio components especially, I don't know that you are missing much by going to a newer release, other than file/security upgrades.  At least Dapper will be updated until what, middle of next year for desktops?

If you are heavily into wi-fi, that might be a different story.

Is there something in the newer releases that is a must-have?  Be proud of your custom tiBook!

---

### Post by ubuntubrian on 2008-02-21
I am proud to be in such a small, somewhat esoteric set of company! Oh, I just want to have the latest and greatest is all. You know, desktop effects, and such. Pure hedonism. I can boot the live Fedora PPC cd and see the wobbles and all so it's just wobble envy! Ironic at my age!
I luv Ubuntu and have recently converted my brother from windoze-hurray!

---

### Post by stream303 on 2008-02-21
I can relate.  With my nvidia "nv" based iMac, desktop affects are not available, even in Hardy.  On my slower pc, I tried effects for awhile, but eventually turned them off since they just slow down the system.

You compiled Firefox yourself - can you run the latest Firefox side by side and see if you even need to do that anymore?

There might be some nice projects in here while we wait for Hardy to settle:

[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

---

### Post by ubuntubrian on 2008-02-21
I can run "Bon Echo" side by side with Firefox 1.5 but I never run 1.5at all. I installed 2.0 in /optsoit wouldn't conflict with all the stuff that requires 1.5 to run, like OpenOffice and more. So 1.5 works in the background and 2.0, Bon Echo, is my browser.
BTW, I downloaded Hardy alpha live cd and it boots right up. the only issue I see is the sound on my TiBook that goes back to Feisty I guess (tho the Feisty live cd works with sound for me).
Other threads have promising fixes for the sound problem and SSam has said he will make a deb of a kernel that allows sound. I'm going to wait for Hardy RC to see if the sound is fixed but I'm excited about it!:guitar:

---

### Post by VCF on 2008-02-21
Bwahahaha!

I just installed Debian Etch 4.0R3 (using the net install) and am writing this live on a very happy install on my Summer 2001 G3/500 Imac.  

The net install went smoothly (detected all the hardware!), downloaded all the stuff (used University of Waterloo computer club for the packages) , installed gnome (just checked off on the list of things to install along with the standard desktop) and rebooted to a blank screen after logged in.  I did the usual Imac G3 fix to xorg.conf of HorizSync 58-62 and comment out DRI, then sudo killall -HUP gdm and then  gnome comes up looking a lot like Gutsy should have.  Wow is the thing fast!

So long Gutsy, hello Etch!

I'll report if there are any other busts but things are looking pretty good so far.  I'll poke around and see if I can find any things that Etch did that Gutsy didn't.

I haven't tried sound or graphics or anything yet but I'M so happy just to be typing this :)

---

### Post by VCF on 2008-04-04
Just to give an update, Etch is running just fine on my Summer 2001 slot loading iMac G3/500 Indigo.  Everything just works without any tweaking.  It seems to be the equivalent of Gutsy as far as I can tell as far as sound, wired networking & graphics (no Beryl-Compiz-Fuzion, rage chipset too old:( )

However, I've been a busy boy and have installed Gutsy on a Powermac G4 'yikes' and a Powermac G4 AGP with no real problems at all.  I always use the alternate installer and don't fuss with dual booting (I've got lots of machines with OSx!).  Just one bump on the road, fix the modprobe ide-core start-up bug and on with the show!

So I'm back in the Ubuntu PPC fold.  It's good to be back! DAMN I love Linux!

---

### Post by ubuntubrian on 2008-04-04
I'm still fumbling about with Gutsy and am playing with hardy a bit. On my TiBook G4, 1Ghz, I have all the features EXCEPT sound though I hear that the newer kernel modules may fix that. On my G3 Powerbook, Lombard I have all the features including sound but it doesn't recognize my PCI wireless card.
Hmmmm

---

### Post by slacka-vt on 2008-04-04
see what happens when you try to reinstall the desktop.
make sure you got the Gutsy repos in your sources.list
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

