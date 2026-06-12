---
title: "and now here's the problem..."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by yeheii on 2007-06-29
i just finished installing feisty 64bit.
i rebooted and then Grub loaded.
i chose Ubuntu and then the pc just hangs
no signal on the monitor.

i think it's my ati x550 which causes this.
but how do i configure or update my drivers
if it hangs just after Grub?  thanks.

---

### Post by yeheii on 2007-06-29
up

---

### Post by yeheii on 2007-06-29
up

---

### Post by scheuri on 2007-06-29
I kindly ask you NOT to "up" your request or question that often.

I am aware that this problem might be very important to you. Be assured that, if someone is able to help you, that person will answer. But maybe people simply do not know an answer or actually ignoring you.
That might be because you "upped" your request too often too fast or maybe because you do NOT provide us with ANY information at all.

How about telling us what kind of hardware? Which installer you used? Did the PC already work before with another operating system?


And to add something useful to you:
I doubt it is your graphic card. If that would be the case you would at least see the shell (like MS-DOS). 

Greetings
scheuri

---

### Post by overdrank on 2007-06-29
> **yeheii said:**
> i just finished installing feisty 64bit.
i rebooted and then Grub loaded.
i chose Ubuntu and then the pc just hangs
no signal on the monitor.

i think it's my ati x550 which causes this.
but how do i configure or update my drivers
if it hangs just after Grub?  thanks.

Ok I have been searching and really found nothing to help yet, so lets try this. When you get to the grub as soon as you see it use the ctrl, alt, F1 keys all at the same time. Hopefully this will get you to the terminal and you can use the command
[PHP]sudo dpkg-reconfigure xserver-xorg[/PHP]
If you just pick the vesa driver for your card that will at least get you to the gui and then you can install the drivers using envy or any other way you like. Hope this helps!:)

---

### Post by yeheii on 2007-06-29
> **scheuri said:**
> How about telling us what kind of hardware? Which installer you used? Did the PC already work before with another operating system?

And to add something useful to you:
I doubt it is your graphic card. If that would be the case you would at least see the shell (like MS-DOS). 

Greetings
scheuri


hi scheuri,

thanks for replying and
im scheuri for the "ups" ;)

i am using amd 64 x2,  ati radeon x550, 20Gb HD (with win xp installed), 512Mb ram
yup, before it hangs, it displays a message  "kernel is alive..."  or something, i forgot to note that.
and then it hangs, no signal on the monitor.

i've read the sticky on installing feisty with ATI cards.  where should i enter the "sudo apt-get update" command?

---

### Post by yeheii on 2007-06-29
@overdrank

okay.  will try that now. and get back here to update.

---

### Post by yeheii on 2007-06-29
@overdrank

i tried ctrl-alt-F1, but to no avail.
btw, i installed using alternate desktop 64bit
i'm on the screen where i choose which OS to load.
i can press 'e' for edit, and 'c' for command line,
but not ctrl-alt-F1.
and then when i choose to boot to Ubuntu,
this message shows up:

[B]Kernel alive
Kernel direct mapping tables up to[/B]

...something like that,
and then the pc hangs

---

### Post by overdrank on 2007-06-29
> **yeheii said:**
> @overdrank

i tried ctrl-alt-F1, but to no avail.
btw, i installed using alternate desktop 64bit
i'm on the screen where i choose which OS to load.
i can press 'e' for edit, and 'c' for command line,
but not ctrl-alt-F1.
and then when i choose to boot to Ubuntu,
this message shows up:

[B]Kernel alive
Kernel direct mapping tables up to[/B]

...something like that,
and then the pc hangs

Ok c for command line will do and try that command there afetr you login.

---

### Post by Tomosaur on 2007-06-29
That command line is the grub command line, which is absolutely useless for entering Linux commands.

yeheii - you said that you used the 64 bit version of Ubuntu. Unfortunately this version is still under heavy development, and routinely crops up when problems arise. The best advice anyone can give you for the time being is to just try the 32 bit edition. It is far more stable, and much better supported, since the vast majority of people here use it.

However, if you want to carry on with the 64 bit version, then the best thing at this time is to reboot your Ubuntu machine, and write down exactly what the error message is. That's the first step in finding a solution :)

Welcome to the forums anyway, and good luck with Ubuntu!

---

### Post by yeheii on 2007-06-29
@overdrank

um, it said it can't recognize the command.  if i press tab on the command line, it displays all the commands only available

---

### Post by overdrank on 2007-06-29
> **Tomosaur said:**
> That command line is the grub command line, which is absolutely useless for entering Linux commands.

yeheii - you said that you used the 64 bit version of Ubuntu. Unfortunately this version is still under heavy development, and routinely crops up when problems arise. The best advice anyone can give you for the time being is to just try the 32 bit edition. It is far more stable, and much better supported, since the vast majority of people here use it.

However, if you want to carry on with the 64 bit version, then the best thing at this time is to reboot your Ubuntu machine, and write down exactly what the error message is. That's the first step in finding a solution :)

Welcome to the forums anyway, and good luck with Ubuntu!

This sounds like great advice!:popcorn:

---

### Post by yeheii on 2007-06-29
> **Tomosaur said:**
> The best advice anyone can give you for the time being is to just try the 32 bit edition. It is far more stable, and much better supported, since the vast majority of people here use it.

However, if you want to carry on with the 64 bit version, then the best thing at this time is to reboot your Ubuntu machine, and write down exactly what the error message is. That's the first step in finding a solution :)


i see.  i was thinking about that, before downloading which version, 32 bit or 64 bit.  I just wanted to maximize resources.  But since it's buggy, i'll install the 32 bit tomorrow and hopefully it works out smoothly.  thanks for the advice!

---

