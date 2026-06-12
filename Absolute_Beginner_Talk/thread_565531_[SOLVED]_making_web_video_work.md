---
title: "[SOLVED] making web video work???"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by bhold on 2007-10-02
This should not be that hard so I must have messed up something. I want my feisty system to play web video - at all sites - just like my XP system does.

I have followed all instructions at:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)
[http://linuxappfinder.com/blog/video_on_the_web_plugins_required](http://linuxappfinder.com/blog/video_on_the_web_plugins_required)

Still cannot play web video at all sites as reliably as XP - suggestions appreciated.

(Getting closer but still cannot see video at foxnews.com, just a black screen)

Thanks   -- Bob ](*,)

---

### Post by j.bunce on 2007-10-02
It's not supported by Ubuntu, but try automatix: [www.getautomatix.com](www.getautomatix.com). It'll install the firefox mplayer and flash plugin that I think you want.

---

### Post by bhold on 2007-10-03
Thanks for your suggestion j.bunce. The aubomatix web site is having a problem, so far I have not been able to get to the installables. But I already have the plugins you mentioned installed. Will automatix add anything else that might help?

I should have mentioned in my original post that the browser I primarily use on Ubuntu is Firefox, although Epiphany has the same problem.

Interesting that Suse 10.2 / Konqueror has no problem playing foxnews.com videos - but no audio! When I have time I will attempt a comparison of installed packages between my Suse and Ubuntu systems, maybe that will show what I need to get both working.

Personally, I kind of enjoy poking around with this stuff and trying to get it to work - yet I can see how those attempting to migrate from Windows to Linux could find it frustrating. Oh well, that is a topic for other threads.

-- Bob

---

### Post by philinux on 2007-10-03
to get fox news you need the firefox flash plugin its in the repos. I wouldnt touch automatix it can bust your rig.

By the way to get the foxnew vids to works you also need

1. cookies turned on
2. adblock turned off

---

### Post by bhold on 2007-10-03
In synaptic, searched on firefox flash plugin. The following shows what is installed on my system and what is available. Anyway, it still does not work. Do I need more of the packages from this list? If so, which ones?

[IMG]/home/bhold/Desktop/Screenshot-Synaptic Package Manager .png[/IMG]

Well, inserting image into this post did not work, maybe the attachment will. \

---

### Post by nickpaton on 2007-10-03
Please could you list / attach the folder contents of :

 /usr/lib/firefox/plugins

/usr/lib/mozilla/plugins

---

### Post by nickpaton on 2007-10-03
Rather than the previous post, carry out the following steps:

Looking at the topics you've checked, the most relevant for you is the last one which mentions mplayer.

So install *mozilla-mplayer* via Synaptic.

and try again.

If that still doesn't work please could you then post the contents of the folders I previously listed.

---

### Post by bhold on 2007-10-03
mozilla-mplayer was already installed, I re-installed, still does not work. Attached are the requested folder contents.  Thanks   -- Bob

---

### Post by nickpaton on 2007-10-04
Thanks for that, and apologies for the delay in getting back to you.

You need to get rid of all the libtotem plugins in both the mozilla and firefly plugins folders - easiest way is to delete them using nautilus (gksudo nautilus).

Let me know how you get on and good luck!

---

### Post by bhold on 2007-10-04
I removed the libtotem* files from /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins by using synaptic to remove package totem-mozilla. Now the contents of those directories are as follows:

bhold:~> ls /usr/lib/firefox/plugins
flashplayer.xpt        mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt
libflashplayer.so      mplayerplug-in-rm.so   mplayerplug-in.xpt
libjavaplugin.so       mplayerplug-in-rm.xpt  nphelix.so
libunixprintplugin.so  mplayerplug-in.so      nphelix.xpt
mplayerplug-in-qt.so   mplayerplug-in-wmp.so

bhold:~> ls /usr/lib/mozilla/plugins
flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.so
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt
libjavaplugin.so        mplayerplug-in-rm.so   mplayerplug-in.xpt
mplayerplug-in-dvx.so   mplayerplug-in-rm.xpt  nphelix.so
mplayerplug-in-dvx.xpt  mplayerplug-in.so      nphelix.xpt
bhold:~> 

Unfortunately, this did not work- still getting just audio but no video at foxnews.com.

---

### Post by nickpaton on 2007-10-04
Hi Bob

Unfortunately because I'm behind a remotely operated server with parental controls on it, I am unable to access Fox news for some reason (I'll be asking the admin to see what is blocking it).

Can you try this [CNN video news]("http://edition.cnn.com/2007/US/10/04/philly.shootings/index.html#cnnSTCVideo") link

*EDIT* - Rechecked the link and now doesn't work on mine, so you may need to click on one of the other advertised vids on the page.

If not working (mine does):

Had a look at  your plugins and they are similar to mine with a couple of differences:

Both have flashplayer.xpt  in and mine doesn't (may not be relevant).

On Mozilla plugin folder you additionally have nphelix.so  and .xpt.

On my Firefox plugin folder, every plugin EXCEPT nphelix.xo and .xpt are symlinked to the Mozillar plugin folder.

So it may be worth looking at helix and how that's installed.

uninstall helix-player and mozilla-helix-player
 
```
sudo apt-get remove helix-player mozilla-helix-player
```

Also uninstall Real Player if you originally installed it, since it can clash with Helix.

Reinstall:

```
sudo apt-get install helix-player mozilla-helix-player
```

This should automatically set up the links to the Firefox plugin folder, but if not it may be worth symlinking:

```
sudo ln -s /usr/lib/helix/player/mozilla/nphelix.so (and separately .xpt) /usr/lib/firefox/plugins/
```

If that doesn't work I'm not sure what else to suggest, but I have assumed you're on Feisty.  If you're not (sorry should have asked earlier) can you get back to me.

Good luck again!

---

### Post by stoer on 2007-10-04
Hi
I've had the same problem in the past.
I found these two links helpfull, maybe something there for you.
Hope it works out.

[http://linuxmint.com/forum/viewtopic.php?t=372](http://linuxmint.com/forum/viewtopic.php?t=372)


[http://linuxmint.com/forum/viewtopic.php?t=3330](http://linuxmint.com/forum/viewtopic.php?t=3330)

---

### Post by bhold on 2007-10-04
Hi folks,

I have tried the helix player and plugin re-installs, adding the links, and the new /usr/lib/mozilla/components directory. None have worked. The only thing left for me to try is the greasemonkey installation and script, have not had time to try it yet.

nickpaton, fyi, I am able to watch video at cnn.com, no problem - would be interested to hear if you can see foxnews.com video if you get a chance to test it.

Thanks for your suggestions.    -- Bob

---

### Post by nickpaton on 2007-10-04
Bob

Unfortunately my parental controls (Dans Guardian - excellent!) blocks Foxnews for some reason, but not CNN.
Also because DG's on a remotely controlled server, I'm not able to easily find out why this might be so, but I will ask the admin to look into it (we've had some bizarre reasons for the most innocuous sites).

So can't help you there!

I would suggest Stoer's suggestion and see where that goes.

BTW does youtube work OK?  Could you just watch CNN instead??!! LOL

---

### Post by nickpaton on 2007-10-04
Bob

Also found [this post]("http://ubuntuforums.org/showthread.php?t=138437") admittedly for Dapper.

I had a look at the Stoer's second link and for me it showed I had a problem with BBC vids!!

Aaagh!!

Nick

---

### Post by nickpaton on 2007-10-04
Bob

Apologies if you keep reading this and it changes, but from further research withing these forums and Stoers post that you need to install the Firefox Greasemonkey plugin and modify the script as follows:

Greasemonkey is now simply installed from [here]("https://addons.mozilla.org/en-US/firefox/addon/748").

Then modify the script typically via [this link]("http://vlajbert.blogspot.com/2005/11/update-foxnews-friendly-video.html") which can now be carried out with a single mouse click.

I would also have a good read about adblocking etc etc since this seems critical.

Nick

---

### Post by bhold on 2007-10-04
Hello folks,

I have never had any problems with youtube, as long as the flash plugin is installed.

Anyway, the link provided by stoer for installation of greasemonkey and the Foxnews Friendly script did the trick. Not only does it allow foxnews.com video to play but also seems to filter out the ad clips.

I don't even watch that much web video. Its just that I was browsing a few threads and saw that people seemed to be having problems, and got curious what it would take to make it work.

Thanks for an educational discussion.    -- Bob

---

### Post by nickpaton on 2007-10-04
Glad to hear that Bob

You never stop learning here!

Nick

---

