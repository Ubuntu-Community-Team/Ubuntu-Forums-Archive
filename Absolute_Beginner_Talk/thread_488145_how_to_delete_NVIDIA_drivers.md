---
title: "how to delete NVIDIA drivers"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-06-29
hey i've installed NVIDIA drivers but now i can't log in - how do i get everything back to how it was to log in again?

i can get to the command prompt and use sudo/gksudo commands - would it have backed up my xorg.cfg (or something) file?

---

### Post by starcraft.man on 2007-06-29
Did the install go bad or is it just an xorg issue? Either way, quickest way to get back to the GUI is to boot to grub and then select recovery mode.

When you get to the terminal as root type this in:

```
sudo nano /etc/X11/xorg.conf
```

Then scroll down the page (with arrow keys for up down left right) and find the device section for your card, it should be labeled nvidia something. Find the driver line like this:

```
Section "Device"
        Identifier      "nVidia Corporation NV40 [GeForce 6800 GT]"
        Driver         [COLOR="Red"] "nvidia"[/COLOR]
        BusID           "PCI:1:0:0"
```

and change the nvidia to [COLOR="Red"]"nv"[/COLOR]

That will do it. Push ctrl + O (letter) and push enter to save and overwrite. Then ctrl + X to exit. Then:

```
sudo reboot
```

Then boot up and log in like normal. We can go from there and figure out what went wrong.

Btw, that was the Nano editor for your information. It is a text editor that can be used in the terminal without any GUI :).

---

### Post by bodhi.zazen on 2007-06-29
> **Beatbreaker said:**
> hey i've installed NVIDIA drivers but now i can't log in - how do i get everything back to how it was to log in again?

i can get to the command prompt and use sudo/gksudo commands - would it have backed up my xorg.cfg (or something) file?

```
cd /etc/X11/
ls
```

Look for a back up ...

```
sudo cp <backup-xorg.conf> xorg.conf
sudo /etc/init.d gdm restart
```

starcraft.man: The nv driver may or may not work, better to advise the vesa driver ;) Don't need to reboot, just restart gdm. Just a friendly FYI on those two things ...

---

### Post by starcraft.man on 2007-06-29
> **bodhi.zazen said:**
> 

starcraft.man: The nv driver may or may not work, better to advise the vesa driver ;) Don't need to reboot, just restart gdm. Just a friendly FYI on those two things ...

True enough, but hes got an NVidia card, I haven't seen the nv drivers fail often if ever for people who had driver trouble. As for the reboot, ya, I know, "sudo reboot" was less letters to type than "sudo /etc/init.d/gdm (re)start" :p

---

### Post by Beatbreaker on 2007-06-29
starcraft.man:

i did all of your fist steps above but i still get the same result - when i boot it shows the loading screen then just goes to a black screen when it's finished. on the black screen i can type stuff in but nothing works - i've go tthe blinking cursor to type but nothing before that.

is there a way to jsut remove all of the nvidia drivers?

i've seen that both you and bodhi have replied since so i'll follow those steps too

also great to see Nano!! i didn't know i could do non GUI editing like that!!! thanks for showing me - i'll let you know how the other steps go

...i think i might use envy instead next time hey?

---

### Post by starcraft.man on 2007-06-29
> **Beatbreaker said:**
> hey i did all that but i still get the same result - when i boot it shows the loading screen then just goes to a black screen when it's finished. on the black screen i can type stuff in but nothing works - i've go tthe blinking cursor to type but nothing before that.

is there a way to jsut remove all of the nvidia drivers?

Whose way did you use? Both should work, the NVidia drivers being installed poorly doesn't affect the vesa/nv drivers or the back ups bodhi pointed you to. Maybe something else not working? Did you change anything else in the xorg? We might have to look at it... can you boot a Live CD of Ubuntu and then mount the drive? That is the failsafe.

Edit: Yes, Envy is a good installer for NVidia and ATI cards, from everything I've seen its rate of success is around 95% (a few people get minor issues, they always get solved).

Edit 2: DOH! I forgot to post how to mount a linux partition in case you don't know,[ heres how,]("http://www.psychocats.net/ubuntu/mountlinux") Do that from a live CD if neither of our ways work (including trying "vesa" instead of "nv" in the xorg section I told ya to edit).

---

### Post by Beatbreaker on 2007-06-29
i tried the replace of "nvidia" to "NV" and that didn't work

i also couldnt find a backup of xorg.conf - there SHOULD be one but i can't find it (or it's renamed it to something i can't i can't identify easily)

what caused the problems in the first place is the code

> sudo nvidia-glx-config enable

is there a way of just deleting all the changes that that command made?



...it dosen't make a difference that i'm using Kubuntu does it?

---

### Post by bodhi.zazen on 2007-06-29
Try this : ```
sudo nvidia-xconfig
```

---

### Post by starcraft.man on 2007-06-29
> ...it dosen't make a difference that i'm using Kubuntu does it?

Absolutely not. xorg is xorg.

> **Beatbreaker said:**
> i tried the replace of "nvidia" to "NV" and that didn't work

i also couldnt find a backup of xorg.conf - there SHOULD be one but i can't find it (or it's renamed it to something i can't i can't identify easily)

what caused the problems in the first place is the code



is there a way of just deleting all the changes that that command made?


I not sure, but Linux is sensitive to caps. You should have changed it to "nv". To be safe, please change it to the "vesa" driver, all lower case please. That should do it IMO.

---

### Post by Beatbreaker on 2007-06-29
i want to think you guys for you help, you really do a great job! 

- once again i've learnt alot (ie: the nano and ls commends) but i'm doing a reinstall again

---

### Post by starcraft.man on 2007-06-29
> **Beatbreaker said:**
> i want to think you guys for you help, you really do a great job! 

- once again i've learnt alot (ie: the nano and ls commends) but i'm doing a reinstall again

Ok, no problem. Your welcome :D

Oh and don't forget Envy, it (almost) always gets those drivers in hassle free, I bet it works for ya.

---

### Post by bodhi.zazen on 2007-06-29
> **Beatbreaker said:**
> i want to think you guys for you help, you really do a great job! 

- once again i've learnt alot (ie: the nano and ls commends) but i'm doing a reinstall again

LOL, you are most welcome. Thank you for marking the thread as solved.

So others may benefit, what worked ?

> **starcraft.man said:**
> Ok, no problem. Your welcome :D

Oh and don't forget Envy, it (almost) always gets those drivers in hassle free, I bet it works for ya.

I think Beatbreaker is trying to say install beryl ?

---

### Post by starcraft.man on 2007-06-29
> **bodhi.zazen said:**
> LOL, you are most welcome. Thank you for marking the thread as _solved._

So others may benefit, what worked ?


YAY! I didn't even notice he did that. Good job!

> I think Beatbreaker is trying to say install beryl ?

Oh, uh, well good luck with that. We open 24/7 if any more problems happen :p.

---

### Post by Beatbreaker on 2007-06-29
i reinstalled Kubuntu and used envy and the same problem has happened. 

i've gotten Beryl to work no problems at all on my last instillation of Ubuntu. It was so easy, i didn't get any issues at all! Now just installing the NVIDIA drivers on Kubuntu have caused so many issues 

you guys really do a good job, i hope that one day i'll be able to help people out with this stuff also. I've got alot to learn but i'm very egar to know as much as possible.

---

### Post by Beatbreaker on 2007-06-29
> **starcraft.man said:**
> Absolutely not. xorg is xorg.



I not sure, but Linux is sensitive to caps. You should have changed it to "nv". To be safe, please change it to the "vesa" driver, all lower case please. That should do it IMO.


..oh my god i completely forgot that linux is case sensitive (years of windows use has made me stupid)

'nv' worked no problems - i'm now back in Kubuntu, so i've tried to use ENVY but it's failed on me. What should i do? I'll consult the [envy site too]("http://www.albertomilone.com/nvidia_scripts1.html") in the meantime.

---

### Post by abn91c on 2007-06-29
> **starcraft.man said:**
> Did the install go bad or is it just an xorg issue? Either way, quickest way to get back to the GUI is to boot to grub and then select recovery mode.

When you get to the terminal as root type this in:

```
sudo nano /etc/X11/xorg.conf
```

Then scroll down the page (with arrow keys for up down left right) and find the device section for your card, it should be labeled nvidia something. Find the driver line like this:

```
Section "Device"
        Identifier      "nVidia Corporation NV40 [GeForce 6800 GT]"
        Driver         [COLOR="Red"] "nvidia"[/COLOR]
        BusID           "PCI:1:0:0"
```

and change the nvidia to [COLOR="Red"]"nv"[/COLOR]

That will do it. Push ctrl + O (letter) and push enter to save and overwrite. Then ctrl + X to exit. Then:

```
sudo reboot
```

Then boot up and log in like normal. We can go from there and figure out what went wrong.

Btw, that was the Nano editor for your information. It is a text editor that can be used in the terminal without any GUI :).

 I just had the same problem, you solution works!! 
Nvidia GForce MX200
Thanks :D

---

### Post by Beatbreaker on 2007-06-29
is this a solution to the entire issue? will the nvidia drivers work now no problems (ie; for Beryl?)

i''m using an 6600GT in an AGP slot BTW - it's in the "new" category i think

---

### Post by Beatbreaker on 2007-06-30
for some reason Envy dosen't work too well with my system - alhtough i remembered how i configured my video card last time (and this may not be the besy way bit it's working)

i went to the Desk Top Effects in the system menu - and it prompted me to install the video card, it installed the right one, and on restart the video works no problems!!  (i mght go into xorg.conf to see how it's been configured so ppl know

---

### Post by Beatbreaker on 2007-06-30
here ya go, unfortunately i don't have the one that didn't work up in the thread either (it's long gone!) but might help for reference sake

> Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

---

