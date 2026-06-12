---
title: "Logitech Quickcam Messenger"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by dunklegend on 2007-05-07
I am trying to use skype but I can't because I use my Logitech Quickcam Messenger because Ubuntu won't recognize it, or maybe I'm just too dumb to set it up.

Can somebody help me?

I am using Feisty Fawn

Thanks in advance!

---

### Post by dunklegend on 2007-05-07
I did a quick google search for a driver but I found a lot of options, I tried several but they didn't work for me, so I don't know if those drivers don't work with feisty or if I'm doing something wrong.

Is there someone who installed a quickcam messenger successfully in Feisty?

If the answer is yes, can you post what you did?

There are very few things that I want to do that I can only do in windows and using Skype is one of them.

Please help me so I can ditch XP once and for all.
:)

---

### Post by dunklegend on 2007-05-07
This is the code for my camera:

Bus 001 Device 003: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

I obtained it by typing

```
lsusb
```

in the terminal.

I don't know if that is useful but that's the first step in one of the pages that I found.

Actually I did the whole procedure in that page but for some reason it didn't work.

---

### Post by dunklegend on 2007-05-07
The procedure also said to install camorama.

I installed it but I don't get an image from my web cam.

Anybody with a Logitech Quickcam Messenger that could help me.

In the meantime I'm still googling and reading, and I will post here whatever I try, but if somebody has the knowledge and can help me, please do so.

I would rather enjoy my new OS than having to reinvent the wheel just to install an old camera.

Ubuntu rocks:guitar:

---

### Post by dunklegend on 2007-05-07
The procedure that I'm following gives me the source code for the driver, I ran the script but it gave me this message:

[COLOR="Teal"][!] The QuickCam driver is already loaded!
You should first remove the (old?) module by issuing
        rmmod mod_quickcam || rmmod quickcam
as root, otherwise I will fail to install the new module.[/COLOR]

I tried typing rmmod mod_quickcam || rmmod quickcam in the terminal but I get these errors:


[COLOR="Teal"]ERROR: Module mod_quickcam does not exist in /proc/modules
ERROR: Module quickcam does not exist in /proc/modules
[/COLOR]
 
How can I remove the driver, or better how can I make the driver that is installed work?

---

### Post by dunklegend on 2007-05-07
Am I in the wrong forum?

If I am where should I put it to get some help.

I don't think that this should be a very difficult problem, after all Logitech cameras are very common.

---

### Post by dunklegend on 2007-05-07
I found another post that could fix my problem:

[http://ubuntuforums.org/showthread.php?t=111225]("http://ubuntuforums.org/showthread.php?t=111225")

It asks to install kernel-headers 2.6.10 for i386 from synaptic, and the kernel sources.

How do I do this?

I looked in synaptic but there's no kernel-headers

---

### Post by dunklegend on 2007-05-08
OK after trying different ways of following the procedure that I linked to in my previous post I was able to install easycam2 and supposedly it installed the driver for my camera.

But now I don't know how to check that my camera is working

Anyone can help?

---

### Post by battleshipterry on 2007-05-09
I have been trying to get my QuickCam Home logitech to work to reading along with your progress and I am new to ubuntu and have a less then smart question the program Camorama you talked about is loaded in Synaptic but does not apper in any applications listings I typed in a terminal Camorama and it said (bash: Camorama: command not found)  it will not run how do you get it to start?


Sorry just new for a short time.:confused:

---

### Post by battleshipterry on 2007-05-09
I reloaded it and it know runs and appers in Graphics menu thanks anyway know to get web cam working it displays my ATI tv card video but not yet logitech cam.

---

### Post by Praill on 2007-05-26
I cannot get my quickcam messenger to work in the new kernel. It worked in the edgy kernel but not the feisty.
;(
o well.. guess we have to wait

---

### Post by S-99 on 2007-06-05
I have the same problem here as well.

---

