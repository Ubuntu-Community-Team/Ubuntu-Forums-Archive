---
title: "need to install program without internet"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by mrpresident on 2006-12-29
my wireless card (bcm4306 chipset) does not work in ubuntu.

i read that i need to extract the firmware and then it will work. bcm43xx-fwcutter is apparently the program that will do this. so i am suppossed to use the following command.
```
sudo apt-get install bcm43xx-fwcutter
```

problem is i dont have wired internet access so the above command wont work for me. so using windows i went online and downlaoded the program "bcm43xx-fwcutter-006.tar.bz2" from the bcm43xx team website. when i extract the files they end in .c or .h extensions.

is there anyway i can use the program i downloaded and install it from ubuntu i.e. without apt get or going online.  seems kind of stupid to me that to make my internet work i have to install a program that needs to be downloaded from the internet.

BTW when i use ndiswrapper and my windows driver it says error on line 144 or something.

---

### Post by teaker1s on 2006-12-29
don't waste your time with bcm43xx-fwcutter  as its crappy 12mb/s use this [howto ]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")
for 54mbs

burn deb packages to cd or you will need ubuntu alternate iso and

sudo apt-cdrom add

apt-get update

you can now install without internet access

---

### Post by bluedeer on 2006-12-29
I know you already mentioned trying ndiswrapper, but if you decide to give that another try, check out the instructions in [this thread by deathbyswiftwind]("http://www.ubuntuforums.org/showthread.php?t=189070").  That thread specifically mentions the 4306, and we used that to set up both of our laptops (which obviously both have Broadcom 4306 cards) without any problems.  We had to do this a second time after later having to format one of the laptops - not related to networking in any way, btw - and those instructions worked as well as they had the first time.

We had tried to use the fwcutter program and couldn't get it to work, but we haven't had any problems with ndiswrapper and the bcmwl5 drivers.  If you need to get the drivers or the gui - mentioned in 4th post in that thread - you could always log in to Windows and put them on a USB flash drive or CD.  I also copied his instructions into a text file and put it on the USB drive with the drivers and gui.

(If you decide to follow the thread linked above, make sure to do what he says at the end...re-modprobe ndiswrapper after the first restart, and then add ndiswrapper to /etc/modules/.)

We were practically banging our heads against the wall for several hours trying to get wireless to work before we found that post.  ](*,)

---

### Post by mrpresident on 2006-12-29
thank you very much for the reply.
im gonna read through the link and try it now. but i notice that it is for bcm4311 and i have the bcm4306 (rev3) chipset. is that going to be a problem?

EDIT: @bluedeer, thanks for the reply. yes i will give ndiswrapper another go first.
ill let u guys now how it goes.

---

### Post by teaker1s on 2006-12-29
should work you will just need to extract the correct windows inf driver for your card from driver cd

---

### Post by mrpresident on 2006-12-29
i just reinstalled ubuntu and started goigng through the guide that Bluedeer linked to. when i enter ```
sudo modprobe ndiswrapper
``` it returns ```
FATAL: error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

this is on a completely fresh install aswell.
[B][U]

EDIT: just found this...[/U][/B]

If you get an error saying 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument 

then try this.

```

sudo apt-get install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper 
```

but then i get an error message saying:```

target '/usr/sbin/ndiswrapper' is not a directory
```

(isnt this because the 2nd line deletes the directory tho??)

EDIT #2
im  an idiot. i typed the ln command in wrong.

[B]WOOOOOOOOOOT got my internet working.
couldnt have done it without u guys tho, thank you, i really appreciate your help.[/B]

---

### Post by teaker1s on 2006-12-29
\\:D/ ubuntu is great

---

### Post by bluedeer on 2006-12-29
Way to go...glad everything worked out!  8-)

---

