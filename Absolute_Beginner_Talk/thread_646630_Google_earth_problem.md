---
title: "Google earth problem"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by jeddah_fbi on 2007-12-21
Every time i start Google earth from Applications-->Internet-->Google Earth
it tries to start but it freezes like the attached pic but when i type in the terminal 

$ DISPLAY=:0 googleearth

it starts but i can't resize or move the window any solutions ??

am using ubuntu gutsy 7.10

thx :D

---

### Post by Pumalite on 2007-12-21
Remove it and reinstall it using the binary file from the site. (right click>Make it 'Executable)
Then double click and it installs itself.

---

### Post by asmiller-ke6seh on 2007-12-21
I installed Google Earth using AUTOMATIX - and it went like a dream.

---

### Post by steve-shinn on 2007-12-21
I downloaded the binary and it works a dream :)

---

### Post by Pumalite on 2007-12-21
Automatix:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by asmiller-ke6seh on 2007-12-21
> **Pumalite said:**
> Automatix:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

I'm aware of the criticisms. Still, to simply install Google Earth, it works well.

---

### Post by Pumalite on 2007-12-21
At the cost of possibly breaking your system. Simplest way is installing a binary file. And surer.

---

### Post by rune0077 on 2007-12-21
I get the same error with the binary as the OP. Something to do with 64bit maybe?

---

### Post by stchman on 2007-12-21
google earth is in the medibuntu repos.

---

### Post by tarekeldeeb on 2007-12-23
> **rune0077 said:**
> I get the same error with the binary as the OP. Something to do with 64bit maybe?

same here !

---

### Post by hyper_ch on 2007-12-23
don't use automatix, it's dangerous and as pointed out: GE is in the Medibuntu repositories. They are safe.

---

### Post by rune0077 on 2007-12-23
> **hyper_ch said:**
> don't use automatix, it's dangerous and as pointed out: GE is in the Medibuntu repositories. They are safe.

Tried that too. Same result. No luck.

---

### Post by hyper_ch on 2007-12-23
what result?

---

### Post by gabkdlly on 2007-12-23
I installed Google Earth from the Medibuntu repositories, and every time I try to start it, I get the startup image, and then Xorg crashes, bringing me back to gdm's login screen.

---

### Post by stchman on 2007-12-23
> **gabkdlly said:**
> I installed Google Earth from the Medibuntu repositories, and every time I try to start it, I get the startup image, and then Xorg crashes, bringing me back to gdm's login screen.

Do you have openGL drivers installed?  GE uses openGL for its 3D rendering.  If you do not have openGL drivers then you will crash to your login screen after trying to run GE.  Happened to my ATI equipped laptop.

---

### Post by erfahren on 2007-12-23
are you trying to run google earth with desktop effects enabled? it doesn't work well with desktop effects.

--- absolutely no need for automatix with gutsy.

---

### Post by rune0077 on 2007-12-23
> **hyper_ch said:**
> what result?

What the OP described in the first post. The loadscreen will come up, then freeze and turn grey, and then nothing happen.

---

### Post by beanco on 2007-12-26
I must not have openGL drivers installed because I keep getting sent back to the login screen.

1. how do I install the drivers?

2. I am still on feisty, is this going to be a problem?

robi

---

### Post by jeddah_fbi on 2007-12-26
I can't uninstall the google earth i have
what to do :(

---

### Post by erfahren on 2007-12-26
> **jeddah_fbi said:**
> I can't uninstall the google earth i have
what to do :(
how was it installed? through Synaptic or from a download from the Google Earth site?

---

### Post by jeddah_fbi on 2007-12-27
I followed the instructions below:
=============================================================================
 How to install Google Earth (World map utility)

Google earth is a world map viewer. It can show 3D buildings and bridges in 3D view. It shows satellite pictures by default. The latest version also includes sky viewer. See [http://earth.google.com/](http://earth.google.com/) for more details.

Google Earth is available in the Medibuntu Package archive. To install google-earth from Medibuntu:

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
sudo aptitude install googleearth

Alternatively you can install Google Earth directly from the Google installer:

Download Google Earth in to Your Desktop. Open terminal and run:

chmod +x Desktop/GoogleEarthLinux.bin
sudo Desktop/GoogleEarthLinux.bin

Follow the instructions to complete the instructions. To uninstall Google earth, do the following:

sudo su
/opt/google-earth/uninstall

=============================================================================

and it wont uninstall even with the instructions above :(

---

### Post by erfahren on 2007-12-27
if you used the instructions:
> 
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
sudo aptitude install googleearth

then you installed it from the Medibuntu repos using aptitude. You should be able to go through Synaptic Package Manager to uninstall it. (System > Administration > Synaptic Package Manager) seach for googleearth and remove it.

or you can just do:
```

sudo aptitude remove googleearth

```
-----------------------------------------------

If you installed it from a download directly from the Google (Google Earth) site then it would be different, and would actually depend on *where* you installed it to. (It *can* be installed into your home folder.) Those type of installers (.bin installers) usually have a uninstall script included with them. In those cases you just change directory into its folder and type "./uninstall" or whatever,

useful links:
[How to install ANYTHING in Ubuntu](http://monkeyblog.org/ubuntu/installing/)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by Kzin on 2007-12-28
> **erfahren said:**
> 
If you installed it from a download directly from the Google (Google Earth) site then it would be different, and would actually depend on *where* you installed it to. (It *can* be installed into your home folder.) Those type of installers (.bin installers) usually have a uninstall script included with them. In those cases you just change directory into its folder and type "./uninstall" or whatever,
I used the bin directly from google.  Just ./uninstall didn't work, sudo ./uninstall didn't work, passing the uninstall script to a shell didn't work.  I followed those exact instructions...

sudo su
/path/to/uninstall

That worked like a dream... Think you have to be root to do it.

---

### Post by erfahren on 2007-12-28
> **Kzin said:**
> I used the bin directly from google.  Just ./uninstall didn't work, sudo ./uninstall didn't work, passing the uninstall script to a shell didn't work.  I followed those exact instructions...

sudo su
/path/to/uninstall

That worked like a dream... Think you have to be root to do it.
oh ok...

GoogleEarth's installer used to install the program into a directory in the user's home folder by default. Root permissions weren't necessary. Apparently that changed.

---

