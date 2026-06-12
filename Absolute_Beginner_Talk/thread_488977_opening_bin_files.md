---
title: "opening bin files"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-06-30
how do i open a bin file and install it it is a firmware the instruction is here
```
Original RPC-2 Firmware version BYS3 for the SONY DVD RW DW-D22A



Flash in Windows using "LtnFW"



If the drive is not detected after a misflash, then flash in DOS with mtkflash (1.69 or higher)

Use this command: "mtkflash # w /b BYS3.bin"

Where # is replaced by one of the following numbers:

1 - Primary Master

2 - Primary Slave

3 - Secondary Master

4 - Secondary Slave



If using mtkflash 1.80.1, then do not include the "/b" flag. Use this command: "mtkflash # w BYS3.bin"







Downloaded from dhc014.rpc1.org
```
but i have no idea how to install it can someone help me plz

---

### Post by nanotube on 2007-06-30
well, if they don't have a firmware flashing tool for linux, then you have to do it in win... the .bin file is the firmware itself, but you have to have the software that will actually flash it onto your hardware.

---

### Post by cogadh on 2007-06-30
And before anyone suggests it, **do not** try using Wine to run a Windows-based firmware flash utility, it will not be pretty.

---

### Post by zerobinary on 2007-06-30
but then how do i flash it 
???
try this MtkWinFlash already still no goal 
plz help me

---

### Post by cogadh on 2007-06-30
If you don't have a Windows installation to run the firmware flash from, then check to see if the manufacturer has a bootable floppy disk method.

Is there a particular reason you need to flash your firmware? Unless it corrects a particular problem you are having, it is generally not necessary.

---

### Post by zerobinary on 2007-06-30
i need it badly otherwise i can't burn dvd -r for my burner

---

### Post by cogadh on 2007-06-30
What drive model do you have?

---

### Post by zerobinary on 2007-06-30
Sony Dvd Rw Dw-d22a

---

### Post by cogadh on 2007-06-30
I have noticed that you have two other threads on this issue. In the future, you should only post a single thread per problem, otherwise all of the troubleshooting is spread out too much and none of us who try to help you have all of the necessary information. It seems that there is more info in [this thread]("http://ubuntuforums.org/showthread.php?t=488228") on the issue, so I will move my responses over there.

---

### Post by zerobinary on 2007-06-30
na i start two thread because on e is dead no one goes thre 
second i start it so i t can grab people's attention and hopefully they help 
me since new thread is on the top people tend to not click on next page lol

---

