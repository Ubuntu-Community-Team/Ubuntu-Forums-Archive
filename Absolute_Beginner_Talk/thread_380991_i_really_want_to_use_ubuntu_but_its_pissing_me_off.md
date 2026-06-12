---
title: "i really want to use ubuntu but its pissing me off !!"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by mitch707 on 2007-03-10
ok i have the ubuntu edgy AMD64 cd and it doenst work with my graphics card i tried installing the drivers and the other stuff but i get xserver failed blah blab blah and have done this many of times and ubuntu live cd used to work on my laptop perfectly but not it doesnt and i really want ubuntu on my desktop. All i see is a blank screen with a blinking cursor like this _

here are my specs (desktop) 
AMD 64 Venice 2.2 GHZ

MSI K81 SLI lite

2x 73OO LE nvidia cards 

200GB hard drive 

1 GB of RAM

---

### Post by taurus on 2007-03-10
Boot into recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default and use **vesa** as a driver for your graphic card.  Once you have X running again, you can then install nVidia driver for it.

Once you're done reconfigure X, reboot with

```
shutdown -r now
```

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by gameman12 on 2007-03-10
first off, NICE COMPUTER!!!!

second, you should try installing 32-bit onto ur 64-bit machine. i have read many times that 32-bit OS is wicked fast on 64-bit machines. 32-bit i believe is backwards compatable and has many more devices and programs that will work with it.

hope this helps

---

### Post by mitch707 on 2007-03-10
thanks i will see if it works and oh thanks i like my computer i have windows vista ultimate but i hate it so im switching to linux oh and it was the 32bit cd

---

### Post by mitch707 on 2007-03-10
wait ok super new to linux how do i boot into GRUB ?

---

### Post by gameman12 on 2007-03-10
u installed it onto ur 200gb harddrive correct? if that is than it is in windows' mbr (master boot record) which means that when you turn on the commputer ur bios should run, then grub should start.

---

### Post by taurus on 2007-03-10
When you reboot, you would see a logo of your mobo and whatnot.  Then, you will get to GRUB screen (you should see the word GRUB somewhere on the screen) where you have three seconds to press Esc key to see the menu.  That's your GRUB.

---

### Post by gameman12 on 2007-03-10
my posts are competeing with a staff member, so i'm gonna stop posting 'cause i know i'm gonna be wrong. :lolflag: 

good luck with ubuntu :guitar:

---

### Post by mitch707 on 2007-03-10
no its not on my HD i cant use the live CD its has no  kind of GUI or graphical interface all  can get is the command pormpt at that screen thats all black with a _

---

### Post by mitch707 on 2007-03-10
thanks i hope i do to

---

### Post by bulldog on 2007-03-10
> **mitch707 said:**
> no its not on my HD i cant use the live CD its has no  kind of GUI or graphical interface all  can get is the command pormpt at that screen thats all black with a _

When ubuntu isn't installed,you can't install your graphics driver :) 
Try the 'alternate install cd' which has a text based installer and no graphical interface.

---

### Post by ragadanga63 on 2007-03-10
wowww!! real time Q&A!  Ubuntu community rocks!

---

