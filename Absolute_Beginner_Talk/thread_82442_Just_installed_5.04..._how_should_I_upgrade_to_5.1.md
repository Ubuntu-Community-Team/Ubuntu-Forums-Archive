---
title: "Just installed 5.04... how should I upgrade to 5.10? (Solved)"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by Sunnz on 2005-10-26
Hello there,

I am a new user of UBuntu, I ordered the CD sometime ago and I haven't got the time to try it untill now. And after installation, I realise a new one has come out.

Well, is it possible to upgrade without getting another CD?

I had looked at [https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28upgrade%29) but I never used debian or apt before, so I don't really know...

I have some experience from Fedora Core and Gentoo... and their package manager (yum and portage.) however, I am completely new to ubuntu.

Please give me some pointers of what should I do now, as I am standing here quite confused... thank you!

---

### Post by aysiu on 2005-10-26
Follow the instructions here:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

and make sure you choose the **breezy** list, not the hoary one.

Then type this in a terminal ```
sudo apt-get update
sudo apt-get dist-ugprade
``` There--you're done.

---

### Post by Sunnz on 2005-10-26
Ohhhh it is that easy? Thank you very much for your timely reply!!! :)

---

### Post by Sunnz on 2005-10-27
Just two more questions:

Would the update via apt-get update the kernel as well? Or do I need to download the source and build it by hand?

Is there any guide to use apt? I want to install thunderbird and stuff...

Thanks again.

---

### Post by aysiu on 2005-10-27
*apt-get update* just updates the database of what the available packages are and what versions you have installed versus what's in the repositories.

*apt-get upgrade* upgrades the packages you have currently installed.

*apt-get install* installs a package

*apt-get remove* removes a package

*apt-get dist-upgrade* upgrades to the latest distro version (often also upgrading the kernel)

For more info, type ```
man apt-get
``` in a terminal

---

### Post by Sunnz on 2005-10-27
So how can I search for a specific package? I tried apt-get install thunderbird but it said that it can't find it...

---

### Post by Xian on 2005-10-27
[QUOTE=Sunnz]So how can I search for a specific package? I tried apt-get install thunderbird but it said that it can't find it...[/QUOTE]
Like this:

```
$ sudo apt-cache policy mozilla-thunderbird
mozilla-thunderbird:
  Installed: (none)
  Candidate: 1.0.7-0ubuntu05.10
  Version table:
     1.0.7-0ubuntu05.10 0
        500 http://us.archive.ubuntu.com breezy-updates/main Packages
     1.0.7-0ubuntu1 0
        500 http://us.archive.ubuntu.com breezy/main Packages
```

Or you could:

```
$ sudo apt-cache search thunderbird
mozilla-thunderbird - Mozilla Thunderbird standalone mail client
mozilla-thunderbird-dev - mozilla thunderbird development files
mozilla-thunderbird-inspector - mozilla thunderbird dom inspector extension
mozilla-thunderbird-offline - mozilla thunderbird offline extension
mozilla-thunderbird-typeaheadfind - mozilla thunderbird typeaheadfind extension
mozilla-thunderbird-enigmail - Enigmail - GPG support for Mozilla Thunderbird
```

---

### Post by aysiu on 2005-10-27
Or you could just use Synaptic, the graphical frontend for apt-get. See the second link in my sig for more details.

---

### Post by Sunnz on 2005-10-27
Oh ok... what about apt-cache search?

Well Synaptic wouldn't let me, installing thunderbird with apt at the moment! :p

Thanks for the help guys.

---

### Post by Sunnz on 2005-10-27
Umm... finished the installation... what does this mean:
```
Updating mozilla-thunderbird chrome registry...find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.
```

---

### Post by Quirky on 2005-10-27
It's just a warning, no need to worry. Really! 

It is a small "bug" in the script but nothing dangerous. It seems 'find' has added a warning for this situation:

find . -name "foo" -maxdepth 1

and it should now be written as follows to avoid seeing the message, though the find will work as expected if you do it the previous way:

find .  -maxdepth 1 -name "foo"

So this script has not been updated.

---

### Post by Sunnz on 2005-10-27
Oh I see, thanks for the help!

---

