---
title: "azureus totally ****** up"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by elustran on 2007-06-28
my azureus was being a little buggy - it would appear to be working for a while, then my download and upload speeds would cut down to zero.  Not to go into too much detail, I tried a few things to get it working, but to no avail.  So, if all else fails, reinstall, right?

Wrong... I tried uninstalling azureus from the add/remove function in the applications menu and then reinstalling, only to find that azureus would stop working immediately after start.  I tried uninstalling again, and checked to see if the azureus directory was still there - it was, along with its contents.  I tried uninstalling via the synaptic package manager, which didn't work, so I finally deleted the directory manually, hoping that I wasn't going to miss something, and then reinstalled it.

I'm still getting the same general problem - Azureus fails right after the load bar finishes, briefly flashing the first configuration window.  I'm getting no error messages.

Ideally, I'd like to get azureus to work, but if I can't, I just want to make sure it's completely gone from my system.  I would appreciate any help

---

### Post by chandler on 2007-06-28
What java version do you have installed?  Does your ISP have bandwidth caps or a policy against P2P traffic?  Do the color of the smiley faces change when running fine and not?  (Green to red, constant blue, etc)

---

### Post by Rocket2DMn on 2007-06-28
if you run "azureus" from terminal you will see the errors.  A lot of problems have been fixed by cleaning out the azureus logs in ~/.azureus/
You can get their in nautilus by going to your home folder, hitting ctrl+h to show hidden files, and entering the folder called ".azureus"

---

### Post by viciouslime on 2007-06-28
For some reason the ubuntu version of azureus is modified and has been pretty broken ever since breezy. The best thing to do is install the package again, then manually download this file: [http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.4.jar?download]("http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.4.jar?download")

Then, using sudo so as to be able to write to the correct directory, overwrite /usr/share/java/Azureus2.jar with the file I have linked to for you. You'll have to rename the downloaded file to "Azureus2.jar" too.

Hope that helps...

---

### Post by elustran on 2007-06-29
> **chandler said:**
> What java version do you have installed?  Does your ISP have bandwidth caps or a policy against P2P traffic?  Do the color of the smiley faces change when running fine and not?  (Green to red, constant blue, etc)
I have java version 5 installed, and I don't think my ISP has any p2p policies in place - I've never had real problems before.  When azureus was still loading, the NAT would be red, and the distributed database would be yellow, but they'd both turn green after a couple minutes.  Several minutes after that, my speeds would drop to zero, but my lights would still be green.

Back when there was a windows box here using utorrent, there were no significant problems, though sometimes the internet connection would go out and we'd have to reset the modem.  Because of that, in azureus, to make sure I wasn't stressing my internet connection, following the azureus wiki, I made sure that settings like my maximum connections were set appropriately for my bandwidth, but I still had problems.

---

### Post by elustran on 2007-06-29
> **viciouslime said:**
> For some reason the ubuntu version of azureus is modified and has been pretty broken ever since breezy. The best thing to do is install the package again, then manually download this file: [http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.4.jar?download]("http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.4.jar?download")
.
The issue from before was that I was unable to reinstall azureus - attempting to remove the package from add/remove or from synaptic package manager would still leave the original files there before trying to install azureus again, I would like to make sure that everything that the package installer placed in the first place is gone.  Previously, I  tried removing the .azureus folder manually, but that didn't work.  Are there any other directories or files that get installed by the package manager?  I recall reading somewhere that, as a java program, azureus should only install into one folder, but I'm not sure I trust that, since I've continued to have problems.

I hope the fix you've offered will work, but I want to make sure I've reinstalled the software properly.

Alternately, is it even worthwhile trying to get azureus to work, or should I just scour it from my system and use something like Deluge instead?

Thanks for your help.

---

