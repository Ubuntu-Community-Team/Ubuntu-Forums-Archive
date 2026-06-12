---
title: "Big Problem With Xgl"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by degro on 2007-01-19
Hello. My name is Dan and i'm kinda new to linux. I'posting this here after a few unsuccessful attempts of getting everything to work on ubuntu edgy 64 bit, 32 bit and opensuse 64 and again 32 bit.

My greatest problem is that i wasn't able to install my graphics card and always when fglrxinfo-ing i had the mesa drivers. (my main purpose was to install xgl and beryl or compiz). I've been searching for a while and found out its quite difficult to install ati drivers. it is :grin: . 

My pc looks something like this( :oops: ):

m2n motherboard

athlon64 3000+

512 ddr2 800mhz

ati radeon x550 (my biggest problem)

I would really appreciate if somebody who had problems before with the graphics card or knows how to properly install the drivers told me what distro would best fit my computer and which one deals best with ati cards... (eventually links to the best drivers...). Thanks a lot.

Respect, 
Dan.

---

### Post by riven0 on 2007-01-19
Well, if you don't want Ubuntu, I heard PCLinuxOS is great for new users and the like. 

Otherwise, just stick with Ubuntu and install the official ATI drivers. That works most of the time.

---

### Post by degro on 2007-01-19
i don't know what to say... i'm really confused now :) 

i love ubuntu. worked great... all the features except for the sound and the video driver...

now, i guess it's just me or something that i can't install the drivers. :D i heard that the ati drivers don't work with xorg 7.2, then found out it worked, don't know what to do more :))

my opensuse is screwed up too, no gnome anymore, it won't load because i installed the ati drivers and it says it can't find any display. guess i'll try ubuntu.. again.. and again.. and again..

---

### Post by riven0 on 2007-01-19
degro, for your ATI card, have you tried these steps yet?:

> sudo apt-get install xorg-driver-fglrx
> 
sudo aticonfig --initial
> 
sudo aticonfig --overlay-type=Xv

And then try rebooting.

---

### Post by degro on 2007-01-20
hello again.
i posted here yesterday about my problems installing my video card.

I FINALLY MANAGED to install it, in fglrxinfo i got the correct version and i tried to install xgl and beryl. it all went fine, i created the session, i threw it in startup programs and... CRASH

when i reboot and select the xgl session, it says it lasted just for 10 seconds and i get this error log:

> etc/gdm/PreSessions/Default: Registering your session with wtmp and utmp
etc/gdm/PreSessions/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/log/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "root"
/etc/gdm/Xsession: Beginning session setup...
stdin: is not a tty
Could not init font path element /usr/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/lib/X11/fonts/100 dpi/, removing from list!
Could not init font path element /usr/lib/X11/fonts/75 dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
(gnome-session:6779): Gtk-WARNING **: cannot open display:


please help, tell me if it is because of my video card or something, or because i did something wrong.. please answer.

yours faithfully, 
dan

---

### Post by degro on 2007-01-20
thanks for the interest in helpin

---

### Post by degro on 2007-01-20
> etc/gdm/PreSessions/Default: Registering your session with wtmp and utmp
etc/gdm/PreSessions/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/log/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "root"
/etc/gdm/Xsession: Beginning session setup...
stdin: is not a tty
Could not init font path element /usr/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/lib/X11/fonts/100 dpi/, removing from list!
Could not init font path element /usr/lib/X11/fonts/75 dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
(gnome-session:6779): Gtk-WARNING **: cannot open display:

when loading the xgl session, it screws up. 

......
...
.

---

### Post by steven_mckenz on 2007-01-20
You don't even give an hour after your other post for someone else to help you, before you start bashing other people for not taking their time out to help you?

Yikes.  Calm down, or nobody's going to want to help you for attacking them.

---

### Post by aysiu on 2007-01-20
Don't forget that some people may want to help but have no idea what the problem is.

Do you want me to post "I have no idea how to help you, but I do care about your problem"?

If so, here I go:
I have no idea how to help you, but I do care about your problem.

steven_mckenz is right, though--one hour on a weekend for a relatively obscure problem is not long to wait, especially on a volunteer-run forum. For more information, read [To all those with zero-reply threads...](http://www.ubuntuforums.org/showthread.php?t=82471)

---

### Post by DerHesse on 2007-01-20
It's joust a guess: You could try reinstalling "console-setup". 
It can be easily done with synaptic or with apt-get.

I can understand you are in a hurry, but please don't bark.

---

### Post by degro on 2007-01-20
hey :D im no dawg.

i understand i overreacted. im not really in a hurry. im just excited and i cant wait to get this thing going. because i've seen screenshots and small desktop recordings and i simply love it.

besides that, yes, i am sick of windoze, too. vista is a ram sucker.

1. what would reinstalling console-setup do? or help
2. how do you do it.

thaaanks.

---

### Post by DerHesse on 2007-01-20
$ apt-get install console-setup

---

