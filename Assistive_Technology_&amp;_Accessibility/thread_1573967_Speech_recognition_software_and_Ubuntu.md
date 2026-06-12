---
title: "Speech recognition software and Ubuntu"
date: 2010-09-13
forum: Assistive Technology &amp; Accessibility
---

### Post by andymorton on 2010-09-13
Hi,

I won't bore you with the details but among other things I'm finding increasingly difficult to type because of neurological problems. I've just had a meeting with someone from university who said they could get me some speech recognition software to write assignments. I was wondering if anyone knows of any which will run on Ubuntu rather than just Windows. (I don't have Windows on either of my computers)

Thanks
andy

---

### Post by philinux on 2010-09-13
Moved to Assistive Technologies

---

### Post by andymorton on 2010-09-13
Sorry, I didn't know this part of the forum existed :D

---

### Post by UndiFineD on 2010-10-31
A functional application I work on is Simon Listens:
[https://launchpad.net/~simon-listens](https://launchpad.net/~simon-listens)
[https://launchpad.net/~grasch-simon-listens](https://launchpad.net/~grasch-simon-listens) <-- has a ppa

And I work on voxforge
[http://www.voxforge.org/](http://www.voxforge.org/)

Julius is another that wants to work with asterisk.

HTK is a common engine for recognition

another potential possibility for people that want to speak but can't, think accessible
[http://www.emotiv.com](http://www.emotiv.com) <- working on ubuntu software

so as usual, plenty of options

---

### Post by dewdrop_world on 2011-01-23
Just in case someone else stumbles across this thread -- the original post asks about solutions to help with typing. Unfortunately, the [Simon handbook]("http://simon.gibolles.com/doc/0.3/simon/en/index.pdf") says (my emphasis):


> The current release can be used to set up command-and-control solutions especially suitable for disabled people. *However, because of the amount of training necessary, continuous, free dictation is neither supported nor reasonable with current versions of simon.*


So quite likely, this will not meet the OP's needs.


I tried for a while to use NaturallySpeaking with wine, but found it to be too unstable. Also, I don't care for the fact that wine audio seems to work well basically only with ALSA, while I'm running Jack routinely. So currently I'm using NaturallySpeaking running in a Windows XP virtual machine on virtualbox. That does what I need well enough, though it isn't a perfect solution and I would, of course, prefer to be using open source.


I've searched but never found a fully functional open source speech-to-text app for Linux. NS+XP+VB is probably the best available currently.


James

---

### Post by dewdrop_world on 2011-01-23
> **dewdrop_world said:**
> Also, I don't care for the fact that wine audio seems to work well basically only with ALSA, while I'm running Jack routinely.

 Correction: I found this only just now, describing a pulseaudio backend for wine.


[http://art.ified.ca/?page_id=40](http://art.ified.ca/?page_id=40)


With that, maybe I'll give NS+Wine another try later on. I'm having good success with the pulse-jack solution by the author of KXStudio; wine --> pulse --> jack "should" (in theory) be OK.

---

### Post by Megaptera on 2011-01-23
Hi andymorton,
Have you looked at Vinux? It's got this description at their site:
Vinux is a remastered version of the popular Ubuntu 10.10 Maverick Meerkat distribution optimised for the needs of blind and partially sighted users. By default it provides three screen-readers, two full-screen magnifiers, global font-size and colour changing facilities as well as support for USB Braille displays. When you boot the live CD you will be greeted by the Orca screen-reader/magnifier which enables you to navigate the graphical Gnome desktop using keybindings, as well as providing full screen-magnification if required.  For those who prefer to work in a simple text based console there is the Speakup screen-reader. A second full-screen magnifier is provided by the Compiz Window Manager, which uses 3D technology to allow you to magnify and navigate the whole screen  using the mouse, or move a resizable virtual magnifying glass around the screen. The Gnome  Desktop Manager itself provides you with global keybindings to change the font size and/or the colour scheme on the fly. Finally, Brltty provides Grade 1/2 Braille output via the Orca screen-reader_. By default all of the screen-readers use the same Espeak Speech Synthesizer via Speech-Dispatcher which provides a seamless experience for the user when switching from one screen-reader to another_!

[http://www.vinux.org.uk/faq.html](http://www.vinux.org.uk/faq.html)

I hope this (or the software) is of interest to you?

---

### Post by dewdrop_world on 2011-01-23
Vinux appears to have good support for **text-to-speech**, but if I read correctly, the OP wants **speech-to-text**. Those are entirely different problem domains.

---

### Post by Megaptera on 2011-01-24
My apologies.

---

### Post by foxmuldr on 2011-03-05
> **andymorton said:**
> I still maintain the point that designing a monolithic kernel in 1991 is a fundamental error. Be thankful you are not my student. You would not get a high grade for such a design (Andrew Tanenbaum to Linus Torvalds)

Excellent quote, and quite true. All of us who use Linux have kernels today that are 32 MB compressed, and 90% of that is unnecessary flotsam for machines we'll never see or use.

- Rick C. Hodgin

---

### Post by foxmuldr on 2011-03-05
> **andymorton said:**
> I've just had a meeting with someone from university who said they could get me some speech recognition software to write assignments. I was wondering if anyone knows of any which will run on Ubuntu rather than just Windows. (I don't have Windows on either of my computers)

Andy, for the purchase of some additional memory, you could run a virtual machine inside of your Linux machine.  On this you could run Windows with its speech-to-text software.

This would allow you the best of both worlds.

The additional memory is to support the hypervisor.  You'll lose some performance in the Windows machine, but if all you're using it for is the speech-to-text, it should not be an issue.

You can use VMware, Virtual Box, or any of the other free virtualization tools, and then use even an old version of Windows like Windows 98 or XP, as these will likely run the software just fine, and be small enough to be very un-intrusive to your system's resources.

I'm not a fan of using Windows software, but there are a lot of specialized apps written specifically for it for this purpose.

Hope this helps.

- Rick C. Hodgin

---

