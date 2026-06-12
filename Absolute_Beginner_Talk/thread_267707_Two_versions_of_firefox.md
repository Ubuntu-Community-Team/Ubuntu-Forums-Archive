---
title: "Two versions of firefox?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Boatswain on 2006-09-29
I'm not entirely sure how this happened, but I appear to have two versions of firefox set up.  If I use the pre-provided shortcut or type 'firefox' at the terminal, I get 1.5.0.2, whereas if I close any currently running instances of firefox and run  usr/bin/firefox.ubuntu I get 1.5.0.7 with the Ubuntu firefox start page.  How do I get rid of just the old version and make the new one the default?

Thanks!

---

### Post by aysiu on 2006-09-29
Did you install Firefox from the Mozilla website at all? And, if so, how did you "install" it?

P.S., if you're using Gnome, you *really* don't want to "get of... the old version," but you can certainly "make the new one the default."

---

### Post by Boatswain on 2006-09-29
> **aysiu said:**
> Did you install Firefox from the Mozilla website at all? And, if so, how did you "install" it?

P.S., if you're using Gnome, you *really* don't want to "get of... the old version," but you can certainly "make the new one the default."

I did at some point install Firefox from the mozilla website, downloading the tarball and extracting it, etc.  I think it's updated since then automatically--I just noticed this whole thing the other day, but I imagine it's been this way for a while.                                                                        

So the question is how do I make 1.5.0.7 the default, I guess.  And why do I not want to get rid of 1.5.0.2, as long as I keep my preferences, extensions, bookmarks, etc around?

Thanks again

---

### Post by aysiu on 2006-09-29
I really can't tell you how to make 1.5.0.7 the default unless I know *exactly* what you did to install it and that you're absolutely sure that 1.5.0.7 is the Mozilla version and 1.5.0.2 the Ubuntu version.

Truth be told, even Ubuntu's version is up to 1.5.0.7 at this point. I don't know why you're still at 1.5.0.2.

As for not removing it, it's because the way Ubuntu has packaged Firefox, a lot of things in Gnome are dependent on Firefox's rendering engine. Are you hard-up for hard drive space?

---

### Post by Boatswain on 2006-09-29
Well, it looks like modifying the symlink to run 'firefox.ubuntu' rather than 'firefox %u' does the trick--what is the '%u' bit all about, anyway?

As for the disk space--well, I'm running on a laptop, so space is a bit more precious to me than it would be on a desktop.  Plus, I just like to get rid of things I don't need.  It's like cleaning up after myself.  Not that I do that in the real world too much...

Thanks for the help, anyway!

---

### Post by johndoe32102002 on 2008-03-26
I need to install two versions of Firefox.  I am running Ubuntu Hardy.  Hardy installs Firefox 3.0b.  Whenever I try to install Firefox 2.0.x or SwiftFox 2.0.x, and run "firefox" or "swiftfox" from terminal, it pulls the Firefox 3.0b up.  I need Firefox 2.0.x because it is compatible with certain addons that I need to use (GSpace).  Please help.

In the past when I use apt-get, aptitude, adept, dpkg, or synaptic to install *.deb files, it only allows me to install one version: the latest.

Thanks.

---

### Post by glennric on 2008-03-26
> **johndoe32102002 said:**
> I need to install two versions of Firefox.  I am running Ubuntu Hardy.  Hardy installs Firefox 3.0b.  Whenever I try to install Firefox 2.0.x or SwiftFox 2.0.x, and run "firefox" or "swiftfox" from terminal, it pulls the Firefox 3.0b up.  I need Firefox 2.0.x because it is compatible with certain addons that I need to use (GSpace).  Please help.

In the past when I use apt-get, aptitude, adept, dpkg, or synaptic to install *.deb files, it only allows me to install one version: the latest.

Thanks.

You should start a new thread if you want to get help on these things.  This thread is nearly two years old.  Here is a link on how to do what you are asking: [Firefox New Version]("https://help.ubuntu.com/community/FirefoxNewVersion")
I have attached a script that will do it all for you.
Download the version of firefox in tar.gz form and gunzip the attached script in the same directory as the tarball of firefox.  Then type
```
sudo ./firefox-new-version firefox-tarball-filename.tar.gz
```
Then if you type firefox in the terminal or click on a firefox launcher you will get the version you installed with the script.

---

