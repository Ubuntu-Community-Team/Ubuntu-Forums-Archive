---
title: "Unity 2D PPC"
date: 2011-05-15
forum: Apple Hardware Users
---

### Post by newbody on 2011-05-15
Hello,

do you know how I can use Unity 2D on my PPC G5?

LG

---

### Post by pauljwells on 2011-05-15
just install 'unity-2d-default-settings from synaptic (this should install about six other packages) then select 'unity-2d' from the session menu on the login screen.

You will find that the colours are all wrong - I have a fix for that and I can probably send you a link to download my recompiled debs.

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1754092]("http://ubuntuforums.org/showthread.php?t=1754092")

Here are my debs - these fix both the ppc colour and the show with mouse at side of screen issues

[http://dl.dropbox.com/u/18375146/Unity-2D.tar.gz]("http://dl.dropbox.com/u/18375146/Unity-2D.tar.gz")

---

### Post by newbody on 2011-05-15
Thanks for your response, but in synaptics I always get the message of a broken package

---

### Post by pauljwells on 2011-05-15
Ah, then that's a different question entirely! I'm afraid I'm not an expert on this. There is a lot of info on the forums if you search for broken packages.

Have you tried this?

```
sudo apt-get update && apt-get dist-upgrade
```

---

### Post by newbody on 2011-05-15
> **pauljwells said:**
> Ah, then that's a different question entirely! I'm afraid I'm not an expert on this. There is a lot of info on the forums if you search for broken packages.

Have you tried this?

```
sudo apt-get update && apt-get dist-upgrade
```

I get this message with the package:
dependant of:  unity-2d  but it is not installable

---

### Post by pauljwells on 2011-05-15
run the code I posted above and post the output from the terminal

then run

```
sudo apt-get install unity-2d-default-settings
```

and post the output of that also

You ARE running 11.04 aren't you??

Take a look at this thread - it might help. If you don't have any ppas or externally installed apps then there shouldn't be any broken packages in the repos. vlc is broken at the moment but that shouldn't affect unity-2d

[http://ubuntuforums.org/showthread.php?t=947124]("http://ubuntuforums.org/showthread.php?t=947124")

---

### Post by newbody on 2011-05-15
first:

E: Sperrdatei /var/lib/dpkg/lock konnte nicht geöffnet werden - open (13: Permission denied)
E: Sperren des Administrationsverzeichnisses (/var/lib/dpkg/) nicht möglich, sind Sie root?

English: Couldn't open lockfile /var/lib/dpkg/lock
Locking not possible

Second
 unity-2d-default-settings : Hängt ab von: unity-2d ist aber nicht installierbar

(Unity -2d-default-settings depend of unity -2d, which isn't installable

Of course I'm running 11.04

---

### Post by pauljwells on 2011-05-15
Did you run as sudo? Try running:
sudo apt-get update

then:
sudo apt-get dist-upgrade

Also make sure that you don't have either synaptic or update manager running! Your output basically says that the command didn't run for one of these reasons...

BTW, I speak German if it helps ;-)

---

### Post by newbody on 2011-05-16
If you speak german, here's my output :)



	  **XXX@localhost:~$ sudo apt-get update**
[sudo] password for XXX: 
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426) natty InRelease
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) natty InRelease                 
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426) natty/main TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426) natty/restricted TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426) natty/main Translation-de_DE
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426) natty/main Translation-de
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426) natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426) natty/restricted Translation-de_DE
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426) natty/restricted Translation-de
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426) natty/restricted Translation-en
OK   [http://ports.ubuntu.com](http://ports.ubuntu.com) natty Release.gpg
OK   [http://ports.ubuntu.com](http://ports.ubuntu.com) natty Release
OK   [http://ports.ubuntu.com](http://ports.ubuntu.com) natty/universe powerpc Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) natty/universe TranslationIndex
OK   [http://ports.ubuntu.com](http://ports.ubuntu.com) natty/universe Translation-de
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) natty/universe Translation-de_DE
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) natty/universe Translation-en
Paketlisten werden gelesen... Fertig
**XXX@localhost:~$ sudo apt-get dist-upgrade**
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Paketaktualisierung (Upgrade) wird berechnet... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
**XXX@localhost:~$ sudo apt-get install unity-2d-default-settings**
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder, wenn Sie die
Unstable-Distribution verwenden, dass einige erforderliche Pakete noch
nicht erstellt wurden oder Incoming noch nicht verlassen haben.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 unity-2d-default-settings : Hängt ab von: unity-2d ist aber nicht installierbar
E: Beschädigte Pakete

---

### Post by pauljwells on 2011-05-16
Hmmm
All I can suggest is that you try to install unity-2d first, using the same kind of command and see why it won't install. What version numbers do you see in synaptic for the unity-2d packages? I have 3.8.4.1 ubuntu1

It wouldn't hurt to try installing my packages, they won't break anything

---

### Post by newbody on 2011-05-16
> **pauljwells said:**
> Hmmm
All I can suggest is that you try to install unity-2d first, using the same kind of command and see why it won't install. What version numbers do you see in synaptic for the unity-2d packages? I have 3.8.4.1 ubuntu1
 
It wouldn't hurt to try installing my packages, they won't break anything
 
 
I think source.list is my problem too.
I saw that source.list is my cd
 
So I used this [http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc](http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc)
 
Now I have some languages and packages and updates
But I think its the wrong source.list
 
I miss unity packages

---

### Post by newbody on 2011-05-16
I reapaired my source.list.
Now I have unity 2D!!!!

But how can I fix now the bug with the colors

---

### Post by pauljwells on 2011-05-16
> **newbody said:**
> I reapaired my source.list.
Now I have unity 2D!!!!

But how can I fix now the bug with the colors

Pay attention Herr newbody!! :-D

[http://dl.dropbox.com/u/18375146/Unity-2D.tar.gz]("http://dl.dropbox.com/u/18375146/Unity-2D.tar.gz")

These are my patched versions of the installers you need. Just unpack the tarball to a directory and then in a terminal, cd to the directory and:

```
sudo dpkg -i ./*.deb
```

Once installed, be careful not to upgrade them in synaptic, because that will just reinstall the default ones.

Version 3.10 will have these (and other) patches applied, so wait until those appear in the lists until you upgrade.

** EDIT **
These bugs (and others) are now fixed in the daily build repo

```
ppa:unity-2d-team/unity-2d-daily
```

---

### Post by pauljwells on 2011-05-16
unity-2d is a bit buggy, so create a new keyboard shortcut to run the following short script line:

```
killall unity-2d-launcher
```

I assigned it to Ctrl-Alt-U, now whenever the launcher does something odd I can just type three keys to restart it.

---

### Post by newbody on 2011-05-16
Wow!!!!!!!
 
Thanks a lot
 
many many many thanks

---

### Post by pauljwells on 2011-05-16
You're welcome :-)

BTW, I prefer Clementine to Banshee. It also had a colour bug and I patched that. The deb is here:

[http://dl.dropbox.com/u/18375146/clementine_0.7.1-0ubuntu2_powerpc.deb]("http://dl.dropbox.com/u/18375146/clementine_0.7.1-0ubuntu2_powerpc.deb")

---

### Post by pauljwells on 2011-05-20
@newbody

Please look out to see if you get this bug:

[https://bugs.launchpad.net/bugs/758787]("https://bugs.launchpad.net/bugs/758787")

If you do, please add yourself to the 'affects me' list.

Thanks!

---

