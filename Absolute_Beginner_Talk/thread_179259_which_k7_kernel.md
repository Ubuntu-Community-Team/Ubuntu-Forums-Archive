---
title: "which k7 kernel?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by mannock on 2006-05-19
after just installing breezy i assume i need to update to the correct kernel,  but looking at the list in synaptic i see six different k7's some with smp at the end of the title.  how do i know which one to use?

---

### Post by Suzan on 2006-05-19
The kernel with smp (symmetric multi-processing) is for dual core processors.

---

### Post by macdo on 2006-05-19
Choose the one called linux-k7. That is a 'fake' package that will install all the right bits and pieces.
It's recommended that you reboot after updating your kernel.

---

### Post by mcduck on 2006-05-19
[QUOTE=macdo]Choose the one called linux-k7. That is a 'fake' package that will install all the right bits and pieces.
It's recommended that you reboot after updating your kernel.[/QUOTE]
this is the right way to do it :)

If you install specific kernel version, you'll get that kernel version, but no automatic kernel updates. But if you install the linux-K7 metapackage you'll always have the latest kernel version available, and you also get all related packages for your kernel (like restricted modules)..

---

### Post by mannock on 2006-05-19
oh dear,  installed linux-k7    now it will only boot to a screen load of error text,  i can only boot to the old 386 kernel.   the processor is amd duron 1.6 ,  perhaps the k7 is not the one?     the errors are something to do with
'failed to start x server'      if i click yes to resolve,  it disables  GDM and leaves me with a command prompt with no graphical interface,   waiting for me to log on, which i don't know how to do in text,  and i don't suppose there would be any point.

---

### Post by macdo on 2006-05-19
log on: use your username and password at the prompts.
Then type startx, which should start X (the graphical display manager)

I have absolutely no idea why it should have done that, though...

---

### Post by Kimm on 2006-05-19
Did you have any restricted modules installed?

Like the Proprietary NVIDIA Drivers?

---

### Post by mannock on 2006-05-20
yes Kimm,  one of the first things i did after installation of breezy  was to install the nvidia drivers.  that centralised my display so was worth doing.   could this be the problem?       anyway,  running the 386 kernel seems fine,   i just can't resist fiddling,   if i see a newer or better version of something i have to install it,  gives me peace of mind i suppose,  that is,  if everything is bang up to date then there is less likelihood of problems......in theory  lol .       and i like things tidy,  so if the k7 is not for me,  next question is,  how do i remove it.   it's on my grub menu you see,   dual booting with xp,   so i set the default to be the 386,  fine,  but it must be taking up a lot of space on my hard drive.....or not?

---

### Post by Kimm on 2006-05-20
Ah, that would explain it. You see, the drivers are compiled specificly for the kernel that uses them, since the nvidia driver is compiled for you i386 kernel, it will not work on your k7 kernel.

Did you install the NVIDIA driver using the repos (by installing nvidia-glx) or did you build the one found on the NVIDIA website?

If you installed from the repos, then you should intsall this package:
linux-restricted-modules-k7

if you installed manualy using the installed on the NVIDIA website, you have to uninstall that driver and them reinstall it.

uninstall using: sh NVIDIAxxx.sh --uninstall

---

### Post by mannock on 2006-05-20
i used synaptic to install nvidia-glx and nvidia-settings.       so...now i install   linux-restricted-modules-k7  ?       ok,  i've done that,  rebooted,  but it's not listed in the grub menu,   just the i386  which i'm using and the k7 which didn't work.   ah, perhaps now i can use the k7?      i'll try it.

---

### Post by mannock on 2006-05-20
it works,  oh joy,  relief etc.     thanks for the help.

---

