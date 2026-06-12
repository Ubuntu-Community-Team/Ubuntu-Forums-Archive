---
title: "graphics card overclocking......"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-24
hello.
while i was looking through synaptic for nvidia related stuff (i have an nvidia 7600gs agp card) i noticed that there a couple of applications that let you overclock the graphics card, so i thought id have alook at them.
anyway i installed them and i cant find out how to run them, as i dont see them listed in applications or anywhere else, the apps are called - nvclock and nvclock-gtk and nvclock-qt like ive said ive installed the, so how do i get them to run ? and has anyone tried them and what were the results ?
cheers

---

### Post by Bachstelze on 2007-05-24
nvclock is run through the command line, nvclock --help will give you a list of all options. The two others are just GUIs for it, try to run them through the command-line too.

---

### Post by techno-mole on 2007-05-24
cheers, i tried to run them from the command line, got nvclock to run, but i couldnt really get it to do much, the other 2 wouldnt run from the command line.
if i run nvclock in terminal i get a big list of stuff, and there was a couple of commands i tried to run, mainly there was --memclk speed, so i tried running it by typing nvclock --memclk speed and all that happens is, well nothing i also tried another command which was --nvclk speed and again nothing happens, so im scratching my head a little, it seems i can only run some of the commands, but not all, so perhaps its something to do with the graphics card its self ? i know that the 7600gs's can be overclocked a fair bit (you get a program to do it, which only runs under windows :(, there one that comes with the card, and then theres rivatuner)
would you need to be root ? the other thing is that theres a command for seeing what temperature the card is at, but when i typed this command it said that may card doesnt support temperature monitoring, but it does, i can go to the nvidia settings application and see what temp the gpu is at.
cheers.

---

### Post by Bachstelze on 2007-05-24
Of course you need to be root...

---

### Post by techno-mole on 2007-05-24
ive tried using nvclock as root, but it still doesnt work, well that is to say i cant use the commands i mentioned and actually get them to do anything.
ive had no luck either in actually getting the nvclocks with a gui to run either (ive double checked to see if they are installed)
cheers

---

### Post by techno-mole on 2007-05-24
ive managed to get access to the core and memory by using coolbits, but im having trouble getting to auto detect to work.
heres the link for getting coolbits to work (nvidia cards) [http://ubuntuforums.org/showthread.php?p=2711589#post2711589](http://ubuntuforums.org/showthread.php?p=2711589#post2711589)

maybe it will help some other people, worked for me, i had been trying to use nvclock with not much luck - WARNING - overclocking anything on your system may cause alot of problems and may result in the death of you system, or part of it, so be very careful. :D
cheers

---

### Post by chronic on 2007-05-24
i wouldnt bother OCing ur gfx card. iv been overclocking for years (under windows) and the benifit you get from it is minimal and since the linux drivers arnt that great to start off with. i wouldnt bother if i was you. the benifit you will get will be so small you will probaly never notice.

plus you dont want to run the gfx card overclocked unless you need to. youll stress your card (making it last less time) and will probably need to get some after market cooling.

---

### Post by techno-mole on 2007-05-24
its not so much overclocking, so if my agp cards speeds are set at 400mhz on the core and memory im not trying to put them up to 600mhz (this would be bad, and probably melt the card) all im trying to do is run the card at its optimal frequencies, which for my card is 415 on the core and 425 on the memory, you'd be surprised what a difference running it on optimal speeds makes to general performance (for example beryl runs alot better when the card is at its optimum speeds) and in game performance, and as i have discovered just by setting this particular card up like i do i can then turn up stuff like aa and such and get a better look in game, where as if i leave it at stock speeds it doesnt like aa turned on at all.
(i know i said the memory is 425, but its actually 850mhz its down to the type of memory it uses)
generally overclocking is bad for your system, but if you can get a good balance then you do get a performance gain, for example my cpu is and amd 3200 (64bit) which runs @ 2.01 ghz stock, ive been running it @ 2.5 ghz for months and i do get better performance out of it, ive also managed to keep the temperature right down aswell, its idle temp is 32 degrees c and under load it goes up to 45 degrees c, the highest ive had it was 60 degrees c, and i had to hammer the thing to get it that high.
its all about balance (imo)
cheers

---

