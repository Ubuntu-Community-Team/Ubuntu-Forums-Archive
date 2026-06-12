---
title: "Trying to install NVidia graphics drivers"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by tone33 on 2008-02-06
I have successfully installed 64 bit Ubuntu 7.10 under dual boot on my Vista machine.  It is up and running - i can access the internet, etc.  I am trying to update/install the drivers for my NVidia GeForce 6600GT graphics card and am not sure how to do so.  I have read through the installation instructions on nvidia's site, but being new to Linux I'm stuck on a couple of steps.

1) How do I stop/terminate X and boot to a VGA console?

2) How do I change the runlevel - does telinit 3 change it to 3?  even after a reboot or is that just for the session I'm in?

Thanks.

---

### Post by Presto123 on 2008-02-06
You don't have to go through all of that. 

1. Search Nvidia in Add/Remove and install. (Driver will show up as Nvidia Binary X-org Driver)
2. After installation: Go to your Restricted Drivers Manager in the System menu and enable the card.
3. Reboot

And I always say to right click on the desktop and add a launcher for the configuration settings. Name it something like Nvidia (if you so choose) and type this as the command and hit ok:

```
gksudo nvidia-settings
```

---

### Post by tone33 on 2008-02-06
so while i was waiting on a reply (all 10 minutes lol) I came across another post and was able to install the driver by stopping X.  By doing this, have I done the same thing as I would have done by installing it from the GUI (Add/Remove) as you said?

---

### Post by Presto123 on 2008-02-06
Possibly. I have never had to do it like you were asking.

There may be some difference in the final product.

---

### Post by zigx on 2008-02-06
very true.,

---

### Post by FuturePilot on 2008-02-06
No, you installed the latest driver manually. When you use the Restricted Driver Manager you install the driver from the Ubuntu repositories.

---

### Post by Presto123 on 2008-02-06
> **FuturePilot said:**
> No, you installed the latest driver manually. When you use the Restricted Driver Manager you install the driver from the Ubuntu repositories.

So, he did get the updated driver. Thanks for that info FuturePilot.:popcorn:

---

### Post by tone33 on 2008-02-06
Looks like I got it thanks!  now to figure out the dual monitor setup via Twinview...

---

### Post by linuxuser187 on 2008-02-06
hi everyone!, i to have a question, i'm running 64bit ubuntu on my laptop and it has a geforce 7200 go, originally i tried using the restricted driver that came with ubuntu but my laptop would freeze all the time so i used gui envy and let it detect my card and installed the nvidia driver this way, everything works like a charm and under applications>system tools>nvidia settings the nvidia manager detected my 7200 go properly including the video ram, the system hasn't frozen or crashe once for days on end so i'm happy, However the only thing that is messed up is that when i have a window open there is no tool bar at the top so i don't have my minimize, expand or close buttons, i can't seem to move the windows as well, does anyone know how i can fix this? I am not running compiz fussion nor have installed it. I have tried to re-format and re install ubuntu and then do a fresh install with envy but no good as i still have the same issue. i tried installing compiz and emerald theme manager just for fun but no good as well, is there a way to re-install my gnome window manager, maybe it will solve the issue

---

### Post by Presto123 on 2008-02-06
Yeah...looks like an old issue. Try this in terminal and CTRL+ALT+BACKSPACE:

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

That changes the default depth and could fix this issue.

---

### Post by hyperair on 2008-02-06
> **linuxuser187 said:**
> hi everyone!, i to have a question, i'm running 64bit ubuntu on my laptop and it has a geforce 7200 go, originally i tried using the restricted driver that came with ubuntu but my laptop would freeze all the time so i used gui envy and let it detect my card and installed the nvidia driver this way, everything works like a charm and under applications>system tools>nvidia settings the nvidia manager detected my 7200 go properly including the video ram, the system hasn't frozen or crashe once for days on end so i'm happy, However the only thing that is messed up is that when i have a window open there is no tool bar at the top so i don't have my minimize, expand or close buttons, i can't seem to move the windows as well, does anyone know how i can fix this? I am not running compiz fussion nor have installed it. I have tried to re-format and re install ubuntu and then do a fresh install with envy but no good as i still have the same issue. i tried installin compiz and emarld theme manager just for fun but no good as well, is there a way to re-install my gnome window manager, maybe it will solve the issue

Compiz Fusion is installed by default in Ubuntu Gutsy. Turning on Desktop Effects turns on Compiz Fusion.

---

### Post by linuxuser187 on 2008-02-06
Dude you kick ***! I sincerly want to thank you so much that if you were here i would buy you a beer! I was stuck on this issue for a while and couldn't figure it out! Thank You!!! It worked like a charm!

---

### Post by linuxuser187 on 2008-02-06
I didn't turn on desktop effects because i know that it turns on compiz fusion but i didn't know that compiz fusion was installed by default, thanks for the info!

---

### Post by hyperair on 2008-02-06
No problem.

---

### Post by laurencelewis on 2008-02-10
Im having problems with this as well. Except when i try to install the driver from add/remove programs it says as follows:

"NVidia binary X.Org driver ('new' driver) cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type"

I dont get why its mentions amd64 as my cpu is an intel Q6600,  I have also tried downloading and installing the driver from the nvidia website but i get an error saying something about wrong coding.

Any ideas?

Oh yeah my graphics card is an 8800 GTS 512.

Cheers

---

### Post by laurencelewis on 2008-02-11
bump bump

---

### Post by hyperair on 2008-02-11
Well since you're using an 8800 card, you need to get the driver from NVidia's site. It's not provided by Ubuntu.

---

