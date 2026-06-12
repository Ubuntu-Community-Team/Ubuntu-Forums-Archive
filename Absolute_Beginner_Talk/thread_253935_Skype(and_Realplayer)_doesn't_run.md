---
title: "Skype(and Realplayer) doesn't run"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by harerama on 2006-09-09
Hello,

I thought I've installed skype using "sudo dpkg -i skype_1.2.0.18-2_i386.deb" and when I go applications>internet skype is there but it won't run. Also I did for Realplayer applications>Sound&Video it is there but it won't run. Method I used installing for real[player is below. Can anyone help me? Thank you.

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)
Installing RealPlayer10 from a .deb file

RealPlayer requires libstc++5, the GNU Standard C++ Library v3. Make sure it is installed before you proceed.

      sudo apt-get install libstdc++5

      Download the RealPlayer .deb package from the [WWW] Debian-Marillat repository and install it using dpkg:

      wget -c [http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb)
      sudo dpkg -i realplayer_10.0.7-0.0_i386.deb

      RealPlayer should now be installed on your system.

---

### Post by RobsterUK on 2006-09-09
Maybe you could try installing Skype with EasyUbuntu, I did it this way and it works fine.

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by harerama on 2006-09-09
Thank you. Ok now my terminal says this

-desktop:~/easyubuntu$

 I think I've managed to easyubuntu installed? But what should I do next ? should I install also skype?

---

### Post by rapha on 2006-09-09
Looks like you got easyubuntu unpacked and have changed into the folder.

About your Skype/RealPlayer problem: I've installed Skype 1.2 yesterday as well, but it wouldn't come up. Now I've instead installed Skype 1.3 Beta (can get a .deb on their website) and it works like a charm. No idea why (devs: it just sat in a poll() forever).

Installed RealPlayer as per the method you posted and works fine here. What output do you get when you type "realplay" into a terminal window?

---

