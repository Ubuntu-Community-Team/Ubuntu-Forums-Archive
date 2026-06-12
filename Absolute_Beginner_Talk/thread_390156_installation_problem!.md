---
title: "installation problem!"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by wilcome on 2007-03-21
Hi, Im totally new with linux but I want to install ubuntu in a partition. The problem has come right at the begining I burn de cd live for amd64 version 6.10 and it breaks with this message at the screen: "signal out of range". My computer is this:

AMD Athlon (tm) 64 Processor 3200+
2.01 GHz, 1 GB RAM  

The video card is NVIDIA geforce 6600 LE 

I've search information about this problem but people say to install the nvidia card drivers of it's website but, how to install them if I can't install ubuntu? now I am in windows XP (I want to keep it in other partition). 
   Other people say to try manually select the resolution of the screen I chose all of them (mine is 1280x1024x32)  and doesn't work.
     Finally I have read things like recompile the kernel of ubuntu but with the right changes, but I have totally no idea about how to do this. Please how can the motto of ubuntu be so unrealistic for me. I want ubuntu! I want Beryl! but i don't know "c" or how to programme things :(. Please help me!! (sorry about my bad English I'm foreign).

---

### Post by fakie_flip on 2007-03-21
The 64 bit version of Ubuntu Edgy Eft would not work on my system either. I have a similar system.

AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
Nvidia Geforce 6600 LE 

Installing the 32 bit version works.

---

### Post by wilcome on 2007-03-21
thank you. I'll try it as soon as posible but it's a pity that it cannot work with 64 bit distribution. What difference will be between them (64 and 32 distribution) ?

---

### Post by sad_iq on 2007-03-21
It's supposed that the 64 bit version should work faster...the problem is that not every app. is optimized to work with it( java I think, and many more!!!)...however running a 32 bit version of ubuntu doesn't make your computer slower!!
 About the signal out of range...you should try using a lower res(800x600 or 1024x768).

---

### Post by fakie_flip on 2007-03-21
If you'd really like to use the 64 bit version, then I suggest you report a bug to launchpad, so that the Linux and Ubuntu developers can fix the problem that is probably specific with your hardware in the next release of Ubuntu, Feisty, and then you can try installing the 64 bit version again. If they don't know the problem exists, it won't be fixed.

BTW, I attached a few screenshots of the errors I got when trying to boot the 64 bit version of Ubuntu Edgy.

---

### Post by wilcome on 2007-03-22
confirmated, the normal cd version "ubuntu-6.10-desktop-i386.iso" doesn't work. I've have try it with 800x600, 1280x1024x32 (my resolution), and it doesn't work. Now you'll sugest me to donwload the alternate install cd? I've spent 4 cd's and 1 dvd (I tried fedora core too) and no solution. I'm begining to throw in the towel :'(. Feeling very silly and not a human been.

---

### Post by sad_iq on 2007-03-22
Let's try this then...boot(with any ubuntu cd)...and at the **Start Ubuntu** screen press F6...there will be a line with a lot of text...find **quiet** and **splash**...delete them...then press Enter!
 That way we will see where the boot process is stopping!!!

---

### Post by wilcome on 2007-03-22
Here I put you a video of what happends. Sorry about the quality because is too poor and sorry too for the beginning is a little confuse. 

     [http://www.youtube.com/watch?v=s50PhqEQ0yU](http://www.youtube.com/watch?v=s50PhqEQ0yU)

Really it crash just when it has to enter to the desktop.

---

### Post by sad_iq on 2007-03-22
Why don't you boot in the normal way(you booted with safe graphic mode)...remove *quiet* and *splash* and boot...don't mess with screen resolution just yet!! 
 Also if it still hangs try pressing ALT+F1 and see if something changes(won't do much...just to see if something happens )!!!

---

### Post by wilcome on 2007-03-22
I have done it in the way you say the video only show me playing Alt+F1 but I have try Ctrl+alt+f1 too. This is the video of the new try. One silly question could the screen and not the nvidia graphic card be the problem? :S.

[http://www.youtube.com/watch?v=Agri40hIyCY](http://www.youtube.com/watch?v=Agri40hIyCY)

---

### Post by ed-j on 2007-03-22
> **wilcome said:**
> Hi, Im totally new with linux but I want to install ubuntu in a partition. The problem has come right at the begining I burn de cd live for amd64 version 6.10 and it breaks with this message at the screen: "signal out of range". My computer is this:

AMD Athlon (tm) 64 Processor 3200+
2.01 GHz, 1 GB RAM  

The video card is NVIDIA geforce 6600 LE 

I've search information about this problem but people say to install the nvidia card drivers of it's website but, how to install them if I can't install ubuntu? now I am in windows XP (I want to keep it in other partition). 
   Other people say to try manually select the resolution of the screen I chose all of them (mine is 1280x1024x32)  and doesn't work.
     Finally I have read things like recompile the kernel of ubuntu but with the right changes, but I have totally no idea about how to do this. Please how can the motto of ubuntu be so unrealistic for me. I want ubuntu! I want Beryl! but i don't know "c" or how to programme things :(. Please help me!! (sorry about my bad English I'm foreign).

Hello, I am a beginner too!

First: There *are* no "foreigners" to Ubuntu or Linux:) !!!

Second: Please tell me if you connect to a PCI Internet card, or if you connect by cable to your Motherboard, or if you are Wireless?

Third: Please tell me what kind of monitor you are using?

Fourth: Put the towel in cold water if you are hot, or wrap it around you if you are cold: It is better to have a towel, than not have one! :)

---

### Post by wilcome on 2007-03-22
thank you for consider me inside this big family ;).

Second: Please tell me if you connect to a PCI Internet card, or if you connect by cable to your Motherboard, or if you are Wireless?

I connect with a PCI Internet card to a adsl router.
(some more data :S 

   Multimedia:
      Audio Adapter          BrookTree Bt878 Video Capture Device - Audio Section
      Audio Adapter          Creative SB Live! Value (CT4830) Sound Card
      Audio Adapter          Realtek ALC850 @ nVIDIA nForce4 (CK8-04) - Audio Codec Interface
   Network:
     Network Adapter     NVIDIA nForce Networking Controller...
 )

My monitor (following the data of Lavalys Report is:  LG Flatron 1715S  [17" LCD] .


VERY NICE SENTENCE!!:

 Put the towel in cold water if you are hot, or wrap it around you if you are cold: It is better to have a towel, than not have one! 

Thank you ;).

---

### Post by ed-j on 2007-03-23
Hi wilcome!

Try the 32bit version of Edgy 6.1.
This should install fine. If you still get the message "sync out of range" check that your Internet connection/cables are ok: This is the only time I have seen this problem, when the Internet or NIC's are not properly connected.
I you manage the install, go to Add/Remove in accessories, type in nvidia and you will find the drivers for the 6600LE without going to the Nvidia site.

If problems are still really bad,  keep trying the forum, there are very many helpful and knowledgeable people. There is also a place in the Ubuntu site where you will find "Free Disks". Ubuntu CD'S will be sent to you free of charge.

Keep trying):P All the best!  :-)

---

### Post by wilcome on 2007-03-24
I did it in your way but no way, my pc doesn't like 6.10 distribution (any of them) so I've seen today the new beta release and guess!!! yeah!!! it runs!!!! [COLOR="Red"][COLOR="DarkOrange"]_**[U]*[U]the amd 64bit 7.04 beta distribution  runs _*[/U]**[/U][/COLOR][/COLOR]in my computer!! so I will begin the installation tomorrow if I have time. Thank you for all your help and attention!.

---

### Post by ed-j on 2007-03-24
> **wilcome said:**
> I did it in your way but no way, my pc doesn't like 6.10 distribution (any of them) so I've seen today the new beta release and guess!!! yeah!!! it runs!!!! [COLOR="Red"][COLOR="DarkOrange"]_**[U]*[U]the amd 64bit 7.04 beta distribution  runs _*[/U]**[/U][/COLOR][/COLOR]in my computer!! so I will begin the installation tomorrow if I have time. Thank you for all your help and attention!.
Hey wilcome!

That sounds amazing! Feisty 7.04 is meant to become the next Ubuntu in April?
Post in and let us know how you get on.=D> :grin: \\:D/

---

### Post by wilcome on 2007-03-25
You can see it in [www.ubuntu.com](www.ubuntu.com) in the section last news Ubuntu -7.04 Beta Released -.

---

### Post by ed-j on 2007-03-25
You're a :KS =D> . All the best!

---

