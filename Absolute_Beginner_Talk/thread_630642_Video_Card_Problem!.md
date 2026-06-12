---
title: "Video Card Problem!"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by tahsocks on 2007-12-03
Hey,  I appreciate you probably get a million questions like this.. but I thought I'd ask the community, as about 3 hours of net searching have been in vain...


I cannot for the life of me get Ubuntu to play video files. I have all the codecs etc that are required to play the file types.. when I try to run (for example) an AVI through mplayer it pops up 'ERROR opening/initializing the selected video_out (-vo) Device'. 

I am running the latest version of Ubuntu, after just updating!

The computer I am running, apparently the graphics card (according to linux) is a SIS 530/620 PCI/AGP VGA Display adapter.

It says device type is unknown, so i presume its using processing power for the display.

Any clues how to resolve this? Be grand if you could!

---

### Post by Dapman01 on 2007-12-03
wipe that smirk off your face and listen

Have you installed your video drivers?

---

### Post by tahsocks on 2007-12-03
I cant find them!

I don't know how to install them either and the documentation only seems to cover nvidia, ati, intel etc.

Sorry about the grin..!

---

### Post by Crafty Kisses on 2007-12-03
> **tahsocks said:**
> I cant find them!

I don't know how to install them either and the documentation only seems to cover nvidia, ati, intel etc.

Sorry about the grin..!

Post the following output:
```
glxinfo
```

---

### Post by Hospadar on 2007-12-03
also, have a look at the restricted drivers manager System->Administration->Restricted Driver Manager  and see if there are some drivers there for you to install.

---

### Post by tahsocks on 2007-12-04
Right ok.

I have posted glxinfo, and it produces an error 

'Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 142 (GLX)
Minor opcode of failed request: 3 (X_GLXcreatecontext)
Serial number of failed request: 16
Current serial number in output stream: 17.'

There is also no restricted drivers to be installed.

I haven't a clue what this means..

---

### Post by GSF1200S on 2007-12-04
Also, post the results of:

```
lspci
```

That may help someone if it doesnt help me...

---

### Post by tahsocks on 2007-12-04
right, when i post that it comes up with loads of stuff.. presumably just the gfx card is relevant?

it says

01:00.0 VGA COMpatible controller: Silicon Integrated systems (SIS) 530/620 PCI/AGP VGA Display adapter (Rev 2a).

---

### Post by tahsocks on 2007-12-04
Right.. I have solved the problem! It is now playing video..

However, all my video has a thick pink line through it...?!

Whatever could this be?

---

