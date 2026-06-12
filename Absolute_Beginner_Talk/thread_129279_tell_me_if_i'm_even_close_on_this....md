---
title: "tell me if i'm even close on this..."
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-02-13
a lot of my problems with linux come from what i think is a failure to understand the basic nature of how computers work. as i imagine it, a computer is a machine that redirects electricity, to various parts of the machine, in order to get a particular result. i imagine that these redirections of electricity are triggered by the input of various devices like keyboard, mouse, etc. and that these input devices have a physical connection to the electricity, either directly or indirectly, that causes the electricity to be directed where it needs to go. is there anything other than electricty powering a computer, essentially? if the above isn't completely retarded, how would a file trigger the redirection of electricity? i guess if i understood how files had power, i'd have a better grasp on how linux works, if indeed linux is all about files.

(if you haven't already done so, please note that my questions require a 'computers for morons' type response. thanks.)

---

### Post by raublekick on 2006-02-13
i take it by files you mean configuration files? well, a program reads the configuration file and parses it to build usable information. 

this is just an example, and definitely not right, but let's say apt works like this:
you have sources.list
when apt loads, it reads sources.list
each line contains information, if the line begins with # then it is ignored
if the line does not begin with # then it is a repository and is stored in an array in apt called repos
then when apt figures out what packages it needs, it takes the first element of the repos array, and if that fails, it uses the next element, and so on until it finds a useful repo or it fails.

sorry if that's not really what you are asking. you are correct that a computer is basically just +/- bursts of different voltages, but there are several abstraction layers too.

---

### Post by Ptero-4 on 2006-02-13
Basically the computer processor (The computer equivalent of a person's brain or mind) Does all the electricity redirecting based on input/output instructions paased to it by the BIOS (the part that tells the computer how much hard disks it have, from which to boot, etc) and the operating system (read: Ubuntu) on your hard disk. In older computers this redirection is controlled solely by the operating system (OS) and the BIOS only controls the electricity redirection during the early boot procedure before the hard disk is turned on and the OS is run. In newer (post-2002) computers the BIOS does electricity redirection all the time and is the one that defines which OS/programs can be used by modifying the electricity that goes to/comes from the hard disk such that the processor and other devices can't comunicate clearly and correctly with the OS. All of this done depending on which OS/programs are in the system and what the user is trying to do at each moment during his/her computer usage time.

---

### Post by mcduck on 2006-02-13
I'm not sure if I followed correctly what you wrote, but I think you got the point.  It's all about electricity that controls electricity..

By the way, files are just the same, they're nothing but electricity (or changes in magnetic field when stored on your HDD, but that is converted to electricity by your disk heads when you read the disk.)

Here's a nice site with lots of articles about how things work: [http://www.howstuffworks.com/]("http://www.howstuffworks.com/")

The articles are very simple, and there are lots of them from many different areas. Some that might help you are:
[http://computer.howstuffworks.com/microprocessor.htm]("http://computer.howstuffworks.com/microprocessor.htm")
[http://computer.howstuffworks.com/hard-disk.htm]("http://computer.howstuffworks.com/hard-disk.htm")
[http://electronics.howstuffworks.com/bytes.htm]("http://electronics.howstuffworks.com/bytes.htm")
[http://electronics.howstuffworks.com/diode4.htm]("http://electronics.howstuffworks.com/diode4.htm")
[http://electronics.howstuffworks.com/digital-electronics.htm]("http://electronics.howstuffworks.com/digital-electronics.htm")

I suppose you'd have to work for Intel or some other big manufacturer to really understand what's going on inside your machine, so you shouldn't worry about that too much. For most people computers work by magick anyway, and those people still get the job done ;)

---

### Post by fuscia on 2006-02-13
[QUOTE=mcduck] For most people computers work by magick anyway, and those people still get the job done ;)[/QUOTE]

the more i can do myself, the more i can save magicks for when i really need them. (gosh, i'm wise.)

thanks for the responses so far, guys. here's a specific example of what baffles me: the other day, i installed another wm to play with. it didn't show up on the wdm menu of options, so i had to edit 'wdm.config' by just adding the name of the wm to the list. the wm then appeared on the options list and, not only that, it actually went to that wm. how does that happen? if i understood that, then i think it would be easier for me to understand the solutions offered to me for various problems and would have an idea what to use my limited initiative on, regarding further study.

---

### Post by Klaidas on 2006-02-13
This stuff is interesting, but sometimes I just try not to think about it - it gets too complicated \\:D/

---

### Post by fuscia on 2006-02-13
[QUOTE=Klaidas]This stuff is interesting, but sometimes I just try not to think about it - it gets too complicated \\:D/[/QUOTE]

i'm too lazy to go into depth myself. i'm hoping to get an informal overview, and so far, this thread is going that way.

---

### Post by Iowan on 2006-02-13
Not to cloud the issue (pardon the upcoming pun...) but most electronic devices are actually powered by SMOKE!  Electricity is only used to regulate the flow of smoke.  Once the smoke leaks out of a device, it must be replaced.

---

### Post by wrtrdood on 2006-02-13
[QUOTE=Iowan]most electronic devices are actually powered by SMOKE!  Electricity is only used to regulate the flow of smoke.  Once the smoke leaks out of a device, it must be replaced.[/QUOTE]

Quite right!  That's what's in all those little black packages.  :rolleyes: 

BTW:  a computer is simply a machine that allows humans to make more mistakes and to make them faster... :p 


Fuscia, part of what's "magic" is that developers have taken all the hard work of getting this electronic wonder to do what so fascinates us.  The electricity you describe can be reduced to the idea of electronic switches.  They are either on or off.  The *Central Processing Unit *knows of nothing else.  It has been told in what position to place those switches to give a certain result.  The advantage is that it can change those switch positions at lightening speed.

  In the early days of personal computing, giving a computer those instructions was tedious at best.  Some of us "oldies" called it "bit-twiddling".  This is called a *machine language*.  Manufacturers create the basic machine (CPU) with an internal library (instruction set) of how to accomplish certain tasks.  A programmer then feeds a list of these intructions to the CPU one at a time to produce a specific result.

What we use today is significantly more complex and thus the reason for the term "high level languages".  Reading other posts you've probably run across the mention of some of these languages such as C, C++, BASIC, Python, etc.  They are called languages because they allow us to "talk" to the mindless CPU in something similar to what we're already used to.  There is no difference in the final result.  The hardware only understands on or off.  A compiler simply converts all that human understandable prose in to something the CPU can use.

This is what you experience when you install a new package which is made up of hundreds, sometimes thousands of these lines of instructions that have already been through this conversion and are available to you in the form of something called and executable.  The mention of the configuration file is little more than you adding a new instruction to a list that a special processing component understands.  When it encounters this new instruction an entire array of special operations take place that you as the user will never even know happened.  Normally all you see is the new choice to do something different, as you described.  This is also a form of instruction.  The machine sits and waits for you to answer an implied question: what do you want me to do now?  Your selection then directs the machine to perform tasks specific to that request and execute the program responsible for making that happen.

Sorry.  I get long-winded at times.  :)   I hope this sheds a little light on the subject, though.

---

### Post by fuscia on 2006-02-13
wrtrdood, that was a nice explanation. i appreciate the fact you figured out i'm a non-technical person and tailored your response accordingly. in fact, everyone who responded has been most sensitive to my need in that regard. no need for the 'linux-deer' so far.

another thing that crossed my mind today is that i wonder if menues are just graphical representations of the terminal (itself being a graphical rep. of the shell? is that right?). if i'm correct, that would be an example of realizing how much things overlap. (western music becomes a lot simpler when you realize there's only 12 notes to chose from.)

[quote=Iowan]Not to cloud the issue (pardon the upcoming pun...) but most electronic devices are actually powered by SMOKE! Electricity is only used to regulate the flow of smoke. Once the smoke leaks out of a device, it must be replaced.[/quote]

what are you trying to do? leave me in a fog???

---

### Post by Zyphrexi on 2006-02-13
I just stumbled upon this, but I think if you focused less energy on understanding the philosophy and ecology of a system, you'd have more energy to break it.

Breaking it then leading to fixing it, of course then leading to knowledge, and the wisdom to not do the same thing over again. (unless of course you lost the knowledge and are therefore using said wisdom to restore knowledge.)
Essentially this is how I learned, all the fun small stupid things come along eventually, and you can either use them as earplugs and pretend you can't hear reason, or you can drown them, so you don't have to listen to their incessant nonsense. 

The point being here, is that your avatar is hot. And if you look like that, you should come over here A.S.A.P, and also bring some cheetos, as I am out of them.

---

### Post by fuscia on 2006-02-14
no worries, i break it all the time. and btw, it's not the philosophy i'm after. it's the essential structure. it's like having an outline for a presentation. 

that's zhang ziyi in my avatar, not me. i look more like a guy, if you know what im' saying.

---

### Post by mips on 2006-02-14
fuscia,

Read the links below, should give you a pretty good idea of how computers work, if you don't understand some of it just ask. I kinda sorted them in the order low level (bits/bytes/transistor) to high level (software/os).

[http://computer.howstuffworks.com/boolean.htm](http://computer.howstuffworks.com/boolean.htm)
[http://computer.howstuffworks.com/bytes.htm](http://computer.howstuffworks.com/bytes.htm)
[http://electronics.howstuffworks.com/digital-electronics.htm](http://electronics.howstuffworks.com/digital-electronics.htm)
[http://electronics.howstuffworks.com/diode.htm](http://electronics.howstuffworks.com/diode.htm)
[http://electronics.howstuffworks.com/motherboard.htm](http://electronics.howstuffworks.com/motherboard.htm)
[http://computer.howstuffworks.com/bios.htm](http://computer.howstuffworks.com/bios.htm)
[http://electronics.howstuffworks.com/microprocessor.htm](http://electronics.howstuffworks.com/microprocessor.htm)
[http://electronics.howstuffworks.com/computer-memory.htm](http://electronics.howstuffworks.com/computer-memory.htm)
[http://electronics.howstuffworks.com/ide.htm](http://electronics.howstuffworks.com/ide.htm)
[http://electronics.howstuffworks.com/hard-disk.htm](http://electronics.howstuffworks.com/hard-disk.htm)
[http://computer.howstuffworks.com/3dgraphics.htm](http://computer.howstuffworks.com/3dgraphics.htm)
[http://electronics.howstuffworks.com/monitor.htm](http://electronics.howstuffworks.com/monitor.htm)
[http://computer.howstuffworks.com/operating-system.htm](http://computer.howstuffworks.com/operating-system.htm)
[http://computer.howstuffworks.com/pc.htm](http://computer.howstuffworks.com/pc.htm)

Probably one of the better websites out there.

---

### Post by fuscia on 2006-02-14
[quote=mips]http://computer.howstuffworks.com/bytes.htm[/quote]

i never knew about number systems other than decimal (never took math seriously...ever). now i can see why nietzche might have thought that "sometimes, 2+2=5". back to reading...

edit:...which also relates with robert darnton's ideas as expressed in *the great cat massacre*.

edit2: big thanks to both mcduck and mips for hooking me up with howstuffworks.com.

---

