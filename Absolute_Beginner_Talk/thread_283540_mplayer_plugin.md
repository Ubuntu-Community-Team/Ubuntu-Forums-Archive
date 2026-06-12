---
title: "mplayer plugin"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Bloch on 2006-10-24
The mplayer plugin in my firefox browser worked perfectly up until a couple of days ago.

Then I did two things: I installed the new flash 9 (which works fine) and in one of the updates there was a new version of mplayer (and presumably the plugin too, I didn't look closely)

Is the newer version broken? I try to keep my system fairly standard so I don't run into problems. How can it be that a newer version of mplayer doesn't work? 
I already tried reinstallinmg using Automatix, and it just reports that I have the latest versions.

When I enter
about:plugins
at the address bar there is no mention of mplayer, when I try to play embedded media I get a warning that a plugin is missing

---

### Post by TitusDalwards on 2006-10-24
you can hold the version of mplayer bu using Synaptics, so your system becomes before updating time, and you can use mplayer plugin.

---

### Post by Bloch on 2006-10-24
I'm not sure I understand your reply Titus. But to state the problem again, automatix seems to think I have the latest plugin, everything worked well until a few days ago and the last update, but firefox claims no plugin is installed.

Is there some extra installation to do? Am I the only one with this problem? (I keep a fairly standard setup)

---

### Post by TitusDalwards on 2006-10-24
if firefox claims no plugin, you can copy mplayerplug-in.so file in  firefox/plugins directory, after you update mplayer maybe mplayerplug-in.so file could be changed or removed.

---

### Post by Bloch on 2006-10-24
The mplayerplug-in.so file is in the /usr/lib/mozilla-firefox/plugins directory. I uninstalled and then reinstalled mplayer plugin using synaptics.

Once again, has anyone had a similar problem? Did the recent update to mplayer cause the plugin to disappear?

When I set up my system I just used automatix. Where is the problem cominmg from? I have tried to keep a fairly standard system, and now this happens.

---

### Post by adza on 2007-03-11
the mplayer plugin in the repositories is now not installable... does anyone know where else i can get this from? This is by far the hardest thing i've come across on ubuntu to date.... :S

---

### Post by kolinab on 2007-03-12
I'm experiencing the same problem as you with Mplayer. Here's a bump.

---

### Post by Goliath! on 2007-03-13
Ugh!  I can't get the darned mplayer firefox mplayer to work.  I installed Dapper from the live disk, then upgraded to Edgy.  When I go to a site that has .wmv or .wma, I get the message about needing a plugin.

I have tried everything I can think of.  I have spent about 17 hours on this already.  Can anyone help?

Does anyone have mplayer firefox plugin working on Edgy?

---

### Post by kolinab on 2007-03-13
That's the funny thing. I HAD it working for weeks. Now in the last few days it's a no-go. It's like Firefox doesn't even know the plugin is there.

---

### Post by Goliath! on 2007-03-13
That's right Kolinab.  I can get mplayer to play .wmv files from the command line or from the gui if I use Open With.  But it just won't run from within Firefox.  Anyone have any ideas how to convince Firefox the plugin is there?

---

### Post by Goliath! on 2007-03-14
Weirdness.  Yesterday Firefox couldn't see the mplayer plugin.  Today it can.  Gosh, Ubuntu is getting more like Windows every day!

Anyway, Firefox saw the plug in but it still wouldn't play wmv.  So I finally found this:

[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

It works, sort of.  It plays the video cleanly, with sound and everything.  But it plays it in a separate window and the image is a fixed size (full-screen just shows the same size image in a big white box).  It also throughs out an extra error message or two.  It's not pretty but it works.

---

### Post by kolinab on 2007-03-14
I'm still here. I'm listening. My silence is me being baffled.

To be honest I haven't spent much time troubleshooting the problem. I'll diddle some with it tomorrow. I wasn't SUPER happy with Mplayer anyway, so I might try getting the VLC plugin working. I'll post my results, forsure.

. . . ahh OK - I'll try the extension! hang on . . .

---

### Post by kolinab on 2007-03-14
Hey - Fantastic! You're right it's not pretty. I get a couple errors too, but my audio stream is working that I haven't had working for days. 

Good going - hopefully we can find a more elegant solution later on.

Thanks for getting my plugin working again!

---

### Post by thecdrdog on 2007-03-14
It works it works it works!!!!!!!!! Thanks as long as it works again I don't care how ugly it is.

---

### Post by novice1 on 2007-03-15
I have NEVER been able to get streaming audio/video to work within FireFox.  The link to mozilla add ons given earlier works as mentioned with a couple of funky error windows -- I get streaming audio -- have not tried to stream video as yet.

However, I do have mplayer plug in for Mozilla Firefox installed and it does not work at all.  I reinstalled, removed and reinstalled, completely removed and reinstalled mplayer plug in NONE of which fixed the problem.  But using the file browser I found that in the /usr/lib/firefox/plugins directory I found the following files tagged "(link broken)" and each of their icons had a big white X in a red box :

mplayerplug-in-gmp.so    and mplayer-in-gmp.xpt

If you try to launch these files you get an alert box that tells you the file is broken and offers to put it in the trash for you.  If I click "Move to Trash" it fails because I am not logged in a Root. The point is that I got the files so marked even from a reinstall, removal and reinstall and a complete removal and reinstall.  It appears as though the files have not been installed correctly or that they are bad files. They don't work right out of the box - it seems

I am Ubutu 6.10 Edgy and I used the Synaptic Package Manager to install or reinstall mplayer.  

Any one have ideas, suggestions or comments about what to do about this?

---

### Post by stuart62 on 2007-07-14
I have a different issue with MPlayer Plugin, one site I have an issue where it displays MPlayer plugin but it doesn't buffer. This only happens with firefox on Linux, when running Firefox under Windows I do not have this issue.

---

### Post by cytutchi on 2007-07-15
Hey there!

I'veinstalled the mpayer but i get sound and no visual!!!!
i only get the loading info n stuff but they dodnt go away

Help :/

---

