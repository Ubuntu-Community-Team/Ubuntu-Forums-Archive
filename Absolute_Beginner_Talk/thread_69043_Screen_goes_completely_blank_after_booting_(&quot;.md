---
title: "Screen goes completely blank after booting (&quot;Hoary Hedgehog&quot; v5.04)"
date: 2005-09-25
forum: Absolute Beginner Talk
---

### Post by Sirin on 2005-09-25
(This happens on the LiveCD and the Full Version.)

Did'nt know where to post this, but here is my problem. It does the text bootup, but when it gets into graphical mode, the screen goes blank and the monitor goes on standby, as if the computer were off. The sound is perfect, the loading is perfect. In fact everything is perfect, it's just only the monitor.

While trying over and over again to get it running correctly, I've noticed a line in the text bootup session that wrote "[FONT=Lucida Console][[COLOR=Red]Error[/COLOR]] Temporary failure in name Resolution.[/FONT]" Does anybody know how to fix this?

---

### Post by papangul on 2005-09-25
search for 'EE' & 'WW' in /var/log/Xorg.log and post it here. What is your graphics card or chipset?

---

### Post by Tiede on 2005-09-25
It sounds like your graphics card might not be properly recognized... Do you know what it is exactly?
And the name resolution failure is not related to the monitor problem you're having, it's an internet address resolution failure, probably you notice it at the line were it tries to connect to [http://ntp.ubuntulinux.org/](http://ntp.ubuntulinux.org/) Are you connected via dial-up. That might explain it. But you should not worry about it for now, as it has nothing to do with the graphics problem. It's only as harmful as a 404 error under any browser ;)

---

### Post by Sirin on 2005-09-25
[QUOTE=Tiede]It sounds like your graphics card might not be properly recognized... Do you know what it is exactly?
And the name resolution failure is not related to the monitor problem you're having, it's an internet address resolution failure, probably you notice it at the line were it tries to connect to [http://ntp.ubuntulinux.org/](http://ntp.ubuntulinux.org/) Are you connected via dial-up. That might explain it. But you should not worry about it for now, as it has nothing to do with the graphics problem. It's only as harmful as a 404 error under any browser ;)[/QUOTE]

My graphics card is an Intel 82865G Integrated Graphics Device. Is that supported?

---

### Post by Tiede on 2005-09-25
any updates on your graphics card/chipset or your Xorg.log so far? Or is your ubuntu boxen not at immediate proximity?

---

### Post by Sirin on 2005-09-25
[QUOTE=Tiede]any updates on your graphics card/chipset or your Xorg.log so far? Or is your ubuntu boxen not at immediate proximity?[/QUOTE]

Well, I can't get to the Xorg.log because I can't see the screen to find it. And as said earlier, My graphics card is an Intel 82865G Integrated Graphics Device.

---

### Post by papangul on 2005-09-25
Your graphics card is fully supported so no problem , I think. You can boot up in recovery mode and access the xorg.log from command line.

---

### Post by Sirin on 2005-09-25
Never mind, people. I got it. Now, for the first time ever, I'm using Ubuntu (And it's nice, even nicer than my old Fedora Core 1)! Thanks for the help, people! :)

---

### Post by papangul on 2005-09-25
What was the problem, I'm feeling curious.

---

### Post by CammanB on 2005-09-25
I'm having the exact same problem with my screen going blank right after booting as well, and I'm completely new to this whole Linux thing, so any help is appreciated.. there seems to be some sort of problem with the OS recognizing my network, as the computer I have has both a wireless card and a wired network card in it (the wired has nothing plugged into it, however)  I was running Windows 2000 on it and there is no problems with the card itself when it comes to connecting to the internet, however. During setup I was not able to configure my network ( I guess because the wireless is significantly slower)... but for the time being I am stuck with a PC with no working OS... any help is appreciated...  :-?

---

### Post by papangul on 2005-09-26
@CammanB
your problem has nothing to do with network, just when is the screen going blank? What is your graphics card or chipset?

---

### Post by CammanB on 2005-09-28
Never mind, I fixed my problem as well... I have an extremely old graphics card that is integrated into the motherboard (the only reason I don't hate it is that it was free).. and ubuntu tried to use a driver that was for the same brand of card but I guess too advanced... I called a linux guru friend of mine and he told me to use "vesa" for the time being until he could come over and mess around with it, and that worked.... now the only issue is getting the wireless card to work... but hopefully he can help me with that too! :-p

---

