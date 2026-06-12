---
title: "rt kernel for ubuntu ppc"
date: 2008-10-18
forum: Apple Hardware Users
---

### Post by Alexstone on 2008-10-18
It feels like i've damned near scoured the planet looking for an answer to this, but i've yet to find an RT kernel for Ubuntu PPC. 

I have a full workstation setup with a AMD dual core X2 with Ubuntustudio, (i'm a full time composer of classical music) and it works well with the Ubuntustudio flavour.

But i also have an old G4 laptop that i use when travelling, and jotting a few notes down. I've dumped MacOS, and this laptop does good service with the PPC version of Ubuntu.
However everything is, by nature of the non RT construction, non realtime, and as expected the latency is woeful.
I've tweaked a lot to get Ubuntu running well on the laptop,  but i've hit the buffers now in regards to writing music, and using Audio/Midi programmes. I built a 2.6.27 kernel using dpkg that increased the Hz to 1000, and that works ok, but it's not realtime, there's a continuing challenge with the RTC timer, and a few other bits and pieces resulting from using time critical apps in a non RT environment.

So, my Questions.

1. Has anyone built an RT version of Ubuntu, or Ubuntustudio for PPC?

If so, could you please point me in the right direction to obtain this?


2. If there's no RT version, i may have to try baking my own kernel, and going from there.

Has anyone attempted this, and if so, could you please share your notes and experiences gained from doing this?


Alternatively, is there any other Linux distro PPC RT version that is already built, that i can experiment with?

I can appreciate PPC doesn't get considered as a viable alternative for those of us who own this equipment, and want to tuxify it, but i think there's enough users who would willingly dump Mac, and use Linux instead. They may not always make enough noise to be noticed, but after years of being on the sidelines, one can hardly blame potential Linux PPC users for thinking they are expected to just fade away.

I'm not criticizing anyone here, as i'm appreciative of the fact i have a linux ppc version to use, but i can imagine there's a lot of potential linux ppc users out there who would draft ppc computers into service as additional boxes for audio/video production use (using network, and/or netjack to lash 'em together), and breathe new life into a studio or graphics environment, if they had the chance.

Any help or sound practical advice for this would be appreciated.

Alex.

---

### Post by tiresia on 2008-10-21
> **Alexstone said:**
> 

1. Has anyone built an RT version of Ubuntu, or Ubuntustudio for PPC?

2. If there's no RT version, i may have to try baking my own kernel, and going from there.



I would be very interested to this subject - I am also a musician. But I never tried to build a new kernel in this direction, also because I'm not sure that it could give me a big difference on my platform (I have a PowerPC G5 2x2.5)
You may find this interesting:
[http://ubuntuforums.org/showthread.php?t=430221](http://ubuntuforums.org/showthread.php?t=430221)

---

### Post by stream303 on 2008-10-27
A quick way to reduce latency is to disable the powernowd daemon.  What I actually recommend for musicians that don't want to go the custom kernel route is to replace powernowd with **cpudyn**, as cpudyn has only two states - save and full power, and the latency is vastly improved.  You can install cpudyn from the repository, and it will automatically disable powernowd.

Powernowd is fine, but it has more than two states, and sometimes latency can become an issue in audio / editing applications.  You *could* run without any power saver, but at least cpudyn seems to behave well in this application.

---

