---
title: "Gnash not plugging into Firefox"
date: 2007-09-11
forum: Apple PPC Users
---

### Post by dynamicv on 2007-09-11
I activated the backports feature on Add/Remove and installed the Gnash 0.8.0 package.  However, it doesn't appear to want to run in Gnome nor plug into Firefox.  Selecting it from the Applications menu does nothing, and checking [noparse]about:plugins[/noparse] in Firefox doesn't list it as installed.

Before I remove it and try the compile from source route, is this a known problem with the backport package or have I just missed a step?

---

### Post by kansei on 2007-09-11
I have the same trouble (on Gutsy.. so didn't need to go through backports). It's definitely installed, but it's still using libflashplayer.so even though I told it to completely uninstall the adobe player.

---

### Post by Auria on 2007-09-12
AFAIK the web plugin comes as a seperate package - install it too

---

### Post by kansei on 2007-09-12
> **Auria said:**
> AFAIK the web plugin comes as a seperate package - install it too

Yes, it is a separate package, but you don't even need it now. just opening firefox and going to a page with flash pops up the 'you need a plugin to view this page' thing and it lists both Adobe Flash (preselected for some unknown reason???) and Gnash. It goes through an install process for Gnash, but for me just says "gnash is already installed" and dumps me back to the non-working page.

I'm experiencing the same on my 32 and 64 bit Gutsy laptops.

---

### Post by Tearstone on 2007-09-15
I am having the same issue :(

---

### Post by bodek on 2007-09-16
I had the same problems, but not any more ;) Just in the synaptic package manager I chose to install gnash, and mozilla-plugin-gnash. Now firefox displays some of the flash pages without problems and doesn't ask for any missing plugin.
Never tried to install plugin through firefox, it never worked.

---

### Post by kansei on 2007-09-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/133197](https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/133197) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/133197](https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/133197)

the info in the first post on that bug report seems to have fixed it for me :)

---

### Post by MisterRik on 2007-09-23
> **kansei said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/133197](https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/133197) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/133197](https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/133197)

the info in the first post on that bug report seems to have fixed it for me :)

I couldn't follow that discussion at all, but then I'm a noob.

---

### Post by kansei on 2007-09-24
> **MisterRik said:**
> I couldn't follow that discussion at all, but then I'm a noob.

I can give you commands to copy and paste in that case :)

Open up your favourite terminal (Applications > Accessories > Terminal is a good one.. you said you were a noob, so I gotta go all out lol) and issue this command:

```
sudo ln -sf /usr/lib/gnash/libgnashplugin.so /usr/lib/mozilla/plugins/flashplugin-alternative.so
```

that should do the trick. Of course quite and restart Firefox after doing this, then try going to a page with flash. You'll notice that with flash video sites it'll be a bit buggy or weird looking. For me, on youtube, I can play/pause videos just fine but I can't seek or adjust the volume (the controls appear garbled).

---

### Post by MisterRik on 2007-09-25
Nope, still nothing :(

---

### Post by kansei on 2007-09-25
Did you previously have Adobe's proprietary Flash player installed? --through the flashplayer-nonfree Ubuntu package or otherwise

If you did, you'd have folders like /home/[your user name]/.macromedia and libflash files around. After uninstalling flashplayer-nonfree all sorts of macromedia junk was still on my computer so I ran a few searches and deleted a few hidden folders and files. I figured it was better to start with a clean slate.

Hopefully the update for Gutsy that I guess fixed this issue (I manually fixed it myself hours before the patch was committed) gets to Feisty Backports soon


> **the bug report page]
gnash (0.8.1-0ubuntu1) gutsy said:**
> 
  * debian/mozilla-plugin-gnash.prerm: Fixed upgrade procedures
    for people with ubuntu3 and ubuntu4 packages

  [ Alexander Sack ]
  * debian/mozilla-plugin-gnash.prerm: run update-alternative --remove-all
    when no other alternative was installed. (LP: #133197)
  * debian/mozilla-plugin-gnash.postinst: install gnash flash alternative for
    midbrowser.
  * debian/mozilla-plugin-gnash.prerm: remove midbrowser alternative in prerm
    accordingly.
  * debian/mozilla-plugin-gnash.dirs: take care that midbrowser plugins dir
    exists during postinst
  * update patches in turn of changes to upstream code base:
    - drop use_pkglibdir_for_unversioned_libs patch - applied upstream
    - update disable-testsuite which didn't apply because of change code base
      in proximity
  * debian/gnash-common.install: install shared libs of final releases as well

 -- Alexander Sack <asac@ubuntu.com> Thu, 13 Sep 2007 10:10:38 +0200


---

### Post by Auria on 2007-09-25
> **kansei said:**
> Did you previously have Adobe's proprietary Flash player installed? 

no, since this is the PPC forum ;)

---

### Post by kansei on 2007-09-25
> **Auria said:**
> no, since this is the PPC forum ;)

whoa how'd I get in here? *runs away*

sorry for any misinformation guys

---

### Post by hebetude on 2008-02-21
Hardy has an oddly installed version of Firefox 3.  Earlier versions contained both FF2/FF3 so I imagine the botched install is related to attempts to have both coexist on the same install.

Anyways, I got gnash to work on 64bit Hardy by symlinking to my home directory
```

sudo ln -s /usr/lib/gnash/libgnashplugin.so ~/.mozilla/plugins

```

32-bit Flash is for suckers :lolflag:

---

### Post by yesudeep on 2008-06-25
There should be no need to manually create all symlinks.  

Gnash is an alternative to Adobe Flash, so there's the hint 
"alternative".  Ubuntu comes with a program called 
update-alternatives that lets you switch between alternatives 
pretty easily.  The list of alternatives is found here:

```

/etc/alternatives

```

To switch mozilla browsers to using Gnash, just type this:

```

$ sudo update-alternatives --config mozilla-flashplugin
There are 2 alternatives which provide `mozilla-flashplugin'.

  Selection    Alternative
-----------------------------------------------
*+        1    /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
          2    /usr/lib/gnash/libgnashplugin.so

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/gnash/libgnashplugin.so' to provide 'mozilla-flashplugin'.

```

Now fire up Firefox or Swiftweasel or whatever Mozilla-based browser
you're using, and look under the Addons > Plugins tab.  You should see
Gnash installed.  It's just as easy to switch back to Adobe Flash 9.

Cheers,
Yesudeep.

---

