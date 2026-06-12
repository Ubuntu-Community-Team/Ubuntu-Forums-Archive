---
title: "[SOLVED] Launch browser, launch e-mail hotkeys are now messed up in Gutsy Gibbons"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-10-19
I've bound control+shift+F and control+shift+E to Firefox and Thunderbird respectively through System -> Preferences -> Keyboard Shortcuts.  They worked fine in Feisty Fawn.

However now whenever I try to open the browser with the shortcut it takes me to file:///home/username as the home page.  Whenever I try to open my e-mail client it says: Couldn't execute command: mozilla-thunderbird.  Verify that this is a valid command.

(/usr/bin/thunderbird exists, mozilla-thunderbird used to be a shell script generated to launch thunderbird).

---

### Post by Billy_McBong on 2007-10-19
[COLOR="Blue"]i think the command is thunderbird now not mozilla-thunderbird
and you can just change the homepage:roll:[/COLOR]

---

### Post by AncientPC on 2007-10-19
I can manually launch Thunderbird, but I want to do so through a hotkey.  However, System -> Preferences -> Keyboard Shortcuts -> Launch E-mail Client -> mozilla-thunderbird.  How do I change Launch E-mail Client to not open mozilla-thunderbird but to /usr/bin/thunderbird instead?

As for the browser, the shortcut is passing the argument file:///home/username to the browser so it opens up extra pages which I don't want.

---

### Post by Frak on 2007-10-19
You need to set System->Preferences->Prefered applications to the thunderbird you want to run.

For the browser, put the url after it ex.
firefox [http://www.google.com](http://www.google.com)
instead of just
firefox

---

### Post by AncientPC on 2007-10-19
Thank you Frak, that was exactly what I was looking for.  I realized that the hotkey was still pointing to Thunderbird v1.5, while Gutsy upgrade removed/installed Thunderbird v2.0 but didn't update the hotkey.

Same thing with the preferred browser.

Now I just need to find out how to install Thunderbird v1.5 again . . .

---

### Post by rlelina on 2007-10-19
So you're seeing Thunderbird? I just did a new install of Gutsy and I can't see Thunderbird anywhere. When I manually installed it, it won't run because it's looking for libstdc++.so.5. Gutsy has libstdc++.so.6.

Any suggestions on how I should proceed? Thanks.

---

### Post by Frak on 2007-10-19
Try swiftdove: [http://swiftweasel.wiki.sourceforge.net/Swiftdove](http://swiftweasel.wiki.sourceforge.net/Swiftdove)

---

### Post by AncientPC on 2007-10-19
> **rlelina said:**
> So you're seeing Thunderbird? I just did a new install of Gutsy and I can't see Thunderbird anywhere. When I manually installed it, it won't run because it's looking for libstdc++.so.5. Gutsy has libstdc++.so.6.

Any suggestions on how I should proceed? Thanks.
I suppose I was able to download and re-install TB 1.5 because the libraries were already on my system, but if your trying to install 2.0 have you simply tried the official repositories?  (i.e. "sudo aptitude install thunderbird", It should handle the library dependencies.)

---

