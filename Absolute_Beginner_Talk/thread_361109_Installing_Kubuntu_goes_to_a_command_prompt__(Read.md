---
title: "Installing Kubuntu goes to a command prompt  (Read 2 times)"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by greywolfexcel on 2007-02-14
Hello,

I am a Linux newbie, and figured that since Ubuntu seemed to be the most popular (and newbie-friendly) version of Linux, I'd start out with that. I grabbed Kubuntu because I saw some stuff about the KDE desktop vs GNOME that I liked better.

I just downloaded and burned the live CD of Kubuntu and was looking forward to installing it when after I chose the "Start Kubuntu" option, I was greeted with an unfriendly-looking command prompt, not the installation GUI I expected. I figured out how to reboot with the "sudo reboot" commmand, but attempting to continue the install with "boot: live" or "boot" told me that the command "boot" did not exist. I had already checked the CD to make sure it had no errors, and it did not (0 checksum errors found), so I tried booting it in the safe graphics mode, but to no avail - I still got the command prompt like before.

I went to the #Kubuntu IRC channel on irc.freenode.net, but no one was able to help me aside from guessing the problem might be my video card. I did a bit of research, but didn't find any problems similar to mine, although I did find that in [this ]("http://www.ubuntuforums.org/showthread.php?t=262092")topic that my card, an ATI 9250, was unsupported by Ubuntu 6.10 unless it had a newer driver version:

The problem is that I don't even have Kubuntu installed, so how am I supposed to install drivers for an OS that doesn't even exist yet? It seems like a terrible catch 22 - I need linux drivers to install linux, and I need to install linux for the drivers...

My question is, what do I need to do to get Kubuntu to install? I'll even settle for a text-install as long as I can get Kubuntu working so that I can install the drivers I need. Is the video card even the problem at all? Finally, is there a way I can disable the ATI video card short of taking it out of the slot so I can use the default video card to install Kubuntu?

Thanks for your time.

---

### Post by Sklasko on 2007-02-14
Do you get any errors when trying to boot the LiveCD? If not, have you tried the command "startx" when you get to that "unfriendly" command line? You might be able to start X and KDE that way.

If all else fails, you could try using the alternate CD to install. It may sound and even look intimidating but it's just as simple as the LiveCD installer. It just has a different look.

---

### Post by greywolfexcel on 2007-02-14
If I get any errors, I don't notice them because the text flashes by so fast (although even seeing text in the first place when Kubuntu is supposed to be starting might be a sign of an error itself...)

I'll try the startx command and see if that works, and if it doesn't I'll try the alternate CD when I get home tonight. Do you think the problem has anything to do with my video card?

---

### Post by nickoli_02 on 2007-02-14
Try using the vesa driver instead of the default ati. The ati driver wont work for my video card at all (ATI X700)

```
sudo dpkg-reconfigure xserver-xorg
```

When it asks what driver to use, select vesa.

---

### Post by greywolfexcel on 2007-02-14
> **Sklasko said:**
> Do you get any errors when trying to boot the LiveCD? If not, have you tried the command "startx" when you get to that "unfriendly" command line? You might be able to start X and KDE that way.

I just tried that, and got a bunch of info on linux starting up, and then I got this message, and was returned to the command line:

```

(WW) ****Invalid Mem Allocation **** b: 0x20000000 e:0x27fffff
(EE) I810(0): Cannot read V_BIOS
(EE) I810(0): VBf initialization failed
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server "0.0" after 0 requests (0 known processed) with 0 events remaining

```

That "fatal error" doesn't sound too good... I'll try nickoli_02's suggestion and if that doesn't work, then I'll grab the alternate install CD.

Edit: I changed the driver in the dpkg-reconfigure menu to vesa, but it didn't really help. I got basically the same error as above, but with the VBf initialization message missing (I think that's good), but with another message about VESA not being able to find the device at 0:2:0. I'm guessed that it thinks that is supposed to be the bus location of my card, so I typed:

```
lspci -x
```

(since I saw that command and its explanation in the config menu) and I saw the bus address for my card as 01:01.1, so I tried to input that in the driver PCI address config screen, but it said it was an invalid format. I'm downloading the alternate cd now to see if it will work.

2nd Edit: Oh, I just remembered. I ran startx right after I configured the video driver the first time, and one of the errors it gave me was this:

```
 [17179570.096000] PCI: Cannot allocate resource region 0 of device 000:00:02.0
```

Hope that helps as well.

---

### Post by greywolfexcel on 2007-02-15
Well, I downloaded the alternate cd and burned it to an ISO and went through the text installation which was relatively painless, but when now when I choose to boot to Kubuntu, it brings me to a command line screen. I think that I can solve this by updating the drivers in the previous thread, but if I download them on windows, how does that help at all? Kubuntu didn't recognize my wireless internet usb card (probably because it's DLink), so I can't connect to the internet through kubuntu anyway. I'll probably be able to fix this later, so I'm not worried, but I'd really like to see a GUI sometime soon. 

As an added bonus, now when I choose to boot up windows from the dual boot selection screen, I get this message:
```
Starting up...
_
```

Where the '_' is a blinking underscore, and nothing happens. I waited for about 20 minutes until I just said forget it and went to bed. It recognizes that windows is installed, and I'm positive my repartition wasn't too small (I was using about 50 GB on an 80GB hard drive, and I repartitioned it to be 65 GB large), so what is going on?

Thanks for any help.

---

### Post by greywolfexcel on 2007-02-16
Well, I ended up taking my video card out and relying on the integrated video card to install Kubuntu, which worked. I'll be able to back up my windows drive before reformatting *everything* and starting over from scratch, and partition my drive with windows this time, and *then* install Kubuntu again. I've got it figured out from here; thanks for all your help! :)

---

