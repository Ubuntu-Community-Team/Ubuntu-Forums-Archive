---
title: "bold fonts in firefox with Ubuntu 10.10"
date: 2010-12-15
forum: Art &amp; Design
---

### Post by gamblor01 on 2010-12-15
I just recently upgraded my machine from 9.10 to 10.04 and then to 10.10.  I'm not really sure which of the two upgrades "broke" the fonts but they are hideous now.  I went to System -> Preferences -> Appearance -> Fonts and changed the default size from 11 to 10 which seemed to help a bit through gnome/nautilus/etc.

Unfortunately, the fonts in Firefox are just downright terrible.  For some reason everything is insanely bold and hurts to look at.  See the attachment for an example of what gmail looks like with some bogus account I just made.  I have tried changing the preferences in Firefox to "allow pages to choose their own fonts" but even with that option set, it doesn't seem to do anything.

Anyone know how I can fix this?  As far as I know the only modifications I have made were to install the msttcorefonts back in 8.10 or maybe 9.04?  This box has been upgraded several times over the past few years so I don't really remember when I installed that package...


Has anyone else experienced this?  Can anybody help?  I'm almost unable to use my machine at the moment because the fonts are so unbearable.  :(

---

### Post by gamblor01 on 2010-12-15
Well I seem to have fixed the bold font issue by uninstalling msttcorefonts and then reinstalling it (though it has since been renamed to ttf-mscorefonts-installer).  After doing that and then restarting X the bold font issue is resolved.  Unfortunately the fonts are still hard to read.  Here are some examples of screenshots from random webpages that illustrate the issue.

Anyone know how to fix this?  I have been in the font config changing the values like crazy in there and nothing seems to help.  I have 10.10 installed on my work computer and it looks beautiful, though that was a clean install and not an upgrade.  It's also a different monitor and resolution as well.  Both are using the 260.19.06 nvidia driver though...

---

### Post by gamblor01 on 2010-12-19
Well I have fixed some of this stuff just by playing around with the fonts in Firefox.  I noticed that using Opera the fonts all looked very nice, so I just set Firefox to use the fonts I desired instead of letting pages define their own.  Then I played around with the fonts being used and the sizes of them.  Things are definitely not as good as they were in 9.10 but are considerably better.

I think this has something to do with my resolution or something because the fonts on my work computer look great.  I guess I'll just keep playing with things and hopefully I fix everything.

---

