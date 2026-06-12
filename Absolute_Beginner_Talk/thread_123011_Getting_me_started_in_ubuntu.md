---
title: "Getting me started in ubuntu"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by Fffan on 2006-01-29
Well, Im in need of quite a bit of help, ive been a windows user my whole life, from the time with oregon trail and win95 in the computer labs, good memories, and have become somewhat of a poweruser in windows, am very confident in it and do very well, but it still has its problems, crashes, hangups, i dont have problems with viruses, but i just want to do linux. 

  First, my machine specs: 
AMD64 3200
1gig kingston RAM 400mhz
200gig HDD (i think i did a 30gig linux partition, all i had left)
Powercolor ATi Radeon 9600pro 256MB AGP8x GPU
VIA Envy24PT/HT PCI soundcard
   I got Ubuntu 5.1 64bit to dual boot just fine, IBM P260 moniter running 1920x1440 like a dream, everything great with the OS itself, and i really love it so far. Now, i want to not want to live without it. Problems im encountering: the biggy: Totem music playing, music playing in general, now, im gonna go through all those help files again, but most of them arent specific, which brings me to my next problem, i have no idea how to install something, and havent been able to yet. Its not that afriad of the terminal at all, i just dont know how to use it, so if i could get a good understanding of how that kind of thing works that'd be great.

That's all ill ask for now, im trying to go slow.

I have soda and fraps on standby, ill be up all night, so please help :)

thank you!

---

### Post by UbuntuDupe on 2006-01-29
Good move, good move.  By going on and on about how great Ubuntu is, you'll probably get more attention.  People here don't like to deal with pesky issues like Ubuntu locking you out of your computer and stuff like that.  It's a real downer for them

---

### Post by Fffan on 2006-01-29
Yes, the ones just shouting off complaints do seem rather bothersome, im just trying to understand how to use it the new OS, which i imagine is to be expected. Im very surprised the dual boot was as easy as it was, and that nothing on my PC has fried.

oh, and i suppose ill fix a mistake in my parent post, *ubuntu 5.10, but you already knew that :)

---

### Post by Puptentacle on 2006-01-29
Ffan, I recently asked a music question in here and music is a BIG issue with me. 

As far as specific questions, ask away! I wasn't too hot on Totem, VLC was a little better (I REALLY have to have an EQ function!), some others had some features I liked but the one that really made me happy (so far) has been Amarok. Sort of a resource hog but the player sounds great, all the functions work and the gui is quite nice. 

So, what do you specifically need to know?

---

### Post by dueY on 2006-01-29
[QUOTE=Fffan]Totem music playing, music playing in general[/QUOTE]

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by dueY on 2006-01-29
[QUOTE=Puptentacle] I wasn't too hot on Totem, VLC was a little better (I REALLY have to have an EQ function!), some others had some features I liked but the one that really made me happy (so far) has been Amarok. Sort of a resource hog but the player sounds great, all the functions work and the gui is quite nice. [/QUOTE]

I use VLC for watching movies on Windows sometimes when other players can't open a file.  It's great.  And amaroK is my choice for music player as well.

---

### Post by Fffan on 2006-01-29
Thanks for all the replies!

Before I go on with installing the plug-ins i figure ill ask, are these going to go smoothly on the 64bit? i was going along with Automatix and got the 64bit error message or something. Ill install 32bit if i must, but i like the idea of 64bit, even if its placebo, i might get around to installing ubuntu on my 32bit laptop someday (after i figure out playing music, that is)

i have an album or two encoded in .ogg, only a couple because my Zen doesnt play .oggs, but i thought id give it a try, and the song played on the computer, but there was no sound, so i suspect is has something to do with the sound card. theres no sound on startup either, i run a digital opitcal cable out to my amp, ill check around for the drivers again but last time i looked i couldnt fine them, and again, i wouldnt know how to install it. I do need my music, as i knew i was gonna be on linux all night tonight i went ahead and dug up some more records, my PC is my CD player, and thats not working out so well right now.

What i meant by them not being specific is theyre pretty much "install this, type this, your done!" and i need a little more explanation than that.

---

### Post by hen3rz on 2006-01-29
> from the time with oregon trail

I love Oregon trail! It was the first computer game i ever played.

> i have no idea how to install something, and havent been able to yet. Its not that afriad of the terminal at all, i just dont know how to use it, so if i could get a good understanding of how that kind of thing works that'd be great.

Have a read of this webpage:

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

> Totem music playing, music playing in general

Check this out:

[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)

For music playing I would recommend Amarok not Totem:

[http://amarok.kde.org/](http://amarok.kde.org/)

its for KDE but it runs fine in gnome.

---

### Post by Fffan on 2006-01-29
Success! Almost, the .mp3s now play (thanks for the wiki article) but, theres still no sound, there is red light through the optical cable, but theres no signal through it, according to my amp. 

Again: VIA Envy24PT/HT

give me a second to dig up an 1/8 to RCA and see if it its pumping it through line out

---

### Post by Fffan on 2006-01-29
a-Ha! thats it, the music definitly works, its coming out of the lineout from the onboard sound, any ideas how to enable my PCI soundcard?

---

### Post by Perfect Storm on 2006-01-29
What about xmms? It's like winamp.

---

### Post by Perfect Storm on 2006-01-29
[QUOTE=Fffan]a-Ha! thats it, the music definitly works, its coming out of the lineout from the onboard sound, any ideas how to enable my PCI soundcard?[/QUOTE]

Have you disable the onboard sound in the BIOS?

---

### Post by Fffan on 2006-01-29
i thought i had, because it improves game framerates, but perhaps not, right now im listening with headphones so its not a major concern, although i would appreciate the clearness of the PCI card amped and all, but i wont bother at the moment

i will, however, check out xmms

---

### Post by Fffan on 2006-01-29
All right, perfect example, im at the xmms website and a few different options are offered:

tar.gz
tar,bz2
src.rpm

which one do i choose? is it going to work with amd64? 
so yes, lets take this step by step, which on do i download

---

### Post by Perfect Storm on 2006-01-29
I have no experience with 64 bit, but did you check apt-get first if it's avaible for 64?

```
sudo apt-get install xmms
```

---

### Post by Fffan on 2006-01-29
well that was just about sooperdooper easy, sweet, the particular skin looks really bad at such a high resolution, squint-worty text and the like, but ill see if i cant figure out how to get a new one.

---

### Post by Perfect Storm on 2006-01-29
You can use winamp skin for it or head to gnome-look.org for skins too.

Here's mine: [http://ubuntuforums.org/gallery/showimage.php?i=160&c=member&imageuser=19](http://ubuntuforums.org/gallery/showimage.php?i=160&c=member&imageuser=19)

---

### Post by Fffan on 2006-01-29
Well, before i go playing around with looks, i got mp3 files on the HDD to play, now how do i play an AudioCD? it opens soundjuicer on default, which doesnt work, and i dont know where the CD driver is via directory

same question i imagine, how about ripping a CD?

---

### Post by Fffan on 2006-01-29
Nevermind on how to rip, i figured it out on soundjuicer, does XMMS do CD ripping?

---

### Post by Perfect Storm on 2006-01-29
Not what I know off (If someone know please post). But you can use grip to rip music CDs.

requires universe to be enable in your sourcelist.
```
sudo apt-get install grip
```

If you want xmms to start up when inserting a CD:

```
gnome-volume-properties

```
(Also found in System tab ---> Preferences ---> Removable Drives and Media)

Go to multimedia tab and under Audio CD disc there's a command box. write this in the box:

```
xmms -p /media/cdrom
```

Also if you want to change player for a specific music-file. Right click the file and pick **Properties**. Go to **Open with** tab and choose which playere should play this kind of music-files. If your player aren't in the list click **add** and find what you seek.

---

### Post by phen on 2006-01-29
maybe you like to get some general information on how to install software: There a near to zero applications that you install like a typical windows program (go to the website, download, execute, clicking next next next in the installation wizard). 

You are able to download nearly everything with synaptic, the package manager. You don't google for applications anymore, but you use the search within synaptic. Synaptic downloads lists of software automatically, and let you search them. To add many many applications to your synaptic database, you have to add repositories.

AddingRepositories link here: [https://wiki.ubuntu.com/SoftwareManagement](https://wiki.ubuntu.com/SoftwareManagement)

Try the wiki for other questions, too. it is very well written and comprehensive :-)

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

I hope you enjoy your new system! my voice goes to amarok, btw :-) You should find a CD-Player app inside the menu (Multimedia?). Amarok is able to play CDs, XMMS should be, too. There is no real "driver" for your cd. but you can try "lsmod" (LiStMODules) inside a terminal, to see all loaded modules. you should find the content of a cd in /media/cdrom

---

### Post by steve.horsley on 2006-01-29
[QUOTE=Fffan]a-Ha! thats it, the music definitly works, its coming out of the lineout from the onboard sound, any ideas how to enable my PCI soundcard?[/QUOTE]

Try System->Preferences->Sound, and see if you have a choice of default sound card. I also had to change the soundcard in the preferences for the little speaker icon / volume control on the gnome panel.

They defaulted to the on-board sound but I use an SB-live card.

---

### Post by Fffan on 2006-01-29
I was able to change the default sound card to my PCI card instead of onboard, as well as changing the output device on the volume icon prefences and all, but its still playing through onboard line out and not PCI lineout, let alone optical out

im going to reboot and turn off onboard sound and see if that helps, any other suggestions?

---

### Post by phen on 2006-01-29
sound under linux can be a bit complicated: there are many different sound-architectures: oss, esd, arts and alsa. maybe you changed the settings of one, but use the other? the window manager uses a default sound server, but applications can be set up to use another. i never really understood :-)

turn off onboard sound, and try to find the right settings. but if nothing helps and your install is new anyway, reinstall.

---

