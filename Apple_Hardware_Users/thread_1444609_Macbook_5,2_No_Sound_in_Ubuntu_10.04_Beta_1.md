---
title: "Macbook 5,2 No Sound in Ubuntu 10.04 Beta 1"
date: 2010-04-01
forum: Apple Hardware Users
---

### Post by ErsinG on 2010-04-01
Hello there.

I'm using MacBook 5,2. 

Although i tried very hard, i coulnd't get the sound working on 9.10.
I read a post in this forum about the new kernel version in 10.04 beta 1 makes the sound work out of the box in Macbook 5,2's. 

Now i freshly installed a copy of Ubuntu 10.04 Beta 1 on my mac (ofc 64 bit version) and no sound either..

Checked the sound sliders, none is muted.
Can any1 help me with this problem?...

Thanks.

---

### Post by ZeroLinux on 2010-04-02
in Terminal:
After Installing you need to unmute front speaker
Go to Terminal (Application -> Accessories -> Terminal) and there write alsamixer. Then go 3 times press right arrow key and press m
And then yo can press the key "Up" to set volume level you like
Esc to exit
Enjoy

---

### Post by ErsinG on 2010-04-02
yeah thanks for the reply. 

it's now "working" however it's not working as it should be.. when watching a movie or smth, i keep hearing parasites and sometimes it does not work at all for emesene notification sounds etc. 

the thing is, in sound preferences, my hardware is shown as <internal audio, analog stereo output> 
is there any chance of making the digital sound driver working and get a flawless sound? or am i asking for too much?

---

### Post by ZeroLinux on 2010-04-02
May be you'll try to install other kernel from backports
1) In the "Software Sources" allow backports
2) Update (reload packages info)
2) Go to Synaptic package manger
Check smth like linux-backports-...alsa-generic for yor linux version (lucid)
Install and reboot

---

### Post by ErsinG on 2010-04-02
Now trying.. Thanks for your help. 
I'll post updates

EDIT : After i installed that modules and reboot, sound wasn't working at all again.
(I double checked both sliders from volume control and alsamixer...)

I'm now removing the modules again.

---

### Post by ZeroLinux on 2010-04-03
You can try to change level of the output signal
To do it install "PulseAudio Device Chooser"
Write in Terminal 
sudo apt-get install paman (it was in my case)
or
sudo apt-get install padevchooser (may be it works also)

Start it from Application -> Sound & Video -> PulseAudio Device Chooser
Click on its the icon in the upper-right corner. Choose Manager... -> Tab "Devices" -> In the tree "Sources" ->
find device with "output" string and cange the level of signal
It may help to get rid of noise.
May be you need to turn off some input sources for not to have unnecessary sounds.

---

### Post by oohshiny on 2010-04-04
Sorry to go off-topic here, but did you need any special boot options apart from "acpi=off" to get 10.04 working? My Macbook 5,2 kinda froze up using the Beta 1 LiveCD...

---

### Post by sototallycarl on 2010-04-04
Same boat here. 10.04 in a Macbook Pro 5,2 is a pain!

I got it to boot and instal from CD by adding nouveau.noaccel=1 blacklist=vga16fb boot options. I also left acpi on because my keyboard and trackpad stopped working half way during the install with it off.

My problem now is upon boot from hard disk it freezes at isapnp scanning. No idea how to get past this though...

Edit: Just blacklist isapnp too like so: nouveau.noaccel=1 blacklist=vga16fb,isapnp Still no idea what its for or why it matters. Everything I use normally works like normal so I am not too worried about it

---

### Post by qazwsxedc on 2010-04-25
Hellow 
I've got the same problem =( 

There is no sound on macbook 5,2 
i've unmuteed everything but still it dosen't work =(( 
_______
Maybe the problem is connected with driver that i've mark at System -- Preverences -- Sound  --- Hardware (what device shoud be marked? )

---

### Post by linuxopjemac on 2010-04-26
this seemed to work in Karmic, I don't know about Lucid:
[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=25](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=25)

---

