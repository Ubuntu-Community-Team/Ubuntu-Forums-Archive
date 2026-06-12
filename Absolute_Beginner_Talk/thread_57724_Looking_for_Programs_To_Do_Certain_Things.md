---
title: "Looking for Programs To Do Certain Things"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by Solomon on 2005-08-17
Hello,

I have been using Windows since the days of 95. Awhile back, a friend encouraged me to install Ubuntu and give is a test drive. After waiting about a month for my CD's to arrive in the mail, I finally got them. Since then, I reformatted my drive and installed Ubuntu. Windows was needed to be re-installed anyway. Consider this a trial basis ;)

In any case, I am looking for two good programs. One, an FTP client. This is needed. I use to use CuteFTP for Windows but alas, No Linux variation. The same lies true with WinAmp.

I am looking for programs that compare but are for Linux and will work on Ubuntu. I also don't have much knowledge on installing on this system so directions are VERY helpful.

---

### Post by bvilches on 2005-08-17
I recommend gftp as a FTP Client and XMMS because it's similar to WInamp.

Be sure to read the guide at: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by bored2k on 2005-08-17
FTP: gFTP (my fav)
Media Players: beep-media-player, muine, rhythmbox (just a few)
[http://www.sosdg.org/~larne/w/Screenshots](http://www.sosdg.org/~larne/w/Screenshots)
[http://muine.gooeylinux.org/muine.png](http://muine.gooeylinux.org/muine.png)

---

### Post by aysiu on 2005-08-17
[Linux equivalents for Windows programs](http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml)

---

### Post by Brunellus on 2005-08-17
[QUOTE=Solomon]Hello,

I have been using Windows since the days of 95. Awhile back, a friend encouraged me to install Ubuntu and give is a test drive. After waiting about a month for my CD's to arrive in the mail, I finally got them. Since then, I reformatted my drive and installed Ubuntu. Windows was needed to be re-installed anyway. Consider this a trial basis ;)

In any case, I am looking for two good programs. One, an FTP client. This is needed. I use to use CuteFTP for Windows but alas, No Linux variation. The same lies true with WinAmp.

I am looking for programs that compare but are for Linux and will work on Ubuntu. I also don't have much knowledge on installing on this system so directions are VERY helpful.[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

Lots of people ask this, thus, the sticky thread.

---

### Post by Solomon on 2005-08-17
My bad. Sorry.

On this topic tho, I want this:

[http://www.xmms.org/](http://www.xmms.org/)

How do I install it, what do I download? Im lost. :/

---

### Post by Brunellus on 2005-08-17
[QUOTE=Solomon]My bad. Sorry.

On this topic tho, I want this:

[http://www.xmms.org/](http://www.xmms.org/)

How do I install it, what do I download? Im lost. :/[/QUOTE]
 enable the universe repository in synaptic, then install it via synaptic.

---

### Post by Solomon on 2005-08-17
Ok Im sorry how exactly do I do that?

---

### Post by aysiu on 2005-08-17
[QUOTE=Solomon]Ok Im sorry how exactly do I do that?[/QUOTE]

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by bored2k on 2005-08-17
[QUOTE=aysiu][http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)[/QUOTE]
 1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install beep-media-player

Or

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. Upper panel > System > Administration > Synaptic > Search and Destroy ;)

---

### Post by Solomon on 2005-08-17
[QUOTE=bored2k]1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install beep-media-player

Or

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. Upper panel > System > Administration > Synaptic > Search and Destroy ;)[/QUOTE]
 none of it worked....

---

### Post by bored2k on 2005-08-17
[QUOTE=Solomon]none of it worked....[/QUOTE]
 Care to explain ?


After you do all the steps, it _has_ to work. At least give us the displayed error ;).

---

### Post by Solomon on 2005-08-17
Ok nvm I tried doing it again and it worked. Last time it said some process was busy. I dunno.

---

### Post by bored2k on 2005-08-17
[QUOTE=Solomon]Ok nvm I tried doing it again and it worked. Last time it said some process was busy. I dunno.[/QUOTE]
 You probably had Synaptic running while trying an apt job.

---

### Post by Solomon on 2005-08-17
How do I add skins? I cant find the correct directory >.>

---

### Post by bored2k on 2005-08-17
[QUOTE=Solomon]How do I add skins? I cant find the correct directory >.>[/QUOTE]
 gnomelook.org after you find some, drop them in .bmp or .xmms /Skins I believe (in your Home directory, that is).

---

### Post by Solomon on 2005-08-17
I have no such folders in my home folder.

---

### Post by Brunellus on 2005-08-17
[QUOTE=Solomon]I have no such folders in my home folder.[/QUOTE]
 they're hidden.  There should be an option in nautilus to show them for that folder.

anything that starts with a dot is usually hidden. A user's configuration files for individual applications will usually be stored in a dot directory in his home directory.  so in my case it'd be 

/home/Brunellus/.xmms

or, in short form 

~/.xmms

---

### Post by AgenT on 2005-08-17
[QUOTE=Solomon]I have no such folders in my home folder.[/QUOTE]

What you are looking for is a folder that has the name ".xmms" (without the quotes) in your home folder. Notice the dot, this is important. Also note that dot folders and files are always listed first, then after all dotted ones are listed, it lists regular, non-dotted, ones.

On Panel, click:
Places -> Home

Then click (in Nautilus, the file brower that pops up):
View -> Show Hidden Files

If no such folder exists, then you probably did not start xmms or are doing something wrong. The first time you start xmms it should create this folder for you.

You can also do this:
Places -> Home
File -> Open Location

Your home folder should be written (example: /home/agent). You would then just add the folder ".xmms" so it looks like this:
/home/agent/.xmms/
Click Open and you should see the contents of this folder.

And as the above poster mentioned, the "~" character is the shortcut to your home directory. So for example, these two would be the same thing:
/home/agent/.xmms/
~/.xmms/

---

### Post by Solomon on 2005-08-17
Ok I think something is different. I wanted the XMMS media player but I think I have "Beep Media Player" which is based on XMMS, correct? So where do the skins go for BMP? I do not have a folder in the home directory called .xmms but BPM does load.

---

### Post by Solomon on 2005-08-17
Aha! Got it. Thanks everyone for your help!

---

### Post by pattison on 2005-08-17
I just recently installed ubuntu and was surprised that it is missing a lot of core programs that other distros have. But someone on the forum pointed me to this link:
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)
There is an "Ubuntu addon zip" or something like that on the webpage that not only contains the programs and codecs you need, but it is an idiot level install (good for me). I installed the addon it directly onto the base install and everything worked fine.

---

