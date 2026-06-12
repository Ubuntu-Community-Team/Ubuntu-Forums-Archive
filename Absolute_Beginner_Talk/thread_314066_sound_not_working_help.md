---
title: "sound not working help"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by broekskw on 2006-12-07
ok it's been about 2 week running ubuntu and i do not have sound (got video internet cdrom folppy drives going) here is a screen shot i took some time back and i thing ubuntu does not see my sound card .ok alsa is a program to add on ubuntu to detect my sound card???

thanks for any reply in advance:rolleyes:

---

### Post by tbroderick on 2006-12-07
What sound card do you have?

---

### Post by kennethb on 2006-12-07
I think you need to modify your 'xorg.conf' file to work with your sound card. What is the make and model number of your sound card?

---

### Post by broekskw on 2006-12-07
sound blaster awe 64. how do you modify your 'xorg.conf:mrgreen:

---

### Post by tbroderick on 2006-12-07
> **broekskw said:**
> sound blaster awe 64.

That's an ISA card, right?

---

### Post by broekskw on 2006-12-07
yes it is:D

---

### Post by tbroderick on 2006-12-07
Take a look at this thread;

[http://ubuntuforums.org/showthread.php?t=103180](http://ubuntuforums.org/showthread.php?t=103180)

Specifically post #6. You might have to adjust some IRQ settings in your BIOS.

---

### Post by broekskw on 2006-12-07
thanks will look at this. also how do i check or what is the command in terminal to check to see if i have a xorg.conf 
thanks
:mrgreen:

---

### Post by Adramelech on 2006-12-07
sudo nano /etc/X11/xorg.conf
Read before change it

---

### Post by broekskw on 2006-12-07
thanks again:D when i open this page how to i get the next page to come up, the next page command is  ^v but does not work gor me 
thanks:D

---

### Post by tbroderick on 2006-12-07
xorg.conf is for your xserver not alsa. You don't need to do anything to that. You should check and see what sound module is loaded. From a terminal type;
```
lsmod
```

Look for snd-sbawe. If its not there try to load it with;
```
 sudo modprobe snd-sbawe
```

Then you should edit /etc/modules and put the sound module snd-sbawe at then end of the file on it's own line. You might then need reboot to change your BIOS settings outlined in the other post.

If snd-sbawe doesn't work then try snd-card-sb16.

---

### Post by broekskw on 2006-12-07
great thanks again, will try all again thanks:D

---

### Post by broekskw on 2006-12-07
ok did that and i see the snd-abawe listed so di i just have to edit /etc/modules and put ound module snd-sbawe

take a look at my screen shot
thanks
:mrgreen: :mrgreen: :mrgreen: :mrgreen: :mrgreen: :mrgreen:

---

### Post by tbroderick on 2006-12-07
You won't need to edit /etc/modules then. Just try adjusting your BIOS like in the other thread.

---

### Post by broekskw on 2006-12-07
ok adj my bios but still nothing working, have headphones pluged into the sound card and can hear stadic but thats all.put in a music cd and a program opens up i then select a song but get this error message

how do i get my sound control pannel up to see if the sound is on mute.](*,) ](*,) ](*,) 

thanks

---

### Post by tbroderick on 2006-12-07
Run alsamixer from a terminal and try to adjust the levels.

---

### Post by broekskw on 2006-12-07
ok tried that and get this error screen,looks like i do not have that installed, could this be my problem](*,)

---

### Post by tbroderick on 2006-12-08
Only other thing I can think of to try is to add this line to your /etc/modules

snd_sbawe isapnp=1

Then you have to disable Plug 'n Play in your BIOS.

---

### Post by broekskw on 2006-12-08
holy crap.did a fresh install from cd and tried everything on this post and sound working :mrgreen: :mrgreen:  

the  alsamixer command in terminal finally came up and i adjusted every line that i could and got sound:mrgreen: :mrgreen: :mrgreen:  

now have to go and install video card (but that was nothing compared to this ):mrgreen: :mrgreen:  

this site rocks big time. thanks to all:mrgreen:

---

### Post by broekskw on 2006-12-08
ok back to no sound and i screwed up the video all i get is some error window at boot up can not load ubuntu, 
can comeone tell me what this message at startup is all about
this screen is the last one before the logo screen for ubunto comes up

acpi unable to find or load rsdp

the screen is there for just a few seconds
](*,) ](*,) ](*,)

---

### Post by kennethb on 2006-12-11
If you have 'gedit' installed (which you likely go), then from the command line type:

sudo gedit /etc/X11/xorg.conf

You will be prompted for a password. Enter you root password. Gedit will open and you can edit the file.

You need to pass the 'sudo' command to edit the file as a "super user".

You may also want to update your Ubuntu software. It is pretty good at detecting sound cards.

---

### Post by broekskw on 2006-12-11
thanks kennethb,got everything going and stays going after reboot:mrgreen: :mrgreen: this is truly a great site to be part of:D

---

