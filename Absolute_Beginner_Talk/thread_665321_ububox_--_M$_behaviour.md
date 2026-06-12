---
title: "ububox -- M$ behaviour?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by pifpafpuf on 2008-01-12
Just stumbled over ubufox after an update to Gutsy. Well, ok, there  is a firefox plugin I did not ask for. Seems to be from ubuntu, so it should be ok. What does it?

So I did a 

% dpkg -s ubufox
...
 modifications for ubuntu firefox (default) install
 Extension package for firefox, that ships various modifications
 for the ubuntu default install of firefox.

Wow, great. This helps a lot, doesn't it? 

Rather it reminds me of the nonsense you get with pay-a-lot-for operating systems that tell you to be calm, everything is done for you, don't ask questions, obey. And then they really screw you.

Well, at least the above message mentions that I can savely uninstall. And I think this is a good thing to do for a tool that tells you it is just great without being anymore specific. The suspiscion is, of course, that the only thing it does just great is to call home.

Is this the future of ubuntu?

Is there anywhere an understandable specific description in the ubuntu system about what ubufox does?

Harald.

---

### Post by mister_pink on 2008-01-12
Its nothing sinister! I think it just integrates firefox into your desktop better. What this really means I'm not sure, I guess it might be to do with bookmarks or the graphics. I imagine its done as an extension rather than editing the source so that they don't need permission from mozilla. As it says, if you don't want it its safe to remove. And now the great thing about open source software? There's no way it can call home or anything without someone knowing because the source code is all available [http://packages.ubuntu.com/gutsy/source/ubufox](http://packages.ubuntu.com/gutsy/source/ubufox)

Edit: Looking at it again, I think the changes are just things like that little link in the addons box that says "get ubuntu addons" and some things in the help menu, like translate this.

---

### Post by mikeyphi on 2008-01-12
> **pifpafpuf said:**
> Just stumbled over ubufox after an update to Gutsy. Well, ok, there  is a firefox plugin I did not ask for. Seems to be from ubuntu, so it should be ok. What does it?


Is there anywhere an understandable specific description in the ubuntu system about what ubufox does?

Harald.

I had a look around but couldn't find a definitive description - however, the utility only provides an easier means of installing Ubuntu versions of popular plug-ins for Firefox. You are free to use ubufox or install via Firefox - as always in Ubuntu the choice is yours!!!!!

---

### Post by Paqman on 2008-01-12
AFAIK it just provides an interface between Firefox and apt-get, allowing the extensions to be integrated into the normal package managing system.

---

### Post by GavinZac on 2008-01-12
Its an extension which installs Firefox Add-ons in a similar manner to how Synaptic works, in order to create a seamless feel to the operating system.

Many, many software packages in the Ubuntu repository are edited specifically to work better with Ubuntu, you can recognise them by their having -ubuntu tagged onto their version number. There is nothing sinister about that, and it is partially what makes ubuntu run so great. The only difference here is that it is with a highly visible program and they actually gave you the option to disable it if you so choose.

Don't be so quick to put ubuntu and microsoft in the same sentence ;)

---

