---
title: "How to do dual boot (chrome os/ubuntu)_"
date: 2020-05-02
forum: Any Other OS
---

### Post by nitrospeed on 2020-05-02
Hi, i have installed on my pc Chrome OS according this tutorial [(https://vosveteit.sk/vdychnite-svojmu-staremu-pocitacu-zivot-pozrite-sa-ako-mozete-do-neho-nainstalovat-chrome-os/]("http://vosveteit.sk/vdychnite-svojmu-staremu-pocitacu-zivot-pozrite-sa-ako-mozete-do-neho-nainstalovat-chrome-os/")) and i would make dual boot with ubuntu. Please, can you someone show me tutorial how to do? Thank you

---

### Post by Frogs Hair on 2020-05-02
Dual booting Chrome OS and Ubuntu is not officially supported, moved to ***Any Other OS***.

---

### Post by Hwæt on 2020-05-02
In my opinion, you're best off enabling Linux from the settings and using the Linux shell. Any graphical packages you install there can be started by invoking their name 

```

gimp

```

as an example. They'll show up as bona fide app icons in the ChromeOS browser under 'Linux Apps' and you can pin them to your bar. They'll work graphically just like they would in Ubuntu.

The reason I caution against Crouton and the like (the way to do this) is that Crouton requires rooting the device. Using the built-in Linux capabilities will not. And as anyone can tell you, a rooted Chromebook is a potential hotbed for any usual *nix malware.

But if you really, really want to dual boot Ubuntu, follow the steps in the [ReadMe on the Crouton repository.]("https://github.com/dnschneid/crouton")

---

### Post by nola-guy on 2020-05-04
which Chrome OS do you have?  I know Cloudready's version of Chrome will not work dual boot. The only way to dual boot it  is to install each OS on a separate HD , with the other drive disconnected, then use the bios boot select to choose the OS. Otherwise, when you add another OS it will break Chrome. and even after you do a boot repair, Chrome OS will break  boot every time it updates. It does not tolerate other boot loaders. At least that's how it is with Cloudready. I experienced it first hand, then found it on their support page. Here is where they ended support: [https://www.neverware.com/blogcontent/2018/1/2/dualboot-a-long-goodbye](https://www.neverware.com/blogcontent/2018/1/2/dualboot-a-long-goodbye)  I could not find the latter  post from CR support where they stated that their updates may break booting.

---

