---
title: "Help installing Alsa 1.0.16"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Smith101 on 2008-03-31
I'm trying to fix my sounds problem and I've come across the solution though when I try to install the new ALSA I get this Error.

in the terminal
tar xvpjf alsa-driver-1.0.16rc1.tar.bz2
cd alsa-driver-1.0.16rc1
./configure --with-cards+hda-intel

after I run that it's say

Checking for GCC...GCC
checking for C compiler default output filename...configure: error: C compiler cannot create executables.

What should from here.

Can anyone help?

---

### Post by Michael.Godawski on 2008-03-31
You can try to install this package which is as the name suggests essential for compiling from source.

```
sudo apt-get install build-essential
```

---

### Post by stchman on 2008-03-31
> **Smith101 said:**
> I'm trying to fix my sounds problem and I've come across the solution though when I try to install the new ALSA I get this Error.

in the terminal
tar xvpjf alsa-driver-1.0.16rc1.tar.bz2
cd alsa-driver-1.0.16rc1
./configure --with-cards+hda-intel

after I run that it's say

Checking for GCC...GCC
checking for C compiler default output filename...configure: error: C compiler cannot create executables.

What should from here.

Can anyone help?

I have a script to automate the process.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

Worked on my HDA Intel equipped laptop.

---

### Post by Smith101 on 2008-03-31
Thanks stchman  for the awesome script though I'm having trouble executing it.

I open the terminal log in as Root. I save the file to my Home folder then I use
        chmod 755 ~/alsa_setup.sh
But that doesn't seem to work. This is that last thing I need, then I'm finally done with this. 

Thanks again stchman.

---

### Post by stchman on 2008-03-31
> **Smith101 said:**
> Thanks stchman  for the awesome script though I'm having trouble executing it.

I open the terminal log in as Root. I save the file to my Home folder then I use
        chmod 755 ~/alsa_setup.sh
But that doesn't seem to work. This is that last thing I need, then I'm finally done with this. 

Thanks again stchman.

You don't need a root terminal.

Download it to your home folder and use the chmod statement to give it executable privileges.

---

### Post by Smith101 on 2008-03-31
Ok I make the script executable but it does nothing. The terminal does nothing any ideas? The terminal quickly opens then quickly closes. Am I doing anything wrong?

---

### Post by stchman on 2008-03-31
> **Smith101 said:**
> Ok I make the script executable but it does nothing. The terminal does nothing any ideas? The terminal quickly opens then quickly closes. Am I doing anything wrong?

Do not use a root terminal.

Open up a terminal and do each command in a terminal one at a time:

```

cd ~

wget http://www.stchman.com/tools/alsa/alsa_setup.sh

chmod 755 ~/alsa_setup.sh

sudo ~/alsa_setup.sh

rm -f ~/alsa_setup.sh


```

The first line will change to your home folder.
The second line will download the script to your home folder.
The third line will change the permission of the script to execuable.
The fourth line will execute the script as root.
The fifth line will remove the script as it is no longer needed.

The PC will reboot after the script completes so you will need to do the last line after the computer reboots.

---

### Post by Smith101 on 2008-03-31
this is what I get 
--16:36:12--  [http://www.stchman.com/tools/alsa/alsa_setup.sh](http://www.stchman.com/tools/alsa/alsa_setup.sh)
           => `alsa_setup.sh.1'
Resolving [www.stchman.com](www.stchman.com)... failed: Name or service not known.

?

---

### Post by stchman on 2008-03-31
> **Smith101 said:**
> this is what I get 
--16:36:12--  [http://www.stchman.com/tools/alsa/alsa_setup.sh](http://www.stchman.com/tools/alsa/alsa_setup.sh)
           => `alsa_setup.sh.1'
Resolving [www.stchman.com](www.stchman.com)... failed: Name or service not known.

?

The URL works just great.  I do not know what the problem is.  Can you navigate to my site?

---

### Post by Smith101 on 2008-03-31
Ok I think it timed out.

~$ cd ~
~$ wget [http://www.stchman.com/tools/alsa/alsa_setup.sh](http://www.stchman.com/tools/alsa/alsa_setup.sh)
--16:46:10--  [http://www.stchman.com/tools/alsa/alsa_setup.sh](http://www.stchman.com/tools/alsa/alsa_setup.sh)
           => `alsa_setup.sh.3'
Resolving [www.stchman.com](www.stchman.com)... 209.205.39.25
Connecting to www.stchman.com|209.205.39.25|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,860 (1.8K) [application/x-sh]

100%[====================================>] 1,860         --.--K/s             

16:46:18 (131.59 MB/s) - `alsa_setup.sh.3' saved [1860/1860]

$ chmod 755 ~/alsa_setup.sh
~$ sudo ~/alsa_setup.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libncurses5-dev instead of ncurses-dev
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libncurses5-dev libstdc++6-4.1-dev
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc cvs gettext-doc
  glibc-doc manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 gettext libc6-dev libncurses5-dev
  libstdc++6-4.1-dev linux-libc-dev patch
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 6949kB/10.9MB of archives.
After unpacking 44.8MB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter






Should I insert the Disc?  Then after it's installed will it automatically reboot?

Or am I doing something wrong?

---

### Post by stchman on 2008-03-31
> **Smith101 said:**
> Ok I think it timed out.

~$ cd ~
~$ wget [http://www.stchman.com/tools/alsa/alsa_setup.sh](http://www.stchman.com/tools/alsa/alsa_setup.sh)
--16:46:10--  [http://www.stchman.com/tools/alsa/alsa_setup.sh](http://www.stchman.com/tools/alsa/alsa_setup.sh)
           => `alsa_setup.sh.3'
Resolving [www.stchman.com](www.stchman.com)... 209.205.39.25
Connecting to www.stchman.com|209.205.39.25|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,860 (1.8K) [application/x-sh]

100%[====================================>] 1,860         --.--K/s             

16:46:18 (131.59 MB/s) - `alsa_setup.sh.3' saved [1860/1860]

$ chmod 755 ~/alsa_setup.sh
~$ sudo ~/alsa_setup.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libncurses5-dev instead of ncurses-dev
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libncurses5-dev libstdc++6-4.1-dev
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc cvs gettext-doc
  glibc-doc manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 gettext libc6-dev libncurses5-dev
  libstdc++6-4.1-dev linux-libc-dev patch
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 6949kB/10.9MB of archives.
After unpacking 44.8MB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter






Should I insert the Disc?  Then after it's installed will it automatically reboot?

Or am I doing something wrong?

Delete all alsa_setup files in your home folder.  They are conflicting.

Also enable all the repositories (main, universe, multiverse, restricted) and redo.

---

### Post by Smith101 on 2008-03-31
After the reboot now I have no sound at all. When I click volume control it says:

No Gstreamer plugins or devices installed. What should I do now?

---

### Post by Smith101 on 2008-04-01
no sound, any ideas?

---

### Post by stchman on 2008-04-01
> **Smith101 said:**
> no sound, any ideas?

Does alsamixer tell you you are using 1.0.16?

---

### Post by Smith101 on 2008-04-01
No it's stuck at 1.0.14

---

### Post by Mauler5858 on 2008-04-01
Please help!!

I ran the script trying to update my ALSA, and now I have no sound.  If i try to open up volume control i get:
No volume control GStreamer plugins and/or devices found

Also when i run alsamixer i get.
```

dustin@Yoda:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

When i try to go to sound and do a test sound with Alsa Mixer selected i get:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

I am running Gutsy, and my sound card is a standard Sound Blaster Audigy 5.1

---

### Post by Mauler5858 on 2008-04-02
bump help!!

---

### Post by stchman on 2008-04-02
> **Smith101 said:**
> No it's stuck at 1.0.14

Then the latest ALSA did not install.

---

### Post by stchman on 2008-04-02
> **Mauler5858 said:**
> Please help!!

I ran the script trying to update my ALSA, and now I have no sound.  If i try to open up volume control i get:
No volume control GStreamer plugins and/or devices found

Also when i run alsamixer i get.
```

dustin@Yoda:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

When i try to go to sound and do a test sound with Alsa Mixer selected i get:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

I am running Gutsy, and my sound card is a standard Sound Blaster Audigy 5.1

That script is mainly for Intel HDA sound cards.

The script automates the commands from this website.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I have an Audigy 2 and it works PERFECTLY out of the box with Ubuntu.

---

### Post by Mauler5858 on 2008-04-02
How can i revert back to my out of the box settings?

---

### Post by Forcestar on 2008-04-02
I have a similar problem to Mauler, someone suggested I use this script ([http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)) to get alsa, now my sound isn't working either...

---

