---
title: "Beginner Questions please"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Forked Tongue on 2008-01-17
Welcome to my thread, and thanks for your time in Advance

I have formatted my Laptop and installed only Ubuntu 7.10 on it.

So i have faced some issues. some of them might be i agree stupid but iam new to Ubuntu so bare with me please.

1.I need more programs for Ubuntu, I do not know the names but i would like programs like WIndows programs such as the following:
[LIST]
[*]Photoshop - For processional Image Editing
[*]Nero - Burn CD's & DVD's
[*]Winamp - Play MP3 Music
[*]Orbit - Downloading 
[*]Realplayer - Play Real Music
[*]Gome Player - Play Movies
[*]Cool Edit Pro - Edit Music
[*]Norton or Kaspersky - Virus Protection programs
[*]Propel Accelerator - an Internet Speed enhancer
[/LIST]

And Kindly where can i download them from please.


2.I heard and seen on Youtube that there are some "Graphics" plugins that i can install on Ubuntu to give better graphical effects, such as when you click the Windows button & Tab "Iam not sure if these are the actuall button" but the screen will zoom out and be on a cube and and then you can rotate the cube to actually scrool between windows.

also when you click on "System" and then go into a sub menu such as "Preferences" the first Menu will burn as an effect to hide it, something like that "Sorry for the bad description", where can i download that please.

3.I will be installing games on my Laptop and i heard there are some kind of Emulator or something like that in order to play Windows Games on Ubuntu. where can i download that please.

4.Ubuntu is in English, However i wanted to install an additional Language which is "Arabic". the problem is when that Keyboard on top showed up, when iam typing and i want to chose arabic it only gives me the option to type in "Arabic Egypt", while iam looking for "Arabic Saudi Arabia".

I do not care actually it's just that when iam typing in "Arabic Egypt" the letters that iam typing and the letters being typed do not match ! .. its like the letters on the keyboard are not the same as being typed. i know this question might be hard so you can ignore it if its hard for you.

5.Where and how can i download more Fonts "Arabic & English" ofcourse please.

6.As a Windows user, Ubuntu is like a whole new cave for me, so i would really appreciate some hints of programs, you know anything as a new Ubuntu user that i should know.


Last but not least, Many thanks and appreciation in advance.


Much appreciated :)

Regards,
Forked Tongue.

---

### Post by aysiu on 2008-01-17
Start with [http://linuxappfinder.com/](http://linuxappfinder.com/) for equivalents to Windows programs.

---

### Post by tigerplug on 2008-01-17
I don't have all the answers, but:

Photoshop = GIMP
Nero = Gnomebaker
Winamp = Amarok
Play Movies with VLC
Norton or Kaspersky ... don't particularly need AV but If you can try ClamAV


Have a look here:
[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

---

### Post by Joeb454 on 2008-01-17
Not so sure about realplayer for Linux, there might be a version.

Also check out Brasero for CD/DVD burning.

Click Applications>Add/Remove and search for it :)

---

### Post by eolson on 2008-01-17
Most of what you are looking for is already installed.  I'd spend some time playing around with the applications and then come back and ask questions to fill in the holes.   You might check out the GIMP as a phote editor,  just to give you and idea.   I wouldn't worry about an anti-virus program too much virii for Linux tend to be very very rare.  I've been running without one for maybe 10 years.  One of the big reasons is writting a virus for Linux is not as easy as it is for Windows and when a vulnerablitly is found, it's usually patched very quickly making all the virus writers efforts useless so nobody bothers.  They go for the easy target.

---

### Post by jryprt on 2008-01-17
#2 try [Forlong's Guide](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#)

---

### Post by leader303 on 2008-01-17
try installing your windows apps with wine!
if you have learned to use a program properly, you might not want to learn a new one by now, and it's plain frustrating not getting any work done because the apps are missing.

---

### Post by kebes on 2008-01-17
[*]Photoshop - For processional Image Editing
You can try "GIMP" or "Krita". If you have a copy of Photoshop, you can try installing it in Linux using "Wine" (it works perfectly on my system).

[*]Nero - Burn CD's & DVD's
There are many. I use "K3B".

[*]Winamp - Play MP3 Music
I use "Amarok".

[*]Gome Player - Play Movies
Try "VLC" or "MPlayer" or "Kaffeine"...

[*]Cool Edit Pro - Edit Music
I'm not sure what's best, but check out "Audacity" and "LMMS"

[*]Norton or Kaspersky - Virus Protection programs
Not usually needed on Linux. But if you want to protect against forwarding Windows viruses you can install "ClamAV"

[*]Propel Accelerator - an Internet Speed enhancer
Probably not necessary (if you want to get really fancy you can modify "iptables" to streamline your connection, but this is complicated and as I said usually not needed).


> And Kindly where can i download them from please.
In Ubuntu, you can install tons of software directly using the "Package Manger"--all the software is downloaded from a trusted repository and installed. Open the Synaptic Package manager (by going Applications > Add/Remove or finding "Synaptic" in the system menu), and search for the names of the programs I mentioned. When you see the one you want, just click install.


> 2.I heard and seen on Youtube that there are some "Graphics" plugins that i can install on Ubuntu to give better graphical effects, such as when you click the Windows button & Tab "Iam not sure if these are the actuall button" but the screen will zoom out and be on a cube and and then you can rotate the cube to actually scrool between windows.
You're thinking of "Compiz" and/or "Compiz Fusion" (previously called Beryl). On modern Ubuntu, this is installed by default, but not turned on. It is called "enhanced desktop effects" and you can activate it easily as long as your graphics card can handle it (and you have the hardware-acceleration driver installed for your card).

If you want more details on how to do that, give us a bit more info on your graphics card, etc.


> also when you click on "System" and then go into a sub menu such as "Preferences" the first Menu will burn as an effect to hide it, something like that "Sorry for the bad description", where can i download that please.
Once Compiz Fusion is installed, all of those effects can be turned on/off in its preferences. (Maybe someone else will give more specific instructions, since I'm not running Compiz right now...)


> 3.I will be installing games on my Laptop and i heard there are some kind of Emulator or something like that in order to play Windows Games on Ubuntu. where can i download that please.
The translation layer you're thinking about is "wine". Follow the instructions here to install:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

There is also a commercial program similar to this called Cedega that you can buy if you want. (Wine is free.)


> 6.As a Windows user, Ubuntu is like a whole new cave for me, so i would really appreciate some hints of programs, you know anything as a new Ubuntu user that i should know.
Yes, the transition can be difficult, since everything is a little different! Feel free to ask lots of questions on the forums, and we'll try to answer as best we can.

---

### Post by Iehova on 2008-01-17
Before I start, welcome to Ubuntu! I'm sure you'll have a blast. Now, unless otherwise specified, all the software I mention can be installed via Synaptic (System > Administration > Synaptic). Linux isn't like Windows where you have to go rooting around the net for software, it's all in one convenient location. Well, most of it.

> **Forked Tongue said:**
> Welcome to my thread, and thanks for your time in Advance

I have formatted my Laptop and installed only Ubuntu 7.10 on it.

So i have faced some issues. some of them might be i agree stupid but iam new to Ubuntu so bare with me please.

1.I need more programs for Ubuntu, I do not know the names but i would like programs like WIndows programs such as the following:
[LIST]
[*]Photoshop - For processional Image Editing
[*]Nero - Burn CD's & DVD's
[*]Winamp - Play MP3 Music
[*]Orbit - Downloading 
[*]Realplayer - Play Real Music
[*]Gome Player - Play Movies
[*]Cool Edit Pro - Edit Music
[*]Norton or Kaspersky - Virus Protection programs
[*]Propel Accelerator - an Internet Speed enhancer
[/LIST]

And Kindly where can i download them from please.

OK, the GIMP can easily replace photoshop for 99% of users, IMHO, once you get used to the fact that the UI is different.

- I personally recommend K3B for disk burning, but you can also use gnomebaker.
- Rhythmbox is installed already for playing music, but I personally use Exaile, because I generally find it to be better.
- There is a realplayer for linux (google it), but I don't use it, because I've never - ever - needed it. There are many programs that can handle Realplayer's formats, but I can't remember offhand. I think Mplayer does.
- The included Movie Player will play DVDs, but not very well. Please read through [this](https://help.ubuntu.com/community/RestrictedFormats) page on the Ubuntu wiki, but basically you want to install the packages ubuntu-restricted-extras and totem-xine.
- For editing music, you might want to try Audacity? I honestly have no idea.
- You don't need an anti-virus on Linux, as has been explained.

> 2.I heard and seen on Youtube that there are some "Graphics" plugins that i can install on Ubuntu to give better graphical effects, such as when you click the Windows button & Tab "Iam not sure if these are the actuall button" but the screen will zoom out and be on a cube and and then you can rotate the cube to actually scrool between windows.

also when you click on "System" and then go into a sub menu such as "Preferences" the first Menu will burn as an effect to hide it, something like that "Sorry for the bad description", where can i download that please.

Compiz (which does this) is installed by default on Ubuntu Gutsy. You can check that it's turned on in Preferences > Appearence > Visual Effects. Assuming it's on and working, install compizconfig-settings-manager, that lets you achieve all those effects.

> 
3.I will be installing games on my Laptop and i heard there are some kind of Emulator or something like that in order to play Windows Games on Ubuntu. where can i download that please.

You have to understand that running games on Wine (which is what you're talking about) is not as easy as all that. The Wine project has achieved great things, but sometimes nothing goes to plan. You can check individual software on [http://appdb.winehq.org/](http://appdb.winehq.org/)

> 6.As a Windows user, Ubuntu is like a whole new cave for me, so i would really appreciate some hints of programs, you know anything as a new Ubuntu user that i should know.

Linux is not windows. Some things are different (like having software repositories), and you have to be prepared for this, which I'm sure you are!

Also, most times you ask for help on this forum or follow a guide you'll be asked to use the command line. This isn't because you _can't_ use the GUI to get something done, it's just quicker that way. ;)

Anyway, have fun, and if you like Ubuntu, spread the love! :P

---

### Post by clong83 on 2008-01-17
It may not be the best overall music player out there, but for the closest thing to winamp, I'd check out xmms.  Most of the other programs you want/need have already been mentioned.

---

### Post by asmiller-ke6seh on 2008-01-17
> **Forked Tongue said:**
> --clip---
And Kindly where can i download them from please.
---clip----

Look at the New Ubuntu User's Resource - see the link in my SIGnature (below, left).

Installation is done using a special install tool - there are several to choose from: there is a command line interface (apt-get) and a graphic user interface (synaptic). Programs are held in REPOSITORIES. There are several popular repositories that can be trusted, so it's a good idea to restrict downloading and installing from those.

---

