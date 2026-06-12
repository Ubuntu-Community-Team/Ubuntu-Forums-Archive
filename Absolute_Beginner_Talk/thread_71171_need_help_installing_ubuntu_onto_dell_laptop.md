---
title: "need help installing ubuntu onto dell laptop"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by helmethedd on 2005-10-02
I'm running an inspiron 2200 and so far ubuntu runs ok, with only a few gliches.
Getting palm zire 71 to sync with ubuntu.
Getting totem to actually play a dvd.
and despite some of the best help i could find, I'm still unable to install java.

Come one come all, if you need more info from me just ask. Go humanity!

---

### Post by emperor on 2005-10-02
You'll need to install "libdvdcss2" to decode incripted DVD's. If using hoary it's in the repos's.
I did not find the lib in the Breezy repos so I had to download it from the internet. I then used 
"checkinstall" to create a package for Breezy.

java, see this link: [http://plugindoc.mozdev.org/linux.html#Java](http://plugindoc.mozdev.org/linux.html#Java)
install instructions for binary: [http://java.sun.com/j2se/1.5.0/install-linux.html](http://java.sun.com/j2se/1.5.0/install-linux.html)

After install, you will need to make a symbolic link in the firefox plugin directory to where "libjavaplugin.so" is located.

Details can be found on forum, wiki or in the ubuntuguide

---

### Post by MetalMusicAddict on 2005-10-02
I have the same laptop. What version of Ubuntu are you using?

---

### Post by emperor on 2005-10-02
[quote=MetalMusicAddict]I have the same laptop. What version of Ubuntu are you using?[/quote] 
i9300, Hoary with a modified kernel from kernel.org; modified to enable DMA on DVD/CD drive. I am not sure yet if Breezy's default kernel will enable DMA without a mod!

---

### Post by helmethedd on 2005-10-02
[QUOTE=MetalMusicAddict]I have the same laptop. What version of Ubuntu are you using?[/QUOTE]
I just installed 5.04 hoary yesterday.

---

### Post by helmethedd on 2005-10-02
Y'all need to dummy it up a bit fer me. I'm in waaaaaay over my head!
Whats a repository?

---

### Post by aysiu on 2005-10-02
[QUOTE=helmethedd]Y'all need to dummy it up a bit fer me. I'm in waaaaaay over my head!
Whats a repository?[/QUOTE] Maybe you should start with this

[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

It's a guide I wrote for new Linux users--everything I wish someone had told me when I first started out. It includes a quick and dirty teminology glossary.

---

### Post by helmethedd on 2005-10-02
ok, everyone is being really helpful and i appreciate it.
I have another question telating to something that keeps popping up.
wut is and how do i create a symbolic link?

---

### Post by TristanMike on 2005-10-02
A "symbolic link" is similar to a "shortcut" in windows. And if you right click you should be able to "Make A Link" which is this "symbolic link"

---

### Post by helmethedd on 2005-10-02
[QUOTE=TristanMike]A "symbolic link" is similar to a "shortcut" in windows. And if you right click you should be able to "Make A Link" which is this "symbolic link"[/QUOTE]
holy cow!! someone made sense to me!! EEEEEEENGLISH!! YAY FOR ENGLISH!
its almost like he's not trying to show off his superior mentle intellect and really trying to HELP me. Cool.
now after waiting for so darned long, i forgot why i needed to know that...lol
man i slay me.

---

### Post by emperor on 2005-10-02
Many of your questions should be answered here, at least concerning configuration.

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

