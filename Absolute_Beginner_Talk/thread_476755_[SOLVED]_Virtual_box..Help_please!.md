---
title: "[SOLVED] Virtual box..Help please!"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-17
i want to play a game sometimes, but it is for Windows!

i got VirtualBox to save me going from one to the other. Windows - Ubuntu - Windows etc....

but i cant play the game as no graphics card is detected. is there a way to sort this out?
or somehow enable my graphics carD in virtualBox?

---

### Post by starcraft.man on 2007-06-17
> **skymera said:**
> i want to play a game sometimes, but it is for Windows!

i got VirtualBox to save me going from one to the other. Windows - Ubuntu - Windows etc....

but i cant play the game as no graphics card is detected. is there a way to sort this out?
or somehow enable my graphics carD in virtualBox?

Nope. That is the nature of a VM. You can't run it right off the card to my knowledge. Parallels is the only one yet it seems to implement gaming well in a VM, and thats only for the Mac. I think thats because of the somewhat uniform hardware and software, thus easier to code it. For games you either run a layer through WINE / Cedega or you dual boot. No options in the VM department.

---

### Post by dreadlord_chris on 2007-06-17
> **skymera said:**
> i want to play a game sometimes, but it is for Windows!

i got VirtualBox to save me going from one to the other. Windows - Ubuntu - Windows etc....

but i cant play the game as no graphics card is detected. is there a way to sort this out?
or somehow enable my graphics carD in virtualBox?

do you mean that the game doesn't detect a graphics card, or that Windows doesn't?
Also, have you installed the Guest Additions?

---

### Post by starcraft.man on 2007-06-17
> **dreadlord_chris said:**
> do you mean that the game doesn't detect a graphics card, or that Windows doesn't?
Also, have you installed the Guest Additions?

Doesn't matter... Virtual Box only emulates a card, it doesn't provide direct rendering directly off of your hardware. The Additions don't add that. If it did, I would so love it to death... >.>

---

### Post by skymera on 2007-06-17
yes i have guest additions.

the game is LiveForSpeed.
i go to run
and error say 'probably graphics error'

---

### Post by starcraft.man on 2007-06-17
> **skymera said:**
> yes i have guest additions.

the game is LiveForSpeed.
i go to run
and error say 'probably graphics error'

Read my above posts, additions or not Virtual Box is not a gaming platform, there would be a lot less dual boots if (maybe I should say when, if they ever do) it was... the error simply means the driver/emulated card is completely inadequate for rendering.

Sorry to rain on your parade, but thats the way it is. VM's are mostly for development testing and running basic apps (no graphics requisite) like Office, Photoshop and Flash.

Edit: Oh and why did I have to post 3 times... no one read what I post now? Geez...

---

### Post by Golyadkin on 2007-06-17
What a virtual machine does is kinda "emulate" a real computer. It pretends to be a real computer, but it is not.   It is a virtual simulation. The graphics card that is being emulated is not a real graphics card, it is just a program that tries to respond to all requests the way a graphics card would. Because this is infinitely slower than having a real graphics card that has hardware to respond supremely fast, you will not get real 3D acceleration in a virtual machine, because it is too slow.

---

### Post by skymera on 2007-06-17
hmmm fair enough, all true.

i was thinking of deleting my Windows.

but i need it for Photoshop and gaming..

but thanks for replies

---

### Post by Golyadkin on 2007-06-17
I dual boot with Windows but I never boot Windows really. What I did was put a second Windows XP in virtualbox, so I can use all programs (like Photoshop) I want by simply starting the machine, without having to reboot. 
[img]http://www.android42.net/got/VirtualBox.png[/img]
If I really want to play a windows game, I boot into Windows, but I am in Ubuntu 95% of the time, even for gaming.

---

### Post by skymera on 2007-06-17
i swapped because my windows loads up sooo slow!
last tie i had to wait 7 mins for my stuff to load :S
Graphics driver
Zone Alarm Internet Suite
AVG Anti spy
Internet sctreens

i dont know why! 
im running a 3.8Ghz pc

can i install Photoshop CS2 in Virtual XP?
also wont it lag real bad? running '2' OS and CS2

---

### Post by Golyadkin on 2007-06-17
I saw a guide to having a seamless setup with virtualbox. It allows you to start Photoshop or any other Windows program from the Applications menu or the panel, loading it  in a window using a remote desktop connection to a virtual machine running in the background. 

Found it: [This is the guide]("https://help.ubuntu.com/community/SeamlessVirtualization")

---

### Post by Golyadkin on 2007-06-17
By the way, I have a 2.2 GHz (AMD Athlon64 X2 4200+) and it starts the Windows XP virtual machine in less than a minute.

---

### Post by skymera on 2007-06-17
no not the Virtual Machine.
my REAL XP.
i dual boot.

---

### Post by Golyadkin on 2007-06-17
Oh okay, I'm sorry :)  I thought you were using a  virtual machine.

---

### Post by dreadlord_chris on 2007-06-18
> **starcraft.man said:**
> Edit: Oh and why did I have to post 3 times... no one read what I post now? Geez...

:p
I read it....

---

### Post by Sugi on 2007-06-24
*wrong section*

---

### Post by bodhi.zazen on 2007-06-24
> **Sugi said:**
> I did some research on VM and graphic drivers, and it didn't look pretty.  It does look like we are out of luck, but a buddy of mine is using a VM under his host as Redboot (it's linux).  He says that he is guesting XP and able to play agains under his VM box.  But i don't know how he did it.  Maybe it has something to do with his Linux box that has a really good VM.  I'm starting to wonder though, he sometimes lies about silly things like that, but the thing is i have played video games with him under my windows boot (dual-boot).  And his brother even said hes using linux.  So, maybe it's possible.  BUT how? : (((

Some games will work and others will not.

I do not know the exact specifications of the virtual box video driver, but no 3D or direct X on virtualbox.

wine will give some directx emulation as will cedega so your friend may be using wine.

If he is your friend, why not ask him how he got up and running ?

---

### Post by Sugi on 2007-06-24
I did some research on VM and graphic drivers, and it didn't look pretty.  It does look like we are out of luck, but a buddy of mine is using a VM under his host as Redboot (it's linux).  He says that he is guesting XP and able to play agains under his VM box.  But i don't know how he did it.  Maybe it has something to do with his Linux box that has a really good VM.  I'm starting to wonder though, he sometimes lies about silly things like that, but the thing is i have played video games with him under my windows boot (dual-boot).  And his brother even said hes using linux.  So, maybe it's possible.  BUT how? : (((

---

### Post by bodhi.zazen on 2007-06-24
> **Sugi said:**
> I did some research on VM and graphic drivers, and it didn't look pretty.  It does look like we are out of luck, but a buddy of mine is using a VM under his host as Redboot (it's linux).  He says that he is guesting XP and able to play agains under his VM box.  But i don't know how he did it.  Maybe it has something to do with his Linux box that has a really good VM.  I'm starting to wonder though, he sometimes lies about silly things like that, but the thing is i have played video games with him under my windows boot (dual-boot).  And his brother even said hes using linux.  So, maybe it's possible.  BUT how? : (((

LOL Sugi

I can move that post somewhere if you like, just post a link to where you want it.

I can then delete double posts :)

---

### Post by michalski7777 on 2007-10-12
i installed virtual box but as i was installing using the  package installer it asked me to agree to the terms of use but it wouldnt let me click ok :S as it was only a viewing window so i clicked cancel which hasnt turned out well for me 

i cant use any kinds of update whatso ever, updatemanager, synaptics, reinstalling nothing what do i do

error(update manager):
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'


....help

---

### Post by bodhi.zazen on 2007-10-12
See this link : [http://ubuntuforums.org/showthread.php?t=340113](http://ubuntuforums.org/showthread.php?t=340113)

This is a common problem and the fix has been edited into the first post in blue.

IF this does not fix the problem please let me know so I can update the how-to.

Thanks in advance.

---

### Post by michalski7777 on 2007-10-12
> **bodhi.zazen said:**
> See this link : [http://ubuntuforums.org/showthread.php?t=340113](http://ubuntuforums.org/showthread.php?t=340113)

This is a common problem and the fix has been edited into the first post in blue.

IF this does not fix the problem please let me know so I can update the how-to.

Thanks in advance.

thank you sooo much i learnt something (hehe :) ) thank you ! worked great

---

### Post by madmatrixz3000 on 2007-10-12
Will stuff like Cuebase and ProTools work in VBox, I know that the Studio package has some good stuff, but I don't want to have to relearn the process of recording, plus I don't know where to start with the needed driver for my firewire soundcard.

---

### Post by bodhi.zazen on 2007-10-12
> **michalski7777 said:**
> thank you sooo much i learnt something (hehe :) ) thank you ! worked great

You are most welcome and thanks for the feedback, it is invaluable in helping others. It is also helpful to mark threads as solved.

> **madmatrixz3000 said:**
> Will stuff like Cuebase and ProTools work in VBox, I know that the Studio package has some good stuff, but I don't want to have to relearn the process of recording, plus I don't know where to start with the needed driver for my firewire soundcard.

I do not know those apps so I assume you are asking about windows programs. I also assume you are asking about running an Ubuntu host and Windows guest ...

In my experience with sound on such a set up, the apps may work, but often sound is choppy. Potential solutions may be to launch you windows guest from the command line with a nice value of say -10 or install the so called "low-latency" kernel. If you install the low latency kernel this requires a re-boot, choose the low latency kernel form your grub menu.

---

### Post by forestpixie on 2007-10-12
> It is also helpful to mark threads as solved.

don't think it's his thread - just joined on at the end :)

---

### Post by bodhi.zazen on 2007-10-12
> **forestpixie said:**
> don't think it's his thread - just joined on at the end :)

:lolflag: hijackers :rolleyes:

---

### Post by forestpixie on 2007-10-12
yesss - it's quite funny when you see a thread for a problem that's quite easy to solve once you've been here a while - and you notice the poster's name and know they've been at it longer :D - I like the ones with 2 years or so between posts :biggrin:

---

### Post by skymera on 2007-10-13
i thought this thread was dead?

o well, i marked solved now

---

### Post by Orbital75 on 2007-10-13
Sorry to say, that's the nature of Virtual Machine as was said above.
VM will allow you to run another OS with pretty much any program you
like but Games however are another story.  It's just best to duel boot
and run the games natively on XP.

Anyways, make sure you have alot of RAM, I'd say at least
a GIG or more to make things run smoothly and not bog down.

---

