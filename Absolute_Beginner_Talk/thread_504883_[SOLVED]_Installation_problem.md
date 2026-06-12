---
title: "[SOLVED] Installation problem"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Flyvapnet on 2007-07-19
I'm new to Linux, so please don't shoot me!  Here's my problem:  I want to install "firefox-2.0.0.5.tar.gz" but I'm baffled by the protocol, primarily because *it doesn't work*.

I managed to unpack the package, thanks to some code on the Firefox web site; and the result (37 items) now resides in a folder named "firefox," located at "home > flyvapnet [my user name]" along with the original tarball package.  Next I followed as best I could the relevant instructions posted at this message board, describing how to install things, which assert one need only type "sudo aptitude install [name of package or whatever]" -- but when I do that, I'm told no such item can be found.

At first I tried that line of installation code for "firefox," the unpacked (37 items) folder; then when that didn't work I tried it for the original package, "firefox-2.0.0.5.tar.gz."  Both times, lines of code flashed by on the terminal indicating all manner of things were happening; but both times I was ultimately informed nothing had been installed, removed or updated.

Here's what I'd like to know -- minus any diversionary references to long documents, please:  What, exactly, do I type in the terminal to install this package?  I just want to install it, sometime today if possible.

Thank you for your patience and understanding.  Please send positive thoughts my way, so that I too may hopefully acquire patience and understanding sooner rather than later.

:confused:

=^..^=

---

### Post by Rocket2DMn on 2007-07-19
You can install firefox from Ubuntu's repositories:
```
sudo apt-get install firefox
```
You do not have to run from a tarball

---

### Post by Majorix on 2007-07-19
Do you absolutely need 2.0.0.5? 2.0.0.4 is installed by default on your machine...

If you need to install something from the repos in the future, use this:
```
sudo aptitude install *packagename*
```

---

### Post by alienexplorers on 2007-07-19
Get the .gz version of Firefox for Linux.  Move the file to your home folder.  In TERMINAL enter > tar -xvzf firefox-2.0.0.5.tar.gz.
Then go into that file and type ./firefox and see if it runs.  If so you can create a shortcut icon on your desktop for Firefox 2.0.0.5 by entering:> /home/username/firefox/firefox.

---

### Post by Flyvapnet on 2007-07-19
Thank you, **Majorix** and **Rocket2DMn**.  However, the "sudo aptitude install [package name]" command is the one which didn't work before; and the "sudo apt-get install firefox" command results in my being informed the latest edition of Firefox is already installed, which it isn't.

The edition of Firefox presently installed is 2.0.0.4, whereas the latest edition is 2.0.0.5.  Alas, what to do!

:(

=^..^=

---

### Post by Rocket2DMn on 2007-07-19
Apparently 2.0.0.5 is in the repositories yet, but it likely soon will be.  You should probably just wait.
You might be able to check for updates from within firefox as well.

---

### Post by Flyvapnet on 2007-07-19
**Alienexplorers**, thank you.  That first line of code you posted resulted in what appeared to be Firefox 2.0.0.5 being installed; but I don't understand your suggestion to "go into that file"  (I don't know how.) and so I just typed "./firefox" at the next prompt, but nothing happened and the browser is still Firefox 2.0.0.4.

At this point, I think I'll take **Rocket2DMn**'s advice and just wait until this latest edition of Firefox becomes available through the usual Ubuntu channels -- as opposed to being available via the Firefox web site.  It's odd, though, that Firefox provides Linux packages for 2.0.0.5 but the darned things don't work.

Thanks all the same, to all of you!  I appreciate your diving in and trying to help me so quickly.

:)

=^..^=

P.S.:  Problem solved!  Thanks to the repositories, I'm now up to version 2.0.0.6.

---

