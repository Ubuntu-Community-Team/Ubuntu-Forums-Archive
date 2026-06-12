---
title: "NDIS Wrapper Question"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by doug.barrett on 2006-01-03
I figured out the make (thanks!) but when I run it, this is what I get when I try to install NDIS:

```
root@dougslaptop:/home/doug/Desktop/ndiswrapper-1.7# make
make -C driver
make[1]: Entering directory `/home/doug/Desktop/ndiswrapper-1.7/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/doug/Desktop/ndiswrapper-1.7/driver'
make: *** [all] Error 2

```

I have put the drivers in the driver folder, so I don't know what I am doing wrong.

Thanks :)

---

### Post by Suger on 2006-01-03
the Linux headers. In synaptic.

---

### Post by doug.barrett on 2006-01-03
Ok, I have done that and this is what I get now

```
make -C driver
make[1]: Entering directory `/home/doug/Desktop/ndiswrapper-1.7/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/doug/Desktop/ndiswrapper-1 .7/driver \
        DRIVER_VERSION=1.7
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: co mmand not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: co mmand not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  LD      /home/doug/Desktop/ndiswrapper-1.7/driver/built-in.o
  CC [M]  /home/doug/Desktop/ndiswrapper-1.7/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/doug/Desktop/ndiswrapper-1.7/driver/hal.o] Error 127
make[2]: *** [_module_/home/doug/Desktop/ndiswrapper-1.7/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/doug/Desktop/ndiswrapper-1.7/driver'
make: *** [all] Error 2

```

---

### Post by MartinJ on 2006-01-03
Do you know that ndiswrapper is available from apt-get / Synaptic?
it's listed as ndiswrapper-utils, there's also a graphical interface: ndisgtk.

Saves a lot of time and effort in compiling...

---

### Post by doug.barrett on 2006-01-03
Awesome thanks! How do I get the graphical interface for it?

Edit:

Nevermind, I'm going to use Automatix to get the GUI for it :)

---

### Post by doug.barrett on 2006-01-03
Ok, I installed that stuff and I lead it into the right direction of the drivers I have for my Wireless card, but after I press install it doesn't do anything.

Scratch that, I copied the files directly to my hard drive and it detected it.

Now it says it found the hardware, but how do I configure it under the network settings? It isn't appearing there.

Thanks.

P.S.  I use a WEP key on my network, but I haven't had a problem connecting through Ubuntu on my PC since I know the hex code for it.

---

### Post by Suger on 2006-01-03
else, you need to
```
sudo apt-get install gcc-3.4
```

The repository version of ubuntu is quite old, I had to compile from source to get my card working (I2220)

---

### Post by carlosqueso on 2006-01-03
try typing ```
sudo modprobe ndiswrapper
``` that should get it to work.  If it does work, you'll need to type ```
sudo ndiswrapper -m
``` if you want it to work at startup.

---

### Post by deadly_paddooo on 2006-01-03
I had a trendnet wireless card 802.11b/g. I used the following link to install ndiswrapper, worked great!
[http://flacknews.blogspot.com/2005/11/use-ndiswrapper-to-setup-wireless-in.html](http://flacknews.blogspot.com/2005/11/use-ndiswrapper-to-setup-wireless-in.html)

After you have done the stuff listed there follow this thread
[http://ubuntuforums.org/showpost.php?p=623496&postcount=13](http://ubuntuforums.org/showpost.php?p=623496&postcount=13)

This will bring the ndiswrapper to start at booting.

Hope this helps!

---

### Post by doug.barrett on 2006-01-03
This is the error I get for modprobe:

```
doug@dougslaptop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

---

### Post by carlosqueso on 2006-01-03
weirdness....what happens when you type ```
ndiswrapper -l
```

---

### Post by doug.barrett on 2006-01-03
It says:

```
doug@dougslaptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
winxp   invalid driver!

```

---

### Post by doug.barrett on 2006-01-03
It says:

```
doug@dougslaptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
winxp   invalid driver!

```

---

### Post by doug.barrett on 2006-01-03
I think I keep getting the error because of this

```
root@dougslaptop:/home/doug# ndiswrapper -i /home/doug/Wink2k/
Installing wink2k
cp: cannot stat `/home/doug/Wink2k/': No such file or directory

```

Because even after that, it says it is installed but it's an invalid driver.

But I think the **cp: cannot stat** error is causing the problems.

Is there a workaround?

---

### Post by byen on 2006-01-03
I am not really sure if this would help you but you might wanna take a look:
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)
goodluck.

---

### Post by Suger on 2006-01-03
What is sure is that 

1 - you want to sudo ndiswrapper -i
2 - you have to give him the full path to the .inf file, not just the directory

---

### Post by etc on 2006-01-03
What is the exactly location of the driver?
cp is giving out an error that says /home/doug/Wink2k/ doesn't exsist, maybe you meant /home/doug/**Win**2k/
But that would be a directory, not the driver

---

### Post by doug.barrett on 2006-01-03
Ok, I am finally getting somewhere here lol.

Thank you for all of your help for those of you whom have helped me.

Right now, I have the card driver installed:

```
doug@dougslaptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
neti2220        driver present, hardware present

```

so it is detecting it, atleast that is what it is telling me.

But when I try to do the modprobe, it says this:

```
doug@dougslaptop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

Thank you again for helping me out :)

---

### Post by doug.barrett on 2006-01-03
Does anyone know how to put the module back, or reinstall it?

Thanks

---

### Post by doug.barrett on 2006-01-03
I have figured it out!

I had to compile the module for the kernel, which was suprisingly easy (and fun to watch :-P)

What I did was I searched Google by searching for "sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found."

That lead me to another topic on this site where someone said that you would either have to recompile the module for the kernel you are running, or use a different distro.  It was about 10 months old so I knew things had to have changed by then.

So I went back to Google and I searched "ndiswrapper kernel module" and I found this site

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/InstallDebian]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/InstallDebian")

Basically to sum up what I got from there is I typed in:

```
sudo apt-get install module-assistant
```

Then once that was installed, I typed in:
```
module-assistant auto-install ndiswrapper
```

That installed the module that I needed.

Once I had done that, I skipped the rest of the instructions since I had the driver already installed succesfully.  So I went back and ran

```
sudo modprobe ndiswrapper
```

That fixed the problem and now I have successfully set up the wireless card on my laptop.

I want to thank you all for helping me through this process!

:)

---

### Post by shawndoggy on 2006-01-21
Oh, man, I'm having the same problem!  I'm trying to set up a Trendware TEW228-PI card and I'm having nothing but trouble.  Tried the ndiswrapper instructions in this thread, and here's what I get.  Any help?

> where 'devid' is either PCIID or USBID of the form XXXX:XXXX
root@garage:/home/shawn# sudo ndiswrapper -i /home/shawn/NETR8180.INF
netr8180 is already installed. Use -e to remove it
root@garage:/home/shawn# $ sudo modprobe ndiswrapper
bash: $: command not found
root@garage:/home/shawn# sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

I'm a complete newb to linux and so far I really REALLY like the interface, but not having wireless is a complete deal breaker (not to mention it's driving me insane trying to fix this).  Please bring be back from the brink!

---

### Post by shawndoggy on 2006-01-21
Wow.  I got it fixed.  Seems exceedingly simple now, but it was REALLY frustrating!  OK what did I do...

First I downloaded all of the ndiswrapper apps using Synaptic.  Including ndisgtk.  But I kept trying and trying using terminal and the instructions provided [here]("http://flacknews.blogspot.com/2005/11/use-ndiswrapper-to-setup-wireless-in.html"). 

For whatever reason, I couldn't get it to work in Terminal.  But then just before I was going to pour gas on the computer and set it ablaze, I looked in System/Administration, and low and behold, there's the ndisgtk app, now entitled "Windows Wireless Drivers".  I ran it and the driver that I was trying to add using teminal was there.  I deleted it and added it again from the same place and viola, I've got internet.

Awesome!  Hope to add more about my impressions with Ubuntu in the weeks to come.

---

