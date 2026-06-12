---
title: "Bootcamp - default OS?"
date: 2007-07-02
forum: Apple Intel Users
---

### Post by grim1234 on 2007-07-02
Is it possible to set the bootcamp loader to load ubuntu (windows) as default?

---

### Post by ivesjd on 2007-07-02
I'm not sure but you can with rEFIt.

---

### Post by grim1234 on 2007-07-02
is it possible to install refit without reinstalling either osx or ubuntu?

---

### Post by ronocdh on 2007-07-02
> **grim1234 said:**
> is it possible to install refit without reinstalling either osx or ubuntu?
Absolutely. In fact, you _should_ install it after OS X! Go [here]("http://refit.sf.net"); there's a package installer for OS X, installs just like anything else.

Also, I think that in the System Preferences, there'll be a panel called "Startup Disks." On my triple boot setup, though, it apparently only recognizes OS X and Windows XP. Bah.

---

### Post by cyberdork33 on 2007-07-02
> **ivesjd said:**
> I'm not sure but you can with rEFIt.

You can?

---

### Post by ivesjd on 2007-07-02
> **cyberdork33 said:**
> You can?

You can configure rEFIt to default to legacy. With a dual-boot that puts Ubuntu first. I dont remember how to do it though, but its not hard.

---

### Post by ivesjd on 2007-07-03
If you edit the refit.conf file in /efi/refit/ (mac side) you can change alot of options. Timeout, legacy first, even the images. I think it is supposed to get even more configureable in the future.

---

### Post by cyberdork33 on 2007-07-03
yes I checked this out last night. not quite configurable enough, but allows you to keep OSX from being the default.

---

