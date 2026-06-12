---
title: "'Wine' for 'Mac OSX' apps?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by jyba on 2007-04-28
Before I get launched on a minor rant, here's my question:

Is there anything like 'wine' for Mac OSX applications? 

After seven years on a Mac I have been using Ubuntu for about five months. I am unbelievably happy with it. I can do things now that I could not have done, or could not have afforded to have done on a Mac. The only grit in the oyster is that sometimes I like to write music. I write it in midi format, use a good quality midi bank to play it back, and when I'm happy with it I export it as an ogg file (or mp3, aif, wav whatever, I don't care, but I want to be able to export it).

 I've just spent the day downloading 'jack', 'lilypond', 'rosegarden', 'qsynth' etc. etc. and have got completely lost. I may be thick but it took me half a day to discover the command 'jackd -d alsa', and even then when I use the command, more often than not, and for no apparent reason I get the stderr...

```
'JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
```

...and, of course, jackd doesn't say which application is using 'device hw:0' and 'ps aux' doesn't help, so I can't stop it, so rosegarden and qsynth won't start up, so I'm left tearing what's left of my hair out; and then for no apparent  'jackd' suddenly works, But neither rosegarden nor lilypond come with any sf2 files, so I have to google for them and they are in sfark format and that requires the sfarkxtc_lx86 unzipper which is supposed to work on linux but doesn't, so in desperation I install 'wine' and download the windows version of it and unpack my sf2 database and gradually everything begins to work but then I find that I can't export the results to ogg.

To cut a long story short, I used to use a beautiful piece of Mac OSX shareware called 'Harmony Assistant'. I could write music on old fashioned staves, it had a midi bank to play back the music, and I could export the final results in ogg or any other format. Is there anything like 'wine' for OSX that would allow me to use the one piece of OSX software that I cannot do without? Alternatively, can anybody talk me through the train-wreck that is audio on linux?

---

### Post by unixdotseth on 2007-04-28
i really dont think there is anything out there  

apple is pretty strict about that kind of stuff

---

### Post by mojo123 on 2007-04-28
if your really desperate you can use wine for a windows application thats runs mac osx applications (not reccomended!)

---

### Post by jyba on 2007-04-28
> **mojo123 said:**
> if your really desperate you can use wine for a windows application thats runs mac osx applications (not reccomended!)

Okay, say I was that desperate, and I'm not saying that I am, how would I do it? :)

---

### Post by mojo123 on 2007-04-28
I doubt it will work but, you can use wine to run a windows application thats runs mac apps


Linux with wine running- a mac emulator for windows running- Your application

---

### Post by unixdotseth on 2007-04-28
i dont think there is a windows app that runs osx apps

anyways your not happy with os x ?

---

### Post by jyba on 2007-04-28
> **sethjliford said:**
> i dont think there is a windows app that runs osx apps

anyways your not happy with os x ?

Yes, sorry, I should have made myself clearer. I am much happier with Kubuntu than I was with OSX, and I wouldn't even consider going back to Windows (which I haven't used for 11 years). 

My problem is that there is one piece of software that I used under OSX which I cannot seem to replicate under linux; hence my request for a virtual machine that could operate that piece of OSX software on the linux platform.

---

### Post by unixdotseth on 2007-04-28
are you running on APPLE HARDWARE ?

and if you are what are the specs?

---

### Post by jyba on 2007-04-28
> **sethjliford said:**
> are you running on APPLE HARDWARE ?

and if you are what are the specs?

I have two old machines. One is a Mac G4 with a 1Gh processor and 1 GB RAM. The other is a pc with a 1 Gh processor and 750 MB of RAM. The Mac has Mac OS 9.2, Mac OSX 10.2.8, and Mac Ubuntu. The pc has Ubuntu and Kubuntu. I have made my home on the pc using Kubuntu and I was rather hoping that I might pull all my old Mac applications across to the pc. I mainly used to use emacs, python, teTex, bash and csound on the Mac and they are all available on the pc using Kubuntu. My only problem is midi music software, which doesn't appear at first sight  to be as advanced on linux.

---

### Post by teddybairs1 on 2007-04-29
Maybe I'm way out of my league here, but is there any way of installing OSX in a virtual environment on Ubuntu using QEMU or another VM software? That way he could have his cake and eat it too. I used to run Win 98 in Qemu (and reactOS, and BeOS) for some games I wanted to play. Ran real well too. 

Just a thought.

---

### Post by unixdotseth on 2007-04-29
i have a apple computer in my basement 

i have a imac g3 
10 gb hardrive
768mb of ram
OS X 10.3

but it runs pretty good
i bought it off ebay for about $70 
it can run tiger but panther works much smoother
it doesnt seem to like any version of linux

---

### Post by eternalsword on 2007-04-29
What kind of audio setup do you have?  When alsa gives that message, it means that a program is hogging the sound device by not mixing.  If you go to the #alsa channel on freenode someone will likely be able to help you as they helped me when I had that problem.

---

### Post by badhat on 2007-05-01
Jyba, so far I have not tried OSx emulation, nor MIDI sequencing, but I have been reading about both, so FWIW:

Regarding OSX in a VM, I think Teddybairs1 is right:  Some people seem to be running OSx86  in QEMU or VMWare.  Evidence is at these links: 
 . ["Why are you still running OSX in a virtual machine?"]("http://forum.insanelymac.com/lofiversion/index.php/t35503.html")
 . ["Run OSX in QEMU"]("http://forum.insanelymac.com/lofiversion/index.php/t5055.html")

If you want to get up to speed on the subject, you might start with the links at the bottom of the [Wikipedia article on OSx86]("http://en.wikipedia.org/wiki/Osx86")

Regarding sequencers under Linux:  If you are still having trouble but still interested in Rosegarden, you might try and see if it works for you under MEPIS or PCLinux live CDs.   I suggest that, because I just read a blog where [someone said it worked easily with Mepis]("http://tinyurl.com/29stgo")  and another blog where  [someone implied it worked with PCLinux]("http://tinyurl.com/27mpjy")  (Both said it was difficult with Ubuntu or Kubuntu.)

Also of course there seem to be great expectations for UbuntuStudio, but the release seems to be delayed.

---

### Post by Calash on 2007-05-01
I have a VMWare session of OSx 10.4.8 running on Ubuntu now.  It is a pain to get setup, you have to extract the DVD to a VM hard disk, then mount that disk as a second drive, and boot the VM session from the CD.  Once setup it is slow...but it works.


The Wiki posted above was the one I followed to get it running.

---

### Post by engla on 2007-05-01
Nobody talks about mac-on-linux, a mac virtual machine that is in the repositories (packages mol and mol-drivers-macosx). Some compiling needed, and I don't think the software is maintained. I compiled the kernel module and made it work under ubuntu 5.10 and 6.06, but I haven't tried it since. But it should work and os x runs decently in it (can be run in window or fullscreen mode. 

The thing is: Sound *almost* works, but the sound is a small bit distorted. OpenGL doesn't work. I think the sound bit could be pretty important for you :(

perhaps it's worth a try.

edit: I had a dual-boot partition with os x (that I never used) that I ran mol from.

---

