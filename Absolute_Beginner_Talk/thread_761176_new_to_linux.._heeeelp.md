---
title: "new to linux.. heeeelp"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by monkeyspoon on 2008-04-20
i just got ubuntu working. yay

now i need help on how to get the internet, nvidia chipset and audio and video codecs working.

is there any way to get the graphics card fully functioning?

---

### Post by dante.regis on 2008-04-20
Hello there!

You can't connect to the Internet from your Ubuntu? How is your setup? A modem that needs dialing (like Dial-up network on windows)? A PPoE connection? Post more info to us! :)

Regarding codecs and nvidia and all that, you will find plenty of documentation on this website, hosted on the official ubuntu servers:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

The forums will also help you very much. Why don't you make a search with your chipset, (like ati x1100 on my case) and see what the results bring? Maybe your questions were already solved here :)

If not, post more info so we can help you out!

Best

---

### Post by SOULRiDER on 2008-04-20
If you go to

System > Administradtion > Drivers (it may not be called that exactly) it will say your vidoe card needs drivers, it will download and install them for you.

You should chekc this out:
[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

---

### Post by scientist1971 on 2008-04-21
soulrider
I have this problem with graphics card too
would appreciate a more detailed description of how to find the location of these drivers in admin
I had a look but could not find what you were talking about
thanks in advance

---

### Post by Paqman on 2008-04-21
It's called Restricted Drivers Manager. Take a look in there and enable anything it has detected.

For audio/video codecs you want to install [ubuntu-restricted-extras](apt:ubuntu-restricted-extras), the [Medibuntu](https://help.ubuntu.com/community/Medibuntu) repository and [vlc](apt:vlc).  There's not a lot that vlc won't play, and Medibuntu gives you access to the dvd playback libraries.

---

