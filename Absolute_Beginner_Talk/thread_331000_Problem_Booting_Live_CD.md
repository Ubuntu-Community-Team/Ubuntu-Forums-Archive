---
title: "Problem Booting Live CD"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by mtgordon on 2007-01-03
Hello Everyone,
I am completely new to the forum and also completely new to Ubuntu. I have never used any Linux distro but keep hearing about Ubuntu so I decided to see what all the fuss was about. I downloaded 6.10 amd 64. I want to try Ubuntu out with the Live Cd option so I rebooted my computer with the disc in. It rebooted and brought up a screen with various options of which the first one was Install/Try live cd or something like that. I hit enter on the first option and it brought up a screen saying it was decompressing linux......done.
Booting kernel. It never went any further after that. I assume it did not boot kernel. What can I do. Any help is appreciated. Thanks

---

### Post by raul_ on 2007-01-04
Check CD for errors. If any errors pop up, reburn the iso file and 4x speed. If that's not the problem try pressing F6 as soon as you see the ubuntu logo and you'll see a line; add noapic nolapic to the end of that line and press enter. If that doesn't work i'm out of ideas :-k

---

### Post by gjtoth on 2007-01-04
> **mtgordon said:**
> Hello Everyone,
I am completely new to the forum and also completely new to Ubuntu. I have never used any Linux distro but keep hearing about Ubuntu so I decided to see what all the fuss was about. I downloaded 6.10 amd 64. I want to try Ubuntu out with the Live Cd option so I rebooted my computer with the disc in. It rebooted and brought up a screen with various options of which the first one was Install/Try live cd or something like that. I hit enter on the first option and it brought up a screen saying it was decompressing linux......done.
Booting kernel. It never went any further after that. I assume it did not boot kernel. What can I do. Any help is appreciated. Thanks

What's your hardware?  Processor, video card, etc.

---

### Post by mtgordon on 2007-01-04
> **gjtoth said:**
> What's your hardware?  Processor, video card, etc.

AMD64 2.4ghz 3800+, nVidia GeForce 6150 ,2gb PC3200 DDR, Checked disc for errors, came up clean. I am lost. I dont know much about this stuff either though. Thanks for trying to help.

---

### Post by kinson on 2007-01-04
I'm not sure whether it might be the situation here, but try:

On the boot screen with various options(as you mentioned :p ), there's a video setting, I think the default is set to VGA, try changing that to something lower and see whether it boots. I had the same scenario, but my screen faded halfway, and this solved it.

Cheers,
Kinson

---

### Post by mykalreborn on 2007-01-04
when the ubuntu logo pops up with a bunch of option choose "start ubuntu in safe graphics mode". it may be a video card problem, although i doubt it. but it's just crazy enough to work. :D

---

### Post by hoges on 2007-01-04
It could most likely be a vid card problem. My ati x800xl didn't work with the live cd, but my laptop did. Not sure about nvidia cards, but there may be a similar problem. I had to install it with the alternative cd. If you want to try it first, though, i've no idea how you could fix the vid driver for it.

---

### Post by tommcd on 2007-01-04
Perhaps you could try the 32-bit ubuntu live CD. That may be a more fail safe place to start with.
If that does not work you could install from the alternate CD. This is a text based installer that should enable you to install without worrying about graphics card problems. The nvidia 6150 chipset should work AFAIK.

---

### Post by mykalreborn on 2007-01-04
> **tommcd said:**
> Perhaps you could try the 32-bit ubuntu live CD. That may be a more fail safe place to start with.
If that does not work you could install from the alternate CD. This is a text based installer that should enable you to install without worrying about graphics card problems. The nvidia 6150 chipset should work AFAIK.

i sopose he has a 64 bit processor , so he can't use the 32 bit ubuntu. or can he? :confused:

---

### Post by raul_ on 2007-01-04
> **mykalreborn said:**
> i sopose he has a 64 bit processor , so he can't use the 32 bit ubuntu. or can he? :confused:

I use it. What you can't use is the 64bit Ubuntu in a 32bit cpu ;)

---

### Post by kinson on 2007-01-04
> **mykalreborn said:**
> i sopose he has a 64 bit processor , so he can't use the 32 bit ubuntu. or can he? :confused:

Actually, he can. You can install Ubuntu i386 with a 64-bit processor no problem. I think the 64-bit edition is supposed to give better performance for 64-bit processors, but I don't think the difference is that much.

I myself am using an AMD64 chip, with Ubuntu64, but I'm planning to format and re-install with a i386 version sometime soon. Flash and all those things just work/install easier on the i386 version(read: kinson is a noob :(  )

Cheers,
Kinson

---

### Post by mykalreborn on 2007-01-04
> **raul_ said:**
> I use it. What you can't use is the 64bit Ubuntu in a 32bit cpu ;)

i didn't know that :D

---

### Post by mtgordon on 2007-01-04
Thanks for all the input guys. I am going to try the 32 bit like suggested. I will post the results for anyone interested. Again, thanks for your comments and your time.

---

