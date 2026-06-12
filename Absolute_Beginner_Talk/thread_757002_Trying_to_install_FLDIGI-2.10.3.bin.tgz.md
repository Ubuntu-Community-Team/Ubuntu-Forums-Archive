---
title: "Trying to install FLDIGI-2.10.3.bin.tgz"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by n0us on 2008-04-16
I'm a Linux newbe!  I want to install the amateur radio digital communications program that uses a soundcard: FLDIGI, the newest version is 2.10.3.  I was able to load an earlier version using either Add/Remove Programs or Synaptic and I can bring it up but haven't used it. 
I can't get either of those loaders to find the newest version even by adding extra repositories.  If I download the version I want ( it's a pre-compiled binary ) I can't get it installed, it just sits there and looks at you when you either right click on it or double click it!
A dependency is HAMLIB 1.2.6
I would rather do this using the GUI and not the terminal.
I'm pretty sure I'm not the only one stuck on this.

               Thanks, Steve - N0US in Nebraska

---

### Post by Het Irv on 2008-04-16
Try right clicking on the the file that "just sits and stares at you"  go to properties and then the permissions tab.  2/3 down you should see a box that says "run as executable"  make sure that this box is checked.

---

### Post by bumanie on 2008-04-16
You may find that hardy heron (1 week) has a later version in synaptic, otherwise, to install a .tgz, you will probably have to use command line.
first you need to > sudo apt-get install build-essential so that you can compile the .tgz I won't go any further if you don't want to compile via command line. Post back if you do and someone will help. you may be able to find HAMLIB 1.2.6 in synaptic, if not google for it.

---

### Post by renfrew on 2008-04-16
Steve,

Just curious?  do you have the latest HAMLIB installed? (1.2.6)... you also need PORTAUDIO2, both of these are apparently available through synaptic

You're gonna need to use archive manager or your favourite archive tool to unpack the FLDIGI tar ball to some directory.. maybe $HOME/bin?   the tar ball is the  bin.tgz that you downloaded.  It looks like thats the only way to get the most recent version, it's not in synaptic yet

check the permissions on the file... it needs to be executable... if your using nautilus just browse to whatever directory you extracted to and right click on the fldigi exe.. select properties from that menu and then look for the 'executable' check box down near the bottom of the permissions tab in the properties window...

You might want to read through the instructions at [http://www.w1hkj.com/FldigiHelp/fldigi-static.html](http://www.w1hkj.com/FldigiHelp/fldigi-static.html) and [http://www.w1hkj.com/Fldigi.html](http://www.w1hkj.com/Fldigi.html) as well

---

### Post by n0us on 2008-04-16
Thanks, I will give it a go this weekend.  Linux is going to take a bit of getting used to compared to " that other OS " !
Oh, I earlier was able to download Hamlib and Portaudio so they are there.

                     N0US

---

### Post by n0us on 2008-04-20
Well, I checked "Run as executable" in permissions ( it wasn't checked ) but no change! I notice a post regarding fldigi and needing an elmer to help install, I'm gonna need one also! Fldigi that I downloaded is a compiled binary file, the author says it should run in Ubuntu right out of the box, I shouldn't have to download the source and compile it.

                            Thanks,  Steve

---

### Post by n0us on 2008-05-18
Mostly gud news....
I upgraded from Gibbon to Heron, now the FLDIGI icon on my desktop that wouldn't do anything when clicked on, now runs the program! With no other changes, but as an added benefit - SATSCAPE now is missing in action, I reloaded it from the website but it met the fate others have mentioned programs sometimes do - it never got installed, just was able to run it once! 
So things are looking up, it took a while to upgrade via my 500Kb ISP ( it would have been nice if Ubuntu would give a time estimate or at least a download size).
Tnx to those who responded to my posts.

           Steve

---

