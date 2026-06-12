---
title: "gxine installation problem"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by samare on 2006-08-02
Hi,

I'm trying to install gxine on Ubuntu6.06. I tried apt-get install gxine but failed. Now I'm trying to do it manualy by downloading the gxine package(gxine-0.5.7.tar). It needed some dependencies such as libmozjs-dev. So, I tried with apt-get install libmozjs-dev but got an error like "couldn't find package libmozjs-dev". Then I downloaded that package(deb file)and put it in /var/cache/apt/archive. Again ran the command "apt-get install libmozjs-dev" and then got an error saying "E: Package libmozjs-dev has no installation candidate". Someone pls explain these errors and help me to install gxine to watch DVDs.

samare:-k

---

### Post by cantormath on 2006-08-02
> **samare said:**
> Hi,

I'm trying to install gxine on Ubuntu6.06. I tried apt-get install gxine but failed. Now I'm trying to do it manualy by downloading the gxine package(gxine-0.5.7.tar). It needed some dependencies such as libmozjs-dev. So, I tried with apt-get install libmozjs-dev but got an error like "couldn't find package libmozjs-dev". Then I downloaded that package(deb file)and put it in /var/cache/apt/archive. Again ran the command "apt-get install libmozjs-dev" and then got an error saying "E: Package libmozjs-dev has no installation candidate". Someone pls explain these errors and help me to install gxine to watch DVDs.

samare:-k

Hey Samare,

Im not sure if you want to get video support and Firefox Flash/java support working without a hassel, but if you do, and you are not just trying to do things manually for the sake of it, I suggest using automatix for dapper.  Here is the Howto.

Just install the Video Codecs, Players, Java, Flash, and Mplayer stuff.  When you are done, it will ask you to restore your repository to what it was , click yes, you are safer using the original repo on the day to day basis.  Here is the link:

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

When you are done, you can remove the package, or just leave it.

---

### Post by adamkane on 2006-08-02
gxine (xine-ui) is better at playing various media:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28xine-ui.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28xine-ui.29)

---

### Post by samare on 2006-08-02
> **cantormath said:**
> Hey Samare,

Im not sure if you want to get video support and Firefox Flash/java support working without a hassel, but if you do, and you are not just trying to do things manually for the sake of it, I suggest using automatix for dapper.  Here is the Howto.

Just install the Video Codecs, Players, Java, Flash, and Mplayer stuff.  When you are done, it will ask you to restore your repository to what it was , click yes, you are safer using the original repo on the day to day basis.  Here is the link:

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

When you are done, you can remove the package, or just leave it.

Hi,

I want to play DVDs. Totem gives errors even after installing the libdvdread3. So,I wanted to try it with gxine. I don't mind playing DVDs even with any other player. As you said I installed automatix. Then I selected Media Players. But it also gives errors in autoscript_dapper(dpkg: dependency problems prevent configuration of bmp-docklet....etc) . And the funny thing is that another message coming up saying "All installation and configuration completed". Please help.](*,) 

samare

---

### Post by adamkane on 2006-08-02
See Post #3.

---

### Post by cantormath on 2006-08-02
Use automatix to install the AUD-Codecs and players and Mplayer.

---

### Post by samare on 2006-08-02
> **cantormath said:**
> Use automatix to install the AUD-Codecs and players and Mplayer.

Hi,

I tried this but automatix failed to do that and gave errors. Anyway I managed to install xine-ui using apt-get as Post 3. I'm still new to Ubuntu and trying all the commands such as apt-get, aptitude, automatix for installing packages. I could do this because I have the Internet connectio at home.This is not good for noobs who doesn't have Internet at home:( . Any recommendations on installing packages???????? 

samare

---

