---
title: "Mac mini wont update, or install any packages"
date: 2007-06-10
forum: Apple PPC Users
---

### Post by Dunks0r on 2007-06-10
Hi there PPC users,

I have been using Ubuntu now since 5.04 but this is the first time i have used PPC ubuntu (6.06) 

So far so good, but something really strange is happening, where i can get all apps to reconise the internet connection, but the system itself, It wont update, it wont allow me to see uninstalled synaptic packages and every time i load add/remove programs it says out of date, try with a working internet connection...

Strange this tho is its time is set off the time server and its correct. I havent had this problem before with any of my x86 installs... its just strange, Network is working fine, because im writing this within VNC thru the actual mini?

Any ideas what could be the problem? By the way i have checked the network settings within Synaptic and they are set for default internet settings. I am not running a proxy server and not running DHCP, But all settings have been put in manually and no problems with any other apps as said.

Thanks for your thoughts in advance.

Duncan

---

### Post by Dunks0r on 2007-06-10
Sorry i should also mention that i am located in Australia, and have checked the sources.list and tried both [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) and the [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) sources (all have had the au. removed)

I know 6.06 has long term support, so should i have to remove or add anything from the sources list?

---

### Post by tcrroadie on 2007-06-10
The repositoies apt is trying to connect to is probably down.  If you remove the au prefix from your apt repository sources, the sources will not work at all.  You could try the U.S. repositories.  Replace au with us

Example 

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
```

You may also want to consider installing Feisty in place of your Dapper installation.  Feisty has many fixes and improvements for the PowerPC platform. 

You can download the installation disk for Feisty PPC from the link below. 

[Ubuntu Feisty Fawn PPC downloads]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")

---

### Post by Dunks0r on 2007-06-10
Thanks for the info, but it seems i should probably read what i am editing! (whoops!)

Much like linux will ignore everything after a "#" so did i, it seems during installation that it decided to blank out all of the sources with a # due to not being able to connect to them and in my frustration i ignored it, I removed all and its working great now.

I did erase all the au. from the sources and its still working? im not using some rouge sources am i?

---

