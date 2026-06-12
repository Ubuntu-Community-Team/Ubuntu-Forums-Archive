---
title: "Issues that came up with new Powerbook..."
date: 2005-04-09
forum: Apple PPC Users
---

### Post by Readis on 2005-04-09
Here are the problems I found when I installed Ubuntu 5.04 last night on a fairly new 17" Powerbook.  But first, the hardware...

[list]
1.67 GHz 17" Powerbook
1.5 Gig RAM
100 Gig HD
AirPort Extreme
128 Meg ATI Mobility Radeon 9700
New trackpad with scrolling capability
[/list] 

I decided to create the partitions from scratch with Disk Utilities when I was reinstalling OSX.  That way I was able to bypass what others were doing.  Meaning, install Ubuntu to partition, reinstall OSX, and then reinstall Ubuntu.  Whatever...  To catch back up, the installs went fine.  There were no errors that came up at anytime.  However, when Ubuntu came up, I was not able to use the trackpad.  And, no sound would work.  I already knew about the Airport problems, so I wasn't surpirsed by that not working. 

To wrap this up... I have no use of the trackpad, and there is no sound coming out of the speakers.  Hard to justify the install.  But, I am hopeful.  I decided to rebuild the machine, and left a 8.5 Gig blank partition so that one day I can install Ubuntu.  I would love to run Ubuntu, just as I do on my PC, but I guess just won't happen yet.

-Readis

---

### Post by khc on 2005-04-14
Does trackpad tracks, and just not do clicks? If so you need to press alt+f2 (or fn+alt+f2).

---

### Post by buzzbuzz on 2005-04-16
i've got the same issues too [i've got exact same setup as well.....just not as much ram  :( hehe].

i'm a _complete newbie_ with linux generally, but i've found a little bit of info so far [and please excuse me if i don't get the terminoligy quite right!]:-

[list]
[*]you are right when you say that the airport extreme card is not supported [apples fault by the sounds of it].
[/list] 
[list]
[*]my trackpad doesn't work at all either [i believe this is because the older apple laps treated the pad as a usb device, but the newer ones use 'apt' or 'aft' or something like that, so 'pbuttons' doesn't help.
[/list] 
[list]
[*]sound doesn't work at all, but i have yet to look into this.
[/list] 

my first priority is to get it wifi'ed. so i've got an Enterasys Networks card [uses 'Atheros'] and tried the default install of Hoary, which detected it fine in the install stage only. however, even though i opened my network up completely i.e. no WEP, open system and allows any MAC address, it couldn't find/connect to it.
 

to cut [what is becoming!] a long story short, with hoary up and running normally it doesn't see the card and when i try to install the drivers that come with it [using 'make' in terminal] it comes back with errors........my search for a solution continues!......however, any help would be greatly received!.......

sorry to go on, but us newbies have alot of initial problems [as you lot know ;)].....and btw this is my first EVER post to any forum.........ahh, the start of a beautiful thing.........

---

### Post by buzzbuzz on 2005-04-16
a quick update......

my wifi card is now working  \\:D/ ......only because i put it in *after* hoary had loaded.
did a quick test and put the card in before it booted up and sure enough it didn't work and it wasn't found under the network settings  :? 

any ideas why, in the interest of expanding my very non-existant [for the time being that is!] knowledge of linux?

---

### Post by philcolbourn on 2005-04-21
see [http://www.ubuntuforums.org/showthread.php?t=24690&highlight=trackpad+powerbook](http://www.ubuntuforums.org/showthread.php?t=24690&highlight=trackpad+powerbook)

trackpad is probably a long way off. others recommend a usb mouse. I am purchasing a logitech mx-900. I hope it works.

UPDATE: The logitech mx-900 bluetooth mouse and keyboard work well - on x86 and ppc (both via USB port). I have not had any luck with the builtin bluetooth device, but others have.

For those that run OS X as well, the mouse and keyboard work with the builtin bluetooth just fine. They will also work when the logitech bluetooth hub is plugged into the USB port.

---

### Post by stressedboy on 2005-04-26
Hello,

To me it happened the same, on my new 12" powerbook, 1,6Ghz, 80MB, 768MBRAM.

- No sound but in the volume viewer I see something happen (soundcard not supportet), even no testbeep

- No trackpad reaction, no click, no cursor move, although a external usb mous works fine

- Brightness regulation buttons stock, volume regulation buttons work

Pleeeaasse help, I'm breaking my head in finding a solution  ](*,) 

Sam

---

### Post by nitrosx on 2005-04-27
I have the same mac (more or less) and I'm having the same issues.
The more important one is the sound: everything seems fine, but there is no sound coming out.

Anybody can give me advice???
Thanks a lot

---

### Post by caveteen on 2005-07-19
I just started a live ubuntu 5.04 on my TI Powerbook 1.0MHz on the first attempt!  'twas my first Ubuntu experience and I'm somewhat impressed.  

I first thought that the audio wasn't working by trying to play a few oggs on Rhythmbox -- I thought it appropriate to listen to SPEAKERBOXX on Rhythmbox, but that's irrelevant.  :) 

The audio came out *very* quitely from the laptop's speakers.  I then plugged my headphones into the headphone-jack and the audio level was perfect.  I haven't had a chance to look into fixing the audio levels in the laptop speakers, but using external speakers (or headphones) is an excellent workaround for now.

Is this similar to what you're experiencing?
-e

---

### Post by aspro on 2005-07-20
I have a PB 12" 1.5ghz/768mb ram

and my sound doesnt work, nor the trackpad, but does anyone know wether there is any progress on the sound front?(perhaps newer drivers in breezy?) I would use ubuntu more than my osx partition if I could listen to music, as I have a usb keyboard+mouse :)

---

### Post by Digitallysick on 2005-07-25
i have the same problem, sounds about pointless to install linux on the powerbook, better off with osx, why install something with no audio/trackpad/airport?? = pointless

---

### Post by eduardgrebe on 2005-12-05
[QUOTE=caveteen]
The audio came out *very* quitely from the laptop's speakers.  I then plugged my headphones into the headphone-jack and the audio level was perfect.  I haven't had a chance to look into fixing the audio levels in the laptop speakers, but using external speakers (or headphones) is an excellent workaround for now.
[/QUOTE]

I had this issue. Start Volume Control (double click the volume applet on the gnome bar). Go to preferences and  switches and switch on "DRC" (so that you can see and set it). Go to switches and switch off DRC.

This solved the problem for me.

---

