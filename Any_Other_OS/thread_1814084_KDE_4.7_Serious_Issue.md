---
title: "KDE 4.7 Serious Issue"
date: 2011-07-28
forum: Any Other OS
---

### Post by laplacian13 on 2011-07-28
I made a duplicate post to this on the openSUSE forums at [http://forums.opensuse.org/english/get-technical-help-here/applications/463438-kde-4-7-serious-issue.html](http://forums.opensuse.org/english/get-technical-help-here/applications/463438-kde-4-7-serious-issue.html) , but I need help as soon as possible for work tomorrow and their forums aren't always as busy.

So I just installed KDE 4.7 via the 1-click installer while I still had the default openSUSE KDE that comes packed with 11.4 installed. I figured the installer would just update from the old one, but I guess I was wrong. There were a ton of dependency issues along the way, butI thought I resolved them (I picked everything that installed over the old files, uninstalled the old files, or installed new things). At the end I got an error that said the installation was partially successful, and that kdebase or kdebase4.7 (I don't remember exactly and can't check now) could not be installed.

Nothing had changed on my desktop so I logged out to log back in, and bam! No more GUI. Okay, that was predictable, I probably just messed something up installing it. I was going to navigate to the 1-click installer file and run it from the command line to fix my problems as the dependency issues would likely no longer be there, but I didn't know the command to run one, so before I restarted and booted into Windows to check I decided to try to just sudo zypper install the kde package I was missing. I was using search to try to find the package and then suddenly my internet cut out.

I restarted my computer to see if the internet would be back on, and then when I started openSUSE there was nothing but an odd grey box in the center asking for my username, a very primitive console in the bottom left, and openSUSE written in bland writing in the background. I tried to log in, but when I do, the screen flashes to a console and text whizzes by too fast to see, and it goes back to the login page. It's not a wrong log in, because if I type something other than my own or root and root's password, it says login incorrect.

Does anybody know how to fix this other than by reinstalling openSUSE? I'd much rather not do that. If I can access the command line I think I can just run the 1-click installed because I've since looked up the command, but I can't think of a way to do it. I also tried the failsafe boot and it does not work either.

---

### Post by madjr on 2011-07-28
hm, i havent had much experience with opensuse lately, but what do you think was the problem, was it a broken dependency or was it that it did not finish installing due to the internet issue?

as for the console i dont really know how to get one, if it were one of the ubuntus i would had given you instructions already, but i'll keep searching see if i can find something for you. Meanwhile keep a live-cd handy just in case.

---

### Post by laplacian13 on 2011-07-28
Exactly the type of quick responses that make me regret switching from ubuntu, fast help is amazing, thank you.


The internet connection didn't cut out while installing, sorry if I was unclear. The kdebase package which I'm assuming is rather important could not be installed even though the old one was uninstalled, is my understanding of the problem. Or at least enough was uninstalled that was not replaced that it is now broken.

It is equally probable that I messed up the dependencies though, to be honest. All in all if I could somehow re-install kde 4.7 I might be set.

I lost internet when I had already lost everything but the terminal...it cut out randomly when it was working.

---

### Post by madjr on 2011-07-28
ok, lets see, i found some posts with some instructions to get a console:

[http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/455595-opensuse-11-4-no-x.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/455595-opensuse-11-4-no-x.html)

[http://forums.opensuse.org/english/get-technical-help-here/64-bit/460931-how-get-login-console-grub.html](http://forums.opensuse.org/english/get-technical-help-here/64-bit/460931-how-get-login-console-grub.html)


hope those help and sorry cant confirm those since i dont currently have opensuse installed...

and yeah lol, i always keep ubuntu as my main distro just because the ease of use and the support is awesome.

anyway when distros get system rollbacks with btrfs (probably next year), recovery will be so much easier, specially on distros that are not as easy nor have the support ubuntu has.

---

### Post by madjr on 2011-07-28
Oh and if you do end up reinstalling (hopefully ull resolve your issue), why not use ubuntu/kubuntu to test out the latest kde... (instructions on kubuntu website)

---

