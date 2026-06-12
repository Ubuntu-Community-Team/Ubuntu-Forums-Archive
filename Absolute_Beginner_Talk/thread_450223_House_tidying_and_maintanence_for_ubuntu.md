---
title: "House tidying and maintanence for ubuntu?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-21
Are there any tasks that I should perform to keep ubuntu ticking along nicely?

Coming from a Windows environment I am used to performing tasks such as defragging, virus checks and the like.  Are such tasks redundant for ubuntu?

Chhers

---

### Post by justleen on 2007-05-21
THe two tasks you named, yes.
Personally, i check my Trash every now and then, and /var/cache/apt (this is where all the downloaded packages go)  to keep my disk space on track..

---

### Post by apienk01 on 2007-05-21
Please correct me if I'm wrong, but I think one can feel very safe in Ubuntu without all these virus checkers and firewalls which are a necessity on Win$. I have never seen a virus on Linux. You would need antivirus if you are using wine a lot, especially if you are using a Win$ email client or Internet Explorer on wine (but why should anyone?). Firewall is not needed as well because there is no spyware on Linux (excluding Win$ spyware on wine, of course). Install it only if you are paranoid about your open ports.

---

### Post by rich.bradshaw on 2007-05-21
sudo apt-get autoclean

will delete the package files that apt keeps around for your convienience - this adds up quickly though.

This just deletes the installers for programs you have installed, so unless you are going to uninstall and reinstall you don't need them.

sudo apt-get clean deletes them all, autoclean just deletes ones over a week old.

You might want to do that...

Everything else takes care of it's self - i.e. disks checked automatically every 30? boots, logs automatically rotated and removed etc.

---

### Post by muso on 2007-05-21
> **the lemming said:**
> Are there any tasks that I should perform to keep ubuntu ticking along nicely?

Coming from a Windows environment I am used to performing tasks such as defragging, virus checks and the like.  Are such tasks redundant for ubuntu?

Chhers

For tidying up redundant files, you might find this link useful:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

As far as I know, defragging is unnecessary, and viruses are rare in Linux - with a standard setup they shouldn't have access to any system files to do any damage anyway.  Just make sure that you don't use root unless you know what you're using it for.

Firewalling I would recommend.  Personally I use a hardware firewall, but if you need it, I'm sure someone can recommend what you need to setup.

---

