---
title: "A couple of questions, please"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by JGKC9AYC on 2006-05-28
First, I'd like to change the Ubuntu symbol that's beside "Applications" to the Gnome symbol.  I'm running the Mac OS X theme & I don't like the looks of the Ubuntu symbol.
Second, when Dapper comes out, will Breezy automatically upgrade to it or will I have to do something?
Thanks!

---

### Post by halfvolle melk on 2006-05-28
For the first question chck this:
[http://doc.gwos.org/index.php/Gnome_Icon](http://doc.gwos.org/index.php/Gnome_Icon)

As for the second, replace all instances of "breezy" with "dapper" by editing this file:
```
sudo gedit /etc/apt/sources.list
```
Once done, type this in a terminal:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by 3rdalbum on 2006-05-28
Actually, assuming you have the latest version of update-manager, you will automatically be given the option to upgrade to Dapper without altering your sources.list.

---

### Post by JGKC9AYC on 2006-05-28
[QUOTE=3rdalbum]Actually, assuming you have the latest version of update-manager, you will automatically be given the option to upgrade to Dapper without altering your sources.list.[/QUOTE]
How would I know if I had the latest version of update manager?
I do remember installing "Automatix" after having issues with Opera not finding certain files upon startup.

---

### Post by JGKC9AYC on 2006-05-28
[QUOTE=halfvolle melk]For the first question chck this:
[http://doc.gwos.org/index.php/Gnome_Icon](http://doc.gwos.org/index.php/Gnome_Icon)
[/QUOTE]

I tried that & got a "No such file or directory".
I went to that directory & saw no Gnome icon.

***Edit***
OK...got that took care of...got the foot, but was trying for the Apple logo...hehehe.
Regarding Dapper...would I be better off doing a fresh install or no?
Thanks!

---

### Post by JGKC9AYC on 2006-05-28
Also, when Dapper comes out, what version of Firefox & Opera will it have?
Is Dapper using the KDE desktop or Gnome?
Will it have Azureus as well or is there a better bittorrent for Linux?

---

### Post by aysiu on 2006-05-28
[QUOTE=JGKC9AYC]Also, when Dapper comes out, what version of Firefox & Opera will it have?[/quote] Ubuntu doesn't have Opera. And Firefox will be 1.5.0.3. In fact, I think it is now in Dapper already.

> 
Is Dapper using the KDE desktop or Gnome? There are three different versions:

Ubuntu (Gnome)
Kubuntu (KDE)
Xubuntu (XFCE)

---

### Post by JGKC9AYC on 2006-05-29
[QUOTE=aysiu]
 There are three different versions:

Ubuntu (Gnome)
Kubuntu (KDE)
Xubuntu (XFCE)[/QUOTE]

Recommendations?  Personal preferences?  Screenshots?  :)

---

### Post by ComplexNumber on 2006-05-29
[quote=JGKC9AYC]Recommendations?  Personal preferences?  Screenshots?  :)[/quote] have a gander at [this]("http://www.linuxnewbieguide.org/"). look at the links on the left to see what gnome, kde, and other look like.

---

### Post by aysiu on 2006-05-29
[QUOTE=JGKC9AYC]Recommendations?  Personal preferences?  Screenshots?  :)[/QUOTE] I'd recommend Ubuntu if you have no experience with Linux and you have at least 256 MB of RAM. It's not that I prefer Gnome (in fact, I'm using KDE right now), but you'll get a larger support base for Gnome on these forums.

If you have 128 MB or RAM or less, use Xubuntu.

If you've had experience with KDE and like it, use Kubuntu.

[http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)

[Gnome screenshots](http://images.google.com/images?q=gnome&svnum=100&hl=en&lr=lang_en&safe=off&sa=N&imgsz=xxlarge)
[KDE screenshots](http://images.google.com/images?q=kde&svnum=100&hl=en&lr=lang_en&safe=off&sa=N&imgsz=xxlarge)

---

### Post by JGKC9AYC on 2006-05-29
I'm running an A64 3200+ w/2 gigs of ram.
I'm trying to wean myself away from XP but it's taking time.
I think I need a Linux for Dummies book, tho.  :)

---

### Post by aysiu on 2006-05-29
Read this for starters:
[http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)

---

### Post by JGKC9AYC on 2006-05-29
If I go into the Synaptic Package Manager & install KDE, would I have a choice at bootup which desktop environment I wanted to use?  And if I did that, which packages should I choose for startes with KDE?
I didn't know if there's a way one can switch back & forth between KDE & Gnome.

---

### Post by aysiu on 2006-05-29
Don't use Synaptic to install KDE; otherwise, it'll be a pain in the *** to remove later, should you wish to do so.

Follow these directions (and, yes, you would be able to switch between the two):
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by JGKC9AYC on 2006-05-29
I appreciate the help & the quick replies.
I assume that I can follow those same instructions to install Xfce on Breezy?
Will Dapper be setup to choose which desktop environment I wish to use or will I have to go through this procedure as well?

***Edit***
I just tried installing it the way you suggested & got the following message:
[I]
"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"[/I]

Ideas?

---

### Post by aysiu on 2006-05-29
[QUOTE=JGKC9AYC]I appreciate the help & the quick replies.
I assume that I can follow those same instructions to install Xfce on Breezy?[/quote] It's pretty similar--just ```
sudo aptitude install xubuntu-desktop
``` instead of ```
sudo aptitude install kubuntu-desktop
``` > Will Dapper be setup to choose which desktop environment I wish to use or will I have to go through this procedure as well? Same procedure. Ubuntu is designed around simplicity:

1. User with only one password
2. One application per task
3. One desktop environment

You can always add more users later or more applications or more desktop environment.s

> 
***Edit***
I just tried installing it the way you suggested & got the following message:
[I]
"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"[/I]

Ideas? It means you're trying to use dpkg (specifically, apt-get or aptitude) while another program is using it (specifically, Synaptic Package Manager or Adept). Close Synaptic or Adept and try again.

---

### Post by JGKC9AYC on 2006-06-02
[QUOTE=halfvolle melk]For the first question chck this:
[http://doc.gwos.org/index.php/Gnome_Icon](http://doc.gwos.org/index.php/Gnome_Icon)
[/QUOTE]

That doesn't seem to work with Dapper.
Can I use a different icon besides the Gnome icon...like perhaps an apple?  ;)

---

