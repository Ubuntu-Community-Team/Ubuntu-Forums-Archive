---
title: "Upgraded to 7.10, Sound Stopped Working"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by RobbieB on 2007-11-18
Hello,
      I've just managed to upgrade from 6.10 to 7.10 and I've lost all sound in Ubuntu.

No errors came up during the upgrade process and I haven't installed any new applications.

Anyone have any ideas?

---

### Post by PointyWombat on 2007-11-18
please post:

lshw -C sound

---

### Post by swaeshampine on 2007-11-18
I, too have just upgraded to 7.10, and am having the exact same problem...

lshw -c sound:
sebastian@sebastian-nte1:~$ lshw -c sound
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

---

### Post by RobbieB on 2007-11-18
*-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-multimedia
       description: Multimedia controller
       product: SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 2
       bus info: pci@0000:05:02.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=32 mingnt=84 module=saa7134

---

### Post by PointyWombat on 2007-11-18
RobbieB,

Try [THIS]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/") post.

---

### Post by RobbieB on 2007-11-18
Followed the instructions from that post but still have no sound.

If I try to open a media file that has any audio i get the error:
"Totem could not play 'file location'
The audio device is busy. Is another application using it?"

If I open the file in Rhythmbox if just says '<title> playback paused'.

And if I go to system > preferences > sound and choose 'Test' next to sound playback I get the error message:

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."

Any help appreciated :)

---

### Post by lemmy999 on 2007-11-18
I had the same problem after upgrading. I suspect that its linked to a change in the kernel. I got round it by reverting back to an earlier version of the kernel.

---

### Post by DutyDuty on 2007-11-18
Exactly what model computer are you on?

---

### Post by srinivaschavan on 2007-11-28
I had similar problem it gutsy. Looks like PulseAudio was causing this problem. Killing the pulseaudio process solves the problem for me.

---

### Post by DutyDuty on 2007-11-28
Good for you. Mark it solved in Thread Tools!

---

### Post by mangobunny on 2007-11-28
I'm having the same problem. None of the suggestions here have worked for me. Here's the lshw -C sound output:
 *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
Any ideas?

---

### Post by jferreir on 2008-01-09
At the risk of sounding like an idiot, double click the speaker icon and make sure all the dials are turned up. 

My sound crapped out on me unexpectedly as well, and although a *single* click showed the volume was full, when I doubled clicked it, I was taken to a different screen where the volume was down. 

I don't understand it, but it worked for me...

---

