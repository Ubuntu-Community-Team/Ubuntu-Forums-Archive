---
title: "How to reinstall firefox with Ubuntu defaults? (ubufox not working)"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by vectorial on 2008-04-08
Hello, everyone! I'm a brand-new Ubuntu user; I just installed it last night.   I'm really happy to be done with Windows. 

I'm having a problem with Firefox; my end goal is to get it set up just as it was when I first installed it last night.  I want to use Firefox as my main browser.  I installed the NoScript, Adblock Plus and Filterset.G Updater extensions.  Then, later, I installed Amarok, which slowed down my system considerably.  I uninstalled Amarok, and now my Ubufox extension does not work.  (I don't know if the Amarok uninstall caused this).  If I navigate from Tools > Add-ons and then click the Extensions tab, there is a link at the bottom right for "Get Ubuntu Add-ons".  When I first used Firefox in Ubuntu, there were many links in the window that appeared.  Now, I get an error message: "There is no matching application available.
To broaden your search, choose "All available applications" or "All Open Source applications"."

The way I tried to fix this was first to uninstall Ubufox, logout/in, then reinstall it.  It didn't work.  Then I tried a "complete" uninstall of Ubufox, logout/in, and reinstall.  That did not work.  So finally (even though I probably should not have) --  I uninstalled Firefox entirely ("complete" uninstall), logout/in, reinstalled Firefox, logout/in, and reinstalled Ubufox.  It still does not work, and now I am pretty sure that when I uninstalled Firefox that whatever version I installed is not exactly the same as the one that came with the OS.

So, after all that, what I want is to get FIrefox to exactly the way it was when I first installed Ubuntu.  How do I do that?  I just want all the components that come with it, and I want Ubufox to work.  Please help.  Thanks very much for your help!

---

### Post by soundalike on 2008-04-08
Hi there

Thought I'd give your thread a bump because I have the same question.  I've ditched Windows and installed Ubuntu but over the past few days I've managed to make it increasingly unstable.  I want to re-install and start again from scratch - but with out losing my data.

Can someone point me to an idiot's guide?

Cheers
Richard

---

### Post by wolfen69 on 2008-04-08
completely remove firefox or whatever, then
```
sudo apt-get clean
```
*then* re-install.

---

### Post by joe.turion64x2 on 2008-04-08
Hello Richard.

There is this hidden folder named .mozilla (note the dot) in your home folder, and there is a folder inside named firefox. If you remove that folder the settings you customized will be gone.

Hope that helps.

Thanks.
Joe.

---

### Post by Moop on 2008-04-08
> **vectorial said:**
> Hello, everyone! I'm a brand-new Ubuntu user; I just installed it last night.   I'm really happy to be done with Windows. 

I'm having a problem with Firefox; my end goal is to get it set up just as it was when I first installed it last night.  I want to use Firefox as my main browser.  I installed the NoScript, Adblock Plus and Filterset.G Updater extensions.  Then, later, I installed Amarok, which slowed down my system considerably.  I uninstalled Amarok, and now my Ubufox extension does not work.  (I don't know if the Amarok uninstall caused this).  If I navigate from Tools > Add-ons and then click the Extensions tab, there is a link at the bottom right for "Get Ubuntu Add-ons".  When I first used Firefox in Ubuntu, there were many links in the window that appeared.  Now, I get an error message: "There is no matching application available.
To broaden your search, choose "All available applications" or "All Open Source applications"."

The way I tried to fix this was first to uninstall Ubufox, logout/in, then reinstall it.  It didn't work.  Then I tried a "complete" uninstall of Ubufox, logout/in, and reinstall.  That did not work.  So finally (even though I probably should not have) --  I uninstalled Firefox entirely ("complete" uninstall), logout/in, reinstalled Firefox, logout/in, and reinstalled Ubufox.  It still does not work, and now I am pretty sure that when I uninstalled Firefox that whatever version I installed is not exactly the same as the one that came with the OS.

So, after all that, what I want is to get FIrefox to exactly the way it was when I first installed Ubuntu.  How do I do that?  I just want all the components that come with it, and I want Ubufox to work.  Please help.  Thanks very much for your help!

Your firefox preferences are stored in a hidden folder in your home directory. Uninstalling Firefox doesn't delete that folder so when you reinstall Firefox it picks up all your old configuration data. Uninstall Firefox and then go to your home directory and enable viewing of hidden files, then delete the .mozilla folder. Now you can do a fresh install of Firefox. I'm not sure what ubufox is but the same should apply to it.

---

### Post by very_japi on 2008-04-08
YOu may want to backup ou bookmarks before deleting the .mozilla folder, it would go like this:

Backup bookmarks

in a terminal run: sudo rm -R .mozilla
Or... graphically: Go to your home folder in nautilus and pres ctrl+H and a bunch of hidden folders will appear

Find the one named .mozilla and delete it.

---

