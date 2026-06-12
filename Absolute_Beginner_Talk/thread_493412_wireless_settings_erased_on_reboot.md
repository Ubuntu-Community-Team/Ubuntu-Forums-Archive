---
title: "wireless settings erased on reboot"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by dnathe4th on 2007-07-05
I used this [guide]("http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php") to finally get my new install to connect to my wireless network.  Unfortunately, upon restarting the system, my settings were somehow erased, and I am back to only being able to select a wired connection to the internet. 
fathermore, the same method I used to connect the first time no longer works, ndiswrapper -l  shows that i have the device driver installed, but sudo modprobe ndiswrapper CRASHes my system, though that was the next step in the guide

Thoughts?

---

### Post by dnathe4th on 2007-07-05
this problem isn't as popular as i was hoping it might be.  actually i can't find any other posts where said wireless settings were erased upon boot.  wheres my buddie who helped me before :-D

---

### Post by dnathe4th on 2007-07-05
So I'll bump thsi again, and add some content.

The part about this little issue that scares me is that I can't just reissue the same commands that worked before, as that crashes my system time and time again

---

### Post by jocheem67 on 2007-07-06
You need to know the name of the chip your pci card is using, firstly....then you go search for ndiswrapper and the name of the chip. 
Then there's the issue of installing ndiswrapper, which is quite an intimidating process for a yet unexperienced ubuntu-user.
It's an intel right?

[http://ubuntuforums.org/showthread.php?t=396204](http://ubuntuforums.org/showthread.php?t=396204)

This is an extensive thread about the intel, it looks like official drivers are on the way or maybe already there....
I suggest you check out the entire thread, there's a lot of info there.

Cheers

---

### Post by kwalters on 2007-07-06
I'm very much a beginner myself, so I hesitate to offer advice.  

But there is a command to make ndis reload automatically on bootup.  I think it is something like

sudo ndiswrapper -m

but I cannot be certain as that is from memory from reading the wireless and networking forum at great length

KW

---

### Post by dnathe4th on 2007-07-06
sudo ndiswrapper -m does nothing for me, it tells me something about it already being there

i managed to get this to work, as long as i have the wireless switch off then i modprobe ndiswrapper.
but there's got to be a better way to automatically do it on boot, without having to turn the wireless switch off.  thoughts?

---

### Post by annda on 2007-07-06
to load the ndiswrapper on boot, you need to tell the system to do so:
```

gksudo gedit /etc/modules
```

Add the following module to the list 

```
ndiswrapper
```

this is quoted from the [feisty guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29") - second hand advice, since my card is natively supported, no need for win drivers/ndiswrapper.

later the guide says something about manual configuration - i don't know if this is necessary or optional in case you don't use the network applet. again, not a user, so my opinions would just be opinions, possibly confusing.

but i can recommend this howto:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by dnathe4th on 2007-07-07
tried that, now ive got all kinds of fun things happening
first, it would get through a lot of the boot, but hand up on loading SPCI modules (i think those are the right initials)
Now, if I let it boot normal, the orange bar freezes 1/3 of the way in
booting in recovery mode, i get this lovely phrase right after Activating swapfile swap (which i always thought was a funny phrase on its own)
```
BUG: soft lockup detected on CPU#0
```
happens usually around 31 seconds


ps incase i didnt already say it, this all comes about after i added ndiswrapper to etc/modules

---

### Post by dnathe4th on 2007-07-07
yep just confirming i cannot find a way to boot that gives me the ability to punch in any commands.  am i gonn have to reinstall :-(

---

