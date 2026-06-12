---
title: "Cannot run Automatix2"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by jopv on 2007-06-09
I'm running Fiesty and have a problem running Automatix2. It was updated via update manager but it does not run anymore.  I get an error message that says the version is for Edgy.  I downloaded the version for Fiesty but when I try to install it I get an error message that says I'm running a newer version.  I'mconfused and need help.

---

### Post by confused57 on 2007-06-09
There's probably a getautomatix Edgy version in your sources.list, you need to delete this entry & then try to install Automatix2 for Feisty:
Open a terminal:
```
cd /etc/apt
sudo cp sources.list sources.list_backup
gksudo gedit sources.list
```

scroll down to the getautomatix repo, it's probably for Edgy...you could just place a # in front of it or delete it....then you should be able to install Automatix2 for Feisty.

I'm not sure if you'd need to remove the Edgy Automatix2 before editing your sources.list.

```
sudo apt-get remove automatix2
```

On second thought it might be best to remove automatix2, then remove the entry in your sources.list, then try to install Feisty automatix.

---

### Post by Madpilot on 2007-06-09
Automatix is best avoided - it's a good way to break things, especially when the time comes to upgrade to a new release of Ubuntu.

What're  you trying to install thru Automatix? I guarantee it's installable without risking automatix on your machine... check some of the links in my sig, for starters.

---

### Post by jopv on 2007-06-09
Thanks All - I've got the feist running againy version running again

---

### Post by jopv on 2007-06-09
There were certain applications I tried to instal but couldn't and then I used Automatix and it did it straight away.  Are you saying I can do the same thing via Synaptic Package Manager?

---

### Post by ramjet_1953 on 2007-06-09
There tends to be two camps regarding Automatix.

Some people say that it can break your system, some say it doesn't.

Personally, I think it has a lot to do with your individual hardware and setup.

Automatix works for the vast majority of people, who just want a system to work and are not interested in looking "under the hood".

Nevertheless, there are now some good guides avalaible on this forum for setting-up your system, for things like codecs, without using Austomatix.

That's what is great about Linux -- choice.

Regards,
Roger :cool:

---

