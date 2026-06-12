---
title: "beginner, install 9.10 on ppc g4 fails"
date: 2010-03-13
forum: Apple Hardware Users
---

### Post by surfmonkee on 2010-03-13
i have a ppc G4 with 10gb hdd and 512 ram and 350 processor.

i have tried to install 6.10 alternate ubuntu package, that started to install but stalled at 6% installing software.

i am now trying out 9.10 ppc alternate ubuntu package.

it is going thro the install and so far so good, but again it stalls at adding software, it went to retrieve 858 files and stopped around 620.

if u have any advice please contribute.  it seems silly to skip this step, however i shall proceed and see where it gets me.

**ok so i re did the software install and it found all 858 files but then it reported it failed ....**

help!!!!!!!

i carried on with the install but skipping the software install section, it has now completed whatever it was doing, rebooted and left me at a command prompt to login, which i can do ok.

where do i go next?

---

### Post by linuxopjemac on 2010-03-13
can you describe a bit what you see ?
it seems like you have a yaboot prompt, but I am not sure. What happens if you hit the TAB button? Do you see boot options ?

---

### Post by surfmonkee on 2010-03-13
thanks for the reply, I can't tell you atm because i am doing another install, I will let you know in a while, thanks for your time.

---

### Post by surfmonkee on 2010-03-13
i have managed to make a copy of debian with the gnome desktop run...

i will go with that for now, at least it gives me good experience of linux based software for the weekend.

i have an ubuntu god at work so i chat to him on monday....

---

### Post by surfmonkee on 2010-03-13
problem solved, i am now running 9.10 alternate ppc and altho it is a bit sluggish it is a battered G4.  

apparently the fail was something to do with me not using encrypted drive, two attempts without this option failed, two using this option worked perfectly and seamlessy, with an internet install and a disc install.


[B]i am stuck in 800x600 screen res and the only other choice is 640/480 yuk.

the monitor is a hp pavillion f1703[/B]

and thanks to this forum i have found the answer in a thread so i am off to do some code and edits on stuff.

thanks for being here ubuntu, ur fabulously goregous.

---

### Post by linuxopjemac on 2010-03-13
read through this post:
[http://ubuntuforums.org/showthread.php?t=1392023](http://ubuntuforums.org/showthread.php?t=1392023)

---

### Post by linuxopjemac on 2010-03-13
you have to find out the horizontal and vertical refresh rates of your type of monitor.

---

### Post by surfmonkee on 2010-03-13
i am trying to find my monitor specs but its not easy.

its one of these and the only specs i can find are its rez but not its frequencies.

[http://www.tomshardware.com/reviews/good,929-23.html](http://www.tomshardware.com/reviews/good,929-23.html)

but thats not the end of it after all.   


the sawtooth G4 has a dvi output and I had a dvi monitor, the Q17, 

for the install that worked I was using a generic 1280 lcd.

i had a brainwave with the working install to shut it down, take the Q17 with its dvi and hook that to the G4.  

disaster, it booted in the other monitors rez but then i edited the X11/etc with 1280/1024 for the Q17 and rebooted, its failed to boot up.... put the old monitor back on vga and it was 'outside of its range'

in true newby style i slapped in a 10.3 os x install disc, wiped the drive clean and now i am starting again... fresh install to the Q17 on vga

**I would like to use the dvi with 9.10 on this sawtooth... so more searching i fear...**..

its all good fun, another reinstall won't hurt me one bit, at least i get to remember the new encryption passwords.....


saturday night geek in town, omg. xx

---

### Post by whereareyoutakingme on 2010-03-21
i just input the 9.10 desktop powerpc ISO on a DVD and popped it into my iMac PowerPC G4 (PowerMac 4,2):

2.1 Ghz single core, 256mb RAM, 60Gb HD, 32mb VRAM

It got past the Ubuntu splash screen that you see before it boots into the Live DVD, but hung up while running some of those commands that scroll down the screen DOS style.  The screen was white with orange text that was flashing on and off while running the commands.  It appears to be hanging up during this process and even after 2-3 minutes of waiting, it fails to move forward.

Any thoughts/suggestions?

---

