---
title: "Slow boot and error message"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by anthonyp on 2007-06-16
OK guys firstly I am pretty much retarded when it comes to Ubuntu :popcorn:

I have tried it b4 with no success, but now Microsoft have shafted me with my latest legit copy of Vista Ultimate 64 so I installed Ubuntu (feisty fawn 7.04) back onto my laptop.

Now i think it takes ages to load and i noticed there is an error message during the boot up. But it all boots fine (just slow).

Now i tried to 'print screen' the message to copy it and post it up but i cant even get that to work :S

So I have a problem and I have no idea how to resolve it. I don't understand half the jargon and i have tried to learn it but its just to Chinese for me :(
I think Microsoft has polluted my brain :p

Don't know where to start, don't know where to finish... the error doesn't really bother me as everything seems to be working semi fine (its glitchy in many places but i can live with it), we only use this system for browsing the net and emails etc anyways.

Just would like to see why the boot up and shut down takes so long. Sorry to ramble on so much.


Cheers
Grimace

---

### Post by Skrynesaver on 2007-06-16
Post a copy of the file
/var/log/boot
This should contain the error message, Very often a slow boot is network related, failing to get an address from the router/DHCP server

---

### Post by anthonyp on 2007-06-17
> **Skrynesaver said:**
> Post a copy of the file
/var/log/boot
This should contain the error message, Very often a slow boot is network related, failing to get an address from the router/DHCP server

Ok ill uploads it in a sec just gotta boot the lappy up :p
In the mean time I have been reading heaps (trying to learn...) and mang this is one fast forum :D

back in a sec :D

---

### Post by anthonyp on 2007-06-17
:confused:

(Nothing has been logged yet.)

Edit: i tried to 'pause' the loadign screen to note down the error message.. but pause doesnt work either... owell i guess its not really a big error... ???

Maybe i should just start looking at ways to speed up my ubuntu loading and not worry bout this mystery error.

---

### Post by anthonyp on 2007-06-17
sorry double post :S man i am useless.

---

### Post by Golyadkin on 2007-06-17
Hey hey, you are not retarded and not useless :) you are just still learning, and that is good. 

We will help you out here, don't worry, everybody has to learn sometime. :D Welcome to the forums by the way!

Have you gotten a chance to show us the output of the command Skrynesaver suggested?

---

### Post by anthonyp on 2007-06-17
> **Golyadkin said:**
> Hey hey, you are not retarded and not useless :) you are just still learning, and that is good. 

We will help you out here, don't worry, everybody has to learn sometime. :D Welcome to the forums by the way!

Have you gotten a chance to show us the output of the command Skrynesaver suggested?

yeah mate, it tells me 'Nothing has been logged yet.'
Thats it :(

---

### Post by anthonyp on 2007-06-17
ok i figured ill just try see what the error says, so armed with my sharpest eye open I restarted and waited for the split second the error appears....  
Finally that moment arrives (after the grub loading screen) and it pops up real fast and the most important part is this 'failure to allocate memory/resource' or something like that, followed and lead with a whole bunch of what seemed to be random numbers.

Is this bad?? maybe its an actual problem with my laptop which by the way I'll add the details.

its a Toshiba M30, with only Ubuntu installed on a fresh HDD. 512mb, 60gb hdd, Nvidia graphics, DVD burner (thats does not read burnt cds or some others with windows or ubuntu).

Cheers
Grimace

---

### Post by Skrynesaver on 2007-06-17
The error may have been logged in
/var/log/messages
failing that run "dmesg" after logging in
Off out to do a bit in the garden, but I'm sure others will lend a hand.
PS. Learning a new OS isn't instantaneous but Ubuntu is certainly a convenient ramp over the learning curve and these forums are the most helpful place I've ever been ;) As Randal Schwartz famously remarked, "The computer is the game"

---

### Post by Golyadkin on 2007-06-17
The command "dmesg" will make loads of text race past your screen, so to take it in chunks for each page type:
> 
sudo dmesg | less

which will get you scroll through it with page up and page down.

---

