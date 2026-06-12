---
title: "Making Logitech 350 USB headset work the easy way."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by blazoner on 2007-07-25
Here are the steps I used to get my Logitech 350 USB headset working using Feisty Fawn 7.04. 

(This is basically a note to myself, in case I have to reinstall from scratch, and have lost all my notes yet again, but I hope it helps others with the same process.)

1) Plug in the headset. (It should automatically detect it. You also may need to reboot.)

2) Verify that your system detected your device. Open a terminal, then type (or copy and paste):```
cat /proc/bus/input/devices
```It should output with a section something like this:> I: Bus=0003 Vendor=046d Product=0a02 Version=0100
N: Name="Logitech Logitech USB Headset"
P: Phys=usb-0000:00:13.0-3/input3
S: Sysfs=/class/input/input4
H: Handlers=kbd event4 
B: EV=3
B: KEY=c000000000000 0


3) Go to System>Administration>Services and check the box next to Audio Settings Management (alsa-utils).

4) Go into System>Preferences>Sound and choose USB Audio for all your options.

5) In your terminal, type (or copy and paste):```
asoundconf list
```Your headset should be listed. Mine was listed as "Headset". Again in your terminal, type/paste:```
asoundconf set-default-card Audio
```Replacing "Audio" with the name of your headset. "Headset" in my case.


You should now have basic functionality from your headset.

6) Now, go into System>Preferences>Sound, highlight  "Speaker" in the box under "Default Mixer Tracks" and close Sound Preferences.
You should now be able to change the speaker volume with the in-line volume control. If not, Right-Click the "Volume Control" applet in your panel, choose "Preferences." Again, highlight "Speaker" and close.

An important note on the Logitech 350 USB headset: The in-line "Mute" button will only mute and unmute the headset microphone, and cannot be mapped to the system mute. This is because it doesn't send any information to the system at all, rather, it is a hardware function of the headset that disconnects the feed to and from the microphone only.

These are the basics. There is information out there on advanced topics such as swapping back and forth between sound drivers whenever your headset is plugged/unplugged as well. If I end up running across that stuff again, I'll either write it up, or include links to it in this tutorial. In the mean time, Google is your friend.

---

### Post by panth0r on 2007-10-16
Thanks man, this little helper got at least sound working on my Logitech 350 Headset on an IBM Thinkpad T42 running 7.04 Ubuntu.  Thanks again!

---

### Post by lifeontilt on 2007-11-30
Thanks a bunch for the info!
I am newbie and small guides and how to's like this help many people use Ubuntu more and more everyday. This is an ideal example of something useful that people should share instead of keeping it in private note. After all this is what Ubuntu is all about.

---

### Post by kthxbai2u on 2007-12-15
>>>.<<< O_______________--ooo i got basic functionality, in the sense i can control the volume from the control on the headset wire, but nothing coming out of the headphones. I got lost at the "preferences" part. this doesnt seem to exist O_o I have system settings, a settings menu, a system menu, a utilities menu, and nowhere in the audio config that i did find can you select to output to usb. I think im missing a sound config-tool package or something? O_o:confused::confused::confused::confused::confused::confused::confused:

[EDIT]Ehhmm... Are you using Gnome? Cause I'm KDE. I'm going to try to use Gnome but I use KDE for my programming because I have it set up the way I like. If I configured it to work in Gnome would it work in KDE?[/EDIT]

[EDIT2]Yeh its in Gnome and the settings cross over to all accounts in each session type :D ty for cached page i add to my not yet created wiki :D[/EDIT2]

---

### Post by howardf42 on 2007-12-22
1) Plug in the headset. (It should automatically detect it. You also may need to reboot.)

**lsusb shows the Logitech Headset present.**

2) Verify that your system detected your device. Open a terminal, then type (or copy and paste):```
cat /proc/bus/input/devices
```It should output with a section something like this:

**Operative word: "should"  No such device shows up here.**

3) Go to System>Administration>Services and check the box next to Audio Settings Management (alsa-utils).

**Check.**

4) Go into System>Preferences>Sound and choose USB Audio for all your options.

**Not available in any of the pull-down lists**

5) In your terminal, type (or copy and paste):```
asoundconf list
```Your headset should be listed. Mine was listed as "Headset". Again in your terminal, type/paste:```
asoundconf set-default-card Audio
```Replacing "Audio" with the name of your headset. "Headset" in my case.

**There's that word "should" again. Only thing listed is the built in Intel chipset, ICH6**


You should now have basic functionality from your headset.

**Man, you sure like that word!**

These are the basics. There is information out there on advanced topics such as swapping back and forth between sound drivers whenever your headset is plugged/unplugged as well. If I end up running across that stuff again, I'll either write it up, or include links to it in this tutorial. In the mean time, Google is your friend.[/QUOTE]

**I'd like to get to the advanced stuff if I can only get the basics down.  Thanks for any help you or anyone else can contribute.**

---

### Post by kaston on 2007-12-30
ok this guide got my headset working properly, which is great but now i can't seem to get sound back to my laptop speakers again.  i basically reversed all of the instructions.

went into System>Preferences>Sound and chose "autodetect" for all options, which was the setting before i changed them to USB headset

then typed the following into a terminal:
asoundconf list  

which only listed "Intel"

then typed:
asoundconf set-default-card Intel 

but i still have no sound from my normal laptop speakers.  help!

---

### Post by Spydr4590 on 2008-01-27
This guide is gold love it and cherish it.

---

### Post by tehceej on 2008-04-17
I did everything the tutorial said to do.  Ubuntu recognizes my device, Logitech 350, my sound card works with speakers, but guess what?

**My headset will not work**

Any suggestions?

---

### Post by blazoner on 2008-04-17
What is the output of ```
asoundconf list
```in your terminal?

---

### Post by wormser on 2008-04-24
This worked for me with a Logitech ClearChat Comfort USB Circumaural Headset.  I had to reboot to get the mic to work. 

Thanks.

---

### Post by mike0000 on 2008-06-12
haha i cant get past the first step, the computer doesnt recognize it? the blue light on the volume control doesnt come on. any ideas?
im sure this is a stupid question but nothing is working

---

### Post by ex.hav0k on 2008-06-27
i have the audio working great until i try and adjust the volume, at which point the left channel goes all the way down and the right channel is the only one control able.  i tried to click the link button below the two channels, but they won't link unless i move the right channel all the way down to where the left channel is.  as long as i don't try to adjust the volume (system volume or inline volume) the levels will stay the same.  they reset if i unplug it and plug it back in.  is there anyway to fix this?

also, im having troubles getting my mic/audio to work with teamspeak.  i'll probably try and google that, but if anyone can point me in the right direction, i'd be very grateful.

---

### Post by ex.hav0k on 2008-06-27
i got the headset to work with teamspeak by putting /dev/dsp1 as the sound driver, but the volume thing is still an issue.

---

### Post by ex.hav0k on 2008-06-27
ok, so, after screwing around for a while, i kinda got the headset to work as i like.

after setting alsamixer as the default sound controller by following your setup, i was stuck with these media buttons that would still control the gnome-volume-manager controls.  i tried to look under the keyboard shortcuts to see if i could change the command of the keys, but it would not let me change the command, just the key.

so, i didn't know how else to set the keys to run a command so i downloaded xbindkeys.

```
sudo apt-get install xbindkeys xbindkeys-config
```

now, xbindkeys-config allows you to use a GUI to edit the .xbindkeysrc located in your home directory.  you can edit it by hand or you can use the GUI... the GUI is a lot more helpful than trying to follow the examples they have in the docs.  soooo.

```
xbindkeys-config
```

(you're going to want to go to the keyboard shortcuts under system>prefs>keyboard shortcuts and disable your media buttons, at least the volume ones.  click to reassign and push backspace.)

now that they're unassigned:

click new, name it mute, click get key and push your mute key to register it as the key you want to assign the command to.  now in the action box, put:

```
amixer set Speaker toggle
```

this will allow the mute button to mute and unmute when pressed.  (this part took me a while to figure out and i almost wrote a script before my friend was like, just put toggle, see if that works.)

next, you'll want to do your volume-down in the same format with this action:

```
amixer set Speaker 5%-
```

and volume-up:

```
amixer set Speaker 5%+
```

so now, instead of the buttons ******' with your levels through gnome-volume-manager, they'll control the alsa levels.


the one thing that i wanted to know how to do was how to remove gnome-volume-manager without having to uninstall ubuntu-desktop.  i removed the volume applet, and i want to see if theres a alsamixergui applet that can replace it.

---

