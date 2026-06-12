---
title: "Screen Resolution/problem with widescreen?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-08
Hi,
I'm on a 22" widescreen monitor. I've been able to get my screen resolution up to 1280 x 1024 by using "dpkg-reconfigure -phigh xserver-xorg", but it will go  as high as 1680 X 1050 (which I know from using Vista). 

I notice in browsing with Firefox that photos are stretched out wider than they should be and it seems that this is because of the lower resolution. Am I right? Would getting the highest resolution of 1680 x 1050 fix that?

I've tried running the xserver-xorg many times and have tried choosing only the highest resolution and it seems that the only way to get the highest resolution (1680) is by getting my ATI X-1650 accelerated driver installed. 

I've tried the Envy program several times; it worked once on one (1) kernel only, which made me suspicious, so I uninstalled it. Every other attempt with Envy has given me a blank screen on the reboot. 

Does anyone have any other ideas on how to get the highest resolution to work? I know I'm not the only person with this problem, so I would hope a fix is being developed for this.

Thanks for any help or suggestions,...Frank B.

---

### Post by Dexter Bip on 2007-06-08
I think I'll leave the actual solution to better minds but, as far as this is concerned:

> I notice in browsing with Firefox that photos are stretched out wider than they should be and it seems that this is because of the lower resolution. Am I right? Would getting the highest resolution of 1680 x 1050 fix that?

The answer is yes. 1280x1024 is not a widescreen resolution. So your monitor is effectively stretching what is roughly a 4:3 resolution over a wide display. You can see this by dividing the larger number in the resolution by the smaller one. 1280/1024 gives you 1.25, whereas 1680/1050 gives you 1.6, which is much closer to a proper widescreen ratio (16/9 = 1.77)

---

### Post by Brightbelt on 2007-06-08
Thanks Dexter, at least I know that nothing else is wrong with the monitor or my Ubuntu installation.

Like I said, by using Envy, I was able to get the accelerated graphics driver installed successfully on one (1) kernel only at one point. But that just didn't seem right to keep it that way. 

Thanks for your quick response,...Frank B.

---

### Post by Dexter Bip on 2007-06-08
I've been wrestling with getting a widescreen resolution to display on my monitor for days myself, so I know how it feels. I'm an utter newb here so this advice might be worthless, but have you tried directly editing ***(EDITED DUE TO INITIAL STUPIDITY>)*** /etc/X11/xorg.conf? That's what worked for me in the end.

open the file and scroll down to where it says

```
section "screen"
```

then, where it says something like:

```
SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480" 
```

try adding in the highest resolution which you think your monitor and graphics card supports. So, assuming it is 1680x1050, edit it to say this:

```
SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
```

then restart the X session (ctrl-alt-backspace) and, if it hasn't automagically switched to the right resolution, have a look at the screen resolution settings in the GUI to see if it's now displayed in there.

(backing up xorg.conf first is almost certainly a good idea, just in case you accidentally do something daft before you save and need to revert from the CLI. Like I did. Twice.)

---

### Post by Brightbelt on 2007-06-08
Ok Dexter, I'm willing to try BUT how do you make AND save a backup,... AND how do you reapply that backup when your system goes screwy on you??

I really would like to know these things because, I'm sorry but, so many guys just say these things and leave the details unspoken. So for non-geeks like me, it's like having NO INFORMATION at all !!

Many Thanks for following up, Frank B.

---

### Post by Styx on 2007-06-08
> **Brightbelt said:**
> Ok Dexter, I'm willing to try BUT how do you make AND save a backup,... AND how do you reapply that backup when your system goes screwy on you??

I really would like to know these things because, I'm sorry but, so many guys just say these things and leave the details unspoken. So for non-geeks like me, it's like having NO INFORMATION at all !!

Many Thanks for following up, Frank B.



to make a back up use

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk
```

and if you need top restor your system you can use one of the virtual konsoles use ctrl+alt+F1
there you can log in as your normal user and then 

```
sudo cp /etc/X11/xorg.conf.bk /etc/X11/xorg.conf
```

to restart your x session you need to go back to it by pressing ctrl+alt+F7
there you can restart it with ctrl+alt+backspace

If that dose not work you can go back to the first konsole by pressing ctrl+alt+F1 
and typ

```
sudo killall kdm
kdm
```
if you have gnome juse gdm in place of the kdm

hope it helps

---

### Post by timcredible on 2007-06-08
fwiw, i installed the ati drivers per the how to at ubuntuguide.org, rebooted, and it automatically reset my 24" widescreen to 1920x1200 at the proper refresh rate, it looks great.  before i installed the ati drivers, it would only do 800x600.  

have you installed your nvidia or ati drivers?

---

### Post by Brightbelt on 2007-06-08
Thanks Styx !!! I've copied that to my text editor, so I'll have it from now on. 

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-06-08
Timcredible,
All this is happening because a regular install of my driver - as well as several other alternate methods of installing -  results in a blank screen....

I will check out ubuntu.org, but my standard method of install has been to go into the Restricted Drivers Manager and enable the driver there. That has not worked for me, so.... here we are etc,....

Thanks for responding,...Frank B.

---

### Post by Brightbelt on 2007-06-08
Ok, in case anyone is still reading, I'm trying:

"sudo /etc/X11/xorg.conf"

and I get 'No Command Found'. 

Ubuntu has a way of surprising you many times over,.....Frank B.

---

### Post by bodhi.zazen on 2007-06-08
gedit will make a back up automatically by adding a ~ to the end of the file name.

So your backup will be at /etc/X11/xorg.conf~

So to edit :

```
gksudo gedit /etc/X11/xorg.conf
```

Then restart X (log out and back in)

If that does not fix your problem, what video card are you using ?

---

### Post by Brightbelt on 2007-06-08
Ok, Well....I sort of found a solution similar to something before but I think I'll take it this time.  My card is an ATI X-1650.

I went into the ENVY interface and this time, I UN-installed Nvidia drivers first, because I had originally had an Nvidia card and changed to ATI because of Vista (this change worked very well for Vista by the way).

What has happened is that by using ENVY to install the Ati driver, I got the change successfully done only on my generic 16 kernel. (I'm on Ubuntu Studio). The Low Latency 16 Kernel reboots to a blank screen.

SO, ....is there any way to change the startup menu so that the generic kernel is the first on the list ? Currently, the Low Latency 16 kernel is the first one.  And I currently don't need the low latency because I'm not recording with this computer yet. 

Many Thanks for following me here, Frank B.

---

### Post by bodhi.zazen on 2007-06-08
You can edit /boot/grub/menu.lst and change the order of your boot options.

---

### Post by Brightbelt on 2007-06-08
Thanks Bohdi!!!

---

### Post by Brightbelt on 2007-06-08
Sorry, Thanks Bodhi !!

---

### Post by Brightbelt on 2007-06-08
Here's what I got when I ran this:   sudo edit /boot/grub/menu.lst
"...
Password:
Warning: unknown mime-type for "/boot/grub/menu.lst" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
..."

lately none of my commands work !! Bummer:( Any ideas about what went wrong here ??

Many Thanks, Frank B.

---

### Post by bodhi.zazen on 2007-06-08
> **Brightbelt said:**
> Here's what I got when I ran this:   sudo edit /boot/grub/menu.lst
"...
Password:
Warning: unknown mime-type for "/boot/grub/menu.lst" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
..."

lately none of my commands work !! Bummer:( Any ideas about what went wrong here ??

Many Thanks, Frank B.

:lolflag:

Small typo. Should be gedit.

```
gksudo **[B]gedit**[/b] /boot/grub/menu.lst
```

[list][*]Note that is a small "L" not a 1[*]You should use gksudo with graphical programs (rather then sudo)[*]You will likely get a "warning" with gksudo , it is a known "bug" but does not cause problems (other then scaring new users)[/list]

---

### Post by Brightbelt on 2007-06-08
Thanks Bodhi !! That worked just fine. 

Btw, would it bother you running things this way? - That is, knowing that the accelerated Ati driver install works on only one kernel and not the other ??? It just seems odd to me. 

Thanks again for your smart and fast assistance, ....Frank B.

---

### Post by bodhi.zazen on 2007-06-08
> **Brightbelt said:**
> Thanks Bodhi !! That worked just fine. 

Btw, would it bother you running things this way? - That is, knowing that the accelerated Ati driver install works on only one kernel and not the other ??? It just seems odd to me. 

Thanks again for your smart and fast assistance, ....Frank B.

I am not so good with ATI so I am not the best to answer you question. If it is anything like the nvidia drivers you will need to set up your ATI with *each kernel*. This also means setting up the ATI card with each kernel upgrade (at least that is the nVidia way).

Wish that was a little easier ...

---

