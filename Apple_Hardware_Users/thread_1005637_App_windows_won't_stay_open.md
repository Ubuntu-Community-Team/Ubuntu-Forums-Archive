---
title: "App windows won't stay open"
date: 2008-12-08
forum: Apple Hardware Users
---

### Post by doctorbighands on 2008-12-08
I just installed Xubuntu 8.10 on my clamshell iBook. When I go to open many apps (not all of them, though), the window will open for a split second and then immediately close. Any ideas why this is happening, and what to do about it?

Thank you!

---

### Post by adamvan2000 on 2008-12-08
Ditto for me.  It's only certain apps, though there appear to be many of them that do this, including most of the games that are windowed, and my VMware console.  I'm using Ubuntu 8.10 on an AMD64 PC, though, so maybe it's not platform specific?

~adamvan2000

---

### Post by yo.keller on 2008-12-09
> **adamvan2000 said:**
> Ditto for me.  It's only certain apps, though there appear to be many of them that do this, including most of the games that are windowed, and my VMware console.  I'm using Ubuntu 8.10 on an AMD64 PC, though, so maybe it's not platform specific?

~adamvan2000

I just installed the latest xubuntu-810 on a iMac G3 350 Mhz. I am not sure how I was able to get the xfce interface being displayed at each login - instead of getting the Mac to shut down - but I observed that I could not open a terminal window or a file browser or a Firefox window. However, the Xfce parameter management window works well! And within this some of the windows work well, some just cannot stay open:confused:

yo

---

### Post by stream303 on 2008-12-10
Man, this is looking like a somewhat global xubuntu issue.  One way to temporarily solve it is to download the ubuntu-desktop, but of course that will set you up for Ubuntu - at least you should be functional for the time being, and then try switching the desktop back to xubuntu after a few weeks of updates.

Just a thought...

---

### Post by Arylon on 2008-12-10
If you can open a terminal, try launching your applications from it, rather than the gui. I've got regular Ubuntu here, but every time an app quits without warning, it will put useful info back to the command line, but only if it was launched from the command line to begin with.

---

### Post by Leslie Viljoen on 2008-12-10
It's the infamous segmentation fault problem. You'll see that the apps you are trying to run will give you a "segmentation fault" if you run them in a terminal. I was able to fix the problem by recompiling the affected packages. 

So there are two known solutions:
1. Get recompiled packages or recompile them yourself
2. Try Debian

At the risk of sounding like a broken record, we have documented this problem (and solutions) here:
[http://www.ppclinux.info/wiki/maclin/Ubuntu_Kubuntu_and_Xubuntu](http://www.ppclinux.info/wiki/maclin/Ubuntu_Kubuntu_and_Xubuntu)

Look under "known issues". We also have a page for Debian, and a "known issue matrix" that might be helpful in surveying what problems you might encounter when choosing a distribution.

Les

---

### Post by Leslie Viljoen on 2008-12-10
BTW: I'm going to move the packages to [www.ppclinux.info](www.ppclinux.info) too. This should make downloading easier, and I'm also going to try and set up a repository on that server so that installing fixed packages is as seamless as possible.

---

### Post by Leslie Viljoen on 2008-12-10
Ok, I have attempted to add a repository to our ppclinux server. Can someone please help to test it?

You need to go to Synaptic:
  -> Settings -> Repositories -> Third-Party Software -> Add

..and add the following APT line:
deb [http://www.ppclinux.info/repo](http://www.ppclinux.info/repo) binary/


Then update, and see if you can install the updated xfdesktop and thunar packages. Let me know how it goes!

---

### Post by Leslie Viljoen on 2008-12-10
If you do try and add my repository, you might need to add my public key to your keyring to verify that it was really me that made the packages.

This is how to do that:
wget -q [http://www.ppclinux.info/repo/leslieviljoen-key.gpg](http://www.ppclinux.info/repo/leslieviljoen-key.gpg) -O - |sudo apt-key add -

If anyone tries the repository please give me feedback on what you had to do and how it went. I want to try and make it as easy as possible to put Xubuntu in a working state.

---

