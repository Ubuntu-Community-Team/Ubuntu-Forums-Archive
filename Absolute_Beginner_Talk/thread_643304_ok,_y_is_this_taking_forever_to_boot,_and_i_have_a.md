---
title: "ok, y is this taking forever to boot, and i have an internet problem"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by napoleon3665 on 2007-12-17
i dual booted vista and ubuntu and when the grub bootloader comes up, i hit enter. it says 

Starting...
Loading, Please wait...

then the screen goes black for a good 10 min, but then al of a sudden theres the ubuntu login screen and everything works great, (well kind of). then once all is good i try to connect to my wireless router and it freezes solid. i dont no if they both are part of 1 problem of if its 2 separate problems, plz help

---

### Post by NT4usB on 2007-12-17
After you hit enter, can you hit Ctrl+Alt+F1 to switch to a tty? You may have to wait a few seconds after hitting enter... give it a couple tries. 
If you get to the tty, you will see the steps Ubuntu is going through to boot and (hopefully) get a clue where it's hanging.

---

### Post by spiderbatdad on 2007-12-17
i was having the same problem for awhile and ended up editing /boot/grub/menu.lst to look like this:
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=XXXXXXXXXXXXXXXXXX
initrd		/boot/initrd.img-2.6.22-14-generic


that is removing quiet and quiet splash not replacing UUID=with exes

---

### Post by Lostincyberspace on 2007-12-17
Install this and reboot
```
sudo apt-get install bootchart
```
then go to var/log/bootchart and their will be an image put it up an we will be able to see what is happening.
I included mine to show a good one.

---

### Post by Lostincyberspace on 2007-12-17
Sorry for go to import the image.

---

### Post by Lostincyberspace on 2007-12-17
Actually that one is bad since fsck decided to run on me. but it will look something like that when it is hanging up on something.

---

### Post by NT4usB on 2007-12-17
I did that just last night... iirc, there's two places where quiet splash show up. One is something like a generic what you want to run every time... near the top of menu.lst. The other place is down on the kernel line.
I don't know if it matters but I nuked it both places (**after backing up menu.lst** of course.)

---

### Post by NT4usB on 2007-12-17
> **Lostincyberspace said:**
> Install this and reboot
```
sudo apt-get install bootchart
```

What a cool ap!
Gonna tuck this one away in the memory banks for sure.

---

### Post by Lostincyberspace on 2007-12-17
> **NT4usB said:**
> What a cool ap!
Gonna tuck this one away in the memory banks for sure.
It is really use full in debugging boot problems, I am glad I found it.

---

### Post by napoleon3665 on 2007-12-18
ok well i booted and did ctrl+alt+F1 and i got it to display the tty, and now the thing tht it is hanging up on is there, it says

[22.472000] Kernel Panic - not syncing : Fatal exception in interrupt. 

then thts it, the lights on my laptop keep lighting up and i can only do a hard shutdown, and now it doesnt even work at all if i go to boot regularly. could this have nething to do with my router problem???

---

### Post by NT4usB on 2007-12-18
I'm out of my league at this point... never had to deal with a kernel panic. Read about them though.
Causes range from easy fix to start over... Someone else may have more info.
A quick Google found [this]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=vxo&q=gutsy+Kernel+Panic+-+not+synching+%3A+Fatal+exception+in+interrupt&btnG=Search")

---

### Post by rkd on 2007-12-18
Were you able to get bootchart installed, as Lostincyberspace suggested? 

I don't know whether the kernel panic prevented it from creating its picture of the boot, but it would be good to check.  Could you boot from the live CD and look in /var/log/bootchart (in your Linux partition of the hard disk, not in the live CD's filesystem) to see whether there is any information there that can help pin down what it is doing when getting the panic.  If you find something, post it here so Lostincyberspace can look it over.

I expect that the panic prevented bootchart from saving its record of the boot, but I've been wrong about such things before.

---

