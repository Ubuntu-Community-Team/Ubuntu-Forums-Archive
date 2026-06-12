---
title: "[SOLVED] Help I need somebody, Help Not just anybody"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by magicbusband on 2007-11-28
Hello I am so new to Linux and Ubuntu that I am beginning to become overwhelmed with all the wonderful possibilites.  I am looking for some basic help with a few problems I am having.  Anyone wanting to help read on, those who are looking for a good laugh at a newbie also read on.


1. Where is the best place to download and install new software from?

2. I am looking for a P2P file sharing software similar to soul seek, preferably soul seek.  I am mostly wanting to download mp3 music.

3. I am looking for a great sound recording, mixing, cutting, and MIDI input software.  I have switched over from windows and I miss Acid Pro, Fruity Loops, and my other sound applications.

4. I have a HD with windows on it and windows is so screwed up that it cant load even if i try to recover and boot in safe mode.  How do I force it to let me open it on Ubuntu, while not loosing all my music home videos and important song creations?

If anyone is able to answer any of these questions I would greatly applicate it.



Thanks

Magicbusband

---

### Post by LowSky on 2007-11-28
nice beatles reference

1. use synaptic or add/remove, both are built into unbuntu
2. check add/remove it has allot of P2P already listed
3. Try using ubuntu studio, availible in add/remove
4. install the HD but dont boot from it, ubuntu should automatically mount the drive

---

### Post by Paqman on 2007-11-28
> **magicbusband said:**
> 
1. Where is the best place to download and install new software from?


System > Administration > Synaptic Package Manager. Should have pretty much anything you need. You can add more repositories to it if they contain software you need.

> 
2. I am looking for a P2P file sharing software similar to soul seek, preferably soul seek.  I am mostly wanting to download mp3 music.


Azureus is pretty good. A lot of people seem to like Deluge, too.

> 
3. I am looking for a great sound recording, mixing, cutting, and MIDI input software.  I have switched over from windows and I miss Acid Pro, Fruity Loops, and my other sound applications.


No idea sorry. Maybe the Ubuntu Studio folks could point you at some good alternatives?

> 
4. I have a HD with windows on it and windows is so screwed up that it cant load even if i try to recover and boot in safe mode.  How do I force it to let me open it on Ubuntu, while not loosing all my music home videos and important song creations?


All you need to do is mount the partition that Windows was installed on and you should be able to browse it. Right click on either panel and add a "disk mounter". That will show all the drives and partitions available. Pick the windows one and it'll show up on your desktop.

---

### Post by civic_si on 2007-11-28
You can install almost any software for ubuntu in the add/remove programs section under applications on you taskbar. there is a selection on the top right corner to allow you to browse and install alot of software.

not sure on the p2p stuff 

Ardour does music mixing but there is a good list of stuff that can be installed for music editing on Ubuntu studio's website under the wiki section.

by default in linux you should be able to copy stuff off of the windows hard drive. look under the computer icon and go to filesystem and look for the media folder and browse the drive for your stuff.

---

### Post by climatewarrior on 2007-11-28
1. The first place to look for new software is in Applications/Add/Remove. There you will have a vast software library. Most of that software is Free(libre) and all of it is free(gratis). It depends on what repositories you have enabled. The second place to look for software is in System/Administration/Synaptic Package Manger. There you will find thousands of packages(software). If the program your looking for is not available in neither of those sources look in the internet for 3rd party repositories. Anf if what you want in not in any repositorie then just dowload directly from the softwares website. The disadvantage of doing that is that it will be a little harder to uninstall and that ubuntu wont be able to take care of the programs upgrades. Althoough most likely 99% of the software you need will be available either in Add.Remove or Synaptic.

2. Dont know. Wait for someelses response.

3. My reccomendations. Audacity and Jokosher

4. Go to Places/Computer and if the HD is connected you should be able to see it there.  Mount it by doauble clicking it.

Theres nothing wrong with asking questions. Everyone was a noob at some time. Nobody was born knowing everything. Actually it is really great that you are learning linux. 

Bye! Good Luck

---

### Post by nsilva on 2007-11-28
1. In ubuntu the best way to install software is using Apt-get, since it downloads all packages from the ubuntu repositories (which have been teste for stability and security =) Google around and you will thousand of post how to use apt-get. If you are not into command line, you can go to the Main Menu and Add/Remove Software

If you dont find a package in those repositories, means that it has not been approve by the ubuntu team. Still you might find packages .deb, that you can download and install. But again there is a lot of documentation out there about this topic.

2. For p2p, you can run Limewire, or Frostwire, there is a lot of options out there, never heard of Soul Seek. If you insist you want to run a Windows program in Ubuntu look into Wine

3. No idea

4. Explain some more, I couldnt really understand what u meant. Is it if you can run the drive under ubuntu without the risk of ruin it? Let me know

---

### Post by lespaul_rentals on 2007-11-28
> **magicbusband said:**
> 1. Where is the best place to download and install new software from?

Try using the Add/Remove Programs application.  You can search for terms, such as "ftp" for a good FTP program, or "msn" for MSN Messenger clones, stuff like that.  Everything from the Ubuntu repositories are safe, supported, and malware-free, so install away!

> 2. I am looking for a P2P file sharing software similar to soul seek, preferably soul seek.  I am mostly wanting to download mp3 music.

You might try this: [http://freshmeat.net/projects/pyslsk/](http://freshmeat.net/projects/pyslsk/)

However, I use FrostWire.  It uses the gNutella network.  It's fairly lightweight and I'm happy with it: [http://www.frostwire.com](http://www.frostwire.com).  Download the .deb file to install on your computer, if you so choose.

> 3. I am looking for a great sound recording, mixing, cutting, and MIDI input software.  I have switched over from windows and I miss Acid Pro, Fruity Loops, and my other sound applications.

I'm not going to lie, Linux isn't the best in terms of applications such as this... :(

Audacity is a fantastic sound recorder/editor.  I'm sure you've used it or at least heard of it, you might like to try it out.  Hydrogen is a great drum program, similar to Fruity Loops.  Try searching Synaptic Package Manager for terms like "midi" and see what comes up.

> 4. I have a HD with windows on it and windows is so screwed up that it cant load even if i try to recover and boot in safe mode.  How do I force it to let me open it on Ubuntu, while not loosing all my music home videos and important song creations?

Is the hard drive formatted with NTFS?  If so, you should be able to mount the hard drive using ntfs-3g and ntfs-config.  You can then drag-and-drop, backup, and recover files.  You probably have no idea what those programs are, but I can help you out with all that when it comes time.

Oh, and if you are going to be working with media, videos, and all that stuff, run this command in Terminal ASAP:

```
sudo apt-get install ubuntu-restricted-extras
```

This will install all the plugins for .mp3, .avi, Java, Flash, etc.  It will save you much hassle later.

So you're a musician?  What kind of music do you do?

---

### Post by magicbusband on 2007-11-28
Thanks for the help I think I can work it out from here. Lespaul_Rentals thanks espacialy for the help how can I contact you with a few questions about my HD?

---

### Post by lespaul_rentals on 2007-11-28
> **magicbusband said:**
> Lespaul_Rentals thanks espacialy for the help how can I contact you with a few questions about my HD?

No problem.  Just start a new thread regarding that specifically, I'll help you out there.

---

### Post by MickS on 2007-11-28
Nice title, Nicotine is P2P application that uses Soul Seek I think, not used it for a long time.

Mick

---

### Post by mocha on 2007-11-28
Nicotine+ is an awesome SoulSeek client...  It's in the repositories.

---

