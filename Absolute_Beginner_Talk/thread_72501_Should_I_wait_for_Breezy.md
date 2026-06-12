---
title: "Should I wait for Breezy?"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by brainz on 2005-10-06
Hi, My hard disk crashed and i bought a new one. I just installed windows on it as elder members in my family are more comfortable using it.
I have a few queries:
1: I'm just wondering should I wait till Oct13th till Breezy officially releases before I install Ubuntu on my box, or install the preview release right away.
2: I want to know what is the difference between the preview release and the official release?
3: At present i have a install cd of Hoary, if i install that , how can i upgrade it to breezy?

---

### Post by nitricacid on 2005-10-06
I have been using The preview version of Breezy since it got released and all is well in my computer.
I don't really know what the difference is, more stable, updated kernel and other apps...

If i were you i would just wait till oct 13th unless you don't want to wait that long.

If you install Hoary and then want to up date to breezy all you have to do is type:
```
Sudo gedit /etc/apt/sources.list
``` in a terminal and then change all the words that say Hoary to the word Breezy.

Save the text to and then type:
```
sudo apt-get dist-upgrade
``` into the terminal.

If done currectly the terminal will show a long list of what is being download and isntalled.
Do NOT close the terminal untill the process is complete.

After completion of the Breezy install restart your system and anjoy.

---

### Post by Kapre on 2005-10-06
[QUOTE=brainz]Hi, My hard disk crashed and i bought a new one. I just installed windows on it as elder members in my family are more comfortable using it.
I have a few queries:
1: I'm just wondering should I wait till Oct13th till Breezy officially releases before I install Ubuntu on my box, or install the preview release right away.
2: I want to know what is the difference between the preview release and the official release?
3: At present i have a install cd of Hoary, if i install that , how can i upgrade it to breezy?[/QUOTE]

brainz - to answer your questions.
1. I would suggest that you wait (having installed Colony 1 and tried to upgrade Hoary to Breezy via synaptic - that didn't go to what I expected it to go) till October 13. The news now (which I'm going to download) is that RC1 has been released (which is the almost final release)
2. Difference between the Colony and official is all (most of them) the bugs have been sorted out and the "final" has less of it.
3. See #1

This is my thought and there are some there that would have other info.

K

---

### Post by brainz on 2005-10-06
[QUOTE=Kapre]brainz - to answer your questions.
2. Difference between the Colony and official is all (most of them) the bugs have been sorted out and the "final" has less of it.
K[/QUOTE]

Oh i see, then if I install the preview release, future updates will take care of the bug fixes right?

---

### Post by nitricacid on 2005-10-06
[QUOTE=brainz]Oh i see, then if I install the preview release, future updates will take care of the bug fixes right?[/QUOTE]

Yes. just use:
```
Sudo apt-get update & sudo apt-get upgrade
```
to update any packages that are available for that release.

To update the distro that is when you have to edit the sources.list and change the names to whatever the next distro is, as i have describe above.

---

### Post by brentoboy on 2005-10-06
I think the short answer is, if you have time to play around with it between now and then, then jump right in, the water's fine.  You might have to use the forums and play with some stuff, but it'll be fine in the end, becuase you are going to update your packages sooner or later anyway.

If you want minimal time investment, just wait, you'll spend less time downloaing updates, and toying with it.

But toying with it is the main reason to install it anyway, right?
:)

---

### Post by Goober on 2005-10-06
I'd say yes, install it.  I installed breezy about 5 days ago, and nothing has crashed, nothing has stalled, it has been more stabler (new word!) then I thought possible.  In fact, it has worked very well, I have added programs, updated, deleted programs, it works well, and is faster for me then Hoary.  And automatically loaded my Hoary partition!

I would say go for it, just don't put any important files on until the 13th just in case.

---

