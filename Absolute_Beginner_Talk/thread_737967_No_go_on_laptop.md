---
title: "No go on laptop"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by miffin on 2008-03-28
I have used Ubuntu on my desktop pc with no problems.  But I really want it on my Dell Inspiron 3800 laptop.  When I put the disk in, it appears to start, then all I get is gobblygook writing on the screen and the laptop freezes.  I am not too technical so is there any chance I might get this going  please?
Thanks
Brian

---

### Post by jan quark on 2008-03-28
are you using the desktop live CD? if yes try either to boot into the save graphical mode
or use the alternate CD to install in text-mode.

I cannot suggest anything more specific because 
> gobblygook writing on the screen
is not so accurate either :)

but there is probably some conflict with the hardware of your laptop

did you have checked the CD for defects?

---

### Post by .nedberg on 2008-03-28
Have you checked the CD for errors?

Else you could try the alternate cd. It does not use the Live system, but uses a text based installer.

---

### Post by miffin on 2008-03-28
> **jan quark said:**
> are you using the desktop live CD? if yes try either to boot into the save graphical mode
or use the alternate CD to install in text-mode.

I cannot suggest anything more specific because 

is not so accurate either :)

but there is probably some conflict with the hardware of your laptop

did you have checked the CD for defects?

Hi.  Just tried the safe graphical mode but that did not work either.  The gobleydegook starts off

361   060000 EIP is at union fs_rename
Then it goes down the page quoting stuff like that.
Can you point me to the alternative cd please as i am not too good around this site.
Brian

---

### Post by bumanie on 2008-03-28
Go here to find the alternate cd download
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/) It usually works if the live cd won't due to hardware conflicts.

---

### Post by miffin on 2008-03-28
Thanks.  I am downloading it now.  Have to go away for weekend soon so might not be able to try it yet.  But, will let you know how it goes as soon as pos.
Brian

---

### Post by stalkingwolf on 2008-03-28
It sounds like your gobblygook is the system checking your hardware.  It may not be freezing up.
Just taking a while to read certain things.  I know that when I loaded on my Dells it took a while
because it could not find a FDD.  Mine have swappable FDD and CD.

As all laptops ( or desktops for that matter) are not created equal it may just be taking a while to look for something that may or may not be there.  This is after all a good thing, the more it looks for and finds
the more likely it will just work.

---

### Post by miffin on 2008-03-28
Thanks for the info.  I will try it again and leave it on longer.  Although it was on for best part of 10 mins. I am also downloading the alternative.  However, I have got to go now for the weekend so will see what happens when I get back.
Bri

---

### Post by mjwhitfield on 2008-03-28
Use the Alt CD, I had the same issue on a Compaq laptop, after I installed from the AltCD it worked fine.

---

### Post by miffin on 2008-03-28
Thanks very much.  Look forward to trying it when I get home.
Bri

---

### Post by miffin on 2008-03-28
Thanks very much.  Look forward to trying it when I get home.
Bri

---

### Post by miffin on 2008-03-31
I am trying alt cd now.  It looks like it might work.  However, i chickened out when it got to the bit about partitioning the disk.  Could you tell me please, if I go all the way will I still be able to use Windows. The main reason being is that the disk could not find my network and until I can sort that out I need to use Windows as my network connection is vital to me.
Thanks
Brian

---

### Post by jakupl on 2008-03-31
heh yeah, the partitoning is pretty intimidating in the alternate cd :)

you can choose the guided partitioning where you keep windows. and yes, if you don't touch the "use full harddisk" or somthing like that, windows will probably be fine.

---

### Post by .nedberg on 2008-03-31
Should not bee a problem as long as you do NOT select "use entire disk" or something like that.

Use guided, resize.

---

### Post by jakupl on 2008-03-31
heh yeah, better clarify that :lolflag:

---

### Post by miffin on 2008-03-31
If I do that then, Will I get a choice of which system I wish to use at any time?

Brian

---

### Post by .nedberg on 2008-03-31
Yes, you will get a choice. The default will be Ubuntu, but that can be changed if you want something else.

---

### Post by jakupl on 2008-03-31
Everytime you turn on the computer, you will get 10 sec. to choose between the os you want. If you dont touch it, it will automatically load ubuntu :popcorn:

---

### Post by miffin on 2008-03-31
Thanks for the info.  But...... I have still chickened out for the moment.  When I got to the partitioning again it stated "this is irreversable" Is that correct?
Bri

---

### Post by .nedberg on 2008-03-31
Well, yes and no...

It is reversible, but it takes some work. I know because I just did it. It is not what you would normaly do, and hence the warning.

Nevertheless: I advise you to keep a good backup of the valuable stuff on your drive before you install. I have never experienced things to go wrong with the installer, but you never know...

---

### Post by jakupl on 2008-03-31
well yes and no... if you format anything... it is of course kinda unreversable... someone else probably explains it better than me...

but please, go for it. The windows **will** still be there if ubuntu goes bananas.

---

### Post by jakupl on 2008-03-31
HAHAHA :D  we started the reply EXACTLY the same, at exactly the same time :lolflag::guitar::popcorn:

[QUOTE=".nedberg"]Well, yes and no...[/QUOTE]
[QUOTE="jakupl"]well yes and no...[/QUOTE]

---

### Post by miffin on 2008-03-31
Thanks.  I think I will wait until tomorrow then so I can pluck up the courage.
Bri

---

### Post by jakupl on 2008-03-31
good luck :KS

---

### Post by .nedberg on 2008-04-01
You might want to take a look at this page. It has a screencast of the install proces with the alternative cd.

[http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2]("http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2")

Good luck!:popcorn:

---

### Post by raipe on 2008-04-01
I have exatly the same problem as miffin.

I have HP pavilion dv9005 laptop. And it should be working perfectly.

First I tried to install ubuntu-7.10-desktop-i386 and it freezed my computer. I cant understund what is the problem. I even tried mandriva and it freezed also in the same spot. Now I installed that alternate version and the install progress finished perfectly. I booted the computer and removed the cd ofcourse and now it freezes when loading! When that ubuntu logo appears its loading and after that only black screen and even capslock and numlock lights dont work.

Im losing my nerves..

Please help, any tips are welcome.

:confused:

---

### Post by jakupl on 2008-04-01
[QUOTE="raipe"]I have exatly the same problem as miffin.

I have HP pavilion dv9005 laptop. And it should be working perfectly.

First I tried to install ubuntu-7.10-desktop-i386 and it freezed my computer. I cant understund what is the problem. I even tried mandriva and it freezed also in the same spot. Now I installed that alternate version and the install progress finished perfectly. I booted the computer and removed the cd ofcourse and now it freezes when loading! When that ubuntu logo appears its loading and after that only black screen and even capslock and numlock lights dont work.

Im losing my nerves..

Please help, any tips are welcome.[/QUOTE]

heh :) this might seem like a stupid question, but first, have you tried to let it load for a really really long time? try that first :popcorn:

---

### Post by raipe on 2008-04-02
Yes well I have :)

I have left that loading over night about 8 hours, but It's just totally freezed and I can only press the power button 5secs so it will end..

](*,)

---

### Post by jakupl on 2008-04-02
then try some boot parameters,

the most common are:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791

try combining then, and individually.

see [_***here***_]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html") if you dont know how to change boot parameters

---

### Post by jakupl on 2008-04-02
maby 'hpet=disable' also

---

### Post by jakupl on 2008-04-02
try also "all_generic_ide" right before "quiet splash"

---

### Post by jakupl on 2008-04-02
I think I've got it!

try "apm=off noapic" and only that....

---

### Post by raipe on 2008-04-02
Oh my god! :)

IT'S WORKING!

I added that apm=off noapic and now this is really working!

Thank you so much!!! =D>

What did that line really do? I think I have to add it permanently now?



:guitar:

---

### Post by jakupl on 2008-04-02
in the terminal write:

```
gksudo gedit /boot/grub/menu.lst
```

at the bottom of the file, you will find this:
```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c98dfc78-177b-40f9-8013-6aea32a8c3d2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

add "apm=off noapic" after "splash"
like this:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c98dfc78-177b-40f9-8013-6aea32a8c3d2 ro quiet splash apm=off noapic
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

save and reboot.

this will probably not survive a system upgrade... so you probably have to do it again if you upgrade to "hardy".

you can also see [here]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html") to make it survive an upgrade.

glad it worked. youre welcome to press the thanks button ;) \\:D/ ------->

---

### Post by miffin on 2008-04-06
I have decided not to go ahead with my Ubuntu installation at the moment as it could not find my network. But, since I have tried the installation from the alt cd I cannot now type a h or g on my laptop.  Can anyone help me sort this please.
Bri

---

