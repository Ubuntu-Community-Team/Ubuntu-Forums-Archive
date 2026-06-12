---
title: "Youtube Crashes Firefox About 3/4 of the Time"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by cam2009 on 2007-04-30
When I view YouTube videos, either on the site or through sites like Digg, they play fine, but if I click home or back, Firefox crashes most of the time. I tried reinstalling flash, and it didn't do anything. When it happens, I can click exit, a not responding window will come up, and I can "force quit" with out any problem. It doesn't seem to be happening with anything besides YouTube videos. Ideas?

---

### Post by whee on 2007-04-30
Does it also happen in other web browsers or do you only have Firefox installed?

---

### Post by Seisen on 2007-04-30
What version of Flash are you using and how did you install it?

---

### Post by cam2009 on 2007-04-30
I'm assuming the first time I installed it, I used whatever method Firefox uses when encountered with a flash file, I think directly through adobe. For installing again, I used:
"sudo apt-get install flashplugin-nonfree firefox"
it's version 9.031.0.2ubuntu1

---

### Post by Sethalos on 2007-04-30
I haven't found any issues myself with youtube, and I'm there quite a bit.  Maybe try clearing your cache and cookies if you haven't already.

Seth

---

### Post by srt5 on 2007-05-01
I get the same problem where my Firefox browser crashes. I think its a problem with the flash plug-in because I tried using Konqueror and I get the same problem.

Another possibility is that it could be a problem with the website itself. I notice that almost each time my browser crashes, the status bar normally says that it is downloading some advert which appears on the page. Since the advert is probably coming from some 3rd party host, this would explain why some people don't encounter the problem (since the site will most probably cycle through a large collection of adverts - it is unlikely therefore that it will affect everyone).

As far as solving this issue, i am not sure. Maybe we will just have to wait until a new version of the plugin is made available (provided that this is a reported bug), or maybe it might be a good idea to try finding an add blocker for Firefox to see if it makes any difference.

If anyone else has a solution - I'd be very grateful for advice. :)

---

### Post by nanotube on 2007-05-01
well, while on rare occasions flash will cause ff to crash, it is certainly not 3/4 of the time. i would suggest you install the adblock plus extension, and enable the easylist filter, and try again. it could very well be some ad crap that's causing you to crash out.
also good to install flashblock, that way you only see the flash you wanna see, and not any of the other flash ad craplets they tend to throw around.

that said, i run the official mozilla build of firefox2 on dapper, so my situation is probably different from yours. :)

---

### Post by srt5 on 2007-05-01
Thanks for the speedy response :) I admit 3/4 of the time is a slight over-exaggeration! But it is very frustrating and sometimes it feels that Firefox just crashes all the time. Thanks for the info on the add blockers, I will give them a go, if they work I will post in this thread. It's very peculiar, I never had this trouble on dapper or edgy.

Cheers :)

---

### Post by tcabeen on 2007-05-01
I'm using the default firefox install on 7.04, with the default flash plugin.  I also have adblock and noscript installed, though.  I have been piddling around youtube for a few minutes, hitting back an d home while videos are playing.  No problems.  Noscript is allowing youtube, of course (or I wouldn't  be seeing any videos), but other sites (doubleclick.net) are blocked.

If it's not one of the ads or cookies doing it to you, then it's gotta be hardware- or driver-based, right?  So yeah, I'm thinking ads, too.

If I find an issue, I'll be back.  All the best with it.

---

### Post by cam2009 on 2007-05-02
I've had adblock plus the whole time, so that's not it. clearing cookies seemed to work, in that I viewed 4 videos without any problem, but it came right back up again an hour or so later. any other ideas? would installing an alternative to adobe flash player be worth a shot?

---

### Post by srt5 on 2007-05-02
Since installing Adblock and NoScript plugins for Firefox, the number of crashes that I encountered whilst browsing flash content on the web has significantly reduced. Content plays fine the majority of time.

I find NoScript particularly good it blocks all scripts by default on websites, and allows you to specify which embedded scripts to allow. For instance, it allows me to allow flash content to be downloaded from YouTube whilst blocking all of the annoying scripts such as add rotators from 3rd party sites.

With this said, Firefox still crashes occasionally (when trying to play some flash content), but nowhere near as often as it did before I suspect that this may be some bug in the Adobe flash player plugin for Mozilla Firefox.

It may be worth trying some other flash players which have Firefox plugins. If you decided to do this please let us know of your progress.

:)

---

### Post by Mechanical on 2007-05-02
I have had the same problem with youtube and all other flash video sites.  I had flash installed through automatix and thought that may be the problem so I removed it and did the manual install as described on the flash website.  Still have the same problems.

---

### Post by towsonu2003 on 2007-05-02
I believe this is a problem with Firefox + Flash plugin[1] rather than a problem with Feisty. I am using Dapper (6.06) with Firefox 2 and the last version of flash that I installed independent from the package manager. Firefox crashes occasionally on flash-rich sites. 

I couldn't find a solution so far. It's nice to have the session restore option though... 

Give epiphany-browser or konqueror a try. They might be better in handling the buggy flash plugin. 

[1] Flash shouldn't be having so many problems, it's sloppy programming. But Firefox shouldn't let some plugin take down the whole browser either...

---

### Post by tcabeen on 2007-05-03
> **cam2009 said:**
> I've had adblock plus the whole time, so that's not it. clearing cookies seemed to work, in that I viewed 4 videos without any problem, but it came right back up again an hour or so later. any other ideas? would installing an alternative to adobe flash player be worth a shot?

Nod to the posts after this.  You said you have adblock, but didn't mention noscript.  Furthermore, my adblock installation has the "subscription" to the US list enabled.

In this case, though, it sounds like NoScript is going to be your best bet.  Give it a shot and let us know what happens.

In my week or so of Ubuntu experience (this time around), I haven't had any crashes while using anything.  It's only the suspend bug that's gotten me.
I hope NoScript does the trick for you.

---

### Post by cam2009 on 2007-05-03
Just tried noscript, and it didn't work. youtube crashed on the first video. on adblock, I chose the default subscribtion back when it was installed, the EasyList for the U.S. I believe.

---

### Post by srt5 on 2007-05-03
Did you go into the preferences for NoScript? I'm not sure where it would be located (I guess it depends on the theme your using) but on mine a little "S" appears at the bottom of the window near the progress bar. By clicking this on the youtube site you should be able to allow youtube but restrict other scripts such as adblock and doubleclick.com

Also are you running AddBlock plugin on firefox? [EDIT] Sorry I misread your post! [/EDIT]

---

### Post by dondad on 2007-05-04
Don't know what is doing it, but I have the same problem. I have noticed that if I make sure to stop the video before closing the tab, it seems to happen much less often. Trying to close the tab with the video running is almost a sure lock up on my system.

---

### Post by Purple Grant on 2007-05-04
Happens to me too.
It seems more prevalent when there's a lot of tabs open, maybe?

---

### Post by cub on 2007-05-14
Same thing here. I used to believe that if I let the video finish playing or stopp last.fm playing it wouldn't crash, but it was just my imagination. Also I haven't seen any difference if I have several tabs open or if I only one firefox, one window, one tab...stills crashes. I have tried with adblock plus and noscript, but it didn't make any difference.

---

### Post by gamow on 2007-05-14
My Firefox also crashes with YouTube and with any page with flash.
I have installed Adblock and flash-plugin-9.0.31.0-release

When running firefox in the terminal I get:
> The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 115 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


running firefox --sync I get the same output.

By the way, how to activate noscript?

(If this is a different problem, let me know and I'll post it in a new thread)
================   EDIT    ========================
Problem Solved.

I have installed flashplugin-nonfree and I don't get this problem with firefox.
Now I can access all pages with Flash.

I hope that helps ;)

---

### Post by baba_oreilly on 2007-05-16
Im having the same problems as you folks seem to be having - flash sites are causing firefox to lock up frequently - I'd say at least a quarter of the time. Is there any way the flash plugin could be causing problems with the other extensions that are installed? That might explain why running flash locks up the whole program. For the record, I've got these add-ons installed and running: NoScript, AdBlock Plus, Download Statusbar, and Forecast Fox. Also, i'll point out that I use Firefox in windows as well, with these same four add-ons, and my windows firefox has never crashed on youtube or any other flash site.

---

### Post by dondad on 2007-05-16
> **cam2009 said:**
> I've had adblock plus the whole time, so that's not it. clearing cookies seemed to work, in that I viewed 4 videos without any problem, but it came right back up again an hour or so later. any other ideas? would installing an alternative to adobe flash player be worth a shot?

I have the same crashing problem. Haven't figured out anything to fix it yet, but I find that it occurs much less often if I make sure to stop the video before closing the tab. Probably not 3/4, but it does crash with disgusting regularity if I try to close the tab with the video running.

---

### Post by Xebec on 2007-05-16
Same problem here. Seems like ALSA problem in Ubuntu: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/25681](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/25681)
Don't know what to do :( Ditch Ubuntu and try another Linux distribution?

---

### Post by Rigar on 2007-05-16
I'am having the same problem and increased the cache updated flash and it just keeps crashing

---

### Post by Rigar on 2007-05-16
Is it possible it could be a setting in the about:config in firefox

---

### Post by Rigar on 2007-05-16
I think it has something to do with the cache myself because I increased the cache and It seems better, could also be a setting in about:config

---

### Post by Rigar on 2007-05-16
Could it also be in the swap file, and how do you do that on Ubuntu

---

### Post by guine on 2007-05-18
You could try using opera, thats what Ive had to do on pretty much every install of ubuntu ive done because firefox became unusable from crashing all the time.

---

### Post by meldroc on 2007-05-18
I'm getting the same problems - when I watch videos in youtube, frequently, if I hit back or otherwise try to navigate, the browser hangs and I have to kill it.  Yes, I've emptied my cache.  Yes, I've reinstalled.  Yes, I've tried waving the usual dead chickens at this, but it doesn't address the fundamental problem - Adobe's Flash player is a buggy piece of crap.

Does anyone else notice it's always the closed source proprietary crap that causes crashes?  Flash, the closed Nvidia drivers, ATI's drivers always cause crashes.  Closed-source developers don't have the motivation to fix the damn bugs - they just work on it until it compiles and pretends to work for them most of the time, then they've got a deadline to meet and new features to implement, so they ship it full of bugs.

People have been bugging Adobe, Nvidia, and ATI to make their damn software stable on Linux, and they won't do it.  If they bother to put any developers on the Linux stuff at all, it's only to add new features, or support new hardware, not to fix bugs.  They don't care about the bugs.

It just completely pisses me off.  When's gnash going to be ready for prime time?

---

### Post by towsonu2003 on 2007-05-18
> **meldroc said:**
> 
Does anyone else notice it's always the closed source proprietary crap that causes crashes? 

I really don't think it's solely a flash problem. After all, the browser shouldn't allow a stupid plug-in to crash it. 

It's like the kernel: if the computer can be hanged because of a problem in a program, the bug gets reported as a kernel bug. The bigger structure shouldn't allow the smaller structure to cripple / crash / destroy it...

So I think the firefox devels aren't free of blame in this case...

---

### Post by teknosexual on 2007-05-19
I don't know how much this will add to the discussion, but for those of you who have Adblock installed, do you also have a Gmail tab open while you are viewing these flash videos? There is a known conflict in Firefox when viewing Gmail with Adblock installed, FF may crash.

So yes, that was a stretch, but just wanted to throw that out there for those who are experiencing crashes (with Flash or in general).

---

### Post by Tye on 2007-05-19
I use Gnash 0.7.2-1build1 plugin for mozilla and derivatives

my ff crashes too

my dad uses his housemates XPP comp and ff crashes for him also (both flash and java)
but not on my XPP (probably completely unrelated)

i have about 300 mb cache and dont use adblock or script block

it happens to me even if i visit goverment site
which have no ads or 3rd party links (as far as i know)

---

### Post by meldroc on 2007-05-19
> **teknosexual said:**
> I don't know how much this will add to the discussion, but for those of you who have Adblock installed, do you also have a Gmail tab open while you are viewing these flash videos? There is a known conflict in Firefox when viewing Gmail with Adblock installed, FF may crash.

So yes, that was a stretch, but just wanted to throw that out there for those who are experiencing crashes (with Flash or in general).

Doesn't look like that's the case with me, and after a quick googling, it appears that this bug manifests with the older Adblock plugin.  Solution is to uninstall Adblock, replace it with the newer and cooler Adblock Plus

I already have Adblock Plus, and my flash/youtube-related hangs occur when I don't have gmail open.

And it appears that this bug doesn't just manifest on Youtube.  Any flash content that does lots of flashy multimedia, especially movies, can cause Firefox to freeze.

---

### Post by meldroc on 2007-05-19
Got a little information that might help.

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/104470](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/104470)

In the comments, there's an alleged workaround:

> 

The workaround seems to work on my system. What I do specifically is:

1. Open a new FireFox window.
2. Go to Youtube and select to open any random video.
3. Press pause so it doesn't reach the end.
4. Minimize that window.
5. Open a new FireFox window.
6. In the new browser, surf the net, watch videos, do whatever.

With at least one instance of Flash running in another FireFox window,
Flash does not crash.

Thank you for reporting this workaround. Though I hope Flash, FireFox,
or Ubuntu will eventually be resolved for so as not to have this problem
with Flash and hda intel sound drivers.

--
Dave M G
Ubuntu Feisty 7.04
Kernel 2.6.20-15-386


Looks like this workaround works for me - Firefox is behaving at the moment, after deliberately trying to reproduce the bug by attacking it with Youtube videos.

It seems that this bug is an interaction between Flash, Firefox, and the kernel drivers for some sound cards (mine's an Intel on-board sound chipset, using the intel-hda drivers.)

---

### Post by teknosexual on 2007-05-19
Found this solution on the [Ubuntu Edgy Guide]("http://ubuntuguide.org/wiki/Ubuntu:Edgy").

Note: if firefox crashes when visiting a website with flash content, do the following:

1. Open the firefox file...

[INDENT]   Ubuntu users: **sudo gedit /usr/bin/firefox**

    Kubuntu users: **sudo kate /usr/bin/firefox**[/INDENT]

2. Add the following line as last but one line of the file: 

[INDENT]**export XLIB_SKIP_ARGB_VISUALS=1**[/INDENT]

3. **Restart Mozilla Firefox **

Now firefox shouldn't crash anymore. ([Launchpad bug report]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/62988"))

Anyone want to try it and  see if it works?

---

### Post by Paul820 on 2007-05-19
Doesn't work for me, just tried it. Firefox keeps crashing on youTube. I have the newest adblock and i got my flashplayer from synaptic.

---

### Post by henklaak on 2007-06-30
Edit: Strike that, the problem HAS reappeared, with ESD off.
===========
Hi all,

The Firefox/Youtube problem suddenly started appearing after I had enabled Software Sound Mixing via
System->Preferences->Sound, Sounds tab, Enable Software Sound Mixing (ESD) 

After I unchecked it again and restarted firefox, the problem has never reappeared.
Hope this helps further investigations...

I'm on Ubuntu Feisty 2.6.20-16 and Firefox/2.0.0.4

Cheers, Henk.

---

### Post by intMain on 2007-07-27
> **henklaak said:**
> Edit: Strike that, the problem HAS reappeared, with ESD off.
===========
Hi all,

The Firefox/Youtube problem suddenly started appearing after I had enabled Software Sound Mixing via
System->Preferences->Sound, Sounds tab, Enable Software Sound Mixing (ESD) 

After I unchecked it again and restarted firefox, the problem has never reappeared.
Hope this helps further investigations...

I'm on Ubuntu Feisty 2.6.20-16 and Firefox/2.0.0.4

Cheers, Henk.

i'll give the ESD setting a try.

---

### Post by intMain on 2007-07-27
ok, disabling ESD didn't work.

---

### Post by stchman on 2007-07-27
> **cam2009 said:**
> When I view YouTube videos, either on the site or through sites like Digg, they play fine, but if I click home or back, Firefox crashes most of the time. I tried reinstalling flash, and it didn't do anything. When it happens, I can click exit, a not responding window will come up, and I can "force quit" with out any problem. It doesn't seem to be happening with anything besides YouTube videos. Ideas?

I have a procedure that has worked for me:

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Hope this helps.

---

### Post by bhold on 2007-07-28
I have the same Firefox problem with Youtube. Ubuntu 7.04, Firefox 2.0.0.5. I haven't spent much time looking for a patch or workaround. except to install the Epiphany browser which works fine with Youtube. Kind of a pain to run 2 different browsers though.

--------------------

I tried installing flash9 nonfree plugin. apt-get and synaptic encounter a checksum error for some reason and don't complete the installation. So I went to [www.adobe.com](www.adobe.com) then downloaded and installed flash9 manually. The install worked, but does not fix the Firefox / Youtube crash. So for now I'll continue using Epiphany for Youtube and occasionally browse these forums for future suggestions.

---

### Post by basher on 2007-07-28
I've been dealing with the same issue.  Here's my conclusion, it has to be a Flash player issue on lower end systems.  When I try to play a 0:30 second YouTube video, the sound is fine and the video is choppy as heck.  So I booted up to XP from a different hard drive and went to the same video in IE and Firefox and have the same results, choppy video, good sound.  Here's my specs:

AMD Athlon XP 3200+, 1Gb Memory, GeForce4 MX 400, 40Gb 7200RPM HD.

But less than a year ago this same computer was my primary computer and I had no issues, it boggles my mind that XP nor Ubuntu can play a Flash video with out jitter????  Is Flash 9 just that bloated??

On this machine I have Desktop Effects enabled with no problems and can run everything else with no issues. I watch full length movies with no problems at all.  My problems come when a web browser and Flash come in to play, on both Windows and Ubuntu.

So I dont' think its a Ubuntu issue but a Flash player issue??  Any thoughts?

---

### Post by veli on 2007-07-31
> **Paul820 said:**
> Doesn't work for me, just tried it. Firefox keeps crashing on youTube. I have the newest adblock and i got my flashplayer from synaptic.

Disable Ad Block on you tube, and FF will never crash.

---

### Post by FuturePilot on 2007-08-01
Seems to be a bug with the Flash plugin. 
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688")
I have the same issue

---

### Post by AaronMT on 2007-08-03
^

Added a submission to that bug note.

---

### Post by chrx on 2007-08-15
youtube always hangs when i use FF under KDE, but not often with Gnome enviroment.
dont no why.

---

### Post by st33med on 2007-08-15
I have installed the Gutsy KERNEL (not the system) and, once I get back to my computer this weekend, I will check to see if the new kernel fixes it or not.

It probably won't, but it is worth the check. Or, can Gutsy Testers confirm this?

---

### Post by Sundel0802 on 2007-08-16
In my case, the solution was to downgrade the installed version of flashplugin-nonfree. Since I don't know how to do that via command line, you get nice pictures instead. :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40803&stc=1&d=1187274690[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40804&stc=1&d=1187274730[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40805&stc=1&d=1187274730[/IMG]

---

### Post by brk3 on 2007-09-01
Can anyone confirm does the above work??

---

### Post by justmoon on 2007-11-11
This fixed it for me (I had the exact leave-YouTube-and-crash problem):

```
rm -f ~/.mozilla/plugins/*flash*
sudo aptitude reinstall flashplugin-nonfree
```

This should do a clean reinstall of the Flash plugin, even if you previously installed Adobe Flex Builder alpha or another customized Flash player plugin.

Please note that this has to be run for every user on your system who has this problem.

Inspired by: [http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html) (only thing I changed is to use aptitude reinstall which works even if flashplugin-nonfree is already installed).

---

### Post by JillSwift on 2007-11-11
> **justmoon said:**
> This fixed it for me (I had the exact leave-YouTube-and-crash problem):

```
rm -f ~/.mozilla/plugins/*flash*
sudo aptitude reinstall flashplugin-nonfree
```

This should do a clean reinstall of the Flash plugin, even if you previously installed Adobe Flex Builder alpha or another customized Flash player plugin.

Please note that this has to be run for every user on your system who has this problem.

Inspired by: [http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html) (only thing I changed is to use aptitude reinstall which works even if flashplugin-nonfree is already installed).The above appears to have worked for me. I've just surfed all over YouTube doing what usually freezes Firefox and it came through just fine. 

Thanks justmoon =^_^=

EDIT: ==============
Dangzit! It froze again >.< Sorry, looks like it may help, but does not solve.

---

### Post by NewDisciple on 2007-11-12
Running FF on two different desktops works all the time.  Play a flash video on one and leave it when finished.  Go
to the other FF browser and play all of the flash videos you want without FF freezing.  Some of the other work
arounds will not succeed on all hardware and systems.

---

### Post by delmir on 2007-11-14
Bump. I confirm this bug. I've upgraded to Ubuntu 7.10 and now firefox 2.0.0.8 and mozilla freezes randomly when viewing flash movies (mainly in youtube). I've installed ddd and ran "firefox -safe-mode -d"... I noticed that hitting break and lookup twice in a row causes firefox to unfreeze! Also, adding this XLIB_SKIP_ARGB_VISUALS=1 to /usr/bin/firefox no longer fix the problem. This seems to be a critical bug. Can someone please point me in the right directions? Thanks in advance.

---

### Post by FuturePilot on 2007-11-14
Well, there's really nothing we can do about this since Flash is closed source. Adobe must fix it.

---

### Post by SmallFish on 2008-02-16
Just to add another count to this thread.

Watching movies in youtube crashed (freezed indefinitely) half of the times. Nothing can be done.

---

### Post by arjanito on 2008-03-31
Hi there.completely remove Gnash and Flash Player.Then install Flash Player again .Works fine for me.

---

### Post by zero777zero on 2008-06-27
> **justmoon said:**
> This fixed it for me (I had the exact leave-YouTube-and-crash problem):

```
rm -f ~/.mozilla/plugins/*flash*
sudo aptitude reinstall flashplugin-nonfree
```

This should do a clean reinstall of the Flash plugin, even if you previously installed Adobe Flex Builder alpha or another customized Flash player plugin.

Please note that this has to be run for every user on your system who has this problem.

Inspired by: [http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html) (only thing I changed is to use aptitude reinstall which works even if flashplugin-nonfree is already installed).

not doing it for me

mine literally DOES crash 3/4 of the time or more, just going to youtube.com (main page) crashes my ff

---

### Post by chrisod on 2008-06-27
Upgrading Flash to the 10 beta [per these]("http://kemal.bioeng-network.org/2008/06/08/how-to-get-rid-of-annoying-firefox-crashes-in-ubuntu-hardy-flashplugin-nonfree/") instructions seems to have solved the Flash crash issue for me.

---

### Post by TheSe7enthSin on 2008-06-28
> **chrisod said:**
> Upgrading Flash to the 10 beta [per these]("http://kemal.bioeng-network.org/2008/06/08/how-to-get-rid-of-annoying-firefox-crashes-in-ubuntu-hardy-flashplugin-nonfree/") instructions seems to have solved the Flash crash issue for me.

This seemed to have fixed this issue. After about 1-2 years of having flash videos crash on me...It feels great to be able to scroll through 20 videos and not have a single crash.

...for now.
*knocks on wood*

---

### Post by DarKnyht on 2008-06-28
This is a know issue in Flash 9, and effects windows and mac also.  As others have said this has been going on for 1-2 years.  Upgrading to the 10 Beta seems to be the best solution for now.

You can look at the story below to see the commentary on the solutions for win and mac.  Unfortunately he couldn't be bothered to address linux, but the advise is still valid when it concerns Firefox.

[http://www.download.com/8301-2007_4-9978341-12.html?tag=cnetfd.mt](http://www.download.com/8301-2007_4-9978341-12.html?tag=cnetfd.mt)

---

### Post by freemti on 2008-06-30
> **TheSe7enthSin said:**
> This seemed to have fixed this issue. After about 1-2 years of having flash videos crash on me...It feels great to be able to scroll through 20 videos and not have a single crash.

...for now.
*knocks on wood*

Seems to be working for me too (knocking sound heard in background)

---

