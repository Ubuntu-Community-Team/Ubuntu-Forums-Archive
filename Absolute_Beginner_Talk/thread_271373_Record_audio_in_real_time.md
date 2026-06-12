---
title: "Record audio in real time"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by IanVaughan on 2006-10-04
Hi, I need to be able to record live audio feeds to disc.
How can I do this?

The audio is via a website that I cant stream, so under windows I normally just started it playing and then set a timed recorder to record the system mixer.

---

### Post by shanepardue on 2006-10-05
audacity is your ticket to recording in real-time. i've heard good and bad things.

---

### Post by bodhi.zazen on 2006-10-05
You could try [url=http://streamripper.sourceforge.net/
]streamripper[/url].

---

### Post by haiku99 on 2006-10-08
the simplest way is to use the record command from sox:

[B]bill@bill-laptop:~$ rec sample.ogg
Send break (control-c) to end recording[/B]


rec has many options...

[B]bill@bill-laptop:~$ rec -h
Usage: rec [OPTION]... FILE [EFFECT]...
Play/record sound files to/from unix style sound devices.

  -c, --channels=CHANNELS      specifies the number of sound channels in FILE
  -d, --device=DEVICE          use DEVICE for input/output
  -f, --format=FORMAT          specifies bit format of sample
                               FORMAT is either s, u, U, A, a, or g
  -r, --rate=RATE              sample rate in hertz of FILE
  -s, --size=SIZE              interpret size of sample
                               SIZE is either b, w, l, f, d, or D
  -t, --type=TYPE              specifies file format of FILE
  -v, --volume=VOLUME          change amplitude
  -x, --xinu                   reverse bit order of sample
                               (only works with 16-bit and 32-bit integer data)
      --file                   next argument is FILE
  -h, --help                   display this help and exit
      --version                output version information and exit
      --silent                 do not display filename of currently played file

EFFECTs are one or more of the following:  avg, band, chorus, copy, cut,
deemph, echo, echos, flanger, highp, lowp, map, mask, phaser, pick, polyphase
rate, repeat, resample, reverb, reverse, split, stat, vibro.

See sox man page for detailed information on supported file types, data
formats, and effect options.
bill@bill-laptop:~$





[/B]

---

### Post by shanepardue on 2006-10-08
i think the simplest is the sound recorder under the sound and video menu, but to each his own.

---

### Post by yasoumalaka on 2006-10-12
Hands down streamripper, with kstreamripper it is awesome. You just enter the  name, url, and description and bam your done. It saves all the info for you and you can use it to just listen if you want. Aslo you can simultaneously record multiple streams. This is more than I ever wanted out of a windows radio recorder that cost 30-40 dollars, but this program is free. Snap aint that the shiznit!

---

