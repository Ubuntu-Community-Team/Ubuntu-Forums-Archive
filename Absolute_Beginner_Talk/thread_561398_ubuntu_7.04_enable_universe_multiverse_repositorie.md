---
title: "ubuntu 7.04 enable universe multiverse repositories?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by robsonet on 2007-09-27
Greetings to all...

I want to see some videos from you tube or other sites but they ask for Java / Flash etc,,, PlugIns and I want to know how to in Ubuntu 7.04 (beginner to Linux) I could enable universe and multiverse repositories?
Thanks,

---

### Post by mendingo84 on 2007-09-27
you should have this lines in your /etc/apt/sources.list

```
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
```

```
deb http://ro.archive.ubuntu.com/ubuntu/ feisty multiverse universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ feisty multiverse universe
```

---

### Post by rsambuca on 2007-09-27
Or to do it via a GUI, you can go to the top menu bar and select "System -> Administration -> Software Sources".  Enter your password at the prompt, and then just click the boxes for the restricted, universe, and multiverse repositories.

---

### Post by P235 on 2007-09-27
You can also modify your sources.list file by replacing it with a set of sources provided by the Ubuntu sources.list generator.

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by r4ik on 2007-09-27
Perhaps a useful link,

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Good luck !

---

### Post by overdrank on 2007-09-27
> **robsonet said:**
> Greetings to all...

I want to see some videos from you tube or other sites but they ask for Java / Flash etc,,, PlugIns and I want to know how to in Ubuntu 7.04 (beginner to Linux) I could enable universe and multiverse repositories?
Thanks,

Hi and you may find these links helpful
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Good luck! :)

---

