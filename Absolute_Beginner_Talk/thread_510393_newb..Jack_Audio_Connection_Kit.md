---
title: "newb..Jack Audio Connection Kit"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by G_J on 2007-07-26
ok i need some help with this..i installed Ardour from add/remove software menu...came up as Ardour GTK..i installed it and now says Jack is not running..i try searching how to install it but couldt find how, all i found were codes to put in da terminal witch didt do anything... so how do i install Jack and make it run so i can finally make music with Ardour?:(

---

### Post by G_J on 2007-07-26
bumping

---

### Post by G_J on 2007-07-26
i finally got Jack install...but now when i click start so it can connect says cant and tell me to check some window i guess is this

18:04:46.416 Patchbay deactivated.
18:04:46.486 Statistics reset.
18:04:47.013 MIDI connection graph change.
18:04:47.022 MIDI connection change.
18:06:58.651 Patchbay deactivated.
18:07:26.799 Startup script...
18:07:26.800 artsshell -q terminate
sound server terminated
18:07:28.413 Startup script terminated successfully.
18:07:28.471 JACK is starting...
18:07:28.472 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
18:07:28.490 JACK was started with PID=23420 (0x5b7c).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210345792, from thread -1210345792] (1: Operation not permitted)
cannot create engine
18:07:28.744 JACK was stopped successfully.
18:07:28.746 Post-shutdown script...
18:07:28.747 killall jackd
jackd: no process killed
18:07:29.017 Post-shutdown script terminated with exit status=256.
18:07:30.538 Could not connect to JACK server as client. Please check the messages window for more info.

---

### Post by por100pre1 on 2007-07-26
Did you install JACK Control?

```
sudo apt-get install qjackctl
```

If so are you using the low latency kernel?

---

### Post by G_J on 2007-07-26
yea i guess i did
> 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

man this sooooo hard..all i wanna do is record music!!....but yea jack anit working

EDIT: 

wait Jack Control is a diffrent thing than Jack da audio connection kit?...if it is i guess i got da control setup but not da connection kit...how you install it?...man im stupid if this is da problem...

---

### Post by por100pre1 on 2007-07-26
Jack should be there too it's jackd. Are you using Ubuntu Studio?

---

### Post by por100pre1 on 2007-07-26
Check if you are using ALSA sound in System> Preferences > Sound and in JACK Control in Setup> Settings > Driver.

---

### Post by G_J on 2007-07-26
yea sound capture is on ALSA all da other 1's are on "autodetect"...no i got Ubuntu 7.04 i belive festy fawn or something like dat...thanks for da help man

---

### Post by G_J on 2007-07-26
YUUUUHOOOOOO!!!!...lol... i got it working!!!.. idk how but i remember you said to check Jack control for Alsa so i went to open and da computer froze i think cause of some scipt or something but i had to turn it off when i turned it on again i opened Jack and clicked start after checking for Alsa....and it connected then i opended Ardour!!!..YAYYYY!! lol but yea dats what happen now i hope i can exort files as mp3's ahhaa but thanks  for your help i appreciate it

---

### Post by por100pre1 on 2007-07-26
Maybe the low latency kernel may be useful here on the "cannot use real-time scheduling" issue... Ubuntu Studio can help you here. Try this:

```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
```

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```
```
sudo apt-get install ubuntustudio-desktop linux-lowlatency
```

Keep in mind that Feisty won't look the same after this!!! It will use a black theme after this. Hope this could be useful.

EDIT: **Glad to know you fixed it.** You can still use the above method for better performance and better looks too.

---

### Post by isaacj87 on 2007-07-27
> **por100pre1 said:**
> Maybe the low latency kernel may be useful here on the "cannot use real-time scheduling" issue... Ubuntu Studio can help you here. Try this:

```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
```

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```
```
sudo apt-get ubuntustudio-desktop linux-lowlatency
```

Keep in mind that Feisty won't look the same after this!!! It will use a black theme after this. Hope this could be useful.

EDIT: **Glad to know you fixed it.** You can still use the above method for better performance and better looks too.

I've already installed the ubuntustudio-look package, so I'm guessing the "new look" won't apply to me right? I have a question though, this low latency kernel improves what aspect of recording?? I notice that my computer struggles to record (let alone over-dub) even though my comp isn't weak...would low latency help me?

---

### Post by G_J on 2007-07-27
good question ^^^

but ok..i found out Ardour dont let me import mp3 files....but Ardour2 does..how can i stall it?..im guessing installing Ubuntu Studio would be da best way?..but how do i install Ubuntu Studio and Ubuntu 7.04 to run together since i read they can dat might be a better option right?

---

### Post by por100pre1 on 2007-07-27
> **isaacj87 said:**
> I've already installed the ubuntustudio-look package, so I'm guessing the "new look" won't apply to me right? I have a question though, this low latency kernel improves what aspect of recording?? I notice that my computer struggles to record (let alone over-dub) even though my comp isn't weak...would low latency help me?

It helped me to use Jack with better performance... actually it works better to me for everything. But **keep in mind that results are not always the same**...

---

### Post by por100pre1 on 2007-07-27
> **G_J said:**
> good question ^^^

but ok..i found out Ardour dont let me import mp3 files....but Ardour2 does..how can i stall it?..im guessing installing Ubuntu Studio would be da best way?..but how do i install Ubuntu Studio and Ubuntu 7.04 to run together since i read they can dat might be a better option right?

Ubuntu Studio is actually Ubuntu Feisty 7.04 with the additional kernel and some more packages... You can add the repos and just install what you want with Synaptic.:)

---

### Post by G_J on 2007-07-27
o are you serious!...ok ok so use this command  from da Studio site

[http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads)

and then go to synaptic and get da other stuff when i search for  Ubuntu Studio?

O and whats da in da other post you posted wit da commands?...a theme or something

---

### Post by por100pre1 on 2007-07-27
> **G_J said:**
> o are you serious!...ok ok so use this command  from da Studio site

[http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads)

and then go to synaptic and get da other stuff when i search for  Ubuntu Studio?

O and whats da in da other post you posted wit da commands?...a theme or something

Those are the basic modules of Ubuntu Studio and yes, they *include* a black and blue theme. If you check the commands they point to install the kernel and the basic installation...

You can try it, if you don't like it you can go back with this:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by 11touche on 2007-07-28
I'll try to get the low latency kernel too with the Ubuntu-Studio desktop...
Hope it's gonna work on my machine!
I'll give you news about me since I get back from this huge change !

---

### Post by 11touche on 2007-07-28
Well, got the LowLatency kernel to work great on my machine, I'm gonna try some performance tests soon.

---

