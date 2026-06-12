---
title: "What are hoary, warty and breezy?"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by shrikantubuntu on 2005-08-24
Someone please tell me what are these terms, warty,hoary and breezy?
thanks

---

### Post by henriette_holm on 2005-08-24
Those are the names of the different versions of Ubuntu.

---

### Post by hashimoto on 2005-08-24
They are the nicknames of differrent releases of Ubuntu. A new (stable) release comes out every six months. First was Warty (or Warty Warthog) in October -04, next was Hoary (or Hoary Hedgehog) in April -05 on now in works is Breezy Badger which will come out in October -05.

See: [https://wiki.ubuntu.com/Releases?highlight=%28releases%29](https://wiki.ubuntu.com/Releases?highlight=%28releases%29)

---

### Post by shrikantubuntu on 2005-08-24
Thanks a lot.
And, Please tell me, how to know which one I am using?

---

### Post by PeP on 2005-08-24
[QUOTE=shrikantubuntu]Thanks a lot.
And, Please tell me, how to know which one I am using?[/QUOTE]
in synaptic: categories->repositories (translation from french, might be depots or something similar)

It shows you all the repositories you are using, so if you see hoary everywhere everything is ok, if it's breezy, you have the experimental version, but you would now it, if it is warty, unlike in windows you can upgrade by changing warty to hoary in each line.

---

### Post by Lord Illidan on 2005-08-24
A quick way is enter

```
cat /etc/apt/sources.list
``` in a terminal, and check for the first line.. which will be the Ubuntu CD used to perform the installation...

For example, mine is```
 deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
``` 

If anyone else has a better way, I knew one which used to be done on Fedora, please say it..

Beat me 2 it!!!

---

### Post by drummer on 2005-08-24
Some other ways: click on the circle of dots 'loading' icon at the top right of Firefox (might only work with the FF from apt) or go to 'System > Help' and there are release notes and a quick guide for the version that's installed (version name is in the text)

---

### Post by Corlian on 2005-08-24
Perhaps there could be a feature in the post-Breezy version, a simple window that gives you a rundown of Ubuntu version, Kernel version, GNOME/KDE version and so on...as a new user I'd find this interesting and helpful.  Though I think I know all the versions I'm running so far, it will change.

---

### Post by void_false on 2005-08-24
When you log in console u see it. Just press ctrl+alt+f1.

---

### Post by TristanMike on 2005-08-24
ummm, guys/girls, what about System-->About Ubuntu. I'd think that would be the easiest way.

---

