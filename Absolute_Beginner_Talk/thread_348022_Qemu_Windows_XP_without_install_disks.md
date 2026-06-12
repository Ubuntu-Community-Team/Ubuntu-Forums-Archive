---
title: "Qemu Windows XP without install disks"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by CongoJim on 2007-01-28
I want to run my printer driver through a Qemu window with XP running in it. I do not have the install disks for xp but I do have xp installed on the computers. First question is is it possible to make the ISO img from the hard drive and if so how?

If I had my druthers I'd use Ubuntu Edgy exclusively but I have a Dell 924 AIO printer and there are no linux drivers for it yet. So as a solution I'd like to see if I can print from a windows window. ie when I have to print something open windows in qemu and transfer the file there and print. Is this even doable? The transfering file and then printing? I realize that normanlly the best solution would be to go pick up a new Linux friendly printer but I live in Kananga, the DR Congo and frankly there isn't a Best Buy to be seen nor do I have the funds to have a new one shipped here. My equipment was a grant from the US embassy to create a lab that is used by 6 high schools and the general publique and that money is long used up so I am looking for alternatives that don't include spending money other than dual booting which is such a waste of energy (I run off batteries a lot, gas gets up around $15/gal here). 

Any of you smart guys able to help me out.

---

### Post by Hossie on 2007-01-28
I dont think its possible that an emulated Windows can directly access external hardware, like printers. Also, copying your windows to an Qemu container is against the licensing terms of Windows, you are only allowed to have one Windows installation per license. As far as I know, VMWare is able to boot a partition as a Virtual Machine, but still you probably wont be able to access your printers.

---

### Post by CongoJim on 2007-01-28
Never hurts to ask right? When you have neither a working post office nor a credit card VMware doesn't look so good. Assuming that I come up with an image of windows, do you think that at least the scanner might work or am I wasting a lot of energy?

---

### Post by Hossie on 2007-01-28
VMWare Server is free.

---

### Post by chrisg0619 on 2007-02-02
The printer will not work on a virtual Windows machine because the hardware has to be recognized by Ubuntu.  Sorry--maybe someone else here has a solution.

---

