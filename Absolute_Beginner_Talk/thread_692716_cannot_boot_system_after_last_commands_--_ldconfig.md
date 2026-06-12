---
title: "cannot boot system after last commands -- ldconfig?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by malrost on 2008-02-10
Oh dear, it appears that I must have really mucked up my Feisty system. I was  trying to install a simple application from source, and now cannot even boot!

I'm troubled by the warning message I get simply trying (and failing) to boot reads 

```
"Display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting 2 minutes..."
```

The kernel messages get to 
```
running local boot scripts (/etc/rc.load)
```
before the display resets and loops back to this point.

I'm writing this from another system, and am not sure even how to go about trying to troubleshoot; any help would be most appreciated. I'll try to describe how I managed to get to this point...

I was simply trying to install an old metronome application I'd used quite some time ago; gtick.

It does not appear in the package manager, nor was I able to find a URL to add to my /etc/apt/sources.list file so that I could use apt-get install. I then tried to build it from source. I've done this before and wasn't afraid; perhaps I should have been.

I downloaded the tarball, extracted it, cd'd to that directory, and and after running ./configure it indicated that it was missing the package gtk+-2.0

I then used synaptic package manager and installed all gtk2 packages I could find. I was still unable to build gtick, so I went to gtk.org.

I dowloaded the latest gtk package (gtk+2.10.9) and similarly began to build IT from source, following the install directions on the site. This stopped and exited, indicating that a few other dependent packages were missing, among them glib and pango (cairo was another, I can't remember the others.)

So I downloaded glib first. I then went into the extracted directory and ran the commands that were suggested for installing the gtk package:

```
./configure
make
sudo make install
sudo ldconfig
```

Make appeared to be a successful build. I tried both of the last two commands as a user before sudo'ing them.

I noticed that after "ldconfig" that my gnome menu options were no longer working. I thought I had seen cairo in the Synaptic package manager before and wanted to install it that way, but was unable to open Synaptic. I tried a few other applications and was similarly unable to open them.

I was still able to use the applications I already had open --I could open new tabs w/in Firefox, for example, but was unable to open another instance of Firefox. None of the /usr/bin/application commands I tried worked either. I think this was when I started to become concerned.

Assuming that my mistake had been ldconfig, I checked the man page for ldconfig. I'm afraid that "configure dynamic linker run time bindings" is a bit over my head, and can't tell from the man page description if this is in fact where I went wrong. So I tried ldconfig -r, and a few other ldconfig options found in the man page that I cannot find now. (If these are important I may be able to dig them out of my bash history they appeared in the man page but do not in the man pages on this (Fedora) system for some reason.)

For some reason I then thought I should restart the system. And now, of course, I cannot even boot this thing. All this for simply trying to install a metronome! I feel a bit foolish.

I don't understand what I managed to, let alone how to go about repairing my system. Any suggestions?

---

### Post by malrost on 2008-02-10
alright, using the recovery mode, I accessed ~/.bash_history

I verified this occured after trying to build glib-2.12.9 from source. 

Hoping to repair whatever damage I may have done w/ ```
ldconfig
```

I read the man pages and then tried the following commands to no avail

```
sudo ldconfig -n
sudo /sbin/ldconfig  -v
sudo /sbin/ldconfig -n /lib
```

And in doing this I somehow messed up my X system? :confused:

I thought widget tool kits could coexist, as well as software libraries (GLib).

---

### Post by jedibrand on 2008-03-04
Has this issue been resolved? I am having similar issues after building and installing glib 2.8.6 (fetched from gtk.org). Like you, my problems started after I relinked my libraries by running ldconfig. In my case, I was attempting to install a beta app called "streamripper", which does exactly that, albeit for a limited stream-format pool. I'm thinking I'll start by looking into gnome dependencies with regards to glib, as well what libraries exactly are tied to glib.

Let me know if you have any luck with this one...it's a dew-zeeh :).

---

### Post by jedibrand on 2008-03-04
So I figured before digging around the tubes I'd given something a try--retracing my steps backwards in taking my gnome out of the predicament I'd gotten into. Guess what, it worked! So, I uninstalled the streamripper app I'd mentioned before (just to be safe--yes, I'm very new to *nix), then proceed to remove glib and reran ldconfig. I made sure to log all the processes save the most important one, ldconfig! Anyhow, for uninstalling/installing just about anything in Ubuntu:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

My guess, and it's very gutsy at that, is that gnome depends on glib for some of the magic it works, or else a lot of stuff on Ubuntu does. In fact, I did an ldconfig -p before going thru the steps I've outlined here, and noticed a bunch of links to glib-2.0. After uninstalling glib 2.8.6 and running ldconfig -p, I found more than a few references to glib, though less than before. 

Anyhow, hope this helps. In closing, take a look at the following post for more info on running multiple versions of glib, as well as appropriate app installation methods using special configuration settings:

[http://ubuntuforums.org/showthread.php?t=608663](http://ubuntuforums.org/showthread.php?t=608663)

---

