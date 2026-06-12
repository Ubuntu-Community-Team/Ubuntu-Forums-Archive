---
title: "Windows continues to haunt me! need help."
date: 2011-10-28
forum: Any Other OS
---

### Post by pierreyy on 2011-10-28
hey guys my cousin gave me a mini 7 inch netbook (form china) to fix.

 it currently has windows ce on it ( horrible) 

 the problem:

   when it boots an error screen pops up as it starts up  the error says:

Fatal Application Error 

Application services.exe has performed an illegal operation and will be shutdown. If the problem persists, contact the program vendor

program: services.exe
exception: 0xC000001C
adress :880A4D28


     the keyboard and touchpad are not responding and any peripherals are also inoperable...

i want to install android on it ( saw it on youtube:P) 

   does anyone have a clue what to do... thanks in advance!


ive tried anything i could think of.... does anyone have an idea because i dont

---

### Post by Luc André on 2011-10-28
When the netbook boots, does the keyboard work so you can access the BIOS?

---

### Post by 2F4U on 2011-10-28
If you want to install a different OS why boot into Windows? Anyways, maybe there is a virus on the machine or the installation is corrupt. Did you already try to boot a liveCD and see if that works? That way you could at least check whether there are hardware problems.

---

### Post by Paqman on 2011-10-28
Sounds like it's got an ARM processor, that's going to limit your options a bit. Android might work, otherwise Debian supports ARM, and there's a semi-official version of Ubuntu for ARM now, but it's certainly not guaranteed to support your exact hardware.

Can you tell us more about the machine? Model number?

---

### Post by pierreyy on 2011-10-28
> **Luc André said:**
> When the netbook boots, does the keyboard work so you can access the BIOS?

nope... plus i dont think wince has a bios... the os is locked but i found smthn online, a guy figured out a way to remove wince and install android instead. thank you for the quick reply!

---

### Post by pierreyy on 2011-10-28
> **2F4U said:**
> If you want to install a different OS why boot into Windows? Anyways, maybe there is a virus on the machine or the installation is corrupt. Did you already try to boot a liveCD and see if that works? That way you could at least check whether there are hardware problems.

it doesnt have a cd input  :P... google seasrch easy pc 7 inch mini netbook....thanks for the quick reply!

---

### Post by pierreyy on 2011-10-28
> **Paqman said:**
> Sounds like it's got an ARM processor, that's going to limit your options a bit. Android might work, otherwise Debian supports ARM, and there's a semi-official version of Ubuntu for ARM now, but it's certainly not guaranteed to support your exact hardware.

Can you tell us more about the machine? Model number?

- it is an ARM processor
-then ill try different os... it says on a tag in the back:

   easy pc e70001

 manufacturer: sungworld
XBARM 
7winch 
1GB 
wifi
bt
1yr 

thanks for the quick reply!

---

### Post by gandaran on 2011-10-28
> 
it currently has windows ce on it ( horrible) 

the problem:

when it boots an error screen pops up as it starts up the error says:
if it's not possible to install android/ubuntu on the netbook cant you reset the windows CE to factory settings like any other windows mobile OS?

---

### Post by pierreyy on 2011-10-28
> **gandaran said:**
> if it's not possible to install android/ubuntu on the netbook cant you reset the windows CE to factory settings like any other windows mobile OS?
  

 it has been done...thats why i thought id go in that direction

---

### Post by pierreyy on 2011-10-28
> **gandaran said:**
> if it's not possible to install android/ubuntu on the netbook cant you reset the windows CE to factory settings like any other windows mobile OS?
  

 it has been done...thats why i thought id go in that direction, i dunno if i can reset the os... either way i want widows out of there:P

---

### Post by pierreyy on 2011-10-28
can i just boot into another OS and install it afterwards? i really need help on this thing,,, thanks in advance

---

### Post by mips on 2011-10-29
Maybe try asking in some Android forums.

Also have a look at NetBSD which runs on almost anything under the sun including toasters.
[http://www.netbsd.org/](http://www.netbsd.org/)

---

### Post by pierreyy on 2011-10-30
> **mips said:**
> Maybe try asking in some Android forums.

Also have a look at NetBSD which runs on almost anything under the sun including toasters.
[http://www.netbsd.org/](http://www.netbsd.org/)

cool... im researching what os to run on it but the main problem is that Windows CE in embedded in the computer.... is there a way i can format the disk inside it and reinstall another OS?

---

### Post by mips on 2011-10-30
Yes, there must be a way.

---

### Post by kurt18947 on 2011-10-30
> **pierreyy said:**
> cool... im researching what os to run on it but the main problem is that Windows CE in embedded in the computer.... is there a way i can format the disk inside it and reinstall another OS?

It depends on whether WindowsCE is embedded on a ROM, EEPROM or some sort of flash disk.  ROM cannot be written to, only replaced - maybe - if it's not soldered in place. EEPROM - **E**lectrically **E**rasable **P**rogrammable **R**ead-**O**nly **M**emory - can possibly be erased and rewritten if you can find the magic incantations.

---

### Post by pierreyy on 2011-10-30
i dont have it with me right now but i was just thinking the same thing... im gunna go home take the thing apart and ill get back to you guys.... i hope its not soldered on then i can just tacke it out, format it, install another os on it and put it back in right??could that be a problem?

---

### Post by mips on 2011-10-30
I suspect you would have bootloader issues. You need to do some research.

---

### Post by pierreyy on 2011-10-30
if i partition it and install another os on it would that be okay?

---

### Post by pierreyy on 2011-10-30
i have no idea how to open this thing up and i rather if i didnt break it:P... any other ideas guys cz im all out ?

---

### Post by PhilGil on 2011-10-30
Knock yourself out: [http://ubuntuforums.org/showthread.php?t=1349626](http://ubuntuforums.org/showthread.php?t=1349626)

I didn't follow the thread closely, so I have no idea whether anyone ever successfully flashed a new OS to one of these devices.

---

### Post by pierreyy on 2011-10-31
wow what a thread... i read something about flashing it in order to make it boot in safemode or whatever... can someone help me out with that ? i really need this to work thanks in advance guys!

---

### Post by skumara on 2011-11-01
can you connect it to desktop with windows and try accessing it through desktop?

---

### Post by pierreyy on 2011-11-01
i dunno which cable to use where to connect them and all... if you can help me ill try ... thnx

---

### Post by skumara on 2011-11-01
do you any usb port in the device?

---

### Post by jl2 on 2011-11-04
get a SD card.
make part 1 dos, part 2 ext2 or ext3
download the tar file put together by abrasive.
unpack in the dos part ( i.e. part1)
you will have one directory called script.
insert card
The SD card M*U*S*T be R/W
power on.
Away you go. It is Debian. Droid is going to be slow on an 8505.
I also have a droid top and I much prefer my debian top. 

here is where you score the tar file
[http://www.projectgus.com/files/abrasive_mirror/wm8505_linux/](http://www.projectgus.com/files/abrasive_mirror/wm8505_linux/)
READ the other thread it is educational.
Here is one of many, many places that describe the installation process.

[http://blog.chinaunix.net/space.php?uid=23225855&do=blog&id=1992198](http://blog.chinaunix.net/space.php?uid=23225855&do=blog&id=1992198)

DO NOT mess with the inbuilt flash.

---

### Post by pierreyy on 2011-11-05
i tried it out ... i think there is smthn im overlooking with the bootloader when i plug the sd card in the netbook continues to boot into wince as if no peripheral device was inserted however if i push the "reset" button located on the bottom twice ( yes i has a reset button:P) it seems to boot into some screen saying that the sd card is not an upgrade image then it just stays on that screen until i reboot it... i seem to have no control over the touchpad or the keyboard, maybe what i have is an 8500 not an 8505 is there anyother way i can do this.... how can i change the name of this thread? thanks for the support guys! looking forward to running debian on the fucker :P

---

### Post by pierreyy on 2011-11-05
> **skumara said:**
> do you any usb port in the device?

yes i does it has 3 usb ports and 1 sd card reader, an ethernet plug  and in/out jacks why do you ask?

---

### Post by skumara on 2011-11-05
[http://blog.chinaunix.net/space.php?uid=23225855&do=blog&id=1992198](http://blog.chinaunix.net/space.php?uid=23225855&do=blog&id=1992198)


have try the other images in that thread?

---

