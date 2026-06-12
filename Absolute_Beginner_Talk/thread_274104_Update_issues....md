---
title: "Update issues..."
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by lodravah on 2006-10-09
Heyall

Just ran "sudo apt-get update" and it was unable to complete update. The same "koti.mbnet.fi" - link that's caused me some trouble before is broken.. So I'm not able to complete a full update. Further I just ran "update manager" and the same broken link is causing problems. Anyone?

Further, as I was trying to update via "update manager" i noticed that the update avaiable is "linux-image-2.6.12-10-386." Might also be update to "2.6.12-10-40" I'm not sure. 

The thing is I'm using this Kernel now: 2.6.15-27-686. What will the update, should it work, do to my 686 kernel? Is there a different kernel-image I should use?

---

### Post by Kateikyoushi on 2006-10-09
You could get a new repository list for example [from here]("http://www.psychocats.net/ubuntu/sources").
Then do a

```
sudo apt-get update
```
and you should be able to update your system.

The new kernel should not do anything to your existing one you will be able to choose from them in the grub menu.

---

### Post by lodravah on 2006-10-09
Okay..

What is a change of repo's going to do to my settings (such as kernel-upgrade, codecs and such?). And which one is the best repo?

---

### Post by Kateikyoushi on 2006-10-09
Repo won't change your system setings, some repos contain more packages like universe multiverse actually it is just a source of packages.
With this you just select a diferent mirror.
I assume you could not finish downloading from that server, so try another.

---

### Post by lodravah on 2006-10-09
So even if it is another repo they essentially contain the same packages? I'm starting to get the hang of Ubuntu now, but there are still a few gray areas...

---

### Post by Kateikyoushi on 2006-10-09
No, repositories contain different packages, what I recommended is to change the server.
There are several servers which host the identical repositories.
You had problem obtaining the list from that server so you could try another.

> What are Repositories?

There are thousands of programs available to install on Ubuntu. These programs are stored in software archives (repositories) and are made freely available for installation over the Internet. This makes it very easy to install new programs in Linux, and it is also very secure, because each program you install is built specially for Ubuntu and checked before it is installed. To organise the software, Ubuntu repositories are categorised into four groups: Main, Restricted, Universe, and Multiverse

---

