---
title: "flashplugin-nonfree"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by ofb on 2008-01-13
Right... I'm trying to get Flash items like YouTube working in Opera again. Those stopped a while ago - just get a grey box now. YouTube still worked in Firefox though.

So, probably a mistake, I tried downloading Adobe's own installer. I ran the shell script for Opera only and recieved the plugin .so in /usr/lib/opera/plugins, but still no YouTube, although the paths all look good in Opera's preferences.

At this point insert much looking around online & at my other machine on which everything works fine. I finally remembered flashplugin-nonfree in Synaptic and checked that. Yes, still installed. But then noticed didn't have the flash plugin listed in /usr/lib/mozilla/plugins or /usr/lib/flashplugin-nonfree. Uh-oh.

Checked YouTube in Firefox. Yep, not working any more.

Chose the reinstall option for flashplugin-nonfree in Synaptic. That didn't fix it. Chose full uninstall followed by install. Still no-go.

If you look at Properties > Installed Files in Synaptic, you'll see it says the flashplugin-nonfree puts files in places like /usr/lib/mozilla/plugins, /usr/lib/opera/plugins, /usr/lib/flashplugin-nonfree. But it's not doing that.

... So I suppose the basic question is how can Synaptic say it's placing the files, when it is not.

Followed by: why is this happening? And what can be done about it?

---

### Post by gn2 on 2008-01-13
Are you using 64-bit? If you are try this: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by ofb on 2008-01-13
No, plain old 32-bit install.

---

### Post by ofb on 2008-01-14
What a mess. See this thread 
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

Nine pages, but the alleged solution at the beginning was updated only a week ago. I'll be trying that next, which in theory may get Firefox working, though not Opera and Konqueror.

Dunno why the above didn't show up when I searched this forum for 'flashplugin-nonfree' before posting, but I would say that's the place anyone interested should post now, and this thread is closed.

---

### Post by RomeReactor on 2008-01-14
Hi. The stable (9.25) version of Opera has problems detecting Flash; the [latest beta (9.50)]("http://www.opera.com/download/linux/?ver=9.50b") corrects this problem. Regarding the problem with the flashplugin-nonfree package, download [this fixed version]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466") and double click on it to install it. Flash should work correctly after that.

---

### Post by ofb on 2008-01-14
RomeReactor, I've just used the method/download from the above thread, which may be the same. It worked for Firefox.

Next I took the older flashplugin-alternative.so from my other, still-working 7.10 machine's /usr/lib/mozilla/plugins and copied it to the /usr/lib/opera/plugins on my main machine & voila I now have YouTube for Opera again.

[IMPORTANT NOTE: That's a sloppy hack and will probably fail with the next upgrade, cause fires, and accelerate hair-loss. Not recommended.]

Some conjecture:

If you try installing/reinstalling flashplugin-nonfree with apt-get instead of Synaptic, you get a checksum error at the end, and the install fails. I'm thinking this happens with Synaptic too, but Synaptic incorrectly proceeds to show flashplugin-nonfree is installed, even though it has installed no files.

This would also perhaps explain why my other machine is still running the older flashplugin-nonfree, even though I do updates. Possibly the update also failed as described, and thus did not overwrite the older files.

Just mentioning that for anyone who may be curious about why this issue hits some machines and not others.

---

### Post by ofb on 2008-01-17
... and the Sloppy Hack failed. Flash is bust in Opera again. No idea how the fix could work for a couple of days and then quit, but it did, and re-applying it has no effect.

---

