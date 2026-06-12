---
title: "Just installed Ubuntu 7.04  - Need help Installinb .bin files"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by foxwiz on 2007-04-21
I am a new Ubuntu user, just installed version 7.04 tonight.  I downloaded two files, RealPlayer10GOLD.bin and jre-6ul-linux-i586-rpm.bin.   I can see these two files on the desktop.  Can someone explain in detail how I can install these files?

Remember I am a new user and don't know Linux at all.  

Thank you.

---

### Post by spin2cool on 2007-04-21
bin files should be executable installers.  Open up your terminal, then do the following:

move to the desktop, chmod the file(to make sure it's executable) and run it:

cd ~/Desktop
chmod +x filename
./filename

---

### Post by spin2cool on 2007-04-21
I should mention that both real player and java can be much more easily installed by using automatix (ww.getautomatix.com).  It's a great little program.

---

### Post by flossgeek on 2007-04-21
> **foxwiz said:**
> I am a new Ubuntu user, just installed version 7.04 tonight.  I downloaded two files, RealPlayer10GOLD.bin and jre-6ul-linux-i586-rpm.bin.   I can see these two files on the desktop.  Can someone explain in detail how I can install these files?

Remember I am a new user and don't know Linux at all.  

Thank you.

**Installing Java 6**

If you want the plugin for mozilla and the java runtime, then you would do the following in a terminal:-

```
sudo apt-get update
```
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

If you want the jdk(for writing java and contains jre) do this:-

```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

Once you have done either of these run:-

```
sudo update-java-alternatives -s java-6-sun
```

Finally open the jvm config file:-

```
gksudo gedit /etc/jvm
```

arrange lines in following order:-

/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr

Save and exit. Thats Java setup! ;-)

Realplayer

See "Install RealPlayer for Linux from the RealNetworks web site" section at:-

[https://help.ubuntu.com/community/RealplayerInstallationMethods#head-6660c7f44edb9d54e6fa9e04c825e0f9540d6107](https://help.ubuntu.com/community/RealplayerInstallationMethods#head-6660c7f44edb9d54e6fa9e04c825e0f9540d6107)

Hope this helps ;-)

---

### Post by flossgeek on 2007-04-21
> **spin2cool said:**
> I should mention that both real player and java can be much more easily installed by using automatix (ww.getautomatix.com).  It's a great little program.

Also I would advise NOT using automatix, it can bork your machine! Besides most things are easy to install in Feisty now, removing the need for automatix.

---

### Post by spin2cool on 2007-04-21
I just used automatix on feisty yesterday and had no problems - I don't know what "borking" you're referring to.

---

### Post by foxwiz on 2007-04-21
Thanks for the replies.  I installed Automatix and installed Java and a codecs program, then I installed Real Player.  

The reason I wanted to install the .bin files is to listen to some music at [www.bobrivers.com](www.bobrivers.com).   I went back to the site and tried to listen to some songs in the audio vault.  I get a window popup saying transfering data but the song never loads, and the window just sits there.

Can someone go to the site to see what I mean?     What do I need to install to be able to play tunes from this site?

Any help would be appreciated.

Thank you.

---

