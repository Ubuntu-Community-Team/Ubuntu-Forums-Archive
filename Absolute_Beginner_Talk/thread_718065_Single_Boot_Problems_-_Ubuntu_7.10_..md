---
title: "Single Boot Problems - Ubuntu 7.10 ."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Pvpede on 2008-03-07
Hi .

I have this "little" problem .

When I turn on my computer and just don't do anything, it wont boot anything.
- I can into my **Boot Menu** - but it's very very very irritating to sit & press F12 100 times just to choose my single HDD.

So, my question is:
**How can I boot just normal, without touching the boot menu?**

---

### Post by Daveth on 2008-03-07
some of things in these pages are 1 solution

[http://users.bigpond.net.au/hermanzone/p15.htm#timer](http://users.bigpond.net.au/hermanzone/p15.htm#timer)

- reduces grub to a few seconds before loading.

---

### Post by Pvpede on 2008-03-08
Uhm .. This is not useful for my problem.

I can't even see the GRUB menu .
- If I don't boot it from the Boot-menu, then it'll stand & do nothing .

---

### Post by handy on 2008-03-08
> **Pvpede said:**
> Uhm .. This is not useful for my problem.

I can't even see the GRUB menu .
- If I don't boot it from the Boot-menu, then it'll stand & do nothing .

Please give more information, if it is not the GRUB menu, what boot menu are you talking about?

---

### Post by SloYerRoll on 2008-03-08
So with the F12 thing. That's called BIOS. It's how your system get's up and running. If it wasn't for BIOS. Computers wouldn't be that good at starting up...

So it sounds like an issue w/ GRUB. 

I'm no expert, but the following will help the gurus looking at all the stuff they need to see (hopefully)

Open up a terminal and go to your grub directory:
```
cd /boot/grub
```
Then make a backup of your grub file in case things get crazy:
```
sudo cp menu.lst menu.lst_backup
```
Then open up your GRUB menu in gedit by doing the following:
```
gksudo gedit menu.lst
```

Now copy all the text and paste it in a reply here. GRUB is a bit above my at this point. I'm still a nOOb as well. But I'm learning.:)

Don't forget to wrap all your code in some code tags so it doesn't take up miles of space (see screen shot below)

BTW I got all this from member confused57. Thank him if any of this helps!

---

### Post by Pvpede on 2008-03-08
There's nothing inside the menu.lst .

Image:
[[img]http://pvpede.be/imuu/thumbs/898492geditthing.png[/img]]('http://pvpede.be/imuu/images/898492geditthing.png')


and, yeah :)
I meant BIOS when I said Boot Menu .

---

### Post by om1 on 2008-03-08
sounds like you need to set your boot order in your bios... i would set your boot order to cd/dvd drive then your hard drive... that should fix your issue... every bios is different just look till you find where to set your boot order...

---

### Post by Pvpede on 2008-03-08
Thanks for the tip :D

I couldn't even remember that I could set it in that BIOS main menu <_<

---

### Post by SloYerRoll on 2008-03-08
> **om1 said:**
> sounds like you need to set your boot order in your bios... i would set your boot order to cd/dvd drive then your hard drive... that should fix your issue... every bios is different just look till you find where to set your boot order...Unless BIOS is all buggered up. This won't have any real effect on how the machine boots up. 

To check the BIOS boot order. When booting, hold down F2 and use the arrow keys to scroll to startup (or the equivalent word)
You SHOULD see that it will boot to the HD first, then optical drives. If not, just follow the on screen instructions and  change the boot order. Don't worry, it's next to impossible to break anything in the startup menu.

What's happening (I think) is that BIOS is trying to boot to the HD and asks Ubuntu what it wants to do. Since GRUB isn't hanging around (empty list) the puter gos to the optical drive. Since theres no media in there. You get the F12 blues. 

I have NO idea how to configure GRUB though. But this should fix all your problems when someone comes in here to help..

BTW:
Without the comments (which Ubuntu ignores anyway) this is what  your grub menu will look like on a single hard drive. *I'm not sure if your settings will be different since I don't know what version your running or if the Kernel end up it the same place in all distros.
```
title		Ubuntu 7.10,     kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=37dcaded-3e3e-4c31-81b9-05e775ed7b00 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10,     kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=37dcaded-3e3e-4c31-81b9-05e775ed7b00 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10,     memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

Edit:
If you can validate the filepaths to the files in the above menu. I'll bet you a paycheck that this will get grub up and running! Just boot into Ubuntu and see if the files are in the location that my GRUB list says. If they aren't, just locate them and change the path.

---

