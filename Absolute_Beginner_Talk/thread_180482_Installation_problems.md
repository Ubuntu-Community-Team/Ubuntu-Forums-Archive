---
title: "Installation problems"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Surefire on 2006-05-22
Hi all first post.

I have been trying to install Ubuntu 5.10 on my Acer Aspire 9500 laptop. The laptop boots from the cd and I press enter for the default instal but the process stops with the message:

uncompressing linux.......ok, booting the kenel.

I have to do a hard reset to get out of this. The cd work fine in my desktop pc so it has to an issue with the laptop. Can anyone offer an explanation?

Thanks

---

### Post by halfvolle melk on 2006-05-22
At what speed did you burn it(assuming you burnt it)? It might help if you burn another at the lowest possible speed.

---

### Post by nanotube on 2006-05-22
hmm, one thing i can suggest (in addition to the previous suggestion)  - try booting with a livecd first, to check if your hardware works for ubuntu?

---

### Post by Surefire on 2006-05-22
Thanks for the suggestions. I have did burn a second cd at a slower speed but still no luck. As I type this I am downloading the live cd version so when thats done I'll give it a try.

---

### Post by mlind on 2006-05-22
have you tried booting with kernel parameters like
```

acpi=off
noapic

```

try with both.

---

### Post by jorn on 2006-05-22
I might not be up to date.
Uncompressing linux - Booting the kernel. That's the screen that's comes up when you have already installed Ubuntu.
How can that message appear during install?

---

### Post by Surefire on 2006-05-24
Right,

Downloaded the live cd image and burned that to cd as suggested. When booting from that, I get the same message as with the instal cd!. 

I tied the acpi=off and noapci at the boot prompt but I got a message saying "couldnt find kernel image acpi=off (or noapic)

On a different tack, I also tried the Knoppix live cd. That got a bit further but my screen just went blank and I had to do a hard reset.

Maybe my laptop just wont work with Linux :( 

Thanks anyway chaps.

---

### Post by nanotube on 2006-05-24
sorry, to be more explicit, at the boot prompt, you have to type
```
linux acpi=off noapic
```
because linux is the kernel, the other things are just options to the kernel.
to try that again, and see how it works. :)

---

### Post by Surefire on 2006-05-25
Right, update:

The command: live acpi=off noapic did the trick:) 

The  Laptop booted fine right until the end and the screen went blank :( I set the screen res correctly when prompted so  I'm a bit stuck. My laptop uses an ati mobility radeon x700 pci express card, could this be the problem (no support yet?)

Thanks for the continuing help.

---

### Post by mlind on 2006-05-25
[QUOTE=Surefire]Right, update:

The command: live acpi=off noapic did the trick:) 

The  Laptop booted fine right until the end and the screen went blank :( I set the screen res correctly when prompted so  I'm a bit stuck. My laptop uses an ati mobility radeon x700 pci express card, could this be the problem (no support yet?)

Thanks for the continuing help.[/QUOTE]

When screen goes blank and boot process seems to stop, press Ctrl+Alt+F1.
You should see command line terminal, which you need to login using your username and password.

Then install propietary ATI drivers, which should do the job
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

After driver install, do *sudo /etc/init.d/gdm restart* or reboot.

---

### Post by Surefire on 2006-05-28
Jesus that looks complicated, think I'm gonna leave it until a more upto date Ubuntu iso comes out. Thanks for the help anyway.

---

