---
title: "No sound, can't install, Absolute Noob needs help!!!"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by QMedia on 2007-07-07
After several months of research and a very bad experience with Vista I finally decided to throw caution to the wind and scrap my Laptop OS with Linux. I went for Ubuntu Studio cause I do alot of media work. I just installed yesterday and I am a NOOB. And I mean a total Noob. I know nothing about code or anything else about programming and stuff. That being said I am having a few major issues. 

1st. I have no sound. I spent all night last night reading help sections and suggestions on how to fix the problem but nothing worked, mainly because I don't know how to make it work. I tried typing commands in the terminal but most didn't work. I know I am doing that wrong.
My sound card is being recognized and everything is unmuted. I went to ASLA but my soundcard isn't there.

When I typed "aplay -l" this is what I got

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: Conexant Analog Audio [Conexant Analog Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital Audio [Conexant Digital Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


in alasmixer everything is unmuted and full blast.

please help if you can, I don't want to go back to Windows.

---

### Post by eternalsword on 2007-07-07
best thing I did when having problems with sound was to go the the #alsa irc channel on irc.freenode.org  Open up Synaptic, it should be in the Administrator menu, or you can run it by pressing alt+f2 and then putting in 
```
gksu synaptic
```

it should ask for a password, just put in yours.

In synaptic, under the Settings menu, click on the Repositories option.  A dialog box should open up.  Make sure the top four boxes are checked, the ones ending in (main), (universe), (restricted), and (multiverse).  Doing that allows you access to more programs to download.  Now close Synaptic.  At this point it is easier for me to give you instructions from the command line, so open up a terminal.

The first command you want to run is
```
sudo apt-get update
```
This will update the lists of programs that can be downloaded, and this should also ask for a password, just enter yours again.

The next command you want to run is
```
sudo apt-get install xchat
```
This will install an irc client that you can use to access the #alsa channel where you can get some good help.  When you ran the first sudo command, it should have cached your password (it keeps it cached for about 5 minutes) so it shouldn't ask for a password this time.  It may ask you to install xchat-common or some other programs.  Those are programs that are required for xchat to run, and just for your information, those requirements are called dependencies.

in xchat, you'll want to change your nickname in the preferences.
to join the Freenode server, it should be in the servers list.
to join the alsa channel, you will need to enter
```
/join #alsa
```
into the textbox next to your username.

If you need more help getting there, just ask, but those guys in the #alsa channel really know their stuff.

---

