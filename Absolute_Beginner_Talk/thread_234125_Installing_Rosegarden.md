---
title: "Installing Rosegarden"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by GuitarHero on 2006-08-11
Im trying to install Rosegarden(a KDE app) in Ubuntu.  It uses scons instead of make to compile and install.  Im getting this error:
```

Checking for kde version          :  3.5.2
Checking for the qt library       :  qt was not found
Please set QTDIR first (/usr/lib/qt3?) or try scons -h for more options
ryan@tank:~/Desktop/rosegarden-1.2.4$

```
I dont know how to set the qtdir.  I checked to see if it was in usr/lib/qt3/ and it was, i dont know why its not set.

---

### Post by Perfect Storm on 2006-08-11
Why not use the Rosegarden from the repo? If you have universe enable in your sourcelist:

```
sudo aptitude install rosegarden4
```




> Checking for the qt library       :  qt was not found

You need to install the headers for QT lib.

---

### Post by GuitarHero on 2006-08-11
I searched for it and it didnt come up in add/remove program so i thought it wasnt in there.

---

### Post by GuitarHero on 2006-08-11
ryan@tank:~$ rosegarden4
Link points to "/tmp/ksocket-ryan"
Link points to "/tmp/kde-ryan"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
rosegarden: main: Showing startup logo
ryan@tank:~$ rosegarden (sequence manager): getSequencerPlugins - getting plugin information
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
[/home/ryan/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa]
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
rosegarden (sequencer): SequencerMmapper : setting size of /tmp/kde-ryan//rosegarden_sequencer_timing_block to 91012
rosegarden (sequencer): SequencerMmapper : mmap size : 91012 at 0xb5ff7000
rosegarden (sequencer): SequencerMmapper::init()
rosegarden (sequencer): Registering with DCOP server
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.10

JackDriver::initialiseAudio - JACK server not running
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
rosegarden (sequence manager): got 70462 pieces of plugin data at GUI side
Profiler : id = querying plugins - elapsed = 530ms CPU,  1.147321000R real
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up



It just repeats that last part over and over

---

### Post by msak007 on 2006-08-11
For what it's worth I never use Add / Remove Programs - for some reason I just don't like using that interface and it never finds what I'm looking for. In Kubuntu I use Adept which has real-time searching - as I'm typing something it filters the package names. But I often revert to the terminal and use "apt-cache search" to look for packages too. So for example:

```
sudo apt-cache search rosegarden
```

returned results for lilypond, rosegarden, rosegarden2, and rosegarden4.

---

### Post by GuitarHero on 2006-08-11
OK thanks for the tip, but what about all those errors?

---

### Post by msak007 on 2006-08-11
Well I had never heard of the program before seeing this thread as I'm not a musician, so I'm afraid I don't know much about it. Does the app launch and you're concerned about the errors, or does it not launch at all? There's quite a few threads on Rosegarden, but I couldn't find anything with your specific errors. The one error at the bottom that you said repeats though does mention a JACK server, which according to [this]("http://rosegarden.sourceforge.net/tutorial/en/chapter-1.html#1_3_2") tutorial on Rosegarden's SourceForge site, is required for audio playback. There are numerous JACK / JACK-related packages in the repos, you might want to take a look at them and see which ones you need to install. Sorry I can't be of more help, maybe looking through some of the threads will give you some tips or suggestions.

EDIT: As far as packages, it looks like you need to install **qjackctl**, which is a GUI for configuring the server and will in turn install the **jackd** package for the JACK server. Aside from that I'm not sure what else you would need.

---

### Post by GuitarHero on 2006-08-11
It takes forever to load, then doesnt work properly.

---

