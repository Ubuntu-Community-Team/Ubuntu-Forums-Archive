---
title: "ubuntustudio: jackd settings on macbook"
date: 2007-06-04
forum: Apple Intel Users
---

### Post by Techneon on 2007-06-04
This is more an application specific query, but for those who might be trying Ubuntustudio on a macbook, I have not been able to determine jack settings that are 'sound' (excuse the pun).

After playing around for a while, I eventually installed Feisty from scratch, and then the ubuntustudio-audio and related packages on top.  I was directed from an IRC conversation on #ubuntustudio to try using the RealTime kernel patch, found [here]("https://wiki.ubuntu.com/RealTime/Feisty").

I cannot run jackd with 'realtime' switched on if I'm not running as root (that's fine for the time being, I just want to get it working).

The following happens regardless of the Realtime priority of jackd.

When using a Frames/Period of 1024 and a Buffer/Period of 2, I get a constant stream of xruns.  If I reduce the Frames/Period below this the stream gets faster.  If I increase it jack won't start indicating that the soundcard won't work with it.

If I increase the Buffer/Period to 3, as a few guides have indicated often fixes problem, jack won't start with a Frames/Period of 1024.  I have to lower it (which is fine).  At a 512/3 combination it seems to have no errors, until I start an audio program (also must be start by root to be seen by qjackctl).  After a program is started, I will get a seemingly consistant stream of 'delay of xxxxx.xxx usecs exceeds estimated spare time of xxxxx.xxx; restart...' (the xxxxx.xxx being ever changing numbers).

Changing the Buffer/Period to more than 3 doesn't seem to affect this in any way.  Changing the Frames/Period down to 256 or lower seems to increase the rate at which the stream of 'usecs exceeds estimated spare time' are popping out.

I should note that the audio goes through phases of seemingly fine followed by horribly distorted when doing it this way.  If you have the 1024/2 default the constant output of xruns gives you all sorts of consistant pops and crackles from a broken distorted audio output, so the 512/3 is certainly a step in the right direction.

Changing the sample rate doesn't seem to affect it, changing whether it is playbcak or capture only doesn't seem to affect it.

I'm thinking that maybe the Intel HDA onboard audio chipset is just crap like any other onboard audio chipset (which isn't too much of a problem), in which case I need to look for recommendations for what else I could use for audio IO from soft synths and multi-track recording that won't give me these issues.  Ideally I'd be looking at an entry-level firewire IO box, but I'm after suggestions to either fix the problem, or what firewire box to get...

[size=1]The hardware in this case is a macbook (bought a month or two before they were replaced just recently), 1.83ghz, 2gb ram, combo drive.

Feisty w/ Ubuntustudio-audio package
2.6.20-15-realtime

Also note that I've noticed, like another person on these forums that alsamixer seems to respond strangly to the onboard speakers, I think it's treating them like some sort of semi-surround as the both the main mix and 'front' seem to control the sound that comes out of the speakers.[/size]

---

### Post by Techneon on 2007-06-04
If anyone would like more information I'm happy to supply, and if a moderator feels this may get more interest in the multimedia forum (where there are other threads on ubuntustudio), then moving it may be a good idea.

---

### Post by spacepluk on 2007-06-10
Hi Techneon,

Try running jack from the command line. I was able to make it work better this way, it seems jackctl is sending some parameters that prevent jack to run well on the macbook.

Saludosss

---

### Post by border on 2007-06-14
I have the same problem you are having
I cannot believe that the soundcard is such crap seen that osx and apple are heavily used for audio work, and the soundcard works very well using the same programs in osx (like jackd and ardour). Ok it is a standard intel sound card, but still.

I seem to be able to get it to work with jackdmp without too many xruns, but I can't run any programs with it, because I don't want to compile every program myself (again), and mess with self compiled and official packages of the same program. Is there a way to dynamically link those programs to jackdmp, so they notice it is running when starting?
Ideally I want qjackctl to work with jackdmp, but that's not a big deal, and this is not the place to ask this question I guess.

back to the macbook, it would be nice if anyone had any hints, since I don't have much time right now to debug the xruns I'm experiencing.

I thought it helped (a little bit) when changing the priorities of certain programs/IRQ's with chrt, but it didn't help enough to get a stable running jackd
jackdmp seems like the best solution

---

### Post by Simon Edwards on 2007-06-15
Have a look at this thread: [http://www.nabble.com/jackd:-A-lot-of-xruns-tf3917323.html]("http://www.nabble.com/jackd:-A-lot-of-xruns-tf3917323.html")

Setting position_fix=1 for HDA and periods=3 fixed it for me.

--
Simon

---

### Post by border on 2007-06-15
That seems to help a bit
It does improve the sound a lot, since I don't hear much of the xruns
But the rapid counting of xruns seems to continue, although at a somewhat lower rate.

Is there a way to add the option position_fix=1 when loading the module snd-hda-intel at startup??
does it work when you add snd-hda-intel position_fix=1 to /etc/modules ?

thanks

---

### Post by Simon Edwards on 2007-06-16
You can also try position_fix=2 and position_fix=3.

Adding the line "options snd-hda-intel position_fix=1" to the end of the /etc/modprobe.d/alsa-base file should make it permanent.

--
Simon

---

### Post by michaeljbergin on 2007-12-13
I had these issues as well running Ubuntu 7.10 generic on my Macbook Pro Core Duo.  The main issue was the sound quality, crackly, and the latency, unusable for Hydrogen.  I found information on mactel-linux.org that pretty much got mine working and seems to be a reliable solution.  Here are the steps I followed to get quality audio working:

1. Stop alsa-utils and remove it from runlevels
  sudo /etc/init.d/alsa-utils stop
  rc.update -f alsa-utils remove
(I had to force the removal on mine)
2. Add snd-hda-intel to /etc/modules
3. Reboot to load the new drivers.

The next step was getting jackd working well which I'm not sure I've completely figured out.  One of the biggest annoyances with jackd is in something about qjackctl.  On my system using qjackctl right out of the repository even if I set the real time priority to 1 and I see it being passed to jackd on the command line jackd still prints an error about not being able to set real time priority to 0??  The fix was to either set this to 2 in qjackctl or run it directly from the command line.  The command line that works for me is: 
  jackd -R -P1 -doss

---

### Post by fabietto0102 on 2008-01-05
Hi guys,

I have a MacBook, the latest, and running Ubuntu 7.10 and I am lately getting interested in Ubuntustudio.

What I don't know is: will Ubuntustudio with its kernel, jackd and all the apps improve the sound quality of my soundcard, or is ubuntustudio only meant to create/work with tracks? I only do playback with Amarok, I am not manipulating or composing any audiotrack, just listening. 

Thanks
Fabio

---

### Post by border on 2008-01-09
ubuntustudio is about the realtime kernel which is highly suggested if you want to play, mix, compose music, and about making audio/music creation/manipulation programs available for ubuntu users.
So if you just listen to music it's not worth the hassle.

---

### Post by phetre on 2008-06-08
In case anybody is still working on this, Hans Fugal has an [excellent essay]("http://hans.fugal.net/blog/articles/2008/06/04/jack-on-the-macbook") on his blog, hans.fugal.net/blog/.

It's worth reading the whole thing, but here's the bottom line:

> So in summary, if you don't care about dmix but only JACK (or any other application using hw:0, which can be all of them if you change your .asoundrc, but only one at a time), set position_fix=3 for snd-hda-intel e.g. in a file in /etc/modprobe.d/ with a line like this: options snd-hda-intel position_fix=3, and do update-initramfs -uk all. If you want a more balanced setup, where you can have JACK running and other well-behaved ALSA applications can use the sound card, leave the module parameters alone and set up realtime and use the following command to start JACK (or equivalent settings in QJackCtl):

/usr/bin/jackd -R -dalsa -ddefault -r48000 -p1024 -n4 -s

If you want to use PulseAudio in this situation, configure it to use the default ALSA device instead of hw:0.

If you like PulseAudio and JACK both, the ideal situation would be PulseAudio using JACK as a backend, JACK using hw:0 with position_fix=3, and the PulseAudio plugin as the default ALSA device. Unfortunately this is just a theoretical ideal, and doesn't work (yet) because of bugs. [BUT SEE BELOW! -phetre]

And finally, if you have no or limited use for JACK, but want to use PulseAudio, just change your .asoundrc as above to make PulseAudio the default ALSA device, so that all applications, ESD aware or not, use PulseAudio.

And then the next day, he posted a way to get PulseAudio working as a JACK client: [http://hans.fugal.net/blog/articles/2008/06/04/pulseaudio-as-a-jack-client]("http://hans.fugal.net/blog/articles/2008/06/04/pulseaudio-as-a-jack-client")

---

### Post by cyberdork33 on 2008-06-08
Please post in the new Apple forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by motin on 2008-06-25
> **Simon Edwards said:**
> Have a look at this thread: [http://www.nabble.com/jackd:-A-lot-of-xruns-tf3917323.html]("http://www.nabble.com/jackd:-A-lot-of-xruns-tf3917323.html")

Setting position_fix=1 for HDA and periods=3 fixed it for me.

--
Simon

Me too! Thanks man.

---

