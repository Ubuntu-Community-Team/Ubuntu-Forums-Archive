---
title: "Newer Source Version than Repository Version"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by studiesinsound on 2008-01-07
Total Noob Question Here:

I am using SooperLooper in Gutsy.
All the repositories show version 1.0.8 being the newest available.  However at the SooperLooper developers website [www.essej.net](www.essej.net), a higher version is available which is reported to solve some stability and latency issues.

I would like to use the newest version.

Questions:
1: Do I need to uninstall the version that came with Ubuntu Studio?  When I use synaptic to mark it for uninstall it says it needs to also uninstall Ubuntu Sound, which seems scary.

2: Is it common for newer versions of software to be available in source but not in the repo's?  Should I simply wait for it to show up in the repo's?  It seem slike the newer version has been available for some time so I don't know how long I should wait.

3: I read some of the discussion on installing from code and get the syntax and all that. I download the tar.gz and unpack it and then run the install, it creates the compiled executable in the same dir I ran the install in.  Is the compiled file all I need, can I simply copy that one file to my home dir and get rid of the tar.gz and unpacked files?

sorry for the noob questions.

I want the most stable version of the software but don't want to screw up my system in the meantime.

---

### Post by barney385 on 2008-01-07
Have you updated your repositories in Synaptic?

---

### Post by thelatinist on 2008-01-07
You should not need to uninstall to update this program. While it is almost always better to install a package from the repositories, if you do need to install something that isn't in the repositories it is easy to do.  I recommend you always untar the source to a new subdirectory and save it. It will make it much easier to unintall if you need to do so later.

This is the procedure I recommend.  These instructions assume that you have downloaded program_name.tar.gz to your Desktop.

```
sudo mkdir ~/src
sudo mkdir ~/src/program_name
cd ~/src/program_name
tar xvfz ~/Desktop/program_name.tar.gz
./configure
make
checkinstall
make clean
```

To explain these commands:

**sudo mkdir ~/src** creates a folder in your home directory to hold the source files for all programs you may install from source. You only need to do this the first time you install something from source.
**sudo mkdir ~/src/program_name** creates a directory to hold the source files for this program.
**cd ~/src/program_name** switches to the directory you just created
**tar xvfz ~/Desktop/program_name.tar.gz** untars the file from your desktop to the folder you are currently in.
**./configure** configures the make file for compilation.
**make** makes the package for installation.
**make install** intalls the package you just created using the make command.
**make clean** removes configuration files from the current directory.

---

### Post by Steveway on 2008-01-07
Also: Better not use make install. I would advice to use checkinstall.
Checkinstall will create a .deb that can more easily be installed and uninstalled, you can even share it with others.

---

### Post by thelatinist on 2008-01-07
> **Steveway said:**
> Also: Better not use make install. I would advice to use checkinstall.
Checkinstall will create a .deb that can more easily be installed and uninstalled, you can even share it with others.

Yes, I keep forgetting to change this.  I've edited my directions to reflect that.

---

### Post by studiesinsound on 2008-01-07
thank you everyone!

I will do this tonight and let you know the results

---

### Post by Steveway on 2008-01-07
Oh, yes I forgot one thing.
If you do a :
sudo apt-get build-dep <packagename>
then it will install the libaries and programs that are needed for compilation of the program.
That's a very helpful code.

---

### Post by studiesinsound on 2008-01-08
hey everyone, thank again for the help.
I messed around with this a bit last night.

Even though i went out to the repositories and got all the dependencies listed on the sooperlooper site, when I do ./config it does a bunch of stuff then tells me the c++ precompiler environment is not sane

so I'm missing something but this has probably crossed over into the realm of a question for the guy who built the app.

Thanks for the general knowledge and best practices on installing from source.  I get th egist.
I'm just stuck in dependency hell right now

:lolflag:

---

### Post by studiesinsound on 2008-01-08
> **Steveway said:**
> Oh, yes I forgot one thing.
If you do a :
sudo apt-get build-dep <packagename>
then it will install the libaries and programs that are needed for compilation of the program.
That's a very helpful code.

thank you steveway, I'll keep this command in mind.

 for soopelooper when I run this command it says "no package found"

---

### Post by zvacet on 2008-01-08
Do you have build-essential installed?If not  

```
sudo apt-get install build-essential
```

---

### Post by studiesinsound on 2008-01-08
interesting
I think I had to do this to get my wireless working on my dell vostro 1000
but I'll do it again, thanks for the tip.
again it will be tonight (laptop is at home)

---

### Post by studiesinsound on 2008-01-09
thank you, installed build essentials, got past that error, now ./configure works but make and sudo checkinstall give me errors indicating certain classes don;t exist in the code.
doh!

I'll email the dude from essej.net

(btw I installed the latest wxwidgets from source per everyone's instructions and that went like a champ.  I like the idea of an src dir in my home fodler.  very nice idea.)

---

### Post by studiesinsound on 2008-01-10
found some artciles elsewhere where users were having the same problem building superlooper.
1 guy seemed to think it was only on 64 bit systems.  Doesn't look like he ever got a fix.

I sent an email to the sooperlooper list serve
awaiting answer

in case anyone here was interested here's the last bit of the output after I type the make command:

if g++ -DHAVE_CONFIG_H -I. -I. -I../..    -I..  
 -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/include/libxml2  
 -I/usr/lib/wx/include/gtk-2.4 -DGTK_NO_CHECK_CASTS -D__WXGTK__
 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -g -O2 -D_REENTRANT -Os -fomit-frame-pointer -mmmx
 -msse -mfpmath=sse -pipe -Wall -D_LARGEFILE_SOURCE
 -D_LARGEFILE64_SOURCE -I/home/john/src/sooperlooper/sooperlooper-1.4.1/libs/pbd
 -I/home/john/src/sooperlooper/sooperlooper-1.4.1/libs/midi++ -MT midi_bind_panel.o
 -MD -MP -MF ".deps/midi_bind_panel.Tpo" -c -o midi_bind_panel.o
 midi_bind_panel.cpp; \
        then mv -f ".deps/midi_bind_panel.Tpo"
 ".deps/midi_bind_panel.Po"; else rm -f ".deps/midi_bind_panel.Tpo"; exit 1; fi
midi_bind_panel.cpp: In member function ?void
 SooperLooperGui::MidiBindPanel::init()?:
midi_bind_panel.cpp:200: error: ?class wxChoice? has no member named
 ?SetWindowVariant?
midi_bind_panel.cpp:200: error: ?wxWINDOW_VARIANT_SMALL? was not
 declared in this scope
midi_bind_panel.cpp:204: error: ?class wxStaticText? has no member
 named ?SetWindowVariant?
midi_bind_panel.cpp:208: error: ?class wxChoice? has no member named
 ?SetWindowVariant?
midi_bind_panel.cpp:220: error: ?class wxCheckBox? has no member named
 ?SetWindowVariant?
midi_bind_panel.cpp:239: error: ?class wxStaticText? has no member
 named ?SetWindowVariant?
midi_bind_panel.cpp:244: error: ?class wxSpinCtrl? has no member named
 ?SetWindowVariant?
midi_bind_panel.cpp:248: error: ?class wxChoice? has no member named
 ?SetWindowVariant?
midi_bind_panel.cpp:259: error: ?class wxSpinCtrl? has no member named
 ?SetWindowVariant?
midi_bind_panel.cpp:263: error: ?class wxButton? has no member named
 ?SetWindowVariant?
midi_bind_panel.cpp:271: error: ?class wxStaticText? has no member
 named ?SetWindowVariant?
midi_bind_panel.cpp:275: error: ?class wxTextCtrl? has no member named
 ?SetWindowVariant?
midi_bind_panel.cpp:279: error: ?class wxStaticText? has no member
 named ?SetWindowVariant?
midi_bind_panel.cpp:283: error: ?class wxTextCtrl? has no member named
 ?SetWindowVariant?
midi_bind_panel.cpp:287: error: ?class wxChoice? has no member named
 ?SetWindowVariant?
make[3]: *** [midi_bind_panel.o] Error 1
make[3]: Leaving directory
 `/home/john/src/sooperlooper/sooperlooper-1.4.1/src/gui'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory
 `/home/john/src/sooperlooper/sooperlooper-1.4.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory
 `/home/john/src/sooperlooper/sooperlooper-1.4.1'
make: *** [all] Error 2
john@john-linux:~/src/sooperlooper/sooperlooper-1.4.1$

---

### Post by studiesinsound on 2008-01-11
no answer from the sooperlooper list serve.
i'm stuck using version 1.0.8 tht is in the repos until further notice.

---

### Post by studiesinsound on 2008-01-25
Solved:
So after alot of monkeying around and things were still not working, and other things were acting weird on my mahcine, I tore the whole thing down and re-installed Ubuntu Studio.
Followed everyone's tips from above and got the latest version of Sooper Looper installed with no problem.

I don't knwo what I did to screw up the system before but after a re-install of the os, I'm set to go.

Thank you everyone for your replies and advice!

-Johh

---

### Post by ^rooker on 2008-04-16
Sorry for reviving an old post, but I've just stumbled over *exactly* the same problem and reinstalling my system was simply *not* an option (Hardy tester)

The reason for the wxWindow errors is that a too old version (2.4) of "libwxgtk-dev" is installed.

Use Synaptic/Adept package manager to **remove "libwxgtk2.4-dev" and install "libwxgtk2.8-dev"**

Here's the quick commandline way:
```
sudo apt-get remove libwxgtk2.4-dev
sudo apt-get install libwxgtk2.8-dev
```


Here's a list of other SooperLooper's dependencies satisfied by packages
```
libsigc++-1.2-dev 
libxml2-dev 
libncurses-dev
libwxgtk2.8-dev
libjack-dev
libsndfile-dev
libsamplerate-dev
g++
fftw3
liblo0-dev
pkg-config
```

---

