---
title: "PCMCIA Hardware Modem not functioning"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by TuxIsCute on 2007-02-13
I have a Zonet ZFM5600-CF PCMCIA II Hardware Modem and am trying to make it work in Ubuntu Dapper but it isn't reading it.  Dapper doesn't even seem to 'see' the PCMCIA II slot.  The modem card works perfectly in Windows XP, but not in Linux.  How can I force Dapper to see the PCMCIA II slot and the modem that is attached?

I checked in the device manager and it has a PCMCIA section but when I click on it I read a message saying that it isn't installed.  How can I install it?  I have the driver Windows uses to run it if that'll help any.

It's an HP Pavillion ze4805WM laptop by the way.

The modem's box says it'll work "out of the box" with Linux.  There is no driver for it in the Linux section of the CD only it says that in RedHat\Suse\Mandrake\Ubuntu to insert the PC card after booting up the system and it should be recognized.  It said it was tested on Ubuntu Hoary/Breezy/Dapper and that it *should* be compatiple with Edgy.  I'm using Dapper and thought YEY!  No work.  But it isn't working!  I tried it on a Hoary install and still nada!  So I figure it has to do less with the PC card which I know is functional and more with the PCMCIA slot in which it is installed.  Does Linux not support PCMCIA slots?  And if so, how come so many people on the internet say that it worked "out of the box" for them on Ubuntu and other Linux distros just like the box claims!?

Someone out there please help me whip my lazy PCMCIA slot into shape by telling me what's wrong!

-Tux is Cute

---

### Post by darthchaosofrspw on 2007-04-30
> **TuxIsCute said:**
> I have a Zonet ZFM5600-CF PCMCIA II Hardware Modem and am trying to make it work in Ubuntu Dapper but it isn't reading it.  Dapper doesn't even seem to 'see' the PCMCIA II slot.  The modem card works perfectly in Windows XP, but not in Linux.  How can I force Dapper to see the PCMCIA II slot and the modem that is attached?

I checked in the device manager and it has a PCMCIA section but when I click on it I read a message saying that it isn't installed.  How can I install it?  I have the driver Windows uses to run it if that'll help any.

It's an HP Pavillion ze4805WM laptop by the way.

The modem's box says it'll work "out of the box" with Linux.  There is no driver for it in the Linux section of the CD only it says that in RedHat\Suse\Mandrake\Ubuntu to insert the PC card after booting up the system and it should be recognized.  It said it was tested on Ubuntu Hoary/Breezy/Dapper and that it *should* be compatiple with Edgy.  I'm using Dapper and thought YEY!  No work.  But it isn't working!  I tried it on a Hoary install and still nada!  So I figure it has to do less with the PC card which I know is functional and more with the PCMCIA slot in which it is installed.  Does Linux not support PCMCIA slots?  And if so, how come so many people on the internet say that it worked "out of the box" for them on Ubuntu and other Linux distros just like the box claims!?

Someone out there please help me whip my lazy PCMCIA slot into shape by telling me what's wrong!

-Tux is Cute

I have the exact same type of PCMCIA modem.

Here's what you need to do.

1. Turn on your laptop and log in to Ubuntu.
2. After the system has fully loaded, plug your PCMCIA modem into your PCMCIA slot.
3. Try to dial out.
4. If it doesn't dial out, open your terminal and run wvdialconf as follows:
```
sudo wvdialconf
```

Then enter in your password. By then, your modem, which should be pointing to /dev/ttyS0, should be symbolically linked to /dev/modem. If you do not wish to use wvdial, then just execute the following:

```
sudo ln -sf /dev/ttyS0 /dev/modem
```

Try to dial out again.

Most, if not all, PCMCIA modems are seen by Linux as an external serial modem (hence the linking of /dev/ttyS0 and /dev/modem).

If you ever have the PCMCIA modem plugged in to the PCMCIA slot before you turn on the computer, chances are very likely that you will have to eject the card and then re-insert it. It was always like that when I had Linspire 4.5 on the laptop. The modem would never work unless I inserted the card after the OS has completely loaded up.

---

