---
title: "Install Help needed!!!"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by devthedude on 2007-10-25
i'm a linux newbie, i installed linux on my second hard disk(alternate cd),
(windows xp on the frist)
installtion went fine but after i boot ,grub menu comes up,
select ubuntu ,ubuntu then loads for a bit then the pc hangs.
i have to manually restart the thing.
my config:
i848 chipset
dual-core
nVidia GeForce FX 5200 graphics card

Any help will be appreciated.

---

### Post by thelocust on 2007-10-25
Try booting in Recovery Mode and post the output.

---

### Post by thane1 on 2007-10-25
Just a thought ... What version of Ubuntu are you installing - 386 or 486.  In my [I]moderate[I] experience there are a fair amount of 486 progs, which don't run properly in Ubuntu (and you'd probably not notice the difference from 386 anyway.)  If you're planning on running Wine, you'll notice this for example.  You could try reinstalling and the reinstallation itself might solve your problem.  If it doesn't, and you're running the 486 version, might you consider installing the 386 version?  Something to consider before you get too far down the road with installing a lot of programs on a 486 installation and then find you need to backtrack and start from scratch with the 386 version.

---

### Post by devthedude on 2007-10-25
> **thane1 said:**
> Just a thought ... What version of Ubuntu are you installing - 386 or 486.  In my [I]moderate[I] experience there are a fair amount of 486 progs, which don't run properly in Ubuntu (and you'd probably not notice the difference from 386 anyway.)  If you're planning on running Wine, you'll notice this for example.  You could try reinstalling and the reinstallation itself might solve your problem.  If it doesn't, and you're running the 486 version, might you consider installing the 386 version?  Something to consider before you get too far down the road with installing a lot of programs on a 486 installation and then find you need to backtrack and start from scratch with the 386 version.

i have installed both the versions i386 as well 64 bit version available on the website
but neither of them work.

---

### Post by devthedude on 2007-10-25
> **thelocust said:**
> Try booting in Recovery Mode and post the output.

recovery mode didn't work,
i'm a newbie so please tell me what is "post the output".

---

### Post by thelocust on 2007-10-26
Sorry budy this is over my head, anybody else?

---

### Post by Flying caveman on 2007-10-26
what happens,? Do you get some kind of error message?  did you try typing startx? does the screen just go blank?   

try reading this  [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Oh, since you used the alternate CD you might have accidently installed a server version with no graphical desktop.

---

### Post by devthedude on 2007-10-26
> **Flying caveman said:**
> what happens,? Do you get some kind of error message?  did you try typing startx? does the screen just go blank?   

try reading this  [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Oh, since you used the alternate CD you might have accidently installed a server version with no graphical desktop.

no,i didn't use the server version
when ubuntu loads (u know ,when the orange bar fills up slowly :with ubuntu written on top)
my pc hangs, the screen dosent go blank but just stays put.
i' ve to manually reboot
my windows xp works fine
i've tried the live cd (desktop)  it also  hangs the same way 
is it a hardware problem

HELP!!!!!!!!

---

### Post by devthedude on 2007-10-26
> **Flying caveman said:**
> what happens,? Do you get some kind of error message?  did you try typing startx? does the screen just go blank?   

try reading this  [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Oh, since you used the alternate CD you might have accidently installed a server version with no graphical desktop.

i am not getting any error message
the orange bar dosent completely fill but jets jammed in the middle
the screen stays put

---

### Post by FighterOfTheNightMan on 2007-10-26
Your menu.lst file may not be configured correctly.  Post your /boot/grub/menu.lst file.  

Regards,

Brandon

---

### Post by Circus-Killer on 2007-10-26
are you by any chance tryna run it on a laptop.
if so, when grub menu comes up, press 'e' for edit.
then add "noapic irqpoll noirqdebug" to the kernel line.
then once you finished adding that, push 'b' on the selected line to boot.

if this gets ubuntu started, the you will need to edit /boot/grub/menu.lst and add those options to the kernel line (so that you dont have to do it at every boot).

---

### Post by devthedude on 2007-10-26
> **FighterOfTheNightMan said:**
> Your menu.lst file may not be configured correctly.  Post your /boot/grub/menu.lst file.  

Regards,

Brandon

thats not the problem
i can boot both OS on the seperate hard disks by the grub menu
the problem is while the  windows boots easily
ubuntu hangs the pc, the orange bar just wont fill up
it still wont start

---

### Post by devthedude on 2007-10-26
> **Circus-Killer said:**
> are you by any chance tryna run it on a laptop.
if so, when grub menu comes up, press 'e' for edit.
then add "noapic irqpoll noirqdebug" to the kernel line.
then once you finished adding that, push 'b' on the selected line to boot.

if this gets ubuntu started, the you will need to edit /boot/grub/menu.lst and add those options to the kernel line (so that you dont have to do it at every boot).

i'm not tryin it on a laptop

---

### Post by devthedude on 2007-10-26
i'm tired of getting ubuntu started 
i'm uninstalling it 
it aint working on my system
and going for another linux
(i know this is ubuntu forms but can any anyone suggest another  easy linux
for newbies!!)

---

