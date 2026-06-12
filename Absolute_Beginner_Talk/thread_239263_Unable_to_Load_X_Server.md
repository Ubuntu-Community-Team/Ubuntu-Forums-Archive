---
title: "Unable to Load X Server"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Zully Quirke on 2006-08-19
Hello! I'm new to Linux, but not new to computers. I feel like such a n00b! I installed Ubuntu on my slave hard drive, but I'm not getting any graphical interface. I get some error talking about it being unable to load X Server, and then it's all MS-DOS-ish. When I went through the install there was no graphical interface either. What am I doing wrong, or additionally what do I need to do? Is there something outside of Ubuntu that I need to have installed for a graphical interface to exist? I also get the same error when I try to boot off the Live CD.

---

### Post by secretlondon on 2006-08-19
You can't boot off the live CD?

It sounds like your graphics card/chip may not be supported. Do you know what make it is?

---

### Post by Zully Quirke on 2006-08-19
Yes; I have an ATI Radeon X160 Pro; 512 MB DDR2.

It starts up, but all I get once the initial splash page (the nifty Ubuntu orange against black as everything starts up), all I get is MS-DOS-y prompt, and an error message that pops up and whines about my x server being unable to load. And I have *no* earthly idea what that is, or why things aren't starting up in the first place.

---

### Post by Zully Quirke on 2006-08-19
It's also worth noting that it directs me to wiki.x.org, though when I go there I have no idea what to do. Do I download all the files in the recent release? Where do I put them/what do I do if anything to activate them?

I'm a hopeless windows user in recovery! ): Admitting you have a problem is the first step?

---

### Post by secretlondon on 2006-08-19
> **Zully Quirke said:**
> Yes; I have an ATI Radeon X160 Pro; 512 MB DDR2.

It starts up, but all I get once the initial splash page (the nifty Ubuntu orange against black as everything starts up), all I get is MS-DOS-y prompt, and an error message that pops up and whines about my x server being unable to load. And I have *no* earthly idea what that is, or why things aren't starting up in the first place.

Well if you've got an ati card then it should be fixable!

I've no experience with ATI cards - the wiki has some info but the built-in drivers should have found your card. Could you paste in the error message you get when you try and boot?

[URL="https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28ati%29"]
The wiki has some info on upgrading your drivers, but you should be getting 2D anyway.. [/URL]

---

### Post by Zully Quirke on 2006-08-19
Sure- how do I copy it from there? Can I select all/copy? I'm afraid I'm not too familiar with commands outside of Windows.

---

### Post by secretlondon on 2006-08-19
> **Zully Quirke said:**
> Sure- how do I copy it from there? Can I select all/copy? I'm afraid I'm not too familiar with commands outside of Windows.

I don't think you can - you'll probably have to use paper :(

---

### Post by Zully Quirke on 2006-08-19
I can do you one better -- digital camera photos. :)

This is the initial error message I get:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

When I click yes, I get the following screens:

[http://www.zullyquirke.com/error01.jpg](http://www.zullyquirke.com/error01.jpg)
[http://www.zullyquirke.com/error02.jpg](http://www.zullyquirke.com/error02.jpg)
[http://www.zullyquirke.com/error03.jpg](http://www.zullyquirke.com/error03.jpg)


After I click Ok, I get this prompt:

[http://www.zullyquirke.com/error04.jpg](http://www.zullyquirke.com/error04.jpg)

Do you need this error message as well?

---

### Post by confused57 on 2006-08-19
> **Zully Quirke said:**
> Yes; I have an ATI Radeon X160 Pro; 512 MB DDR2.

It starts up, but all I get once the initial splash page (the nifty Ubuntu orange against black as everything starts up), all I get is MS-DOS-y prompt, and an error message that pops up and whines about my x server being unable to load. And I have *no* earthly idea what that is, or why things aren't starting up in the first place.

It might be a matter of configuring your xserver:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

The above link basically describes configuring your xorg.conf file:
```
sudo dpkg-reconfigure xserver-xorg
```
You could start with the "vesa" driver, then maybe the "ati" driver for your video card...see the above link for some background and excellent instructions that should help.

---

### Post by Zully Quirke on 2006-08-19
Yay! Thank you so much; I am now posting from Ubuntu. :) Switching over to "vesa" from "ati" seemed to do the trick!

---

### Post by secretlondon on 2006-08-19
> **Zully Quirke said:**
> Yay! Thank you so much; I am now posting from Ubuntu. :) Switching over to "vesa" from "ati" seemed to do the trick!

YAY!

---

