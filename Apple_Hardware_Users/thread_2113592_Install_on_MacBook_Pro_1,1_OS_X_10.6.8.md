---
title: "Install on MacBook Pro 1,1 OS X 10.6.8"
date: 2013-02-07
forum: Apple Hardware Users
---

### Post by jcocteau on 2013-02-07
Hi,

I have decided to use on of of my old MacBooks (MacBook Pro 1,1 / OS X 10.6.8) to install ubuntu for the first time, its the first intel mac so quite old. I believe i require ubuntu 10.10 maverick but cannot locate, any links would be appreciated.

Did try with Ubuntu 12.04 (Precise Pangolin) but the old thing does not want to know about it.

Thanks

---

### Post by DuckHook on 2013-02-08
Firstly, welcome to the forums.

Hmmm. This one will be a challenge. I like making old HW functional again with Linux, but my experience is with PCs, not Macs. Hopefully, some of the same principles apply.

1. Would not suggest 10.10. If it is not already unsupported, then will lose support in months. Nor would I suggest 12.10. The new kernel no longer supports non-PAE CPUs so will definitely not work on your Mac. I believe that even the new 12.04 kernels require PAE CPUs which would account for your woes with 12.04.

2. You can install Lubuntu (the only lightweight 'buntu distro that has a chance with old HW). However, it also comes with new kernel by default, so you would have to do the following:

a) install non-PAE kernel available from [here]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html") using a special mini-iso. BTW, *WebUPD8.org* is an awesome site for doing odd and unusual things with Ubuntu.

b) ****important**** choose *Lubuntu minimal installation* when you are reach "Software Selection". You must not choose Ubuntu or Xubuntu. These will not run on such ancient HW.

c) choose no other apps. Once a minimal version of Lubuntu is running, you can choose additional packages then. You will have to be very careful and choose only GTK apps. Do not install apps that require Gnome, QT, KDE, etc. These will drag in with them the entire edifice of overhead needed to run Gnome/KDE/Unity, and you are trying to use only apps capable of happily running on mountain air and a song.

3. Drop Ubuntu and use Crunchbang, Puppy, Tiny Core or any of the other dozen distros that eat like a bird. These distros are designed for very old equipment--some are still on the 2.6.x kernels and all have repositories of apps that are perfect for old equipment.

4. Stick with only the command line that comes with the mini ISO and use the machine as a server. You can do amazing things with a laptop because it draws very little power and has built in UPS in the form of its battery. Consider using it for a torrent/file/printer/web/mail/media server. Other alternatives are to explore the command line and install command line-only apps that view e-mail (mutt), surf the web (links2), play music (Mp3blaster), even view pdfs (fbgs).

You will have to live with big compromises because the latest and greatest will be off limits to you: no 3D effects, no desktop cubes, no gimp handling GB-sized files, but you will have resurrected an otherwise hopeless and obsolete machine and made it usable again.

Good luck and happy Ubuntuing

---

### Post by jcocteau on 2013-02-08
Thanks DuckHook for both the welcome and the excellent detailed answer. Just did not want the old beast to go to waste.

 I think I will take my time with this and follow carefully, I will let you know how I get on.

Again thanks.
j

---

### Post by pail on 2013-06-02
Hey jcocteau - do you have any update on what worked / didn't work for you?

I'm fairly new to Linux and about to put a MBP 1,1 out to pasture myself, so anything you've learned could be helpful.

Thanks

---

