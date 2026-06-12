---
title: "Lives Video Editing"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by neutrino82 on 2006-08-07
How can I install Lives Video Editing System in Kubuntu? I tried with Synaptic installing the package and his dependencies (after adding deb [http://people.ubuntubrasil.org/~rclbelem/lives/dapper/](http://people.ubuntubrasil.org/~rclbelem/lives/dapper/)   binary/ to sources.list) but when I type "lives" ENTER in the shell I receive the message :"LiVES 0.9.6
Copyright 2002-2006 Gabriel Finch (salsaman@xs4all.nl) and others.
LiVES comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details." and nothing more happens...Thanks everyone for help!](*,)

---

### Post by Kobalt on 2006-08-07
This is not an italian forum - Non è un forum italiano
[http://forum.ubuntu-it.org/]("http://forum.ubuntu-it.org/")

---

### Post by Kimm on 2006-08-07
Usted debe intentar siempre hablar inglés en aquí (de modo que cada uno pueda entender). Utilicé Babelfish para traducir esto... así que espero que tenga sentido.

No entiendo cuál es incorrecto

---

### Post by neutrino82 on 2006-08-08
I translated my post to english. Sorry for the Italian.

---

### Post by greenhat on 2006-08-13
> **neutrino82 said:**
> How can I install Lives Video Editing System in Kubuntu? I tried with Synaptic installing the package and his dependencies (after adding deb [http://people.ubuntubrasil.org/~rclbelem/lives/dapper/](http://people.ubuntubrasil.org/~rclbelem/lives/dapper/)   binary/ to sources.list) but when I type "lives" ENTER in the shell I receive the message :"LiVES 0.9.6
Copyright 2002-2006 Gabriel Finch (salsaman@xs4all.nl) and others.
LiVES comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details." and nothing more happens...Thanks everyone for help!](*,)
I'm having this same problem.  I've spent a couple hours searching around the forums and Google and haven't yet come up with anything.  

Anyone have experience getting LiVES to work on Ubuntu Dapper?

---

### Post by greenhat on 2006-08-13
This may seem obvious to some, but I'm a Ubuntu/Linux noob and it took a while to figure out.

Anyway... I joined the lives mailing list and found the answer.  

You have to have "Jack" installed and the jackd (deamon I guess?) running.  I had to open a terminal and type jackd -d alsa and LiVES suddenly started working.  Actually, I don't know if it's working as in I can edit video yet, but at least the gui came up.

---

### Post by greenhat on 2006-08-13
I guess the alsa driver wasn't a good choice (no idea why :confused: ) so I picked the oss driver when I started jackd ala jackd -d oss, and it seemed to work.  

I am now editing a video with sound! :grin: 

This looks to be the best video editor I've tried in Linux land.  

It would be nice if the dependency on installing and starting jack (with the correct driver) were somehow incorporated into the package/system.

---

### Post by matty_x on 2006-08-14
I'm having the same problem as the original poster.

I added the correct repository to /etc/apt/sources.list

I then ran "apt-get update && apt-get install lives"

I issue the command "lives" from the command line, and get the following message:
> LiVES 0.9.6
Copyright 2002-2006 Gabriel Finch (salsaman@xs4all.nl) and others.
LiVES comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.


I do _not_ get a GUI or anything else.

Additionally, I attempted to install and run jackd, based on the above post by greenhat:
> 
$ apt-get install jackd
$ jackd -d oss
[QUOTE]
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
oss_driver: /dev/dsp : 0x10/2/48000 (4096)
oss_driver: indevbuf 4096 B, outdevbuf 4096 B
oss_driver: using barrier mode, (dual thread)

[/QUOTE]

After running jackd, I still do not get a GUI for lives.

Any ideas? Help?

Thanks in advance!

matty_x

---

### Post by matty_x on 2006-08-14
OK, ok, ok. I got it working.

Instead of using the "jackd" command, I needed to use the "jackstart" command. 

Pretty clear, right? </sarcasm>

> 
##Run the following after starting LiVES from the command line

jackstart --driver=oss


Hope this is of help to someone!

matty_x

---

