---
title: "Display settings IBM T-60"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by gsb005 on 2007-02-22
Hello everyone, I am new to Ubuntu.

I have just installed a fresh copy of Ubuntu on my brand new IBM T-60. I have updated the system with all the patches. However, there is one thing that is really bothering me. My display settings are really bad. I am only getting 1024 with 768 with 0 hertz. And this laptop under windows configuration can run at a much higher resolution and better screen area. Due to this problem, my graphics, moving screens, moving windows is extremely slow and painful. 

I have gone into System-Preferences-Screen Resolution- but the settings mentioned above are the MAX I can go. 
[B]
Please help.... [/B]

---

### Post by carlosfocker on 2007-02-22
Does your T60 have a ati card? if so you may need to uninstall the ATI drivers.

I would suggest [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html) for lastest drivers

or 

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by gsb005 on 2007-02-22
It just doesn't help.. 
first link doesn't lead to anywhere useful
second link asumes you know everything
this is a beginner forum.
step by step instructions- 
please... 
and thanks...

---

### Post by carlosfocker on 2007-02-22
The first link has a link for instructions at the top of the page.  Sorry I just thought it was obvious but you are right that this is a beginners area.  Although, I do want to avoid posting already documented information.  Alberto's guide is fairly easy to follow.  I will walk you through what parts to use. If you have any problems just post back. Also I am assuming you have an ATI video card since thats what the specs say on the newer T60's.  Please inform me if this is not correct.

Steps for latest drivers:

1. Visit this link [http://albertomilone.com/instructions.html](http://albertomilone.com/instructions.html)

2. Follow the **Download and import my GPG key** section

3.  Then follow the **HOW TO ADD the REPOSITORIES** section. 

When asked to pick a repository use one of the following repository.  This depends on your Ubuntu install. 32 and 64 refer to the Processor you own.  

Ubuntu Edgy 6.10

  32bit

    deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/


  64bit

    deb [http://www.albertomilone.com/drivers/edgy/latest/64bit](http://www.albertomilone.com/drivers/edgy/latest/64bit) binary/


Ubuntu Dapper 6.06

  32bit

    deb [http://www.albertomilone.com/drivers/dapper/latest/32bit](http://www.albertomilone.com/drivers/dapper/latest/32bit) binary/


  64bit

    deb [http://www.albertomilone.com/drivers/dapper/latest/64bit](http://www.albertomilone.com/drivers/dapper/latest/64bit) binary/


4. Follow the **To install the ATI driver **section

5. Reboot your computer and pray :)

---

### Post by tgalati4 on 2007-02-22
Before hacking on the drivers, try the following: (in a terminal window)

sudo dpkg-reconfigure xserver-xorg

Then reboot.

The default install uses a "safe" resolution that is common to most laptops.  The reconfigure tries to detect the natural resolution.  Many times it is successful.  When it is not, you have to dig into the specifics.

Windows does the same thing--booting into a lower resolution mode until the video drivers are loaded.

---

