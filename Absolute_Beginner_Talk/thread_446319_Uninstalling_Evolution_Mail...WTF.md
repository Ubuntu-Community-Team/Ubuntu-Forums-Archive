---
title: "Uninstalling Evolution Mail...WTF?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-16
I just tried uninstalling Evolution Mail.  it wasn't listed in the Add/Remove programs section so I searched for it in Synaptic, found the package 'evolution' and marked it for complete removal, but when the confirmation screen came up with the list of other packages that will also be removed a package called 'ubuntu-desktop' was included in the list...WTF IS THAT ABOUT?!?

Either 

1) that's some other package that's parading around with the name 'ubuntu-desktop' for no apparent reason
2) Synaptic screwed up
or
3) The Ubuntu desktop is somehow dependent on Evolution and unstalling it would also uninstall my beautiful GUI :(

[of course there's still 4) I'm screwing up in some other way, but I'd rather not mention that]

I know I can easily hide the Evolution program from showing up in the applications menu, but this retarded dependence issue here (if it exists) really deals a blow to Ubuntu's claim to be free of junk-ware, or at least to being able to remove all the junk ware.  (Evolution gave me a bit of grief before I figured out how to stop it from being my default e-mail client)

Any suggestions?

---

### Post by Ziox on 2007-05-16
ubuntu-desktop is just a ...i think meta-package.  That means that it only points to what OTHER packages to install, the ubuntu-desktop package itself is really nothing at all.  So it's save to remove ubuntu-desktop.  However, if you going to do a complete upgrade to the next version of ubuntu, you need to reinstall ubuntu-desktop package before you try the upgrade....but that's some time in October.

---

### Post by sandpaperback on 2007-05-16
As I understand it "ubuntu-desktop" is just a meta package that groups all the default apps together.  So doing something like "sudo apt-get install kubuntu-dekstop" would install everything that comes with a normal Kubuntu installation.

However, removing one program (like Evolution) won't kill anything, it just sounds scary. :)

Haha.  I'm too slow.

---

### Post by chamberlain2006 on 2007-05-16
Calm down, it's ok.  The ubuntu-desktop package is a meta-package that automatically installs all the programs that come with Ubuntu.  n the other hand, though, there may be other program depending on evolution.  If there are, this may screw you up.  Why do you need to completely remove evolution, anyway?

---

### Post by chamberlain2006 on 2007-05-16
And I just checked.  Nothing important depends on evolution, so it should be safe to remove.

---

### Post by zhinker on 2007-05-16
> **chamberlain2006 said:**
> Calm down, it's ok.  The ubuntu-desktop package is a meta-package that automatically installs all the programs that come with Ubuntu.  n the other hand, though, there may be other program depending on evolution.  If there are, this may screw you up.  Why do you need to completely remove evolution, anyway?
I just found Evolution annoying and a waste of memory since I'm not going to be using it (I know it's really small, but it's still a waste).  

But here's a little problem ziox thought might exist and I'd appreciate knowing whether it's real or not:

"However, if you going to do a complete upgrade to the next version of ubuntu, you need to reinstall ubuntu-desktop package before you try the upgrade....but that's some time in October."

Will uninstalling this package lead to problems/inconvenicnes when I try to upgrade my OS (I'm running Edgy by the way)?  Because when I finally get around to upgrading I'll probably have forgotten all about this little package.

---

### Post by Ziox on 2007-05-16
The best way is to simply do a clean install, aka erase hdd and install via disc.  However, the upgrade manager might just install ubuntu-desktop package first and then upgrade...I really don't know what would happen...never removed that package before.

---

### Post by chamberlain2006 on 2007-05-16
i believe that's true.  When you upgrade to Gutsy (or Feisty, I think you're using dgy) you should reinstall the ubuntu-desktop package, just to be sure.

---

### Post by zhinker on 2007-05-16
> **chamberlain2006 said:**
> i believe that's true.  When you upgrade to Gutsy (or Feisty, I think you're using dgy) you should reinstall the ubuntu-desktop package, just to be sure.
But since it apparently holds meta-data, are you sure it's not currently holding some potentially important information about my system that a newly installed copy of the package will not have?  (what kind of meta data does it store anyways)

---

### Post by Heilige on 2007-05-19
I'm having this same issue and one of the reasons is my dislike for Novell for siding with Microsoft. I don't want a piece of software that may become IP for Microsoft and then they force our hand like always.

---

### Post by Kobalt on 2007-05-19
You can actually remove many things (including Evolution, what I did) using [debfoster]("http://ubuntuforums.org/showthread.php?t=24403").

---

