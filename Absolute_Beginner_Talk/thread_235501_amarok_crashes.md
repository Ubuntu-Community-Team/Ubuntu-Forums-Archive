---
title: "amarok crashes"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by mlie on 2006-08-13
My Amarok crashes whenever I clicked on the PL button or whenever I tried to go to the Full Window view.

---

### Post by rpalyvoda on 2006-08-13
Amarok is a KDE program and is known to be very unstable in Gnome. You may try some gnome native programs, like Listen, Banshee or Rhythmbox.

---

### Post by PRGUY85 on 2006-08-13
Is Banshee as good as Amarok in terms of sheer functionality and things it has?  I have been using several LInux distro and choosing Amarok as my player of choice because of the great features like lyrics, cover manager, ipod functionality and last.fm support.  Does Banshee come close to Amarok in these areas?

---

### Post by justinlb on 2006-08-13
I am using Gnome and have amaroK installed and it works perfectly, there may be some extra files you have to install although I have no idea what they might be.

---

### Post by PRGUY85 on 2006-08-13
Why do you say this about extra files?

I am using PCLinuxOS right now with XFCE and Amarok works like a dream.  Hope it will be the same with Gnome in Ubuntu on my new laptop.

---

### Post by justinlb on 2006-08-13
I was under the impression that you had problems with it on a Gnome desktop and was just stating that amaroK works fine on my Gnome desktop and there may have been extra files my brother installed when he installed amaroK.

Forgive me if I seem stupid, I am still learning.

---

### Post by PRGUY85 on 2006-08-13
No need to call yourself stupid or the like man.  Thanks for wanting to help. Thats all that matters on a community forum.

---

### Post by mlie on 2006-08-13
I've tried running Amarok on both KDE and Gnome, and it crashes on both. How do I use the program again when it crashes? Because right now it just asks me to send email to the developers and close the program itself.

---

### Post by EdThaSlayer on 2006-08-13
Have you tried running amarok using the terminal?
just go to the command line and type in amarok
and you should be able to get a error report of sometype in the terminal.
Then you should be able to find out what library you are missing.

---

### Post by mlie on 2006-08-13
It is running alright but whenever I tried to double click the Amarok icon (ie. to go to the full window view or playlist view) then it crashes.
Then, it launches KMail and asks me to send email to the developers:
> amaroK has crashed! We're terribly sorry about this :(

But, all is not lost! You could potentially help us fix the crash. amaroK has attached a backtrace that describes the crash, so just click send, or if you have time, write a brief description of how the crash happened first.

Many thanks.







The information below is to help the developers identify the problem, please do not modify it.



======== DEBUG INFORMATION  =======
Version:    1.3.9
Engine:     xine-engine
Build date: May 21 2006
CC version: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
KDElibs:    3.5.2
TagLib:     1.4.0
NDEBUG:     true
==== file /usr/lib/amarok/amarokapp =======
/usr/lib/amarok/amarokapp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped

---

### Post by PRGUY85 on 2006-08-13
What version of Amarok are you using?

---

### Post by mlie on 2006-08-13
4.0.3..
I believe that is the newest one?

---

### Post by PRGUY85 on 2006-08-13
The newest one is 1.4.2 beta.

---

### Post by mlie on 2006-08-13
I think I have the newest one.. because I've just installed Kubuntu two days ago..

---

### Post by PRGUY85 on 2006-08-13
Well then I dont know.  Its suppose to work on any Linux Distro if you install the KDE basic stuff and seeing as how Kubuntu IS KDE, it should work.

---

### Post by mlie on 2006-08-13
It works before and I just don't know what I did that made it crashed. I've tried to removed and re-installed the program but it's still the same thing. Is there a way that I can re-start the program all over again?

---

### Post by bhoughton on 2006-08-13
Sorry to hear it's not working.  It seems to work fine for me under Gnome (came installed with Kubuntu-desktop) other than it doesn't seem to let me listen to CDs.  My version that came with Kubuntu-desktop is 1.3.9 so it is definitely not the latest and greatest...

Can the newer version be found in deb format or can it be installed via SVN?

Regards...

---

### Post by walmartshopper67 on 2006-08-21
Ugh, Amarok can be so frustrating - because when it works it's great. I have had more problems with it (on 3 different distros, Mandriva, Mepis, and Ubuntu) though. Right now it is doing the same thing as the parent on this thread. Of course it is doing it now that i'm getting ready to go back to school so that I don't have much time to play with it.:(

---

### Post by orb9220 on 2006-08-21
The latest stable is in synaptic and should be 1.4.1 do not install above that version as it is unstable on many systems. 1.4.1 has been out for a couple of months and has not crashed on me once.

The higher versions are beta and they don't run on my system,

---

### Post by walmartshopper67 on 2006-08-22
The latest according to my synaptic is 1.3.9 - am I missing a repository or something (probably)? I *could* install the .deb (I've seen it somewhere), but I prefer to do it through Synaptic just to keep everything straight.

---

### Post by RS3York on 2006-08-23
To upgrade to Amarok 1.4.1 open a terminal and type (or copy and paste)

```

wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg

```
Then...
```

sudo apt-key add kubuntu-packages-jriddell-key.gpg

```

Then in Adept add the following line to your repository list

deb [http://kubuntu.org/packages/amarok-141](http://kubuntu.org/packages/amarok-141) dapper main


Refresh your repos and then install the new version.
Keep in mind however, that Amarok 1.4.2 has been officially released already. It will likely be released for Kubuntu 6.06 in the next few days.  The repo should follow the same naming conventions as previous releases so it should be:

deb [http://kubuntu.org/packages/amarok-142](http://kubuntu.org/packages/amarok-142) dapper main

Although I would recommend checking kubuntu.org for the official address once it's released.  

I hope the new versions work out better for everyone, personally I've enjoyed the 1.4 series much more than the 1.3 (which was good too) if you use Last.fm among other things...it'll be a nice upgrade. 1.4.2 sounds like a great release for most everyone though since it can keep track of songs even after you move them.

The instructions I gave above are just copied for you from [http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php)

---

### Post by walmartshopper67 on 2006-08-24
Wow, thanks. It isntalled really easily and it seems to be working great. I love Amarok, which is why i get so upset when it breaks.

---

### Post by koshari on 2006-08-24
> **walmartshopper67 said:**
> Wow, thanks. It isntalled really easily and it seems to be working great. I love Amarok, which is why i get so upset when it breaks.

i agree there are a lot of documented bugs in both amarok and the xine engine for amorok, 

mine will barf now and then but for the most is reasonobly reliable, 

IMHO amarok is head and tails above any other music software i have tried, so i stick with it.

it will be very nice when a few of the known bugs are ironed out and it becomes rock solid. the xine crossfade bug annoys me a bit also.

but i guess when you get a development team thats always improving a product as fast as the amarok team do your gonna have a few bugs creep through.

maybe a few dit points with simply bugfixes may be whats needed ?

---

### Post by walmartshopper67 on 2006-08-24
Yeah, they probably need to do what the kernel developers did - just bug fixes for a bit. They are an awesome team too - when I was having problems on Mandriva I sent them an email and the package maintainers got back to me that same day.

---

### Post by mlie on 2006-08-26
I have installed amarok 1.4.2 and still have the same problem everytime I try to view the main window. It launches Kmail and asks me to send email with the subject line: 
1.4.2 [___stripped][validity: 0.73][frames: 100][xine]
When I run amarok on the command line, there are so many messages beginning with amarok:BEGIN or amarok:END
But I couldn't see any error messages.

---

### Post by mlie on 2006-08-26
This is what the terminal prints after amarok crashes. Dunno if it useful information though.
Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x2e0003e
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
~ScimInputContextPlugin()
ICE default IO error handler doing an exit(), pid = 8654, errno = 0

---

### Post by walmartshopper67 on 2006-08-26
Hm. I've never had it do that. You should check out the Amarok site and send them an email. In my experience they've been great and got right back to me (I just filled out the "contact us" thing too, but their site may have changed since).

---

