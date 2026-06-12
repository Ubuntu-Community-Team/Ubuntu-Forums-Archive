---
title: "JACK help"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by lilro on 2007-05-22
hey everyone, im extremely new to the linux scene and im having problems with JACK. i downloaded it via Applications -> Add/Remove -> search: JACK.
after it was installed, i don't understand how to get it to run in order to use Ardour GTK, jackbeat, Jack Control, JackEQ and Jack Rack. im stuck and i have no clue what to do next. plz help:D:D

when i try to run Ardour, i get the error: 
Ardour could not connect to JACK. There are several possible reasons:
1) JACK is not running.
2) JACK is running as another user, perhaps root. (I have no clue what this means.)
3) There is already another client called "Ardour".
Please consider the possibilities, and perhaps Re(start) Jack.

To make it simple, i don't know how to start it.

---

### Post by apunc1 on 2007-05-22
i'm not exactly sure what Jack is, but you if you can't find it in your applications folder anywhere open up a terminal (Applications > Accessories > Terminal) and type the name of the program you installed using synaptic. For example if the program was called "Jack" then type

```
Jack
```

in the terminal to run the program.

---

### Post by lilro on 2007-05-22
ok i tried that and got this:

```
This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *error* Access of CD device /dev/cdrom resulted in error: Input/output error

```

---

### Post by apunc1 on 2007-05-22
[http://ubuntuforums.org/showthread.php?t=431066](http://ubuntuforums.org/showthread.php?t=431066)
[http://ubuntuforums.org/showthread.php?t=327719](http://ubuntuforums.org/showthread.php?t=327719)

---

### Post by lilro on 2007-05-22
thanks for the help. i tried both of those and still can't get it to work. i tried typing jackd in the terminal and got this:
```

jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --silent OR -s ]
             [ --version OR -V ]
         -d backend [ ... backend args ... ]
             The backend can be `alsa', `coreaudio', `dummy',
                                `freebob', `oss' or `portaudio'.

       jackd -d backend --help
             to display options for each backend


```

again, im very new to linux and really have no clue what im doing. but once i get a GUI up then i can figure it out.

---

### Post by apunc1 on 2007-05-22
What program do you want Jack to use? Maybe you can access Jack from that program. From reading the FAQ, it doesn't sound like JACK or its components have a GUI.

[http://jackaudio.org/faq](http://jackaudio.org/faq)

---

### Post by lilro on 2007-05-22
i am trying to use Ardour GTK along with jackbeat,  JACK Control, JACK EQ, and JACK Rack

---

### Post by apunc1 on 2007-05-22
> **lilro said:**
> i am trying to use Ardour GTK along with jackbeat,  JACK Control, JACK EQ, and JACK Rack

duh, you said that in your original post, sorry.
[http://ubuntuforums.org/showthread.php?t=443271&highlight=Ardour+GTK](http://ubuntuforums.org/showthread.php?t=443271&highlight=Ardour+GTK)

---

### Post by lilro on 2007-05-22
still didn't work...bump

---

### Post by Patrick K on 2007-05-22
run this command> /usr/bin/qjackctlYou shouldn't need to be root. If you don't have it, it is in the repos. You can install it from Synaptic search for "qjackctl".

---

### Post by lilro on 2007-05-22
yes it worked!! thanks a bunch

---

### Post by Patrick K on 2007-05-22
You can make a menu item, also, so you don't have to run it from the terminal. Just use that command.

---

### Post by michwill on 2007-05-29
Why are we forced to use JACK again?  Who was the genius architect behind that system?

---

