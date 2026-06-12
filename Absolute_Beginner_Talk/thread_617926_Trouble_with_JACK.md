---
title: "Trouble with JACK"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-11-19
I don't know why, but I can't get JACK to work for me in Gutsy. When I execute the program, it fails and gives the following message:```

18:13:10.579 Patchbay deactivated.
18:13:10.672 Statistics reset.
18:13:10.683 Startup script...
18:13:10.684 artsshell -q terminate
18:13:10.769 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/nick/.kde/socket-harefoot.
18:13:11.041 Startup script terminated with exit status=256.
18:13:11.042 JACK is starting...
18:13:11.042 /usr/bin/jackd -R -dalsa -r44100 -p128 -n2 -D -Chw:1,0 -Phw:1,0 -i2 -o2
18:13:11.056 JACK was started with PID=6907 (0x1afb).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210426688, from thread -1210426688] (1: Operation not permitted)
cannot create engine
18:13:11.240 JACK was stopped successfully.
18:13:11.241 Post-shutdown script...
18:13:11.241 killall jackd
jackd: no process killed
18:13:11.266 MIDI connection change.
18:13:11.450 Post-shutdown script terminated with exit status=256.
18:13:13.331 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```

Please, I just want to do some simple recording. Any help would be wonderful.

---

### Post by doctorbighands on 2007-11-19
Incidentally, is there a multi-track recording program out there for Ubuntu that DOESN'T require the use of JACK? I don't understand JACK; I find it to be nothing but unnecessary and inefficient, and just another thing to go wrong and cause problems. I never saw or had to use anything even remotely like JACK in Window$, and I don't get why I have to use it now. Yes, I know "Linux isn't Windows"; that response doesn't help me. In ACID, Cubase, ProTools, etc., I just plug my preamp directly into my computer, and away I go. Why can't it be that way here? Why do I need some silly third-party roadblock like JACK? I just want to do some painfully simple recording, and I STILL can't figure out any combination of JACK+recording program that will even accomplish that.

So...can I get around the JACK monopoly?

---

### Post by deadgobby on 2007-11-19
Are you using Ubuntu Studio or are you using jackd as a stand along? One is it install Jack Control. This will give you a GUI interface to work with. This will make some easy than using the terminal. Second. There is time you need to make a link from midi device to softsynth to be played.
 See screen shots
Gobby

---

### Post by multifaceted on 2007-11-19
I can't get JACK to work either... and I use Feisty.  If only there were a true digi-direct recording program that works seamlessly...

---

### Post by doctorbighands on 2007-11-19
I'm not using UbuntuStudio. I have the qjackctl GUI installed, and I'm using that.

---

### Post by deadgobby on 2007-11-19
If you want music programming stuff and seems to work very well. There is a Studio 64
[http://www.64studio.com/](http://www.64studio.com/)
 DL the live Cd and try it out. Now, if your sound card does not work off the bat, you need to open up the terminal window in S64 and type in alsamixer and turn up the volume levels.
Gobby

---

### Post by doctorbighands on 2007-11-19
> **multifaceted said:**
> I can't get JACK to work either... and I use Feisty.  If only there were a true digi-direct recording program that works seamlessly...

I wholeheartedly agree.

Truth be told, I haven't managed to get ANY program working seamlessly in Ubuntu so far. Every single time, I run up against weird issues and have to spend the better part of a day troubleshooting.

Okay, maybe that isn't fair...the included Chess program seems to work fine. :mad:

---

### Post by doctorbighands on 2007-11-19
> **deadgobby said:**
> If you want music programming stuff and seems to work very well. There is a Studio 64
[http://www.64studio.com/](http://www.64studio.com/)
 DL the live Cd and try it out. Now, if your sound card does not work off the bat, you need to open up the terminal window in S64 and type in alsamixer and turn up the volume levels.
Gobby

I'll take a look at it. Thank you.

---

### Post by deadgobby on 2007-11-19
Just put in your mind that you require to make links in Jackd with like Rosegarden recording program and so on. Look at this way. Have you ever seen those old modular synths with wires that connect from this to that? Jackd kinda of does the same thing. 
Gobby

---

### Post by multifaceted on 2007-11-19
> **doctorbighands said:**
> I wholeheartedly agree.

Truth be told, I haven't managed to get ANY program working seamlessly in Ubuntu so far. Every single time, I run up against weird issues and have to spend the better part of a day troubleshooting.

Okay, maybe that isn't fair...the included Chess program seems to work fine. :mad:

Fortunately for me, audio recording is the only application that I cannot seem to get working. Most everything else has been relatively easy. However, until I figure this out, I shall still dual boot into WinXp to use Cubase and Reason[I]....Shhhhhhh......
[/I]

---

### Post by rexxxlo on 2007-11-19
i have a question about jack too i try to start and it tells me it is already running

cannot create jack client 
is the jackd server already running 

but i have never used it ?

i want a program like the kxdriver  in winblows to do crossover duty's in the computer and send the lows to one amp and the higs and mids to another one

cant even get jack to run to test it

---

### Post by Drunky on 2007-11-21
> **doctorbighands said:**
> I don't know why, but I can't get JACK to work for me in Gutsy. When I execute the program, it fails and gives the following message:```

18:13:10.579 Patchbay deactivated.
18:13:10.672 Statistics reset.
18:13:10.683 Startup script...
18:13:10.684 artsshell -q terminate
18:13:10.769 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/nick/.kde/socket-harefoot.
18:13:11.041 Startup script terminated with exit status=256.
18:13:11.042 JACK is starting...
18:13:11.042 /usr/bin/jackd -R -dalsa -r44100 -p128 -n2 -D -Chw:1,0 -Phw:1,0 -i2 -o2
18:13:11.056 JACK was started with PID=6907 (0x1afb).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210426688, from thread -1210426688] (1: Operation not permitted)
cannot create engine
18:13:11.240 JACK was stopped successfully.
18:13:11.241 Post-shutdown script...
18:13:11.241 killall jackd
jackd: no process killed
18:13:11.266 MIDI connection change.
18:13:11.450 Post-shutdown script terminated with exit status=256.
18:13:13.331 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```

Please, I just want to do some simple recording. Any help would be wonderful.

Iit looks like you were trying to run Jack in real-time mode.  Do you have the real-time kernel?

Perhaps Jack will not work in real-time mode without the real-time kernel?  Just a suggestion.

---

### Post by Steveway on 2007-11-21
> I find it to be nothing but unnecessary and inefficient, and just another thing to go wrong and cause problems. I never saw or had to use anything even remotely like JACK in Window$, and I don't get why I have to use it now.
Not understanding something and then not getting it to work does not equal with it beeing unnecessary and/or inefficient.
If you read through what jack does, what it can do and how it does it then you will see how awesome it is.
There isn't even something as good as it avaiable for windows.
Also I think Drunky is right, i had the same message when I tried to run it in real-time-mode. A tip from me, if the sound through jack seems to stutter then decrease the sample-rate in jack.
Check my Sig for _one_ example program that uses jack.

---

### Post by Drunky on 2007-11-21
> **rexxxlo said:**
> i have a question about jack too i try to start and it tells me it is already running

cannot create jack client 
is the jackd server already running 

but i have never used it ?

i want a program like the kxdriver  in winblows to do crossover duty's in the computer and send the lows to one amp and the higs and mids to another one

cant even get jack to run to test it

I can't spend too much time to work through this (I'm at work) but I will share some of my experience.

When I first tried to start Jack it wouldn't let me.  It told me that it couldn't connect to the server also.  First I had to adjust the settings first, then Jack started for me.  

You might try [this]("https://help.ubuntu.com/community/HowToJACKConfiguration") and [this]("https://help.ubuntu.com/community/HowToQjackCtlConnections") Ubuntu Help wiki pages as reference.

And lastly, a tip:  it is more useful to explain *how* you tried to start the application and the exact error message.  This will really allow people to key in on what might be the problem.

---

### Post by acl123 on 2007-11-21
I finally got JACK running but the sound is all distorted during playback.

I'm not sure where to start.

Can anyone point me in the right direction?

I am using both ZynAddSubFX and Ardour and they are both distorted.

Also, I don't understand this "real time kernel" thing... can someone explain what it is all about and whether I have to worry about it.

---

