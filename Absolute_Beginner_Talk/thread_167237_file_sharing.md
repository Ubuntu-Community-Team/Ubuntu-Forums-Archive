---
title: "file sharing"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by gehlig123 on 2006-04-28
Where can I find to find a file sharing program ,such as limewire etc,I have no programming experience and am currently using breezy badger 5.10 as an operating system( only used it for 1 week so far) Thanks

---

### Post by henriquemaia on 2006-04-28
[QUOTE=gehlig123]Where can I find to find a file sharing program ,such as limewire etc,I have no programming experience and am currently using breezy badger 5.10 as an operating system( only used it for 1 week so far) Thanks[/QUOTE]

If you have the appropriate repositories enabled (in synaptic - go to System --> Administration --> Synaptic Package Manager ), you can install a few. You'll find Nicotine (Soulseek for Linux), gtk-gnutella (gnutella client), etc.

For the appropriate repositories, check:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by bionnaki on 2006-04-28
the nicotine in the repos is way outdated.
download the latest here: [http://thegraveyard.org/daelstorm/nicotine-patch.php](http://thegraveyard.org/daelstorm/nicotine-patch.php)

---

### Post by trent dillman on 2006-04-28
Since you're using Breezy, try installing Automatix (search for it here on the forums). That will help you install Frostwire, a fork of Limewire.

---

### Post by henriquemaia on 2006-04-28
[QUOTE=bionnaki]the nicotine in the repos is way outdated.
download the latest here: [http://thegraveyard.org/daelstorm/nicotine-patch.php](http://thegraveyard.org/daelstorm/nicotine-patch.php)[/QUOTE]

Thanks. I didn't know about this update.

---

### Post by Perfect Storm on 2006-04-28
Limewire:

```
sudo apt-get install alien
```

Download Linux .rpm version to your Desktop. [http://www.limewire.com/english/content/downloadfree2.shtml](http://www.limewire.com/english/content/downloadfree2.shtml)

```
cd Desktop
sudo alien -i XXXXXXXXXX.rpm
killall gnome-panel
```
*[size=1]XXXXXX is the name of the package*[/size]

Before it can work you need the latest java from Sun.

---

