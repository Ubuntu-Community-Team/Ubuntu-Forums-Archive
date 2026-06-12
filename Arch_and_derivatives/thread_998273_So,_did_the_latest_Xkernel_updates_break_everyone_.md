---
title: "So, did the latest X/kernel updates break everyone else's system?"
date: 2008-11-30
forum: Arch and derivatives
---

### Post by SomeGuyDude on 2008-11-30
I'm furious right now, because after that X.org thing sat in testing for months and showed up in the extra repo, my system is totally wrecked. Amongst the problems:

1) You have to comment out a line in the xorg.conf file now because the variable is unused, which is confusing the hell out of a lot of people.

2) None of my OB config files work, and trying to edit anything via obconf or obmenu tells me it can't access my config files, but now it's looking for them in the root directory for some reason. So I have no wallpaper and my OB menu is that ugly default thing that has almost nothing I've installed. As a result, I have to use the terminal to launch EVERYTHING.

3) Synaptics no longer works. So my touchpad is all screwed up. Cool.

4) I don't have my Alt+F2 launcher either for some reason.

It's finals next week and I have a **** ton of work to do. This update was bad enough that I'm honestly tempted to scrap the system entirely. I like the ideals and I think Arch is far and away the best distro by design, but if these guys are gonna let things like this slip through, I'm out.

---

### Post by bfc on 2008-11-30
That's the main reason I've moved away from Arch...  I love a lot of things about Arch, but I really do not have the time or the desire anymore to deal with stuff "breaking"  I had my fill of that running Gentoo for 4 years...

As for you problem with the new Xorg, make sure you've installed the new synpatics driver (xf86-input-synpatics) and the evdev driver (xf86-input-evdev).  Edit your xorg.conf and comment out all Sections dealing with input drivers (mouse, touchpad, keyboard).  Or even better, try running without an xorg.conf file.

Or if you do not need hotplugging support add the following to your xorg.conf:

Section "ServerFlags"
     Option "AutoAddDevices" "False"
   EndSection

As for your openbox issue, no idea what might have happened there.

Good Luck

---

### Post by handy on 2008-11-30
It pays to check out the Arch news & forums before -Syu ing.  We all get bitten once, then learn that it is nobody's fault but our own for not looking before we ...

MisfitI38, posted this after the last kernel bug that caused many of us problems (including him :-)), (that was when I learned to downgrade, to escape my problems, which really should get you out of trouble too):

***_[http://bbs.archlinux.org/viewtopic.php?id=57205](http://bbs.archlinux.org/viewtopic.php?id=57205)_***

As far as downgrading is concerned, go to:

***/var/log/pacman.log***

& find the packages that in the list that you just upgraded, then go through & use the following:

***pacman -U /path/to/package/package_name-version.pkg.tar.gz***

to replace the new packages with their newly superseded ones which should still be in:

***/var/cache/pacman/pkg/***

That should go a long way to getting you out of trouble.

Watch the Arch forums & you will see what is causing the problem & when it has been solved.

Learning to downgrade like this (which is really quite quick & easy as you will find) means that you can get out of any problems that come with an -Syu, which is why it is a good idea not to clear your cache, or at least have a policy of leaving the superseded packages in. :-)

**[Edit:]** *Using the **pacman -Sc** command when you are sure that you have installed no problems in your last -Syu is a good way to keep your cache size down, but still gives you a quick & easy way out if your next -Syu brings unexpected trouble.*

---

### Post by Marshal0505 on 2008-11-30
You can just turn off hotplugging in xorg as mentioned on the wiki.Which should restore your keyboard mappings and ob hotkeymappings , etc. etc.
Pacman mentioned the wiki link on installing

edit: i found the link i referred to in my pacman.log

less /var/log/pacman.log | grep wiki>>> [http://wiki.archlinux.org/index.php/Xorg_input_hotplugging](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging)

---

### Post by OutOfReach on 2008-11-30
The update broke a few things for me too. But I managed to solve them.
The only thing that broke was X and my Synaptics touchpad.
I managed to solve my keyboard problems by switching to the Evdev-generic-keyboard layout. And I fixed X with the classic Xorg -configure.
Now the only thing left is my Synaptics touchpad.

EDIT: Just finished fixing my Synaptics touchpad. For those who want to know: I removed everything todo with my touchpad in xorg.conf, then I copied /usr/share/hal/fdi/policy/10osvendor/11-x11-synaptics.fdi , to /etc/hal/fdi/policy/11-x11-synaptics.fdi and added a lot of the options from the config file in [this]("http://bbs.archlinux.org/viewtopic.php?id=59110") thread. Exit X, **remember to restart the hal daemon!** then start up X again.

---

### Post by kerry_s on 2008-11-30
come over to debian lenny/testing if you want less work.
you can still do a custom install and things break less.
the only thing that's thrown me so far was the recent fontconfig-config update which now disables bitmap fonts by default, which just happened to be the fonts i was using. easy fix they can be turned back on with: sudo dpkg-reconfigure fontconfig-config
but i choose to just leave them off and change my fonts to the normal sans or mono, since i already have my ".fonts.conf" setup to disable antialiasing for normal text fonts, so i still get the same effect.

---

### Post by smartboyathome on 2008-11-30
And *this* is why I use the easynews repo. Its not only faster, but gets updates on a delay, so that if any of this happens, I know. :)

---

### Post by Barrucadu on 2008-11-30
That's not much breakage. I can't start xorg anymore, with any drivers, or any config file. Starting it results in a complete system freeze, and I have to do a hard reboot. Did I complain? No, I asked for help on the forums, and rolled back to the previous version until I have a solution.

---

### Post by fwojciec on 2008-11-30
> **SomeGuyDude said:**
> I'm furious right now, because after that X.org thing sat in testing for months and showed up in the extra repo, my system is totally wrecked. Amongst the problems:

1) You have to comment out a line in the xorg.conf file now because the variable is unused, which is confusing the hell out of a lot of people.

2) None of my OB config files work, and trying to edit anything via obconf or obmenu tells me it can't access my config files, but now it's looking for them in the root directory for some reason. So I have no wallpaper and my OB menu is that ugly default thing that has almost nothing I've installed. As a result, I have to use the terminal to launch EVERYTHING.

3) Synaptics no longer works. So my touchpad is all screwed up. Cool.

4) I don't have my Alt+F2 launcher either for some reason.

It's finals next week and I have a **** ton of work to do. This update was bad enough that I'm honestly tempted to scrap the system entirely. I like the ideals and I think Arch is far and away the best distro by design, but if these guys are gonna let things like this slip through, I'm out.

A rolling release system will always go through moments like this -- when new version of a package appears and it's necessary to fix/redo the appropriate config files.  The majority of your problems can be fixed by adding:
```
Section "ServerFlags"
Option "AutoAddDevices" "False"
EndSection
```
as was mentioned previously -- although this is just a workaround; a proper fix involves configuring HAL correctly like [wiki](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging) describes.

No idea about the OB problem -- sounds strange.

---

### Post by mentallaxative on 2008-12-01
> **SomeGuyDude said:**
> 
It's finals next week and I have a **** ton of work to do. This update was bad enough that I'm honestly tempted to scrap the system entirely. I like the ideals and I think Arch is far and away the best distro by design, but if these guys are gonna let things like this slip through, I'm out.

Question: why did you perform a system upgrade on critical packages when you know beforehand you won't have time to fix any problems from it? I didn't do any upgrades for nearly a month before my exams to avoid scenarios like this.

---

### Post by wolfvorkian1 on 2008-12-01
No, nothing broke on my system. Knock on wood. I've always figured that one of the greatest strengths of Arch, its rolling release concept could also be its greatest weakness but so far, no problem. 

Question I have though, is since I always keep a tar backup of the entire system, if an upgrade did break the system severely, if I extracted the backup, would that then put me back to where I was before the upgrade hosed my setup? Let's assume  that I've made the backup correctly. 

Unless, I would have to start fiddling all the time, I can't imagine ever changing and not using Arch. So far it is exactly what I want in a Linux distribution.

---

### Post by handy on 2008-12-01
Once you do a session of downgrading as per post_3 in this thread (which is really quite quick & easy once you get going), I think you would find that it is so easy you wouldn't go to the trouble of a full restore from backup.

You downgrade whatever it takes to get the system functioning properly again & participate/watch the Arch forum until you get a solution.

---

### Post by eldragon on 2008-12-01
noone says whats so good about a rolling release, you get 1 package update at a time, instead of a whole system like the 6month cycle ubuntu has.

intrepid came with some issues i couldnt even think where to look at. these updates broke X and X only, and it was all due to a more advanced way to set things up. i think the move to hotplugging is a way forward. learn the new way to set things up instead of disabling it. its here for the better.

setting up a fdi file isnt that hard either...

my fdi file that makes my touchpad work as it used to
```

 cat /etc/hal/fdi/policy/11-x11-synaptics.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- SHMCONFIG PARA PODER USAR SYNAPTICS TOUCHPAD. -->
	<merge key="input.x11_options.SHMConfig" type="string">True</merge>
	<merge key="input.x11_options.vertedgescroll" type="string">true</merge>
	<merge key="input.x11_options.horizedgescroll" type="string">true</merge>


	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by handy on 2008-12-01
We love Arch, for all the reasons why!

Certain sets of circumstances occasionally cause people to move to another distro, which is fine; all the distro's exist for a reason.
_____________

I'm not pushing downgrading as a solution to the current problem that some people are experiencing, I'm just exhibiting it in case anyone is unaware of the process, as it can save your bacon, when you don't know how to fix a problem that you just installed.

---

### Post by will1911a1 on 2008-12-01
Didn't break anything that I'm aware of on my system.  Guess I lucked out.

---

### Post by hrod beraht on 2008-12-01
No, nothing 'broke', but that's that may be because I don't have the HAL daemon running on my system, so I'm pretty quick to notice when something wants to call on HAL. Fortunately I read the news blurb on the Arch main page about the new xorg and hotplugging.
Xorg isn't broken, just different. But I would agree that it's certainly different enough in a way that most people probably aren't aware of.

So if anyone hasn't done a pacman -Syu since yesterday, make sure you read the [[COLOR="Blue"]xorg hotplugging[/COLOR]]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging") wiki page so that you understand what the xorg folks changed!

Bob

---

### Post by eldragon on 2008-12-01
> **hrod beraht said:**
> So if anyone hasn't done a pacman -Syu since yesterday, make sure you read the [[COLOR="Blue"]xorg hotplugging[/COLOR]]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging") wiki page so that you understand what the xorg folks changed!

Bob

amen, i had the luck of knowing what i was getting into since i had configured intrepid before :D

oh, and intel graphics beware, some performance issues there too. gotta wait till 2.6.28 for the fixes there.

---

### Post by Themaister on 2008-12-01
Yeah, I had that problem. I am living on the egde, and usually test out software very early. Xorg-server 1.5.3 scared me though. They should have informed about this in right after install in pacman, and on the main page some time in advance, to prevent confusion. I had no clue how to activate norwegian keyboard with hotplugging until I accidentaly came over the wiki page :p But what doesn't kill you only makes you a more experienced user, right? :D

---

### Post by chachawpi on 2008-12-01
I had to comment out a line in my xorg.conf as well.  It was something to the effect of RGBState or something like that.  I also had to change my color depth from 32 to 24 because 32 gives me a "no screens found" error now.

It was a quick fix though.

---

### Post by bfc on 2008-12-01
> **eldragon said:**
> amen, i had the luck of knowing what i was getting into since i had configured intrepid before :D

oh, and intel graphics beware, some performance issues there too. gotta wait till 2.6.28 for the fixes there.

Yes, the intel graphics performance is poor, and the 2.5.x drivers are still flakey.  Even with Kernel 2.6.28-rc6 the performance was better, but still not great, however, what kills it, is the poor stability of the 2.5.x drivers, I've never had so many X crashes.  From what I'm told the GEM implementation will not be complete until the intel-dri drivers are also updated.

---

### Post by wolfvorkian1 on 2008-12-01
> **handy said:**
> Once you do a session of downgrading as per post_3 in this thread (which is really quite quick & easy once you get going), I think you would find that it is so easy you wouldn't go to the trouble of a full restore from backup.

You downgrade whatever it takes to get the system functioning properly again & participate/watch the Arch forum until you get a solution.

That is quite a horse you have. Big as a moose. 

I spoke too soon about the upgrade not being a problem. Something I didn't know is that apparently the different mirrors put out the upgrades at different times. So the one I use was late and came along after I posted I had no problem with it. X crashed badly and the adding some lines to the existing xorg.conf file didn't help.

What did work though, was renaming the existing xorg.conf file and then rebooting. It said it reconfiguring a new one but if it did, I can't find it. I'm running without one but X is fine now. I assume something in the ether took its place. Thanks for the tip on downgrading, I had already read your sticky on how to get an older kernel. I hope I never have to use it. 

I actually learned quite a bit today about different elements of the Arch system.

---

### Post by handy on 2008-12-01
That kernel bug we had a little while back caused me to learn about downgrading packages & a few other things as well.

Now that I know about the downgrading routine, I feel that I should be able to at least get back to where I was previously, if sometime in the future I download some trouble.  

This to me is such an important piece of knowledge to have.  Which is the reason I may have pushed it a little harder than was really needed in this thread. :)

P.S.

Yes that horse is something else eh!?  I've met a mother Moose & its offspring at Yellowstone when I was in the States once.  A day I will never forget. :-)

---

### Post by rsambuca on 2008-12-02
I'm a little scared to update right now :p  Think I'll wait for a few days.

---

### Post by whitefort on 2008-12-02
Yeah, I got broke too!

Fortunately mine was an easy fix - I just had to comment out a line in Xorg.conf, and all's well again (unless there's something I haven't spotted yet.)

I still regard myself as a Linux newbie, and I think there are few things scarier for a newbie than turning on the PC and just getting a command line (though Arch pretty much helped me get over that terror!)

But just for a bit of perspective, I'd like to point out that in the couple of years I've been using Ubuntu, ***its*** upgrades also broke X for its users at least twice that I can recall.

I've only been using Arch for several months, but given its 'bleeding edge' approach, I'm quite impressed that my system hasn't been messed up a lot more often than it has.

---

### Post by Toffeeapple on 2008-12-02
Apart from strange keyboard behaviour, cured by reading [this]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#How_can_I_get_the_correct_keyboard_layout_.28keymap.29.3F_I_have_lost_arrow.2Fspecial_keys"), I've had painless upgrades on three systems.. : )

---

### Post by smartboyathome on 2008-12-02
I'm afraid to upgrade now since I have an Intel x3100 graphics card. Is performance really that bad now? :(

---

### Post by Nepherte on 2008-12-03
I have a Intel 965 card and didn't have any issues with it or noticeable performance decreases. I do have to mention that I don't use compiz or any other compositing, nor did I check performance with glxgears (who cares if the numbers are lower when I don't notice a performance decrease). It seems I'm lucky since almost everyone with an intel card has problems with it.

That being said, I do have problems getting the right click tab to work with hotplugging enabled. I've posted about it here: [http://bbs.archlinux.org/viewtopic.php?id=60100](http://bbs.archlinux.org/viewtopic.php?id=60100) but not much response to my problem. Any help is appreciated.

Besides the right click tab, I didn't have problems upgrading to 7.4 on several systems.

---

### Post by bonzodog on 2008-12-03
I did the upgrade yesterday, and all I did was comment out the RGB line in xorg.conf, and added my keyboard configuration to the hal input fdi file, as I use a dvorak keyboard. I then copied it to /etc/hal/fdi/policy/. As for Ob, I use that, and you just need to reconfigure it. All your config files, and there should only be 3, are in ~/.config/openbox/, or at least thats where they should be. In there, you should have autostart.sh, menu.xml, and rc.xml.

---

### Post by rsambuca on 2008-12-03
Well, decided to take the plunge and update my system.  89 package updates (310MB).  Any bets it will boot smoothly afterwards? [-o<

Edit:

:: Retrieving packages from core...
:: Retrieving packages from extra...
:: Retrieving packages from community...

---

### Post by rsambuca on 2008-12-03
Ooops, no love.  Wouldn't start the X-server, but all I had to do was the RGB line fix.  Seems OK now.

---

### Post by RiceMonster on 2008-12-03
This update annoyed me. I also had to comment out the RGB line, and disable hotplugging. Then I had to reconfigure my touchpad all over again. That was frustrating. Everything's fine now though.

---

### Post by crimesaucer on 2008-12-03
After disabling the hotplugging in the xorg.conf, I was able to use my multimedia buttons again in xfce4 with my keythouch app. 


I also had to add the "tapping" lines to my xorg.conf in the Synaptics section, as well as add the new 2 finger scrolling and horizontal scrolling lines for the new xf86-input-synaptics driver.


It took about 10 minutes of research and configuring, but there were already a few different posts in the forum and an updated wiki guide when I looked.

---

### Post by handy on 2008-12-04
I chose not to upgrade until today, because I had little space left in which to download anything before my ISP would have throttled back my internet speed.

Anyway, I too had troubles, I had to comment out the RgbPath line in xorg.conf & add the line to turn off hotplugging, as I don't run HAL.

I also had to force the new ATi Catalyst drivers to install, & my screen refresh has slowed down considerably?  There is now 2 to 3 seconds before I get a response when I select a different work space, as an example, when you click on a different workspace, the more graphically intense the display, the slower is its appearance, you can wonder whether the mouse button worked at all.

Using the mouse button to scroll through the workspaces is rendered useless due to the lag.

I'll have a look in the Arch forum & see if anyone has found a way to fix it besides downgrading.

If I downgrade, will I have to go back to the earlier xserver?  I somehow expect I will.  

Hmm, I don't think I like this upgrade.

***[Edit:]** Glxgears is running at about 3650, which is really slow for this graphic card.*

---

### Post by RiceMonster on 2008-12-04
> **crimesaucer said:**
> I was able to use my multimedia buttons again in xfce4 with my keythouch app

Yeah, keytouch wouldn't work with hotplugging for me either.

---

### Post by smartboyathome on 2008-12-04
I decided to take the plunge last night, and it was a nightmare. I had to reconfigure my Xorg as it didn't give me the correct resolution, and boot into Ubuntu so that I could disable booting into X or else I would not be able to use mouse or keyboard. Then I had to disable hotplugging. All in all, X now works with my Intel Graphics card and such, but it was a PITA to configure.

---

### Post by extruct on 2008-12-04
No problems for me (knock knock on wood), nvidia driver with openoffice/eclipse still bugged, I wonder if they are going to fix this at all... Other things seems ok, probably because I don't have touch pad and never used X-Hotplug.

---

### Post by kpkeerthi on 2008-12-05
> **extruct said:**
> No problems for me (knock knock on wood), nvidia driver with openoffice/eclipse still bugged, I wonder if they are going to fix this at all... Other things seems ok, probably because I don't have touch pad and never used X-Hotplug.

That's an issue with NVIDIA binary driver. Unfortunately Arch devs can't do anything about it as the driver is not open sourced. 

Seems nvidia devs already fixed it in [180.11]("http://www.nvnews.net/vbulletin/showthread.php?t=122606") beta. Check out nvidia-beta in AUR.

---

### Post by extruct on 2008-12-05
> **kpkeerthi said:**
> That's an issue with NVIDIA binary driver. Unfortunately Arch devs can't do anything about it as the driver is not open sourced. 

Seems nvidia devs already fixed it in [180.11]("http://www.nvnews.net/vbulletin/showthread.php?t=122606") beta. Check out nvidia-beta in AUR.
Yea I know its not Arch's problem nor Ubuntu's (that I had), just since the bug was reported nvidia released like 3-4 new versions of the driver, and none of them fixes the problem. I do like beta's while their are not related to critical parts of the system (like kernel, drivers, dm, and etc), so I won't try the 180.11 beta driver, the bug is not that critical its just annoying but thanks for the suggestions anyway!

---

### Post by Toffeeapple on 2008-12-05
> I do like beta's while their are not related to critical parts of the system (like kernel, drivers, dm, and etc), so I won't try the 180.11 beta driver, the bug is not that critical its just annoying but thanks for the suggestions anyway!

If it's any consolation, I'm having no problems with the 180.11 drivers : )

---

### Post by fwojciec on 2008-12-05
> **RiceMonster said:**
> Yeah, keytouch wouldn't work with hotplugging for me either.

You should update xf86-input-evdev package to 2.1.0 (the i686 version has just been uploaded to [testing]).  See this bug report for reference: [http://bugs.archlinux.org/task/12342]("http://bugs.archlinux.org/task/12342")

---

### Post by SomeGuyDude on 2008-12-06
> **smartboyathome said:**
> I decided to take the plunge last night, and it was a nightmare. I had to reconfigure my Xorg as it didn't give me the correct resolution, and boot into Ubuntu so that I could disable booting into X or else I would not be able to use mouse or keyboard. Then I had to disable hotplugging. All in all, X now works with my Intel Graphics card and such, but it was a PITA to configure.

I started discovering other fun "quirks" since starting the thread with most of my input devices. Took a good day to get it all fixed. To me, this is not how things should roll.

---

### Post by extruct on 2008-12-06
> **Toffeeapple said:**
> If it's any consolation, I'm having no problems with the 180.11 drivers : )
Ok thanks for the info :)
Maybe Ill try it.

---

### Post by fwojciec on 2008-12-06
> **SomeGuyDude said:**
> I started discovering other fun "quirks" since starting the thread with most of my input devices. Took a good day to get it all fixed. To me, this is not how things should roll.

And how should they roll?
Did you report any of these quirks on the bugtracker so that they can be fixed for everyone?

---

### Post by MisfitI38 on 2008-12-06
Upgrade breakage on Arch is nearly always due to [upstream changes, and/or user negligence. ]("http://bbs.archlinux.org/viewtopic.php?pid=459631#p459631")
If we cannot smooth out our own upgrades, it is irresponsible to blame Arch or Arch devs. It's just not the way Arch works.

---

### Post by handy on 2008-12-06
I'll wait patiently for those upstream to recover the lost speed & functionality.  Without *them*, there is no Linux distro's. One of the major pains in Linux is the problems associated with the xserver imho.  

The fixing of the xserver problems has to rock our boat.

---

### Post by phoochka on 2008-12-08
I'm quite disappointed to be honest. I was really hoping a major distribution such as Arch would be above this sort of stuff. 

Looking at forums/irc channels/mailing lists every time before an upgrade should not be an acceptable part of our "linux environment." I know xserver is notorious for this sort of things, the oh-so-nice-devs do everything in their spare time and I dont really care if someone's grandmother finds linux easy to use or not. I care about ME using linux. Yes I fixed the problem in 2-3mins, but then I could run Crysis on Windows 95 if I really wanted to, but I dont want to! I like to spend hours tinkering with tiling wm configs and my .vimrc, but that does not mean I like bending over whenever I need to upgrade.  

Sorry for the rant, but I really hate it when something I really like messes up like this :<

---

### Post by eldragon on 2008-12-08
> **phoochka said:**
> I'm quite disappointed to be honest. I was really hoping a major distribution such as Arch would be above this sort of stuff. 

Looking at forums/irc channels/mailing lists every time before an upgrade should not be an acceptable part of our "linux environment." I know xserver is notorious for this sort of things, the oh-so-nice-devs do everything in their spare time and I dont really care if someone's grandmother finds linux easy to use or not. I care about ME using linux. Yes I fixed the problem in 2-3mins, but then I could run Crysis on Windows 95 if I really wanted to, but I dont want to! I like to spend hours tinkering with tiling wm configs and my .vimrc, but that does not mean I like bending over whenever I need to upgrade.  

Sorry for the rant, but I really hate it when something I really like messes up like this :<


considering arch's philosophy, your rant has no base. anyway, i experienced less breakage with arch's xorg update than what ubuntu 8.10 brought to the table. and ubuntu should expect grandma to upgrade her computer.

---

### Post by mips on 2008-12-08
> **phoochka said:**
> I'm quite disappointed to be honest. I was really hoping a major distribution such as Arch would be above this sort of stuff. 



Could I suggest you look into Debian Etch, it's a good distro and it's stable but you would have to give up other things that Arch offers. What you want and what Arch is about does not seem to go hand in hand.

---

### Post by chucky chuckaluck on 2008-12-09
funny this issue should come up right about the same time i get a visit from my old pal, the linux deer...

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxdeer2.jpg[/IMG]

translation: i need someone to hold my hand. i've been reading about this X/kernel whatever mess and i am lying in a pool of tears, sucking my thumb. is it safe to update yet? will a siren be sounded when it is? 

ooh! i haven't wet the bed yet! brb!

---

### Post by handy on 2008-12-09
:lolflag:

---

### Post by notwen on 2008-12-09
> **chucky chuckaluck said:**
> funny this issue should come up right about the same time i get a visit from my old pal, the linux deer...

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxdeer2.jpg[/IMG]

translation: i need someone to hold my hand. i've been reading about this X/kernel whatever mess and i am lying in a pool of tears, sucking my thumb. is it safe to update yet? will a siren be sounded when it is? 

ooh! i haven't wet the bed yet! brb!

chuck, you have officially became my hero.  no seriously.

---

### Post by chucky chuckaluck on 2008-12-09
> **notwen said:**
> chuck, you have officially became my hero.  no seriously.

ooh, the power. ooh, the responsibility.

---

### Post by handy on 2008-12-11
I just found something in the Arch forum:

It seems that having a Terminal window open is what is slowing things down in this X.org/Catalyst update. (at least for some of us)

I always have an open Terminal window (with 4 tabs) in the background.  After closing it down, my screen refresh rates look to be back to normal. :-D

---

### Post by mips on 2008-12-13
I updated my Laptop last night and this morning I had to edit the RGB line & disable hotplugging.

Besides that I have no issues.

---

### Post by handy on 2008-12-13
I got a Catalyst update today, it has improved the situation as far as the lag when changing workspaces, when Terminal is open in one of them.

I don't think it is quite as fast as it used to be, but I may be kidding my self. :-)

---

### Post by phoochka on 2008-12-16
> **eldragon said:**
> considering arch's philosophy, your rant has no base. anyway, i experienced less breakage with arch's xorg update than what ubuntu 8.10 brought to the table. and ubuntu should expect grandma to upgrade her computer.

I did not. Ubuntu actually gave me less errors... 

> **mips said:**
> Could I suggest you look into Debian Etch, it's a good distro and it's stable but you would have to give up other things that Arch offers. What you want and what Arch is about does not seem to go hand in hand.

Thank you, I have been thinking of Debian for some time now, maybe this is just the push I needed to get started with it. Will probably also try Slackware.

---

