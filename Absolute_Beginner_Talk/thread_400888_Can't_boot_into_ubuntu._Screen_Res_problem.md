---
title: "Can't boot into ubuntu. Screen Res problem"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Richard777 on 2007-04-04
i can't boot into ubuntu. iv'e tried the recovery thing, and nothing but lines of words roll down and then stop. i can't even type anything in. if i boot into normal ubuntu my screen says to set the resolution to 1240X1024.

Iv'e also got vista installed on another hard drive btw. and it boot selection is in grub.

i'm **NEW** to ubuntu and from what iv'e seen i think it kills vista so much "worked on" aero's. i'd hate to *hate* ubuntu because of sumthing so small like this.

much appreciated to whoever replys and helps me..

---

### Post by amohanty on 2007-04-04
Can you post the exact error message?

Also what do you mean when you say your screen says 'set the resolution to 1240x1024'?

Can you get to the login window?

AM

---

### Post by Richard777 on 2007-04-04
> **amohanty said:**
> Can you post the exact error message?

Also what do you mean when you say your screen says 'set the resolution to 1240x1024'?

Can you get to the login window?

AM
there ithanx for replying. 

i boot up. my screen tells me to set resolution 1240X1024. and thats all i see

i can't get into the login window either.

iv'e never used ubuntu b4 so i don't know what to d

---

### Post by ndefontenay on 2007-04-04
Hi,

can you give more information on your hardware?

Graphical card, screen, is it laptop or PC?

There is plenty of information out there concerning screen resolution problem. Your answer might already exist but we would need to know more about your PC.

Thanks.

In any case, I've found one which talks about screen resolution... We never know.

[http://ubuntuforums.org/showthread.php?t=351647&highlight=915resolution](http://ubuntuforums.org/showthread.php?t=351647&highlight=915resolution)

Give more detail. You'll have more help.

---

### Post by amohanty on 2007-04-04
Ok when you drop into the recovery console from GRUB, wait till all the text scrolls down and you are at the login prompt.

Enter your username and password there.
THen at the command prompt, type **startx**

Now if it fails, post you will drop back to the command prompt. There type the followin:
**cat /var/log/Xorg.0.log | grep EE**
and post the output.

AM

---

### Post by Richard777 on 2007-04-04
my graphics card is a x300ati , screen is 19 inch philips 190S5, and it's a PC

---

### Post by amohanty on 2007-04-04
I have a couple of X300s so it should work. Also th 190S has 1280x1024 as the max allowable res.

Also before you do the **startx** Try the following:
**sudo dpkg-reconfigure xserver-xorg**

Click throught everything, and reboot.

See if that works.
AM

---

### Post by Richard777 on 2007-04-04
ok. what is meant to happen when u go into recovery console. cuz i'm sure what going on with it- is not whats meant to happen

---

### Post by amohanty on 2007-04-04
You should just get a login prompt. 

login:

Or
Something that may look like (if you used ESC at the grub menu)
username@host:~$

AM

---

### Post by Richard777 on 2007-04-04
> **amohanty said:**
> You should just get a login prompt. 

login:

Or
Something that may look like (if you used ESC at the grub menu)
username@host:~$

AM
ok i get this when i get into recovery console

/bin/sh : Can't access tty; job control turned off (init * something* ) [17179576. 160000] Usb 1-2 : device now accepting address 2, error -71


and when i go to normal ubuntu boot and press c for command and then run

 cat /var/log/Xorg.0.log | grep EE

i get error 15. File not found



again, i still havn't even used ubuntu on my computer.

---

### Post by Feba on 2007-04-04
Boot ubuntu normally, then when the monitor blacks out press CTRL+ALT+F4. Try to proceed from there according to the recovery instructions above.

---

### Post by amohanty on 2007-04-04
> /bin/sh : Can't access tty; job control turned off (init * something* )
Oh crap! Search for '/bin/sh : Can't access tty; job control turned off' this in the forums and you will find out why I said that. 
[http://ubuntuforums.org/gsearch.php?domains=ubuntuforums.org&q=%2Fbin%2Fsh+%3A+Can%27t+access+tty%3B+job+control+turned+off&sa=Google+Search&sitesearch=&sitesearch=ubuntuforums.org&client=pub-9806935032004241&forid=1&channel=4258035119&ie=ISO-8859-1&oe=ISO-8859-1&safe=active&cof=GALT%3A%23656565%3BGL%3A1%3BDIV%3A%23FFFFFF%3BVLC%3A656565%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3AFFFFFF%3BALC%3AC00000%3BLC%3AC00000%3BT%3A000000%3BGFNT%3A656565%3BGIMP%3A656565%3BLH%3A50%3BLW%3A184%3BL%3Ahttp%3A%2F%2Fubuntuforums.org%2Fimagesorig%2Fub2%2Fubuntulogo.png%3BS%3Ahttp%3A%2F%2Fubuntuforums.org%3BFORID%3A11&hl=en](http://ubuntuforums.org/gsearch.php?domains=ubuntuforums.org&q=%2Fbin%2Fsh+%3A+Can%27t+access+tty%3B+job+control+turned+off&sa=Google+Search&sitesearch=&sitesearch=ubuntuforums.org&client=pub-9806935032004241&forid=1&channel=4258035119&ie=ISO-8859-1&oe=ISO-8859-1&safe=active&cof=GALT%3A%23656565%3BGL%3A1%3BDIV%3A%23FFFFFF%3BVLC%3A656565%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3AFFFFFF%3BALC%3AC00000%3BLC%3AC00000%3BT%3A000000%3BGFNT%3A656565%3BGIMP%3A656565%3BLH%3A50%3BLW%3A184%3BL%3Ahttp%3A%2F%2Fubuntuforums.org%2Fimagesorig%2Fub2%2Fubuntulogo.png%3BS%3Ahttp%3A%2F%2Fubuntuforums.org%3BFORID%3A11&hl=en)

try a reinstall from an 'alternate' cd and hope for the best. Its possible, there is some critical peice of hardware that is not supported or that grub points to the wrong partition, or the install cd was bad, or a whole bunch of things.

HTH
AM

---

### Post by Richard777 on 2007-04-04
..i was hoping it wasn't gonna end up with u saying that GAH..... ok i'll try a reinstall. thanx man lol.

---

### Post by Richard777 on 2007-04-04
> **amohanty said:**
> Oh crap! Search for '/bin/sh : Can't access tty; job control turned off' this in the forums and you will find out why I said that. 
[http://ubuntuforums.org/gsearch.php?domains=ubuntuforums.org&q=%2Fbin%2Fsh+%3A+Can%27t+access+tty%3B+job+control+turned+off&sa=Google+Search&sitesearch=&sitesearch=ubuntuforums.org&client=pub-9806935032004241&forid=1&channel=4258035119&ie=ISO-8859-1&oe=ISO-8859-1&safe=active&cof=GALT%3A%23656565%3BGL%3A1%3BDIV%3A%23FFFFFF%3BVLC%3A656565%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3AFFFFFF%3BALC%3AC00000%3BLC%3AC00000%3BT%3A000000%3BGFNT%3A656565%3BGIMP%3A656565%3BLH%3A50%3BLW%3A184%3BL%3Ahttp%3A%2F%2Fubuntuforums.org%2Fimagesorig%2Fub2%2Fubuntulogo.png%3BS%3Ahttp%3A%2F%2Fubuntuforums.org%3BFORID%3A11&hl=en](http://ubuntuforums.org/gsearch.php?domains=ubuntuforums.org&q=%2Fbin%2Fsh+%3A+Can%27t+access+tty%3B+job+control+turned+off&sa=Google+Search&sitesearch=&sitesearch=ubuntuforums.org&client=pub-9806935032004241&forid=1&channel=4258035119&ie=ISO-8859-1&oe=ISO-8859-1&safe=active&cof=GALT%3A%23656565%3BGL%3A1%3BDIV%3A%23FFFFFF%3BVLC%3A656565%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3AFFFFFF%3BALC%3AC00000%3BLC%3AC00000%3BT%3A000000%3BGFNT%3A656565%3BGIMP%3A656565%3BLH%3A50%3BLW%3A184%3BL%3Ahttp%3A%2F%2Fubuntuforums.org%2Fimagesorig%2Fub2%2Fubuntulogo.png%3BS%3Ahttp%3A%2F%2Fubuntuforums.org%3BFORID%3A11&hl=en)

try a reinstall from an 'alternate' cd and hope for the best. Its possible, there is some critical peice of hardware that is not supported or that grub points to the wrong partition, or the install cd was bad, or a whole bunch of things.

HTH
AM
OHHH ...thats what i used. alternate cd btw. how do i know if grub is pointing to the right partition . btw ubuntu is installed on my seond sata hard drive

---

### Post by amohanty on 2007-04-04
post the contents of /boot/grub/menu.lst

AM

---

