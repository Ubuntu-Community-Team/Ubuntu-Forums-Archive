---
title: "wine prob"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by poysama on 2007-07-03
I followed instructions on installing wine [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")
here but it after I pasted the first command on the terminal, I am being asked for my password. The thing is, I can only input a character, but my password is longer than a character.

Any help?

---

### Post by LaRoza on 2007-07-03
You can't see the letters, just type and press enter.

```
sudo aptitude install wine
```

---

### Post by Rocket2DMn on 2007-07-03
Linux doesn't show your password as you tye it, not even covering it with *'s.  It's just a security precaution - you are actually typing it in.
Also, you should do your best to install programs from the repositories using a package manager like apt-get or Aptitude or Synaptic.  These programs are known to work in Ubuntu and you will receive better support with them.  Unlike with windows, you don't have to navigate to different webpages to download most programs, you just use the repositories, though there are times when you need to install deb files or even download tarballs (archives) and install by yourself.

---

