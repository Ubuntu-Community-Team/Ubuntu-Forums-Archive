---
title: "The easiest way to absolutely completely clean Ubuntu 7.10  from my hard drive."
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by bastonal on 2008-01-30
I installed 7.10 on my WD SATA Raptor hard drive, several times for various reasons and now I can't get that clean perfectly working first copy I had...Now when I boot up there's this strange screen the last few times I reinstalled 7.10 at the start asking if I want to go to Ubuntu "Generic' (or about five other options) if I do nothing, it boots in seven or eight seconds to sometimes a pink screen with just the mouse arrow....if I reboot I again I might get to my desktop but always the screen resolution has changed, sometimes its at 640x480 or so large I can't find my icons without moving the whole desktop screen over and down and lowering the resolution back to where I had it when I last shut down.

I just want to clean my hard drive of all Ubuntu the easiest way possible and reinstall 7.10 t on a clean hard drive from a downloaded 7.10 disc I burned.

Thanks

---

### Post by oedha on 2008-01-30
what is your display adapter ?
maybe you can install from "install in safe graphic mode"
or
can you login by pressing ctrl+alt+f2 then type down username and password
if you can login.....type :--> sudo dpkg-reconfigure xserver-xorg

regards;
~E~

---

### Post by LowSky on 2008-01-30
hmm, on the live cd go to System> admin> partition editor

this will start Gparted

use Gparted to erase all the partitions, or creat fresh new ones

---

### Post by Niniel on 2008-01-30
Just install over it, but wipe the disk when you do it.
Pop in the live CD and either use the manual option to re-partition your drive - deleting all partitions and creating new ones will remove all traces of everything - or one of the "use the entire hard drive" options. 

Better luck this time. :)

---

