---
title: "Kubuntu 8.04.1 on a PowerBook G4 500"
date: 2009-04-14
forum: Apple Hardware Users
---

### Post by Doncr on 2009-04-14
Greetings,

I finally got Kubuntu running on a G4 PowerBook 500 Ti machine after a lot of messing around. This machine has a Rage Mobilty M3 graphics card in it, and a lot of the advice on installing onto a PowerBook G4 is for the faster models with a different graphics card.

I was going to write up some step by step instructions - and may still do so - but with 9.04 out soon <salivate>just days away</salivate> I might reinstall that.

I got everything running fine, updated to KDE 4.2, decided it was running a bit slow, and installed xfce with apt-get install xubuntu-desktop, and everything seemed to be working fine.

Then it all went horribly wrong.

Booting into Linux gave me the horrible screen I was getting while trying to install. It starts black and then starts going white in a weird pattern - sort of 60´s psychedelia in grey scale. The same screen I was getting with the live cd or while trying to install.

Booting with 'video=ofonly nosplash' did not help.

I tried to boot off the CD to see if there was a rescue mode or a command line boot option, but my CD drive wouldn't work. Co-incidence? I did not think so.

I did a bit of cursing and left it for a couple of days, and then, after some research, tried resetting the nvram and PRAM. Now everything seems to have come back to life. Not only that, but KDE seems smoother, music plays better without crackles I was getting.

Resetting the NVRAM

Boot into Open Firmware by holding down the option-command-o-f keys while powering up the machine.

at the prompt:

```

reset-nvram
reset-defaults
reset-all

```

This should reboot the machine, and let me boot back into Linux. But it did not get the CD Drive working again.

Reset PRAM

Hold down the option-command-p-r keys while booting the machine. Keep holding them down untill you here **two** chimes. The second chime was maybe a minute later ... so wait.

The machine booted, and I was able to read the Ubuntu install disk. The only problem I have now is the screen brightness is at 50% - which is dark.

So I went from  'Ubuntu broke my laptop' (you cannot boot from an external cd drive) back to a running machine. Actually a machine that is running better than before. Now to get the screen brightness back :-)

Don

---

### Post by stream303 on 2009-04-18
Nice job!

One thing I remember from XFCE4 (or Xubuntu) was that it had a pseudo-brightness control - probably not controlling hardware, maybe just an underlying change to the rgb gammas, but that brightness control in Xubuntu might make it a bit more usable.

---

