---
title: "Live DVD doesn't boot"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by squimmy on 2007-03-18
Hi,

I'm trying to boot the Ubuntu live CD, but it freezes with the orange loading bar - like thing. The bar scrolls near to the end and just plain freezes. I have no information beyond that, because it doesn't spit out any information.

My exact comp can be found here: [http://www.ciao.co.uk/Compaq_Presario_SR1519UK__6365040]("http://www.ciao.co.uk/Compaq_Presario_SR1519UK__6365040")
But, i've added an extra: Ethernet card, graphics card (ATi X800 GTO2) and an extra HDD.

Ubuntu is the *only* linux distro which I've found not to boot on my comp, it's very odd.

Thanks.

---

### Post by gh0st on 2007-03-18
I know this seems a bit obvious so apologies if you've done it already ;)
 
Did you try checking that the disc is ok with the option on the Live CD menu, could it be a faulty disc? Worth a look if you haven't checked it. Might not be any help, just thought I'd mention it.

---

### Post by squimmy on 2007-03-18
Yes i've done that, and also done a verify after I initially burnt it. The disc is not to blame.

---

### Post by Jose Catre-Vandis on 2007-03-18
From the sound of it, the CD is booting, but not loading up.

Is it a Dapper 6.06 LTS Live CD? I know this has some problems loading/running installing on some hardware?
Edgy does a better job at this.


Also, try removing your added hardware and see if it will load up OK then. If successful, add back hardware one at a time, til it fails??

At least you could then carryo ut an installation and then add the hardware and go from there?

---

### Post by squimmy on 2007-03-18
I'm using 6.10

I'm really not willing to start messing with hardware, I know the box is compatible with linux. Are there any switches I can pass to see what is happening when the DVD boots so I can see where it is hanging? Then I can work from there.

---

### Post by squimmy on 2007-03-18
Bumpidy bump

---

### Post by louieb on 2007-03-18
Heres a bunch you can try:
Ubuntu cheat codes here [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
or for difficult hardware
Knoppix cheat codes here  [http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
most of these work with Debian based disrtros too.

---

### Post by squimmy on 2007-03-19
Amazing, no verbose mode. How do people debug problems with the Live Cd if there is no verbose mode? I refuse to believe i'm the only one who has ever experienced a problem with the live cd.

I've got nothing to work on as all other linux distro's at least boot. Ubuntu is the only one having this problem.

EDIT:: Yay, managed to see what was happening by pressing F6 and removing the switches "quiet" and "splash". Well, it didn't really help and the last line being displayed is something to do with my HDD. What appears can be seen here:
[URL="http://xs413.xs.to/xs413/07121/DSC00006_wibble.JPG"]
[COLOR="Blue"]http://xs413.xs.to/xs413/07121/DSC00006_wibble.JPG[/COLOR][/URL]

Please help, Thanks!

---

### Post by squimmy on 2007-03-19
I've managed to get somewhat further by noprobing hdd. However now there are X problems. It says something about not being able to start, even if I select "Safe Graphics Mode". My card is an X800GTO2. 

Any ideas?

---

### Post by squimmy on 2007-03-19
w00t! I'm posting from the live cd! To boot, I have to type noprobe=hdd hdd=noprobe to get past it getting stuck. Then, X fails to start, so I let it fail and it will drop me back to a terminal. Then I typed "sudo nano /etc/X11/xorg.conf" and changed "ati" to "radeon". Now X boots.

Now comes the major problem - hdd is the hard drive I want to install onto. T-Y-P-I-C-A-L. So, something to do with the HDD is stopping the comp booting.

Any ideas? The error message when I don't disable probing is a post or two back.

Thanks.

---

### Post by squimmy on 2007-03-20
Anyone?

I'm about to make a new thread...

---

