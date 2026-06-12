---
title: "Using apt-get to insyall new programs"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by racsw on 2006-02-16
Hi,
  Not sure if I should be here to ask this, but I'm not new to Linux, only Umbutu.
I saw a lot of threads from people having various levels of difficulty getting programs from repositories using apt-get, which I have never used.
  I simply want to retrieve programs that I need to install, like emacs, and get it on the computer in the simplest fashion possible.
  In Suse, you simply typed in what you wanted, and it would let you know if the repository had it, and if so, it would download and install it.  If not, then you'd simply do it the old fashioned 3 step way.
  Can you point me to a reliable document that lays out whatever similar procedure applies to Umbutu?

Thanks,
Robert

---

### Post by LanceM on 2006-02-16
Check out section 2.

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by carlosqueso on 2006-02-16
From Aysiu's signature: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by az on 2006-02-16
[QUOTE=racsw]Hi,
  Not sure if I should be here to ask this, but I'm not new to Linux, only Umbutu.
I saw a lot of threads from people having various levels of difficulty getting programs from repositories using apt-get, which I have never used.
  I simply want to retrieve programs that I need to install, like emacs, and get it on the computer in the simplest fashion possible.[/QUOTE]

That is what apt is for.

  [QUOTE=racsw]In Suse, you simply typed in what you wanted, and it would let you know if the repository had it, and if so, it would download and install it.  If not, then you'd simply do it the old fashioned 3 step way.
  Can you point me to a reliable document that lays out whatever similar procedure applies to Umbutu?

Thanks,
Robert[/QUOTE]

Just run synaptic.  It is a GUI frontend to apt.  Click search and install.  If you cannot find a package, add the universe repository (click on repository)  It will update it's database and if you search again, you probably will find your package.

I beleive there are over 13000 packages in the main and universe repos.

If you want to use the command line

apt-cache search emacs.
sudo apt-get install emacs

There.  You've used apt.

---

### Post by racsw on 2006-02-16
I just tried it, and my thanks to you folks, truly.

One question:  It keeps asking me to insert the Umbutu Breezy Badger CDROM.
So I keep clicking, and it then goes onto the web somewhere and gets the file, but for each program, it keeps bring up the CDROm file manager.

Can we get this deleted so it goes to the repositories first?
This is working pretty cool, and I do like it. Nice job.

Thanks again,
Robert

---

### Post by racsw on 2006-02-16
I figured out the cdrom thing, so that's fixed, and adding Universe and multiVerse works great.
Nice job guys, thank you.

Robert

---

### Post by aysiu on 2006-02-16
Sure.

```
sudo nano /etc/apt/sources.list
``` The CD repository is probably the first in the list. Just put a # sign in front of that line (or delete the line completely). Then save (control-x), confirm (y), and exit (Enter).

---

### Post by racsw on 2006-02-16
Before you guys disappear, I installed Emacs using Synaptic.
I can't find the bugger anywhere.  It is installed, that I checked, but I figured if Synaptic installed it, it would also put it into the menu structure.
Not so?


Robert

---

### Post by rvener on 2006-02-16
I am new to linux and Ubuntu, and had trouble with Synaptic. Automatix is another graphical utility that very easily allows you to install programs.  I found it in this forum somewhere.  Search for Automatix.  There were instructions to install it, about 5 typed lines, and then everything I wanted was listed......

---

### Post by mcduck on 2006-02-16
[QUOTE=racsw]Before you guys disappear, I installed Emacs using Synaptic.
I can't find the bugger anywhere.  It is installed, that I checked, but I figured if Synaptic installed it, it would also put it into the menu structure.
Not so?


Robert[/QUOTE]
Most of GUI apps should be added to menu automaticly. You could try 'killall gnome-panel' to reload menus. If it doesn't still show up, you'll have to add it yourself. CLI apps of course are not added to menu.

I haven't used emacs but I recall it's CLI app, so you should be able to launch it by running 'emacs' in terminal.

---

### Post by Lord Illidan on 2006-02-16
[quote=racsw]Before you guys disappear, I installed Emacs using Synaptic.
I can't find the bugger anywhere.  It is installed, that I checked, but I figured if Synaptic installed it, it would also put it into the menu structure.
Not so?


Robert[/quote]

Very few programs get put in the menus, unfortunately.. When you install something, your best bet is to use the terminal to launch it.
Hint : When you go into the terminal, there is no need to type emacs in full. Just type <em> and then press <TAB>. The shell will then either autocomplete the command or give you a list.

---

### Post by racsw on 2006-02-16
Originally, I used Synaptic to get and install Emacs, which didn't work.
So I used "apt-get install emacs21", and not only did it install it, but it was added to the menu structure.
cool...

One thing: I noticed I was getting all these error messages from apt-get involving a repository beginning with "couldn't stat source package list [http://security.umbuntu.com_umbutu_dists_breezy](http://security.umbuntu.com_umbutu_dists_breezy)... -stat - (2 No such file or directory)
About 7 of them for emacs.

Thanks,
Robert

---

### Post by Lord Illidan on 2006-02-16
[quote=racsw]Originally, I used Synaptic to get and install Emacs, which didn't work.
So I used "apt-get install emacs21", and not only did it install it, but it was added to the menu structure.
cool...

One thing: I noticed I was getting all these error messages from apt-get involving a repository beginning with "couldn't stat source package list [http://security.umbuntu.com_umbutu_dists_breezy]("http://security.umbuntu.com_umbutu_dists_breezy")... -stat - (2 No such file or directory)
About 7 of them for emacs.

Thanks,
Robert[/quote]

You either have a spelling mistake in your sources.list - umbuntu.com sounds like one.
Post your /etc/apt/sources.list so we can check it.

And do ```
sudo apt-get update
``` when that happens.

---

### Post by racsw on 2006-02-16
Here you go:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Robert

---

