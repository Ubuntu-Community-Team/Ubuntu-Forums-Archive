---
title: "Mint 11 cant play mp3's"
date: 2011-06-07
forum: Any Other OS
---

### Post by dontgetshocked on 2011-06-07
I have a lot of mp3 files that played before and now only 1 file will play using banshee,rhythmbox or vlc.I dont know what gives,they all are read/write.

I installed using cd version unfortunately but now have dvd version.I dont know how to correctly install the appropriate codecs.

---

### Post by ajgreeny on 2011-06-07
Did you install Mint 11 from the CD or DVD?

If you used the CD, not DVD, and have not updated or added the codecs needed, you will not yet have the equivalent of the full DVD version, ie no ability to run all those close source media formats.

Look on the various pages of the release notes for Mint 11 (I think that's where the info is), and you will see how to overcome the problem.

---

### Post by ghostborg on 2011-06-07
I don't know if this is the same problem I had.
I could not play my mp3 files until I noticed that the files were missing the .mp3 extensions like "song" instead of "song.mp3" .
I never did find the culprit software that striped the extensions. I must have been trying out different music player/organizers. 

GPRename is a program that with some getting used to can rename these.

---

### Post by k357k9 on 2011-06-08
[http://www.howtoforge.com/the-perfect-desktop-linux-mint-11-katya]("http://www.howtoforge.com/the-perfect-desktop-linux-mint-11-katya")

Compare what you have with this list of things.

---

### Post by Nightstrike2009 on 2011-06-08
I have the Linux Mint 11 DVD iso version everything works fine for me including Mp3 playback. ;-)

---

### Post by ajgreeny on 2011-06-08
> **Nightstrike2009 said:**
> I have the Linux Mint 11 DVD iso version everything works fine for me including Mp3 playback. ;-)
Yes, it will if the OP started with the DVD version, but if it was the CD version, some codecs are not installed unless you update and choose to add the codecs as it installs.  If you can not get a network connection until after installation and therefore can't download updates etc as you install, there will be a problem, including mp3 playback missing codecs.

---

### Post by Nightstrike2009 on 2011-06-08
One option would be to install [COLOR="Green"]ubuntu-restricted-extras[/COLOR], the other if i remember correctly would be to use this command:
[COLOR="Green"]sudo apt-get install libmp3lame0[/COLOR]

If i remember correctly this is the lame library for mp3 playback and encoding in Ubuntu (& therefore linux mint too).

Hope that helps :-)

---

### Post by dontgetshocked on 2011-06-09
I installed using the dvd version as well and it did play my mp3's then stopped.???

---

### Post by dontgetshocked on 2011-06-09
I have extras already installed as well as lame.

---

### Post by desktorp on 2011-06-09
Is Fluendo's software possibly part of this problem?

---

### Post by dontgetshocked on 2011-06-09
I do not have Fluendo installed and I just un-installed Pulse audio.I will re-boot and install Alsa and see what happens.

---

### Post by dontgetshocked on 2011-06-09
I installed from cd but now have dvd but dont know how to install codecs.

---

### Post by BrokenKingpin on 2011-06-10
Install Ubuntu-Restricted-Extras... as far as I know it should be available from Mint (as it uses the Ubuntu repos).

---

### Post by dontgetshocked on 2011-06-10
I already have them installed as well as the codecs off the dvd and still no sound or video.

---

### Post by mips on 2011-06-10
> **dontgetshocked said:**
> I already have them installed as well as the codecs off the dvd and still no sound or video.

Then you might have hardware related issues.

---

### Post by dontgetshocked on 2011-06-10
You may be right,if so it's another distro for me unfortunately.
Thanks,

---

### Post by YesWeCan on 2011-06-10
The welcome screen has one-clicks to upgrade to DVD and to install codecs.

If you have disabled the welcome screen you can find it again in Control Centre.

---

### Post by pmcartney on 2011-06-10
I concur with YesWeCan.  Never install MINT from the DVD it says so in the instructions!!  From the cd download the "DVD" editon then the Codecs above it, THEN the upgrages sitting in your tray.  Do this in that order.  However you can get DVD playback free with no Fluento here: ```
http://ubuntuforums.org/index.php
```  Do all it says which if I can do it as a newbie so can you in a TERMINAL.
Cltl-alt-t
 
Guess what it works.
 
 
:popcorn:

---

### Post by athenroy on 2011-06-11
I just gave Mint 11 a spin from the Live DVD and it played MP3s fine.  In fact, they were stored on my Windows partition.

---

