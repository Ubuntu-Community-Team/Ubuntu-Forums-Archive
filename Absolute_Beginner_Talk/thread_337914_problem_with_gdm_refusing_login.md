---
title: "problem with gdm refusing login"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Pollywoggy on 2007-01-13
I am having some problems that I am tentatively attributing to kdm, so I installed gdm (Edgy) but gdm denies me a login because of a missing file from the Human Theme.  I even installed the package human-theme but I can't login even after restarting gdm.  Is there a workaround?

---

### Post by crispy_420 on 2007-01-15
I had a similar problem about a week ago (I think in my case I installed a bad gdm theme). But what got me going again was uninstalling gdm, and that took ubuntu-desktop with it. 

So now I was stuck with command line. To get a gui, I typed startxfce to get xfce running. No I could use xfce to do a complete removal of gdm, including config files. Then I just did a reinstall of both gdm and ubuntu.

This is all assuming you have xfce installed. If you don't you can always install from the command line.

There is most likely a better work around. But this worked for me though.

---

