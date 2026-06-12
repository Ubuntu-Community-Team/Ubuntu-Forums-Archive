---
title: "Lost my GUI - Help please"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-07-11
Hello.  I've been using Dapper 6.06 for a few months now, but I know very little about the operating system.

After a couple of weeks away, I turn on my laptop and I get the message:
> Failed to start the X server............. (etc)
which many of you have seen before, and I've searched this forum for a solution but I'm not getting anywhere with it.

On my screen there is no time to press <yes> or <no> as over-written immediately below these options is:> Ubuntu 6.06.1 LTS david-laptop tty2

david-laptop login: 
which would appear to have put me into the command line.

One solution suggested in a thread I read was to do > sudo dpkg-reconfigure xserver-org and accept all that is offered and then reboot.  But I just come back to the same error.

I have a feeling that it might be do to with an update that happened before I went on holiday.

For your information the kernal is 2.6.15-28-386 and the Graphics card is NVIDIA GeForce Go 6100

I would dearly love some step by step instructions please, or a link to to some guidance (which I haven't found :( )

Thanks,
David

---

### Post by Surkow on 2007-07-11
I assume you have used auto-update and the kernel image has been replaced my a more recent version? When that happens the proprietary nVidia driver stops functioning.

Use the following command:

```
sudo nano /etc/X11/xorg.conf
```

You will be presented with a simple txt editor. Scroll to the section that looks like this:

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
EndSection
```

Change the "Driver" name from "nvidia' to "nv". Use the following to command to start X again:

```
sudo /etc/init.d/gdm restart
```

---

### Post by overdrank on 2007-07-11
> **David Floyd said:**
> Hello.  I've been using Dapper 6.06 for a few months now, but I know very little about the operating system.

After a couple of weeks away, I turn on my laptop and I get the message:

which many of you have seen before, and I've searched this forum for a solution but I'm not getting anywhere with it.

On my screen there is no time to press <yes> or <no> as over-written immediately below these options is: 
which would appear to have put me into the command line.

One solution suggested in a thread I read was to do  and accept all that is offered and then reboot.  But I just come back to the same error.

I have a feeling that it might be do to with an update that happened before I went on holiday.

For your information the kernal is 2.6.15-28-386 and the Graphics card is NVIDIA GeForce Go 6100

I would dearly love some step by step instructions please, or a link to to some guidance (which I haven't found :( )

Thanks,
David

Hi if the thread above does not help you, this thread may 
[http://ubuntuforums.org/showthread.php?t=480287&highlight=NVIDIA+GeForce+Go+6100](http://ubuntuforums.org/showthread.php?t=480287&highlight=NVIDIA+GeForce+Go+6100)
Good luck! :guitar:

---

### Post by David Floyd on 2007-07-11
> **Surkow said:**
> I assume you have used auto-update and the kernel image has been replaced my a more recent version? When that happens the proprietary nVidia driver stops functioning.

Use the following command:

```
sudo nano /etc/X11/xorg.conf
```

You will be presented with a simple txt editor. Scroll to the section that looks like this:

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
EndSection
```

Change the "Driver" name from "nvidia' to "nv". Use the following to command to start X again:

```
sudo /etc/init.d/gdm restart
```

Thanks for you reply (I see there is another reply, which I haven't dealt with yet).

My xorg.conf appears to have two items with the heading 'Section "Device"', one as you describe (except that the BoardName is "GeForce Go 6100") and one that reads:```
Section "Device"
   Identifier  "Generic Video Card"
   Drive  "nvidia"
End Section
```

Should I change them both to nv, or should the second Section be deleted completely?

David

---

### Post by Surkow on 2007-07-11
> **David Floyd said:**
> Thanks for you reply (I see there is another reply, which I haven't dealt with yet).

My xorg.conf appears to have two items with the heading 'Section "Device"', one as you describe (except that the BoardName is "GeForce Go 6100") and one that reads:```
Section "Device"
   Identifier  "Generic Video Card"
   Drive  "nvidia"
End Section
```

Should I change them both to nv, or should the second Section be deleted completely?

David

Change them both to nv to be sure that the proprietary driver won't be loaded. If you are using dual head you shouldn't expect to get support for two screens with the nv driver. When the GUI starts you should use a tool like [envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install the latest nVidia drivers.

---

### Post by David Floyd on 2007-07-11
> **Surkow said:**
> Change them both to nv to be sure that the proprietary driver won't be loaded. If you are using dual head you shouldn't expect to get support for two screens with the nv driver. When the GUI starts you should use a tool like [envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install the latest nVidia drivers.

Thanks for that.  However after entering ```

sudo /etc/init.d/gdm restart
```

as you suggested in your first reply I get the same blue screen error but this time the text box is surrounded by odd graphic symbles and I AM able to select <yes> or <no> (whereas I wasn't able to before).

Can you help me further, please, if I report what the following screens say?

Thanks,
David

---

### Post by Surkow on 2007-07-11
> **David Floyd said:**
> Thanks for that.  However after entering ```

sudo /etc/init.d/gdm restart
```

as you suggested in your first reply I get the same blue screen error but this time the text box is surrounded by odd graphic symbles and I AM able to select <yes> or <no> (whereas I wasn't able to before).

Can you help me further, please, if I report what the following screens say?

Thanks,
David

Sure...but this doesn't sound normal to me. The nv driver should never fail to load (it's the basic 2D driver). I don't think the Dapper repositories include the binary nVidia driver. Trying the following might help:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by David Floyd on 2007-07-11
> **Surkow said:**
> Sure...but this doesn't sound normal to me. The nv driver should never fail to load (it's the basic 2D driver). I don't think the Dapper repositories include the binary nVidia driver. Trying the following might help:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thank you.  I did that and it worked, in as mush as I had a GUI (don't like the resolution though :( ). There would appear to be a replacement xorg.conf as a result.

I then ran envy from the link you gave earlier.  I noticed a few things failed as they wizzed by on the screen.  At the end I was asked if I wanted xorg.conf updated, which I accepted and I also accepted to restart.

It didn't work.  I'm back to the original error screen followed by the command line login prompt.

Any ideas about what I could do now?

Thanks for your help.

David

---

### Post by Surkow on 2007-07-11
It would be nice if you could have posted the error. Somehow you graphics card isn't supported by the newest nVidia drivers. Currently Ubuntu had two major upgrades called Edgy and Feisty (they are already busy with testing a third major upgrade called Gutsy). I would suggest you to upgrade your system to a newer version than Dapper because of included graphics drivers in the repositories.

---

### Post by David Floyd on 2007-07-11
> **Surkow said:**
> It would be nice if you could have posted the error. 

See my opening post to this thread.

David

---

### Post by Surkow on 2007-07-11
> **David Floyd said:**
> See my opening post to this thread.

David

That is a generic error message. :p

I meant this:

> I noticed a few things failed as they wizzed by on the screen.

---

### Post by ARandomKid on 2007-07-11
^When that happens, it generally goes by WAY too fast to read (at least, it does for me...)

so don't be too hard on him if he can't read it all. (Or just do it in pieces with memorizing a little bit each time you reboot...)

I had this exact problem, and was only able to fix it by reinstalling a very old version of linux from a CD. (And afterwards, I immediately requested a Feisty CD in case this happens again. ;x_X WAnt to have a version that isn't 2 years old.)

But then, expect there to be some solution I didn't see. There always is. ;>_>

---

### Post by koshari on 2007-07-11
i would go back to the free driver as you did before to get back into the gui and then use the nvidia driver in the repositories with synaptic, sure its a bit older than the one envy will compile and load for you but i would expect it would be compatible with your kernal.

once you get the gui booting into the basic NV config make a copy of the xorg.conf file with a name you can remember like > xorg.conf.trusty. then if you get back to the point where the gui wont boot its a simple one liner to get back into the basic gui,  ```
sudo cp/etc/X11/xorg.conf.trusty /etcX11xorg.conf
```.

---

### Post by David Floyd on 2007-07-12
> **Surkow said:**
> That is a generic error message. :p

I meant this:

Sorry - I missunderstood.

I've now done ENVY from the command line (sudo envy -t) and captured the output and put it in a text file attached. (well 2 text files as one was too big to attach)

I see others have also replied - thanks, I will have a look at your suggestions.

David

---

### Post by Surkow on 2007-07-12
> **David Floyd said:**
> Sorry - I missunderstood.

I've now done ENVY from the command line (sudo envy -t) and captured the output and put it in a text file attached. (well 2 text files as one was too big to attach)

I see others have also replied - thanks, I will have a look at your suggestions.

David

To be honest...I can't find a problem at all. I think you should use the command that got your GUI back. After that upgrade to a more recent version of Ubuntu and try installing the nvidia-glx(-new) drivers from the repositories.

---

### Post by David Floyd on 2007-07-12
> **Surkow said:**
> To be honest...I can't find a problem at all. I think you should use the command that got your GUI back. After that upgrade to a more recent version of Ubuntu and try installing the nvidia-glx(-new) drivers from the repositories.

Thank you very much for your help.

I will look into upgrading to a later edition of Ubuntu.

David

---

