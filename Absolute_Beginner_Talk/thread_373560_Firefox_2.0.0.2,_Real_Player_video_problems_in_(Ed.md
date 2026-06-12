---
title: "Firefox 2.0.0.2, Real Player video problems in (Edgy)"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Goodson1974 on 2007-03-01
Yesterday I upgraded to Firefox 2.0.0.2 (I'm assuming I had 2.0.0.1 previously!) and now I can't 
view any video content in websites.  It worked fine with the previous version.

I can hear the audio content on sites like [www.bbc.co.uk](www.bbc.co.uk), these work fine so I believe the realplayer audio plugin must be working.

When i click on a link to view a realplayer video in Firefox, the player appears on the webpage showing the player controls, but after a short while the part of the webpage where the player was goes grey (see attached pic).

I'm completely at a loss, I've tried uninstalling realplayer 10 and reinstalling it with Automatix, but the problem is still there.

Any help will be greatly appreciated as I'm rather new to Ubuntu and think it's generally superb :)

---

### Post by khedron on 2007-03-01
Damn, I got that once. Luckily it was near the 6.10 release, so I just reinstalled the system with the new release.

Have you tried downloading the binary from Real's website?

[http://www.real.com/linux/?src=guide&pcode=rn&pageid=cogixPoll&pageregion=footer](http://www.real.com/linux/?src=guide&pcode=rn&pageid=cogixPoll&pageregion=footer)

When you have downloaded the file, do a

```

chmod +x ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin


``` 

and follow the instructions onscreen.

---

### Post by Maestro23 on 2007-03-01
Hmm... I still using FF 2.0.0.1 and just check that site.  When I clicked on a vid, my mplayer-plugin kicked in and  the vid starting loading in the buffer.  After a few seconds, the grey bars you have in your pic appeared and then the vid started playing.

* It asked my to select my player and I picked Real10 even though I don't have it installed.  So that's why my mplayer-plugin kicked in.

Do you have any other media players/plugins installed?  Or try and reninstall RealPlayer as khedron suggested.

Good luck.

---

### Post by Goodson1974 on 2007-03-01
Thanks for the reply khedron

Now to show my complete 'newness' to Ubuntu!

I've downloaded the RealPlayer10GOLD.bin file, but i don't know which folder it should go in when i install it!

When installed, will it be available on the Applications menu, or do I have to do something with Terminal?

Will the install process put the firefox plugins in the right place?

You can probably tell that I'm still learning!!

---

### Post by Goodson1974 on 2007-03-01
Please ignore the reply about where to install RealPlayer!

I've managed to install it to the etc/ folder and got realplayer working.

Unfortunately the problem is the same, audio is fine, but videos are not working.

When i checked about:Plugins in Firefox there only appears to be a realplayer plugin for audio: -
**************************************************************************
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0 on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
***************************************************************************

How do I enable a plugin for realplayer videos???

---

### Post by khedron on 2007-03-01
Heh, I just checked my about: plugins and got the same message as you. Then I tried to play a video from news.bbc.co.uk and got the same problem as you.

Weird thing is, Realplayer has been working for me. Last time I used it was about a week ago, and it was fine then. :(

---

### Post by khedron on 2007-03-01
Hmm, weird. See if this does anything for you:

When you open a BBC news video popup, click on "Preferences" in the top right. Then switch to Windows Media Player. Click ok. The video should refresh (to show a blank). Then click "Preferences" again, switch back to Realplayer.

When I did this, the video launched in the standalone Realplayer. Not as good as launching from within Firefox, but acceptable.

Maybe this is something to do with the recent Firefox update?

---

### Post by khedron on 2007-03-01
Sorry about triple posting, but re:Goodson - if you have a choice, user-installed programs should go in /usr/local (or in ~/bin if you want to keep the program to yourself on a multi-user computer).

/etc is really supposed to be for system settings files. Don't worry this time, it shouldn't mess anything up, but just be aware next time you install a program that asks you where to install it.

If you want to know more about what the different folders are for, try
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

---

### Post by Detonate on 2007-03-01
I have installed realplayer and mplayer many times on different systems with different versions of firefox.  I have found, that it is best to install realplayer first before you install mplayer.  When you have installed Realplayer to your computer, open Realplayer from the menu, and the first time you open it go through the setup and it will install the firefox  plugins.  Then delete the pluginreg.dat file in your /home/username/.mozilla/firefox directry.  This file will be regenerated next time you start firefox.  As a matter of fact, anytime you update any plugins in ff, close ff, delete this file, then reopen ff.  Visit a web site on which you will use realplayer, and use it.  Then install mplayer.  This works for me.  You can also open the mplayer configuration and uncheck the realmedia and smil blocks.  that should keep mplayer from trying to open realplayer files.

---

### Post by Goodson1974 on 2007-03-02
Hi all

I had no luck with viewing any videos in firefox with realplayer trying the above suggestions, so i've decided to let mplayer handle the realmedia side of things for now and hopefully firefox will be fixed asap.

The weird thing is, real videos are now opening in firefox with the mplayer plugin, but the space where the controls should be are grey like the original problem with realplayer!!

Thanks for all the help guys :-)

---

### Post by sedbergman on 2007-03-04
Same problem here. I use Ubuntu Edgy and Opensuse 10.2 and i'm experiencing exactly the same symptoms as indicated in your thumbnail. Also seamonkey is doing the same thing but Opera working fine. Must be a mozilla problem. Sorry i can't help but nice to know it's not me who's damaged my installation.

PS. Using Firefox 2.0.0.2 and Seamonkey 1.1

---

### Post by tyres on 2007-03-05
Hi,

I've got the same problem. Must be the latest Firefox update, as it was working fine before. Anyone know if you can go back a version in Firefox?

Colin

---

### Post by tyres on 2007-03-05
Hi,

I went back to Firefox 2.0.0.1, but it made no difference. Still the same problem with embedded RealPlayer not launching in Firefox. It works stand-alone, though. Must have been something else that changed (Gecko?).

Colin

---

### Post by lahook on 2007-03-06
i'm also have a problem with realplayer and firefox 2.0.0.2 in fiesty
what are the realplayer plugins that need to be in the firefox/plugins folder?
i've been trying to play videos on cbs innertube

---

### Post by proalan on 2007-03-06
Same problem here

only thing I can do for now is paste the stream as a url into the stand alone real player application

---

### Post by lahook on 2007-03-06
i found this info, but i can't try it yet because i'm at work using windows.
maybe it will work

Q. How can I troubleshoot the mozilla plugin?

   1. Confirm that you are using a supported browser (Mozilla 1.0 or later, or Firebird). Other browsers may work, but will not have complete JavaScript functionality.
   2. Confirm that the mozilla plugin that comes with the player has been built with the same major version of gcc as the browser (about:buildconfig will show this information for mozilla, about:plugins will show this information for the Helix Player mozilla  plugin).
   3. Check the about:plugins page, and ensure that:
         1. The Helix DNA Plugin appears, and has registered audio/x-pn-realaudio-plugin
         2. It is the only plugin registered for audio/x-pn-realaudio-plugin. RealPlayer 8, plugger, and mozplugger are things that may try to claim this mime type.
   4. Make sure that "realplay" is in your system path, and that it points to RealPlayer 10. hxplay will also work, but note that most embedded websites require capabilities that are only present in RealPlayer.
   5. Remove ~/.mozilla/pluginreg.dat to force an update of plugin registry info.
   6. Run mozilla from the commandline -- the plugin may log useful information to the console.

---

### Post by lahook on 2007-03-07
I got my realplayer plugin in firefox working by reinstalling from realplayer.
inside the " " is what I typed into terminal

downloaded
open terminal
entered "sudo -i"
cd'd to downloaded folder
"chmod a+x RealPlayer10GOLD.bin"
"./RealPlayer10GOLD.bin"
real player install script starts up
when it asks where to install put in "/usr/lib/realplayer"
then it installs and configures it

i hope this helps

---

### Post by rico001 on 2007-03-08
> **lahook said:**
> I got my realplayer plugin in firefox working by reinstalling from realplayer.
inside the " " is what I typed....

You can also install realplayer easier by using Automatix2.  It should be in the ubuntu Guide

I used a .deb file install of firefox called Swiftfox.  Manually installing Firefox 2.0.0.2 messed up firefox detecting the realplayer plugin for me.  Installing swiftfox deb fixed it.  (I also deleted the firefox directory in /opt/ but I don't think this matters)

---

### Post by Detonate on 2007-03-08
Do you mean that installing Swiftfox fixed the problem in Firefox?  Or do you mean that realplayer now works in Swiftfox?  Which browser are you using?

---

### Post by beercz on 2007-03-09
Hi Guys

I had the same problem, but have now solved it by reinstalling realplayer.

For those who are still struggling, this is what fixed it for me.

Download realplayer from [here]("http://www.real.com/linux/?src=guide&pcode=rn&pageid=cogixPoll&pageregion=footer") to a temporary directory.

Then follow the instructions as given by lahook:

>  open terminal
entered "sudo -i"
cd'd to downloaded folder
"chmod a+x RealPlayer10GOLD.bin"
"./RealPlayer10GOLD.bin"
real player install script starts up
when it asks where to install put in "/usr/lib/realplayer"
then it installs and configures it


The only thing I did differently was to install realplayer in "/usr/local/bin/realplayer"

When installed restart firefox.

Good look.

---

### Post by cic007 on 2007-03-16
I have the very same problem.

I've had it bofore at various stages and it hs been driving me to distraction. When my fathers computer had this problem (also on the BBC website) I had him spend 6months using 'Listen to using Stand Alone RealPlayer' link (basically downloads the .ram which contains the stream address.

Sound is working fine as reported... (bbc radio in real format works)....


I have it working on my other laptop and thought the problem had gone away forever until I got my new dell (sans windows! WITH DISCOUNT!) and installed ubuntu on it.

Now I'm back to the graying out as described.

I originally installed it from the .bin and it didn't make a difference for me.

I reinstalled it in the directory suggested which has still not fixed it.

I'm reluctant to delete te .dat file as I suspect it contains the data for *all* of my firefox plugins (and I have quite a lot). I wouldn't want to lose those settings they took *ages* to set up.

Anyone know if it's easy to edit the file with nano and delete only the realplayer plugin section?


(I could always back it up first in case I screw up).

Cheers Folks!

All suggestions welcomed - bag of cyberpopcorn for the person who solves this :popcorn:

---

### Post by Detonate on 2007-03-16
You can safely delete the file.  Firefox will automatically rebuild it.  I always delete the file whenever I make any changes to my plugins.

---

### Post by silkstone on 2007-03-16
I originally installed Real Player through Applications > Add/Remove. When I had the problem with it crashing on the BBC site, I uninstalled it (Add/Remove) and cleaned out the remaining config files with Synaptic > Status. Then I reinstalled it using Add/Remove, but still had the same crashing problem.

Can you confirm that doing a manual install (as described above) works, even though installing through Add/Remove doesn't?

Thanks.

---

### Post by Goodson1974 on 2007-03-16
I've tried all of the methods described above, but nothing seems to solve it :( 
 
I'm sticking with the mplayer plugins for now.
 
Does anyone know if this is an 'official' bug with Firefox 2.0.0.2?

---

### Post by cic007 on 2007-03-16
> **Detonate said:**
> You can safely delete the file.  Firefox will automatically rebuild it.  I always delete the file whenever I make any changes to my plugins.


I knew I could *safely* delete it. As in that a new one would be generated. I was more thinking that the new one would use the default settings for all of my firefox plugins consequently forcing me to reset them :)

Wouldn't it?

---

### Post by Detonate on 2007-03-17
Hmmm, that requires some thought.  The file tells firefox which plugin or program handles each mime type or extension.  Each of your plugins is individually configured.  I would think that firefox would generate the file based on those individual configurations, but I'm not sure.  For example, if you have mplayer configured not to use smil files, because you want Realplayer to play those files, does firefox know this?  I don't know.  Time for some experimentation.

---

