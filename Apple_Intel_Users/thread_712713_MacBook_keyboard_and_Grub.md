---
title: "MacBook keyboard and Grub"
date: 2008-03-02
forum: Apple Intel Users
---

### Post by Derktoon on 2008-03-02
ok so my question is this....

I installed Ubuntu and Windows on my macbook. (totally nuking OS X) so naturally when i hold down option on the keyboard all i get is windows, selecting that gets me to grub, where my keyboard aparently doesnt work...

so is there a way to put Ubuntu into the same boot menu (thingy) that would display OS X and windows...does that make any kind of sense?

---

### Post by timjayko on 2008-03-02
I would not nuke mac os x if I were you.. its great booting between two unix systems.. and windows if you need to game too

dont trust windows on your macbook.. I had it on mine for a good 5 months, then all of a sudden the keyboard stopped working in it.. windows is a sack of crap

step 1: reinstall mac os x on your macbook.. 

step 2: go here [http://refit.sourceforge.net/]("http://refit.sourceforge.net/")
           download this 

done.. now when you turn on your macbook it will take you to a menu right off the bat to choose between mac os x and other operating systems installed on your harddrive

---

### Post by cyberdork33 on 2008-03-02
yea you want refit. And a firmware update will fix that keyboard problem (which requires OSX).

---

### Post by ronocdh on 2008-03-02
To get the firmware update, you absolutely need OS X, as cyberdork said. So reinstall with OS X and use the system updates there.

If you really don't plan on using OS X at all, you can pare down the installation to just the essentials, substantially reducing the size of the installation, freeing up more space for Ubuntu. Once you have the firmware updates, you can go ahead and nuke OS X again if you really want, but what about when new firmware upgrades come along? I'd recommend keeping the OS X install there in reserve, and using rEFIt, which you can configure to boot into Ubuntu by default.

---

### Post by cyberdork33 on 2008-03-02
you can also install OS X on an external drive and boot from there when you need to.

---

### Post by qiepenguin on 2008-03-06
What is the firmware update that fixes the keyboard problem?  I was able to find "Keyboard Firmware Update 1.0" but it requires Leopard, which I do not have (I'm in Tiger 10.4.6 on a macbook from July 2007).

---

### Post by cyberdork33 on 2008-03-06
> **qiepenguin said:**
> What is the firmware update that fixes the keyboard problem?  I was able to find "Keyboard Firmware Update 1.0" but it requires Leopard, which I do not have (I'm in Tiger 10.4.6 on a macbook from July 2007).It is a firmware update for your machine (i.e. EFI) not keyboard firmware. If you run Software update, you should get it.

---

### Post by qiepenguin on 2008-03-11
> **cyberdork33 said:**
> It is a firmware update for your machine (i.e. EFI) not keyboard firmware. If you run Software update, you should get it.

Thanks, worked like a charm.

---

### Post by mabovo on 2008-03-11
Btw, what's Ubuntu version have You installed ?

I have same MacBook with Hardy and OsX 10.4 working pretty well.

---

