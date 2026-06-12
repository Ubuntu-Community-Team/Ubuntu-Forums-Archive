---
title: "[SOLVED] Nvidia settings error tv out"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-07
Hi sorry back again

I'm trying to set up my Tv out in the nvidia settings dialogue,

I can get in to the settings (in Terminal - nvidia-settings)  and at first it shows both my monitor and tv (although tv is disabled)

if i then configure it for twin view and save to X configuration file i get (in Terminal)

ERROR Unable to create backup file '/etc/X11/xorg.conf.backup

I i then close and reopen the nvidia settings in Terminal the tv has disappeared and only comes back if I reboot.

Would like to get this sorted as it's the last but one thing stopping me migrating completely (other is Cakewalk and vsti's but i'll leave that till another month)

Thanks in advance

---

### Post by m0eman on 2007-05-07
Are you giving yourself root access when you start the nvidia-settings? The way to do this is 
```
sudo nvidia-settings
```
and type in your password and then enable TV. You need to have root privileges when editing the xorg.conf file.

---

### Post by forestpixie on 2007-05-08
Hi thanks - I wasn't when i first posted - then I sussed that one and was able to save the file - but I end up with a white tv screen half on and i assume half off the screen.

Then it seems to screw up my monitor - so that doesn't seem to work properly - Terminal for instance turns all white and I can't see anything.

Have to reboot start recovery so I can get command line - then mv the xorg.conf.backup to xorg.conf and obviously am back where I started 

While all has gone well gonna give up for moment I think - have to watch movies through windows instead

thanks for help

---

### Post by CryoMan on 2007-05-08
> **m0eman said:**
> Are you giving yourself root access when you start the nvidia-settings? The way to do this is 
```
sudo nvidia-settings
```
and type in your password and then enable TV. You need to have root privileges when editing the xorg.conf file.

i have the same problem whatever i do i get these error messages. 

$ gksudo nvidia-settings
ERROR: Unable to determine valid vertical refresh ranges for display device
       'QDS' (GPU: GeForce Go 6800)!


ERROR: Failed to add display device 'QDS' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!

i realy want to wach movies on my plasma with dvi.

---

### Post by m0eman on 2007-05-08
cryoman:
try manually setting the refresh rate on the 'X Server Display Configuration' tab in nvidia-settings for your monitors. The errors you are getting is because nvidia-settings can't detect your refresh rate so manually setting them should fix the problem.

forestpixie:
I'm not really sure but maybe it could be a problem with your resolution you set your TV to in nvidia-settings. I remember I had to set mine to 800x600 to get it to display correctly. (Or maybe even an invalid refresh rate)

---

### Post by CryoMan on 2007-05-09
same errors. 
> ERROR: Unable to determine valid vertical refresh ranges for display device
       'QDS' (GPU: GeForce Go 6800)!


ERROR: Failed to add display device 'QDS' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!


can add this directly to config? what to write?

screen 0 has a refreshrate at 60 hz
screen 1 has 70 hz

---

### Post by m0eman on 2007-05-11
[http://wiki.osuosl.org/display/howto/Set+Up+Dual+Monitors+-+xorg.conf]("http://wiki.osuosl.org/display/howto/Set+Up+Dual+Monitors+-+xorg.conf")

You can try that guide, but that guide is for radeon cards, so you will have to replace the radeon with nvidia, ati with nvidia.

Make very sure you backup your current xorg.conf before editing. And in case something goes wrong, make sure you know how restore your backup in recovery mode if x fails to start.

to backup your xorg file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

to edit your xorg.conf file:
```
gksudo gedit /etc/X11/xorg.conf
```

to restore your backup in recovery mode:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Edit: And double check that all the names in xorg.conf are the same.
Edit2: I would just like to say that editing your xorg.conf file is EXTREMELY risky and even one spelling mistake WILL screw X up and you will boot with no graphical user interface.

---

### Post by forestpixie on 2007-05-11
I did a reinstall - cleared data from the drive so I was installing to a 'clean' drive and I have now managed to get both working fine with little problem, films are poor on the tv very pale and a bit washed out

but that's probably just the tv (although it works in win2k).

Everything seems a lot happier now ubuntu is alone on the drive

resolution on the monitor seems much better too 

all abit odd but that's life

---

### Post by forestpixie on 2007-05-13
Indeed they are so washed out they are in fact black and white - didn't really notice till i sat down to watch -

so I have configured to have seperate x screens which works except for the black and white tv screen

as i said previously it worked ok when using win2k

am now a bit lost in the maze

does anyone now how to get the tv to be colour - would it be because the driver thinks it needs to be ntsc and i need pal?

please help !!!

---

### Post by forestpixie on 2007-05-13
Did it eventually 

added lines to device section 

one to say it was svideo other to say Pal-I

after a reboot and restarting X everything is now in colour

Just got to sort out Vsti instruments and I can say bye bye to windows for ever

Wait for the dust to settle at Ubuntu Studio and have a look at that

Thanks to all in the forum who have helped me and to those hoping!

---

### Post by cadamr on 2007-05-21
i'm having the same problem as Cryoman. 

```
ERROR: Unable to determine valid vertical refresh ranges for display device 'CMO' (GPU: GeForce Go 7700)!


ERROR: Failed to add display device 'CMO' to screen 1!


ERROR: Failed to add X screen 1 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!

```

for some reason it keeps wanting to label the laptop screen, 'CMO', 1 and the crt 0, instead of the other way around. Yes, I'm am doing as root.

---

### Post by drspastic on 2007-06-05
hi there friend. i've looked at the points you raised in your guide and managed to get a display on my tv, but there are these short lines all over it. also, the minimise/maximise button have vanished from around my windows, and the bottom panel doesn't always display the open  programs. also terminal won't load i have to use konsole. i know that this sort of thing will always be a bit hit and miss but i've been messing around with this for days and really need someone to help me finish off tweaking so i can leave it well alone. i won't need to do anything else techy on ubuntu for a long time. 

thanks for all your help so far, especially helping me get my installation back!

any ideas on the above?

---

### Post by forestpixie on 2007-06-05
Hi - I found that I lost min and max buttons from apps if I had Desktop Effects enabled and that seemed to be seperate to problems I was getting with tv.

So have you enbled them and if so what happens when they are off.

As far as tweaking goes I only added two lines to xorg.conf to get the tv in colour.

   ```
 Option "TVStandard" "PAL-I"
    Option "TVOutFormat" "SVIDEO"
```

I assume you now have two screens/monitors shwoing in nvidia-settings - I have mine set up as seperate X screens. Have you tried changing the tv flicker setting that helped me.

I've attached 2 pics, might help you.

Don't forget that to get any settings to save in nvida-settings you must open as su

I think it's best to do 

```
gksudo nvidia-settings
```

but I could be wrong - I read somewhere that sometimes you need to do gksudo instead of sudo with GUI things (I think :) )

and don't forget to backup from the front screen.

I'm happy to help as best I can but if you still run into problems it might be best to start a new thread.

Good luck - and I hope it's a sunny in Cornwall as it is in the Solent

---

### Post by drspastic on 2007-06-05
cheers. i will start a new thread then.thanks. 

 for some reason i dont have the options for tv flicker in the config from nvidia, just digital vibrance only.

desktop effects disabled.

i now only get min/max buttons when using separate x server for the tv and xinerama seemingly.

oh well, on i press!

cheers

---

