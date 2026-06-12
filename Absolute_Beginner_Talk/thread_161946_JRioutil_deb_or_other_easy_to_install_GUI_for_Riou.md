---
title: "JRioutil deb or other easy to install GUI for Rioutil?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by starchildmom on 2006-04-18
I managed to get rioutil working with my Rio S30 (although I have to use sudo to do it). The file names of the music are a long mess. It is awful to sort through. I want to download all of the files to my pc. While I do not mind using the terminal at all, a gui would make wading through the file mess that windows created on my Rio a bit easier. I looked for JRioutil in synaptic and googled for a deb for it with no luck. The instructions for installing it on the website are currently beyond my skills (although if someone was kind enough to give me a step-by-step I would learn ;)  ) as is making my own deb (I would not know where to even start, but again, I am willing to learn). If an alternative to Jrioutil is already available that would be great too.

---

### Post by majstor on 2006-04-18
I dont have Rio and i am newb like you but I installed without probs.

1 DL [http://www.botch.com/~mpilone/projects/jrioutil/jrioutil-1.0.2.jar](http://www.botch.com/~mpilone/projects/jrioutil/jrioutil-1.0.2.jar)
2 go to dir (in terminal) where you DL-it and

 java -jar jrioutil-1.0.2.jar

3.You have Java package installed (like sun-j2re1.5)?

4. Everything is working :)

---

### Post by starchildmom on 2006-04-18
I think it was the java part of the install that was intimidating me. A few years ago I tried a linux distro and it was a java related install that killed it for me.

Anyway... I got JRioutil to open, but it does not recognize my player. I tried running it with and without sudo. Rioutil (with sudo) is working fine.

---

### Post by majstor on 2006-04-18
That Jrioutil is just GUI for Rioutil so it should work.and  installation of java is really easy in Ubuntu (with Synaptic), dont know about other distros. You have to run program as root because:

[http://www.botch.com/~mpilone/projects/jrioutil/README](http://www.botch.com/~mpilone/projects/jrioutil/README)

¨Note that you may have to run the application as root since rioutil
requires root access to devices.¨

Try to contact authors of those programs , maybe they have idea why your Rio cant be recognized in Jrioutil

---

### Post by starchildmom on 2006-04-18
I think I know what the problem is. Even if I run JRioutil with sudo or even login as root and run it, it is running rioutil as a user and closes without letting me access any preferences. 

I will contact the Jrioutil support, but I have a feeling it is more of a manuevering of access in Ubuntu that will solve the issue.

Maybe is I can change the access rights to the mp3 player? I have no idea what its device address is.

---

### Post by brallan on 2006-06-02
I have the same problem. I am unable to run rioutil as a normal user and jrioutil gives me the same error message, that it is unable to access the device, whether i run it as user or su. I tried changing the permissions for /usr/bin/rioutil but that doesn't seem to affect anything. it seems the device needs user access, not rioutil itself. The last few lines of the output from dmesg are probably my device:

```
[4312645.949000] usb 3-1: new full speed USB device using ohci_hcd and address 2
[4313330.232000] usb 3-1: USB disconnect, address 2
[4313334.199000] usb 3-1: new full speed USB device using ohci_hcd and address 3
[4314483.232000] usb 3-1: USB disconnect, address 3
[4314570.199000] usb 3-1: new full speed USB device using ohci_hcd and address 4
[4317591.732000] usb 3-1: USB disconnect, address 4
[4320031.449000] usb 3-1: new full speed USB device using ohci_hcd and address 5
[4322931.982000] usb 3-1: USB disconnect, address 5
[4368657.527000] APIC error on CPU0: 00(40)
[4376469.589000] APIC error on CPU0: 40(40)
[4380508.449000] usb 3-1: new full speed USB device using ohci_hcd and address 6
[4380887.248000] APIC error on CPU0: 40(40)
[4382542.482000] usb 3-1: USB disconnect, address 6
[4392087.449000] usb 3-1: new full speed USB device using ohci_hcd and address 7

```

can anyone tell me how to change the device ohci_hcd? so that rioutil can run it without su mode? It may be a problem in the package that was prepared for ubuntu, maybe i'll try and install from source. 

There IS another option, Krioutil, but it seems to be stuck in development, and I was unable to get it to ```
make
```.

i doubt I have the patience for a command line tool on something like this, but probably only because I've never really used command line tools for anything other than a few simple commands. As sorry as I am to say it, it just seems like less of a hassle to boot into (XPletive deleted) Windows, or toss my beloved Riosaurus into the trash and get a new player....

brian (barcelona)

---

