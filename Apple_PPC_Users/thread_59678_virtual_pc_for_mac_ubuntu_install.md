---
title: "virtual pc for mac ubuntu install??"
date: 2005-08-25
forum: Apple PPC Users
---

### Post by Digitallysick on 2005-08-25
Can i do this?? and has anyone else had success??

---

### Post by calum on 2005-08-25
[QUOTE=Digitallysick]Can i do this?? and has anyone else had success??[/QUOTE]

I've never tried with Ubuntu (why bother when it runs natively on a Mac anyway, and a lot faster-- I just dual boot), but I've installed other flavours of Linux on Virtual PC with no problems.  

Just don't expect the same level of integration with the desktop that you get when you're running Windows in Virtual PC-- i.e. you won't get drag and drop between the virtual desktop and your Mac desktop etc.

---

### Post by Digitallysick on 2005-08-25
so how to i do it??  and will it pickup the connection for the airport wireless?? because if that doesnt work i guess there is no point installing it

---

### Post by calum on 2005-08-25
[QUOTE=Digitallysick]so how to i do it??  and will it pickup the connection for the airport wireless?? because if that doesnt work i guess there is no point installing it[/QUOTE]

Same way you'd install Windows on VPC... start up VPC, select File->New, choose "Install your own operating system" , then choose "Linux" when you get to the "choose operating system" part.  It'll ask you to insert the install CD, and away you go.  (This is assuming VPC v7, I haven't used any other version).

Provided you set up your Ubuntu installation to connect to the internet via DHCP, it should just pick up whatever internet connection OSX is using.  I've used Sun's JDS distro (which is based on SuSE) this way on VPC, and it worked fine with my Airport Extreme.

Be aware that Linux is no different from Windows on VPC, though, in that it will still run a lot more slowly than the real thing.  When [Mac on Mac](http://maconmac.bastix.net/)  develops a bit further, it should be a better option for running Ubuntu in a window on OSX, because you'll be able to run the PPC version of Ubuntu at full speed.

---

### Post by bhagiratha on 2005-09-15
I tried installing ubuntu under virtual pc 7.02 on my powermac, but I ended up messing-up my screen resolution setting which I put as 1920*1200 (the same as on my tiger installed system).

soon after ubuntu reboot, I realize that the screen size was way too big.  Now I want to correct this without install the OS all over again.  Is there a way I can boot from the installing disk and be able to change the resolution size in text mode?


thank you

---

### Post by kingler on 2005-11-17
The problem is due to the fact that
Virutal PC only supports 16 bit color, while Ubuntu is trying 24bit.
What you need to do is to change the config file in /etc/X11/xorg.conf 
default depth should be set to 16 instead of 24. 

[QUOTE=bhagiratha]I tried installing ubuntu under virtual pc 7.02 on my powermac, but I ended up messing-up my screen resolution setting which I put as 1920*1200 (the same as on my tiger installed system).

soon after ubuntu reboot, I realize that the screen size was way too big.  Now I want to correct this without install the OS all over again.  Is there a way I can boot from the installing disk and be able to change the resolution size in text mode?
thank you[/QUOTE]

---

### Post by eakspeasy on 2005-12-02
[QUOTE=kingler]The problem is due to the fact that
Virutal PC only supports 16 bit color, while Ubuntu is trying 24bit.
What you need to do is to change the config file in /etc/X11/xorg.conf 
default depth should be set to 16 instead of 24.[/QUOTE]

Indeed.

I found the how-to for this, but I have a slightly different problem...
There is no X11 whatsoever in my ubuntu. :confused: 

(The PPC iso didn't work with a FAT or unformatted VM and the x86 iso worked for the install, but then I ended up with the display problem.)

Any ideas?

TIA

-Jeff

---

