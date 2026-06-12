---
title: "Azureus on 7.10"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-02-05
Hi fols, 
When I installed the latest version of Azureus downloaded on their website and installing it on the latest java platform, I get this error message:
Aborted (Core dumped)

I have looked over a few pages but I still can't find the answer. Any help?

---

### Post by jken146 on 2008-02-05
The best way to install Azureus is this:

[LIST=1]
[*]Add the Medibuntu repository. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[*]Install Azureus in the usual way.  ```
sudo aptitude install azureus
```
[/LIST]


If you give up on Azureus, I would recommend deluge as a nice reliable bittorrent client.

---

### Post by cozmicharlie on 2008-02-05
I agree with jken.  I would add that you also should check your installation of java.  You need the sun java6-jre installed.  If you installed the icedtea version of java you should uninstall it - there have been a lot of posts with people having problems with iced tea.  To check what java version you are using:
sudo update-alternatives --config java

---

