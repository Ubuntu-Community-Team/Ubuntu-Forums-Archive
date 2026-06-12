---
title: "firefox hangs, crashes. new hd, fresh gutsy install"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-11-22
I recently installed Gutsy on a new hard disk. For some reason, Firefox hangs and then crashes often. Usually, I need to reboot to normalize things.
Why could this be happening and what can I do to fix it?

---

### Post by Dr Small on 2007-11-22
Do any other programs crash, or is it just Firefox ?; And does this happen while on some site with flash or java, or just at random times ?

---

### Post by optimusmedia on 2007-11-22
I've been having a similar problem, but am able to kill it from the system monitor.  If you haven't already, I'd suggest adding it to your top panel. (right click on the panel > select system monitor > click Add > Close).  When it hangs on me, I just click the system monitor and kill process from the services tab.

As to why and how to fix, I hope you find out.  What add-ons or plug-ins are you running?

I am running: DNSStuff Toolbar, FlashGot, Forecastfox, Google Toolbar, NoScript, ShowIP, User Agent Switcher.

I also should say, I have a hard time removing Add-ons.  I usually have to do it manually.  But I think this is because of some conflicts in sharing between a dual boot environment.  Anytime I load this firefox profile from Vista, all my add-ons break.

Again, sorry I have no direct fixes, but hopefully my story will keep you from having to reboot.

Happy Thanksgiving

---

### Post by kleo skywalker on 2007-11-22
Dr Small, other programs don't necessarily crash, often Firefox is the only one I'm using. I doubt it has to do with Flash or Java - I have both installed, but the crashes also happen at times when I'm using neither. For example, it crashed 15 minutes ago, and Ubuntu forums and Gmail was all I had open (I think, not sure).

optimusmedia, thanks for the tip. As for add-ons and plugins, I'm using Google Toolbar, flashplugin-nonfree from the repositories, and DownThemAll!. I don't dual boot, Gutsy only.

---

### Post by Dr Small on 2007-11-22
I had this same problem on my older system too. I would leave it up and running, or be in the middle of a post, and Firefox would just drop. It also happened for Iceweasel, Swiftfox and of course, Firefox.

I blamed it on a bad processor, because while I had Windows, the screen would suddenly freeze at times. Now that I have a new system and processor, it doesn't do it to me any more. But I never could find a sutible fix for Firefox's random crashes.

Trust me, I know what ya'll are going through :D

---

### Post by kleo skywalker on 2007-11-22
It just crashed again, this time when I clicked on a Quicktime video on the Star Wars website.

---

### Post by CitricAcid on 2007-11-23
I had similar problems on Windows. Looks like firefox is buggy. On Windows I upgraded FF to 2.0.0.9. 

Why in Ubuntu repos there is old FF (2.0.0.8)? It is known to be very buggy and soon after releasing it new one has been released (2.0.0.9) fixing previous made errors. Soon there is going to be 2.0.0.10. Why there is such lag on Ubuntu repos?

---

### Post by kleo skywalker on 2007-11-23
> **CitricAcid said:**
> I had similar problems on Windows. Looks like firefox is buggy. On Windows I upgraded FF to 2.0.0.9. 

Why in Ubuntu repos there is old FF (2.0.0.8)? It is known to be very buggy and soon after releasing it new one has been released (2.0.0.9) fixing previous made errors. Soon there is going to be 2.0.0.10. Why there is such lag on Ubuntu repos?

Any ideas on how to upgrade to 2.0.0.9?

---

### Post by kleo skywalker on 2007-11-23
Does anyone know how to upgrade from Firefox 2.0.0.8 to 2.0.0.9 in Gutsy?
Thanks.

---

### Post by MightyMe on 2007-11-23
Sorry to hear you have probs with Firefox. I'm running 2.0.0.8 without problem. 

Dont know if any of this helps, but would bet it has something to do with your plugins. Have you tried to unsintall them all and see if it makes any difference? Or may have something to do with an installed mediaplayer and its plugins...

I have installed my plugins from "ubuntu restricted extras". You can try that.

(From ubuntuguide.org):

"Note: The flashplugin-nonfree module is also automatically installed as part of the ubuntu-restricted-extras meta-package. You can install ubuntu-restricted-extras instead, using the Synaptic Package Manager (or by using apt-get install from the command line terminal). This will install not only Adobe Flashplayer but also msttcorefonts (Microsoft fonts), Sun Java, and some multimedia codecs as well."

Hope this helps.

---

### Post by kleo skywalker on 2007-11-23
> **MightyMe said:**
> Sorry to hear you have probs with Firefox. I'm running 2.0.0.8 without problem. 

Dont know if any of this helps, but would bet it has something to do with your plugins. Have you tried to unsintall them all and see if it makes any difference? Or may have something to do with an installed mediaplayer and its plugins...

I have installed my plugins from "ubuntu restricted extras". You can try that.

(From ubuntuguide.org):

"Note: The flashplugin-nonfree module is also automatically installed as part of the ubuntu-restricted-extras meta-package. You can install ubuntu-restricted-extras instead, using the Synaptic Package Manager (or by using apt-get install from the command line terminal). This will install not only Adobe Flashplayer but also msttcorefonts (Microsoft fonts), Sun Java, and some multimedia codecs as well."

Hope this helps.

I have all those installed already, and through Synaptic - ubuntu-restricted-extras, flashplugin-nonfree, msttcorefonts, sun-java6-jre and whatever else is installed with these by default.
As for the media player plugins, I have mozilla-plugin-vlc  (I installed this) and totem-mozilla (was this installed by default?) installed. Are you saying  one of these could be the cause of these problems?

---

### Post by philinux on 2007-11-23
2.0.0.9 fixes windows instabilities so will probably not hit the repos at all.

---

### Post by kleo skywalker on 2007-11-23
I uninstalled these two media player plugins - mozilla-plugin-vlc and totem-mozilla. Then I went to the same quicktime video on starwars.com. It hung. I rebooted and tried again, it didn't hang, but I can't watch the video anyway - missing plugins.
Why should these plugins be causing Firefox to hang? What do I do to fix this?

---

### Post by Derspankster on 2007-11-23
Firestox crashes/and or quits responding momentarily when I try to use ESPN forums. There are text boxes similar to this one I'm typing in here. ESPN is likely usinhg flash, about everything else on their site is. At any rate, Firefox quits responding or slows way down if I attempt to type in the text box area on any of the ESPN forums. 

I don't have any problem here, typing in a similar text box on Ubuntu forums. I have not noticed any other issues with Flash, if indeed this is a Flash related issue.

---

### Post by kleo skywalker on 2007-11-23
> **philinux said:**
> 2.0.0.9 fixes windows instabilities so will probably not hit the repos at all.


Thanks for the information. I have a question though - if 2.0.0.9 only fixes Windows instabilities, why has Mozilla released a version for Linux?

---

### Post by Derspankster on 2007-11-23
> **kleo skywalker said:**
> Thanks for the information. I have a question though - if 2.0.0.9 only fixes Windows instabilities, why has Mozilla released a version for Linux?

I have been surprised that 2.0.0.9 has not been offered as yet in Ubuntu.

---

### Post by MightyMe on 2007-11-23
Removing some of the plugins was just a thought to see if there was a difference in behavior. Sorry it didn't help. One final test would be to uninstall all plugins and Firefox and make a fresh install of Firefox without any extra plugins to see if that helps. Otherwise I'm out of ideas.

---

### Post by kleo skywalker on 2007-11-24
UPDATE: Uninstalling those plug-ins didn't do the trick. Firefox still hangs. I have to force quit and start it again. I notice that this happens when I try to open a third Firefox window, two already running. Odd, but thought I'd mention it.

---

### Post by kleo skywalker on 2007-11-25
bump

---

### Post by kleo skywalker on 2007-11-25
I'm sick sick sick of Firefox freezing on me every 20 minutes. This didn't happen in Feisty.
Does anyone know why this is happening and how to fix it?
Please help, thanks.

---

### Post by philinux on 2007-11-25
You may have a damaged profile ie .mozilla folder in your home directory.

First I would run

```
firefox -safe-mode
``` 

from the terminal.

---

### Post by kleo skywalker on 2007-11-26
> **philinux said:**
> You may have a damaged profile ie .mozilla folder in your home directory.

First I would run

```
firefox -safe-mode
``` 

from the terminal.

I ran that, and it hasn't crashed in an hour even though I opened tons of tabs and windows. But I can't keep using Firefox in safe mode all the time - without plug-ins or Google Toolbar. so what do I do next?

---

### Post by optimusmedia on 2007-11-27
Disable/uninstall all plugins.. reinstall them one at a time until the problem comes back.  

BTW: I upgraded this morning to 2.0.0.10 and haven't see the issue reoccur. yet :)

---

### Post by kleo skywalker on 2007-11-27
> **optimusmedia said:**
> Disable/uninstall all plugins.. reinstall them one at a time until the problem comes back.  

BTW: I upgraded this morning to 2.0.0.10 and haven't see the issue reoccur. yet :)

How did you upgrade?

---

### Post by optimusmedia on 2007-11-27
Ubuntu auto asked me this morning.  But you can force it like this: 

System > Administration > Update Manager.

Or from terminal:```
 update-manager
```

---

### Post by kleo skywalker on 2007-11-27
> **optimusmedia said:**
> Ubuntu auto asked me this morning.  But you can force it like this: 

System > Administration > Update Manager.

Or from terminal:```
 update-manager
```

I posted before checking the Software Updates alert. It has upgraded, I checked in Firefox and it's version 2.0.0.10, but it's behaving the same! Hangs the second I open a third Firefox window. Absurd and annoying.

---

### Post by optimusmedia on 2007-11-27
mine just hung too. :(

I tried to follow a link to a PDF.  Seems mine always hangs trying to open a new window.  But force quit always works for me and firefox restores my session right to where it was before the crash.  And while that's great ... still... If I wanted constant lock ups, I'd go back to windows ;)

---

### Post by kleo skywalker on 2007-11-27
> **optimusmedia said:**
> mine just hung too. :(

I tried to follow a link to a PDF.  Seems mine always hangs trying to open a new window.  But force quit always works for me and firefox restores my session right to where it was before the crash.  And while that's great ... still... If I wanted constant lock ups, I'd go back to windows ;)

Exactly. I can open two windows with lots of tabs, but it hangs when I try to open a third one. I can force quit but the point is - why is it behaving this way? It didn't use to in Feisty.

---

### Post by optimusmedia on 2007-11-27
hey that's right.. it is whenever i open a third window.. i had missed that.. that will at least help me work around it.  It's got to be a bug of some sort.  I'm currently encased in too thick of a newbie shell to get you an answer, but I'm sure there's someone here who can provide some clues.  

If there's system info I need to post to help identifiy this, let me know. I'll be happy to assist.

---

### Post by optimusmedia on 2007-11-27
To work around and just open tabs and not new windows this should help (a little): 

From Firefox > Edit > Preferences > Select "new pages should be opened in: 'a new tab'" 

With Google toolbar: Manage > Features > Search Box Settings > Check ..open search results in new tab.

---

### Post by kleo skywalker on 2007-11-28
> **optimusmedia said:**
> To work around and just open tabs and not new windows this should help (a little): 

From Firefox > Edit > Preferences > Select "new pages should be opened in: 'a new tab'" 

With Google toolbar: Manage > Features > Search Box Settings > Check ..open search results in new tab.

Hey, I already have those settings (lol, I'm not that new!)
I try to not open a third window, but it's not easy to remember that all the time. So I hope somebody can give us a fix.

---

### Post by wwave123 on 2007-11-28
I had the same problem. After google around, I found out disable google toolbar fixed the hanging problem. Now I'm happy that I got firefox back :)

---

### Post by kleo skywalker on 2007-11-28
> **wwave123 said:**
> I had the same problem. After google around, I found out disable google toolbar fixed the hanging problem. Now I'm happy that I got firefox back :)

I'll have to check if Google Toolbar is causing the problem. Even if it is, I'd like a fix other than getting rid of it - I like Google Toolbar.

---

### Post by optimusmedia on 2007-11-28
> **kleo skywalker said:**
> Hey, I already have those settings (lol, I'm not that new!)

Yeah, I didn't think so, however, I was just trying to save a few steps for someone who may need them.

wwave123, thanks for the lead.  I'll test that too.  But like Kleo, I'm hooked on the Google toolbar (even if it is [_evil personified_ ]("http://www.google-watch.org/")).

---

### Post by optimusmedia on 2007-11-28
FYI: after removing the google toolbar, i have had no problems.  At one time I was even able to open 20 windows. (for testing - I'm not that ADD) ;)

---

### Post by optimusmedia on 2007-11-29
*Seems* to be a Gutsy Bug:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/135110](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/135110)

There I found this post: 
> ... For what it is worth, which is not much, if you substitute in GoogleBar from the firefox addons site, enable GoogleBar, disable stock google toolbar, then the problem does not happen ...

---

### Post by wwave123 on 2007-11-30
I'm totally agree with you guys. I like google toolbar and I use it alot. This problem need to be fixed. But I can't sit around and waiting for the fix, so now the workaround is to disable the toolbar.

---

### Post by optimusmedia on 2007-11-30
> **wwave123 said:**
> I'm totally agree with you guys. I like google toolbar and I use it alot. This problem need to be fixed. But I can't sit around and waiting for the fix, so now the workaround is to disable the toolbar.

That's what I did.  I tried the googlebar from the Mozilla Add-Ins site, but it's just too far behind. :(

---

### Post by kleo skywalker on 2007-12-23
> **optimusmedia said:**
> That's what I did.  I tried the googlebar from the Mozilla Add-Ins site, but it's just too far behind. :(

I just tried that too, disabling Google Toolbar does solve the problem but I want to use the Toolbar!
And you're right, the GoogleBar from Mozilla Add-ons is quite inadequate - I'd have managed with it if only it had the Google Bookmarks button.
It's been a while since the last post to this thread. Has anyone come across a way to fix this? 
And now that we know that Firefox with Google Toolbar crashes when a third window is opened, maybe a new thread should be started with this specific question?
Thanks.

---

### Post by MichaelBKK on 2008-01-04
I've been having this same problem, and can confirm that disabling the Google toolbar seems to get rid of it.  Does anybody know if a bug has been logged for this?

The problem is specific to Firefox + Google on Gutsy.  I'm using the same combo on other systems and not having any problem.

---

### Post by MichaelBKK on 2008-01-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/135110](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/135110) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Answering my own question:  Yes it's in Launchpad, but there seems to be some argument over whether it's Google's problem or Ubuntu's.  It only happens on the Gutsy release of Ubuntu, so I vote it's Ubuntu's problem.

---

### Post by kleo skywalker on 2008-01-04
I just installed Swiftweasel from [here]("http://sourceforge.net/project/showfiles.php?group_id=195473").
You get Google Toolbar, and you can (so far apparently) open as many windows as you like. So till they fix that annoying bug, I'll just use Swiftweasel.

---

### Post by philinux on 2008-01-04
Interesting.

Whats so good about google toolbar? I've never tried it.

---

### Post by kleo skywalker on 2008-01-04
> **philinux said:**
> Interesting.

Whats so good about google toolbar? I've never tried it.

Er... I'm no one to extol its virtues (or enumerate its vices), I just happen to find it useful and convenient. All my bookmarks are in my Google Account, I use GMail and some of Google's other tools like Docs, I like all the different search options; so it works for me.

---

### Post by ElEdwards on 2008-01-04
I'm finding that even without the Google toolbar, my Firefox (2.0.0.10, I think) takes FOREVER to load most pages.  It will start to load a page, go about half-way on the progress bar, then the screen goes to a dark gray for a while.  That even happens with this forum.

I'm presently running a fresh install of Mint 4.0...but the same thing happened with a fresh install of Gutsy 7.10, as well.

I can reboot into WinXP and try all of the same sites in IE....and they all open without any problems or delays. :(

My laptop is a Compaq Presario 2170us / Celeron (2.Ghz) / 512Meg / 40 Gig HDD / Linksys Wireless Card / 10-gig Partition for "/", 15-Gig Partition for "/home" and 1-Gig for Swap.

---

