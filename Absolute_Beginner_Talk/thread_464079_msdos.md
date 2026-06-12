---
title: "msdos"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by pickle521 on 2007-06-04
how can i install ubuntu when my comp is in msdos mode

---

### Post by Bachstelze on 2007-06-04
What do you mean "MS-DOS mode" ?

---

### Post by ltk5 on 2007-06-04
if you're trying to run x type: startx

---

### Post by taurus on 2007-06-04
Did you somehow manage to install the server version instead of the desktop version?

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by Chayak on 2007-06-04
Pickle you're beating a dead horse.  There has been numerous replies to your [other thread]("http://ubuntuforums.org/showthread.php?t=463498&highlight=pickle521") about what you need to do to install to your laptop.  Unless your situation has magically changed you have the exact same issue and everyone has already given you the solution in the other thread.  Have a tech reset your bios to clear the password so you can have the laptop boot off of CD-ROM

---

### Post by Siph0n on 2007-06-04
lol why is everyone giving pickle ubuntu commands when he said he's in MS-DOS mode? :) To install ubuntu, put the install cd in, reboot, and have the bios boot from cd... That'll get you started!!! :)

Siph0n

---

### Post by oilchangeguy on 2007-06-04
> **Siph0n said:**
> lol why is everyone giving pickle ubuntu commands when he said he's in MS-DOS mode? :) To install ubuntu, put the install cd in, reboot, and have the bios boot from cd... That'll get you started!!! :)

Siph0n

read this:
[http://ubuntuforums.org/showthread.php?t=463498&highlight=pickle521](http://ubuntuforums.org/showthread.php?t=463498&highlight=pickle521)
let's not let this thread get carried away like his other thread. there's no need in it.

---

### Post by Siph0n on 2007-06-04
Ok, I just told him how to install ubuntu like he asked... hope it helped! :)

Siph0n

---

### Post by oilchangeguy on 2007-06-04
> **Siph0n said:**
> Ok, I just told him how to install ubuntu like he asked... hope it helped! :)

Siph0n

he's already been told. many, many times.

---

### Post by pickle521 on 2007-06-04
ok guys my other thread was about bios but this one is installing it. i have the cd and i can boot from a cd but my comp doesnt have an os so im trying to install ubuntu but i dont no what file to run in ms dos

---

### Post by oilchangeguy on 2007-06-04
> **pickle521 said:**
> ok guys my other thread was about bios but this one is installing it. i have the cd and i can boot from a cd but my comp doesnt have an os so im trying to install ubuntu but i dont no what file to run in ms dos

what cd do you have? and where did you get it? your computer does not have dos. dos is an old operating system.

---

### Post by Ink-Jet on 2007-06-04
If you have the C.D, and can boot from it, just put it in your C.D drive, and then re-start your computer. It should boot from the C.D, and you should have Ubuntu running.

---

### Post by pickle521 on 2007-06-04
i got my cd from the ubuntu website it is 7.04 and when i turn on my comp i can like chose a drive and enter dir and it gives the contents of the drive

---

### Post by pickle521 on 2007-06-04
o i forgot this in my last reply when i try to run start.exe it says cannot run in dos mode

---

### Post by oilchangeguy on 2007-06-04
you might want to read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by pickle521 on 2007-06-04
i didnt burn my cd tho

---

### Post by oilchangeguy on 2007-06-04
> **pickle521 said:**
> i didnt burn my cd tho

who did?

---

### Post by pickle521 on 2007-06-04
no one i got ubuntu to mail it to me

---

### Post by oilchangeguy on 2007-06-04
> **pickle521 said:**
> no one i got ubuntu to mail it to me

ok, this is not real hard. if the bios has been set to boot from the cd drive, you put the cd in the drive reboot the computer, and you should see ubuntu start to load, and be given the option to start/install.

---

### Post by pickle521 on 2007-06-04
im trying to google a way to boot from a cd using a floppy because im not driving 2 hours to get my bios settings reset

---

### Post by Campingman on 2007-06-04
Great threads, enjoyed them both:
Just a guess but ........
I reckon you need to get the bios reset!

---

### Post by Nekiruhs on 2007-06-04
Just go get the BIOS reset. You cant install from in DOS. The computer has to boot from CD.

---

### Post by Chayak on 2007-06-04
So... now you're admitting that it's the exact same problem as your other thread.  There is a way to install without the CD which is to go through a PXE boot but guess what! You have to set it up in the BIOS.  In short, suck it up and get the BIOS reset.

---

### Post by Calash on 2007-06-04
If you are getting an MS-DOS prompt then you are NOT booting from the CD.  Assuming the CD is in the drive and you CD Drive is working then you need to set the boot order to tell it to boot from CD.  A make and model of the system would help...some allow you to press the F12 key during start up and get a list of available boot devices.

Worst case you will have to go into your BIOS and adjust the boot order.  Reading some of the other replies here leads me to believe his will be an issue, but it may be the only way outside of making your HD not a boot device......not a good idea IMHO.

---

### Post by louieb on 2007-06-04
> **pickle521 said:**
> im trying to google a way to boot from a cd using a floppy because im not driving 2 hours to get my bios settings reset
one boot floppy coming up [Nuts on Smart Boot Manager]("http://louboldt.com/ilinuxsbm.htm")

---

### Post by Bluecircle on 2007-06-04
open your desktop case

move the jumper over on the motherboard to clear the bios setings

put the jumper back to normal



Here are the procedures if the jumpers are present on the motherboard:

    *

      Locate, if possible, the instruction booklet for your motherboard.
    *

      Shut down your computer and disconnect the power plug.
    *

      Now identify where the jumpers are located, then check the present pin location and the location of the jumper on those pins to determine their default location. Tthe default location on the motherboard is to have the jumper across pins #1 and #2.
    *

      Next, move the jumpers from the their default location (Example: from across pins #1 and #2 as above) and then place the jumper across pins #2 and #3.
    *

      Leave the jumper in place for 20 to 30 seconds and then return it to its default location.
    *

      Now plug the power cord back in and restart the computer.
    



go into the now non-password rotected bios

change the boot order so that the cd drive is first

save and quit

put in the ubuntu cd

restart

the ubuntu cd should now begin to load

also:


At times, and without any obvious reason, static discharges as well as other electrical problems can cause the PROM on the motherboard to reset the Bios (CMOS) to its default values and even cause the default Bios password to be set. These are some of the default Bios passwords used with different Bios's, give them a try first.

    * AMI
    * Award
    * bios
    * setup
    * cmos 
    * concat
    * AMI_SW (case sensitive)
    * AMI!SW/
    * AMI?SW/
    * j262




for more information, read your computer's manual on resetting the bios, also use google

if it is a laptop or none of this works, try CmosPwd:

[http://www.cgsecurity.org/wiki/CmosPwd](http://www.cgsecurity.org/wiki/CmosPwd)

---

### Post by pickle521 on 2007-06-04
thanks louieb im installing ubuntu 7.04 right now. oilchangeguy now i can stop buggin u with these threads lol

---

### Post by pickle521 on 2007-06-04
i have one last question it has this little rectangle in the middle of the screen with ubuntu in it and 3 little pictures in the corner what do i do now

---

### Post by Nekiruhs on 2007-06-04
> **pickle521 said:**
> i have one last question it has this little rectangle in the middle of the screen with ubuntu in it and 3 little pictures in the corner what do i do now
Thats called the splash screen, just wait, its loading...

---

### Post by pickle521 on 2007-06-05
can i still install it if i hit start ubuntu in graphics safe mode

---

### Post by Bluecircle on 2007-06-06
ummm... I think you're doing something very wrong? Give us some screenshots or something.

---

### Post by Haus Neuerburg on 2007-06-06
@Bluecircle: really? Because that was the only way my dinosaur comp could display the live CD w/o your eyes getting mad from the monitor flimmering? Installation wud have been poss though, if only the RAM wud have been sufficient ;-) (the alternate CD saved me eventually)

---

