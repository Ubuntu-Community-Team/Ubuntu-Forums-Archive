---
title: "Bios and installing ubuntu"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Flamboy on 2007-06-03
This is the second time I tried to install ubuntu on the same PC; the first time was three months ago and the distibutions were not the same. Anyhow, I was booting to the Live-CD and chose the option "Start or install ubuntu in safe graphics mode", the kernel loaded okay and a bunch of other files aswell but then the screen went blank and said something like "bios age(1999) fails cutoff(2000)". The message was displayed for a few seconds and then the installation went on. But so at the screen with the moving statusbar the program halted and stood for serveral hours untill I grew tired and cut the power. I tried the other option aswell but the results were the same. 

Does anyone know what to do about this? I don't think this is i fault on ubuntu's part but how can I fix it, preferably without having to exchange motherboard or anything as mechanicly demanding.

---

### Post by blackened on 2007-06-03
Download the alternate CD. It uses a text based installer, but it's as dead simple as the live CD.

My machine has nothing but problems booting from live CDs, even though it's not exactly ancient, it just takes too long to bother with.

---

### Post by Flamboy on 2007-06-04
I tried that too this morning, no difference whatsoever.

---

### Post by pappapump on 2007-06-04
Looks to me like you flashed your bios at some point and there is a version conflict.
Also as stated in a previous post, make sure that if you are running an AGP or PCIE video card that you don't have onboard video, and if you do, turn it off.
Come to think of it, that looks like the Y2k bug.........
Try a bios update and see if it resolves your problem.

---

### Post by mlentink on 2007-06-04
Flamboy, if that BIOS really is from 1999, that machine is around eight years old. I am wondering what the specs are? Could you tell us a bit more about it?

---

### Post by Flamboy on 2007-06-04
Well I'm not 100% sure what's acctually in there but eight yers old sounds about right. If I remember this correctly it's an IBM Aptiva 450MHz processor(intel of some kind, perhaps pentium 2 or 3) with 3x128 Mb of RAM. As for th motherboard and bios I know absolutely nothing about them. I think the graphics are integrated but there are boards for sound and network, PCI all of them. Oh of course a smashing 13 Gb maxtor harddrive

---

### Post by pappapump on 2007-06-04
omg, thats about 128 megs too small.

---

### Post by Flamboy on 2007-06-04
Might be but it worked without complaining the last time.

If I was to update my BIOS, where would I find the correct version. The inscription of my BIOS-chip says: v66m BIOS u26 v3.2 r04-h0. I've tried ibm's webpage but can't be sure of which aptiva model I have.

---

### Post by mlentink on 2007-06-04
Hmm. I would say it&#347; a bit underspec'ed. I run my server on a 1GHz PIII, but that's with 384 Megs memory, usually I've got about 128 Megs left and it never uses swap. But with the GUI it becomes a different story, especially because you most likely have shared memory for your video. 
Is adding memory an option? Otherwise I start looking at Xubuntu or other

---

### Post by blackened on 2007-06-04
It's definitely too low in spec to be running a live CD. I'd suggest, like mlentink, that you try running xubuntu. You might also try installing the server version (just skip through the part where it asks you what sort of server you want i.e. LAMP etc.) and then add fluxbox or the like on top of that. Would give you much more of a minimum install.

---

### Post by Flamboy on 2007-06-04
In fact I'm not planning on usning that computer every day; it's more the one I use to try out new things. So as long as the computer is able to run ubuntu at all, I'll bew happy. I've got a far better computer which is currently running xp and I'm quite happy with that but I thought I'd try out linux a little before making a switch.

---

### Post by blackened on 2007-06-04
The older machine will definitely provide you a good learning tool, but won't be a very accurate indicator of the experience of linux on a newer better machine.

---

### Post by Flamboy on 2007-06-04
Perhaps; bu for now learning is what I'm interrested in. You see I excahnged DOS for windows only trhree years ago so all that bash-coding mixex up with dos-commands so I need time to sort it out.

As for the immediate problem; BIOS, is there an age cutoff for all ubuntu distributins or will I have to flash my BIOS in order to get any kind of installation going?

---

### Post by information_entropy on 2007-06-04
I was able to reproduce your “bios age(1999) fails cutoff(2000)" error on an old AMI bios machine.
It goes away if I disable ACPI in the bios.

In this bios set up it is: 
             advanced->advanced chipset setup->acpi control register->disable
and      advanced->power management setup->acpi aware os->no

Your bios is almost certainly different, but this is what you are looking for.

You still get an different acpi error from grub but Ubuntu will still and install and run.
At least it did for me.

The problem is not that the computer is too old. 
It is that it's acpi support is too old.

If you still cannot install it is probably due to not enough memory
a bad CD or CD reader.

It was unclear whether you have 3 128meg memory sticks for a total of 384 memory
128 total will probably not work 384 total will definitely work 
 
I keep old computers to test stuff on too.  ;)

---

### Post by Flamboy on 2007-06-04
I'm looking for something like that right now but haven't found anything yet. Thanks for the information.

And yes it's 384. I figured one computer with 384 is better than 3 with 128 so I threw away two and only kept the memory sticks.

---

