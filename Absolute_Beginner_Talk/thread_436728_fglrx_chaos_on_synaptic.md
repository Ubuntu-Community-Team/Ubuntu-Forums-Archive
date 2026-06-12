---
title: "fglrx chaos on synaptic"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Palmstroem on 2007-05-08
Hi folks,

after upgrading to 64bit Feisty and trying the ATI fglrx_8.36.5 following[ this]("http://ubuntuforums.org/showpost.php?p=2486332&postcount=1") guide I ended up with desktop freezing all the time. Even worse, when going back to vesa :(  I discovered that synaptic always complains that xorg-driver-fglrx-dev must be reinstalled but that there is no archive.

Any help welcome!

---

### Post by useResa on 2007-05-08
My suggestion would be to remove the xorg-driver-fglrx-dev entirely first by giving the following command in a terminal
```
sudo dpkg --remove --force-remove-reinstreq  xorg-driver-fglrx-dev
```Basically with the above command you are asking the package to be removed (the --remove option) and additionally force some extra requests.
The remove-reinstreq asks for a removal of a package even if it is broken and marked for reinstallation, which is the case in your situation.
If you like to know more about the dpkg command, there are many locations where you can find this. One example is [here]("http://www.abc.se/home/m10828/webgine1320e_linux/man__H_dpkg.html").

---

### Post by Palmstroem on 2007-05-09
Thanks a lot, useResa!

Your recipe worked fine. I am sure I have to learn more on package management...

Ubuntu forum is great!:guitar:

---

