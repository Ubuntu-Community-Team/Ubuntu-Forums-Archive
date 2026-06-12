---
title: "Ubuntu Music?"
date: 2008-01-16
forum: Art &amp; Design
---

### Post by jamesmicheallay on 2008-01-16
I've been a user of Ubuntu Studio and Gutsy/Feisty for a while now, and I am very familiary with Audio set ups (as an end-user) for music production on other Operating Systems.  Linux audio has always been cryptic, but potentially flexible.  I'd like to know some of the flexibilities that set Ubuntu Music Production apart from other, typical music production facilities.  It's also important to know the different programs available to Ubuntu, and how to set it all up so that Audio Engineering is understandable to the producer, and not just the application developer.:guitar:

---

### Post by jamesmicheallay on 2008-01-16
So, I've done some studying, and so-far, this is as much as I know about Ubuntu Audio.  Corrections would be welcomed...

What is LADSPA?
LADSPA stands for Linux Audio Developer's Simple Plugin API.  
It is a programmer's interface for creating plugins, just like Mac's AU   and Windows' VSTs.  Even though LADSPA is Linux's native plugin API, Linux 
can also use VST Plugin's via wine with most popular applications.

What is JACK?
Jack is a recursive acronym; it stands for Jack: Audio Connection Kit.
Jack is a low-latency, cross-platform, audio server.  It was originally 
designed for Linux, but has migrated to Mac OSX and recently Windows.  
Jack is unique in the sense that it allows the musician to create complex 
input/output wiring among several programs.  For instance: it is possible, 
through JACK, to wire the output of Hydrogen's Drums and Rosegarden's MIDI to 
Ardour's input for mastering.  JACK provides a simple, user-friendly interface 
to perform routing operations.

What are some applications?
BEAST is a powerful application that allows the user to create and cable 
their own instruments for MIDI use...  

LMMS is commonly called the Linux equivalent to Fruity-Loops for Windows.  
The interface is similar, but there are many different levels of functionality 
that separate it from any windows application.

Rosegarden is a popular and powerful MIDI sequencer for writing, scoring, 
and arranging musical instruments, tracks, and regions.

Hydrogen is a high-quality drum-machine that provides all the standard 
proponents of other, professional, drum machines with a very simple, but sleek
 look.
 
Ardour is the pro-tools equivalent for Linux.  It is a very versatile program 
with a beautifully dark look and a familiar interface for users of Logic and
Pro-Tools alike.  

Audacity is a widely-known audio manipulation suite that provides most of the 
essentials for editing any audio clip or sound effect a user will need.

There are many, many applications that come already on the repositories of 
modern Ubuntu distributions, and many of these programs can be installed right 
off of the install-disc.  Just try to sudo apt-get install any popular 
applications from the Ubuntu-Studio disc and it should all be there.

There are some youtube videos featuring demonstrations of music production 
using Ubuntu audio set-ups.  You can see a video of someone using Ardour, Jack,
and Jammin at this url: [http://www.youtube.com/watch?v=J-GSKglsDkg](http://www.youtube.com/watch?v=J-GSKglsDkg)

---

