---
title: "[SOLVED] CD-RW used to make live disc for older pc"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Calindae on 2008-03-24
I am about to make a live cd for an older pc, but I am not sure if it is going to be able to read a CD-RW. I'm not with the computer yet or I would just burn it and try it. This is gonna be a one shot only type thing, so I'm trying to make sure it will work. Do even pretty old machines have the ability to read CD-RW?

And I am wondering which distro to use. It's safe to think of this machine as the oldest thing that can run Windows ME, I think it was even upgraded to it from Win98 a while after it was purchased. So what is the lightest weight OS that is still somewhat friendly to a windows user (my brother). The reason why I am trying this is because the pc won't come out of safe mode. Apparently he had two mp3 players plugged into it, it froze, and he hard shut it down. 

I was thinking Xubuntu, but I'm not sure if this computer can handle it...

Oh and which iso burner software do you guys use?

---

### Post by djbsteart1 on 2008-03-24
K3b, I cannot comment on whither it will read the CDRW, but you could always just get a standard CDR. As for distro's that depends on whet you want, and how much experience,/ease of use is wanted. 

A very fast distro that has a growing package manager but it is by no means complete is Zenwalk. As it stands it is very complete, yet fast, although it is harder than ubuntu to use as it doesnt use .deb or .rpm files. 
If you want something very challanging there is sSackware or Arch, with Arch it would need to be connect to the internet.
For ease of use i would try xubuntu, or fluxbuntu, there is also pcfloxboxos and an xfce version of pclinuxos. And the usual puppy and dsl.

You could also if you have the time, take two distro's, that way you can see if the performance of the laptop is up to much. also the specs would be useful for giving suggestions of distro's, I have one that I am guessing is similar to that one that handles Zenwalk really well. Its very very fast indeed.

---

### Post by Calindae on 2008-03-24
Do you think DSL will be compatible with an inexperienced windows user? And I read that it doesn't use GNOME or KDE, so is its user interface user friendly?

---

### Post by mattk132 on 2008-03-24
You can't put a live cd on a cd-rw.(trust me I've tried).  However, you can put the text based installer on one.:)

---

### Post by Calindae on 2008-03-24
How does a text based installer work?

Update: I don't have access to cd-r's at the moment, but I do have an ipod nano...
Also, this pc is stuck in safe mode, so whatever I do needs to incorporate that fact if necessary.

---

### Post by AndyCooll on 2008-03-24
the Ubuntu "Alternate" CD is a text based installer. It isn't a Live CD and therefore doesn't let you view the CD before installing. In effect it installs Ubuntu to your hard-drive just as you can choose to do from the Live CD. The main difference is that it isn't pretty since it doesn't have a gui frontend, it's a command line based wizard (though the steps are fairly clear and obvious). If you have a PC with only a small amount of memory this may be your only option.

:cool:

---

### Post by Calindae on 2008-03-24
Well, I just created a puppy linux cd with a CD-RW and it booted up just fine on my laptop. I chose to "finalize" and burn in "disc at once" mode instead of "session at once" so hopefully the old pc will be able to run it when I get to it later today.

---

### Post by djbsteart1 on 2008-03-24
> **mattk132 said:**
> You can't put a live cd on a cd-rw.(trust me I've tried).  However, you can put the text based installer on one.:)

This is not true. I have had Mandriva, Ubuntu, Fedora...... on Rw, they just need burned at a slower rate, around 4x for me. 
DSl isn't the friendliest of thinds, so I would try x/fluxbuntu, see what is thought of puppy, I havn't used it in a bit, but it might still be a little hard.

---

### Post by Calindae on 2008-03-25
The cd-rw worked and I have been working on installing DSL to the harddrive. Turns out the pc was a pentium II 533 MHz 80 mb ram 6 gb hardrive, so  I'm not sure if it can handle x/fluxbuntu. Its running DSL live cd good tho

However, I can't get it to boot from the harddrive. I partitioned it with cfdisk and made hda1 a swap type 82 size=256 mb and made hda2 the rest of the drive type 83 flagged as bootable. Then I rebooted, turned the swap on, then did the DSL-hdinstall command and followed the directions (choosing grub). However when I rebooted without the cd in it would not boot up. I even turned on the boot from harddrive option in the BIOS setup. It just starts to a black screen with a flashing cursor after it counts the ram and detects the mouse and keyboard.

---

### Post by mcdan on 2008-03-25
you say you want to use DSL, have you tried xubuntu, it has lower system requirements, and may run fine on an old system, DSL wouldn't be as good of an all around OS as a ubuntu derivative

---

### Post by Calindae on 2008-03-25
o xubuntu has lower requirements? I didn't know that..i think I'll try it.btw where do find these min reqs.? Ive had trouble finding them.

Edit: xubuntu's min requirements can't be lower than DSL's. DSL only needs like 16 MB RAM...

---

### Post by djbsteart1 on 2008-03-25
> **Calindae said:**
> o xubuntu has lower requirements? I didn't know that..i think I'll try it.btw where do find these min reqs.? Ive had trouble finding them.

Edit: xubuntu's min requirements can't be lower than DSL's. DSL only needs like 16 MB RAM...

That spec will struggle greatly with xubuntu, but fluxbuntu might manage ascould pcfluxboxos. 

KDE and Gnome are the 2 large DE's (Desktop Environments), both require a decent system to run, XFCE is a slightly less instensive DE but is still above you hardware when used with ubuntu. The there are many light window managers such as JWM flux/opem/blackbox all of which do not need to much in the way of resources to run. 


As I recall with DSl, if possible try the LILO loader, it worked when grub didn't.

---

