---
title: "Installation problems"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Hughesy on 2006-12-28
Successfully installed ubuntu on about the 3rd attempt. For some reason the installation kept freezing about half way through ubuntu's 2nd window (the first the ubuntu logo is grey and the 2nd window its green), no matter what type of option i chose, even the live dvd would not work. The only way i could get it installed was to do install it through the text option.

Now its installed the only way i can get to ubuntu is through the safe graphics mode and type "exit", because the laptop freezes when i try to enter ubuntu the normal option.

How do i fix this???

---

### Post by tripwire on 2006-12-28
what graphical card do you use?

---

### Post by Hughesy on 2006-12-28
> **tripwire said:**
> what graphical card do you use?

nVidia GeForce Go 7200

---

### Post by Hughesy on 2006-12-28
bump

---

### Post by riven0 on 2006-12-28
Can you get to the login screen at all? If so, hit CTRL + ALT + F1 to get to the terminal. Then try do an xserver reconfiguration:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by deadgobby on 2006-12-28
A other thing you can do is install Automatix. It has a bunch of Nvidia driver.
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by Hughesy on 2006-12-28
> **riven0 said:**
> Can you get to the login screen at all? If so, hit CTRL + ALT + F1 to get to the terminal. Then try do an xserver reconfiguration:
riven0, 
The only way i can get to the login screen is through selecting the 2nd option on the dual boot screen (sorry i'm at work now and cant remember the exact terms). I think its a configuration or safe mode, and yet this way there is no gaurantees this option works. As the first time i tried it yesterday i was able to get into ubuntu, but took me another 4 times before it worked again. 

will i have to do anything after attempting "sudo dpkg-reconfigure xserver-xorg"?? or should i just try a normal startup?

By the looks of it you guys think it might be the display drivers... what makes you think this? will try the automatix intstallation anyway, it wont hurt. thanks deadgobby!!

Also, i am attempting to install this on a turion 64*2 laptop, i'm used the edgy64 live dvd to install, are there any known problems trying to install on 64bit machines?

Thanks lads

---

### Post by riven0 on 2006-12-28
> **Hughesy said:**
> riven0, 
The only way i can get to the login screen is through selecting the 2nd option on the dual boot screen (sorry i'm at work now and cant remember the exact terms). I think its a configuration or safe mode, and yet this way there is no gaurantees this option works. As the first time i tried it yesterday i was able to get into ubuntu, but took me another 4 times before it worked again. 

will i have to do anything after attempting "sudo dpkg-reconfigure xserver-xorg"?? or should i just try a normal startup?

Alright, you're talking about recovery mode. That'll be similar to Failsafe; it should boot you up to the terminal screen and you can do a reconfiguration from there. 

There is no problem with first trying a normal startup, but if it constantly freezes then it's most likely a graphical related problem, which is why I suggested a reconfiguration; that usually helps me when I run into a problem.

> Also, i am attempting to install this on a turion 64*2 laptop, i'm used the edgy64 live dvd to install, are there any known problems trying to install on 64bit machines?

Thanks lads

The only known problems I've heard with 64bit is that flash player is unsupported. There is a workaround to this, but it's a little more tricky. Check the[ howto here]("http://www.ubuntuforums.org/showthread.php?t=202537&highlight=flash+64bit").

---

### Post by Hughesy on 2006-12-29
Hi again,

unfortunetly things have gone from bad to worse.

I attempted the reconfigure as suggested above, and after going through the settings i made things worse. 

Now i cant even get get into ubuntu through the method i used previously by entering the configuring method and typing exit on the terminal.

I have uploaded a few vids onto utube to show what happens when i attempt to log on. i hope it shows the problems i am having and makes it easier to help... 

[http://www.youtube.com/watch?v=GdHV2ZnJhsw](http://www.youtube.com/watch?v=GdHV2ZnJhsw)
[http://www.youtube.com/watch?v=qq8U1aCw67s](http://www.youtube.com/watch?v=qq8U1aCw67s)
[http://www.youtube.com/watch?v=MgYTExbhNNM](http://www.youtube.com/watch?v=MgYTExbhNNM)
[http://www.youtube.com/watch?v=NnKO44UGxDo](http://www.youtube.com/watch?v=NnKO44UGxDo)

It looks like i'll have to do a fresh install, is this as simple as rewriting over the previous install like in windows?

I had only managed to download automatix onto my windows partition. Not sure how to get it onto ubuntu....

please help...](*,)

---

### Post by jvc26 on 2006-12-29
Installing again will be the same as rebooting windows - open up the live dvd, go through the install steps, partitioning steps - wipe the non-functional ubuntu and reinstall over that. To install the drivers via automatix, you need to boot into the ubuntu and then from terminal 
```
sudo apt-get install automatix2
```
Hope your reinstall works,
Il

---

### Post by Hughesy on 2006-12-30
Reinstalled and had same problem once it was installed.

Managed to get into ubuntu through the reconfig mode, typing "exit" at *username@ubuntu* and then entering username & pass

Once in ubuntu, opened terminal and installed automatix2 from my usb key. 

Restarted the laptop, no change](*,) 

I never honestly thought this would be so difficult and frustrating...

I would probably have given up by now, only for the fact that i need to study the linux OS and learn a bit of Perl programming asap....

Any more suggestions guys??? :???:

---

### Post by Hughesy on 2006-12-30
^ please help...

---

### Post by Sef on 2006-12-30
1) Do you have to use the 64-bit?   You might try the 32-bit.  

2) Are you using the Live CD or the alternate cd?  If you have used the Live CD, try the alternate cd. Sometimes the problems with the video drivers disappear with the alternate cd.

---

### Post by Hughesy on 2006-12-30
have tried both the live dvd and live cd....

will give the alternate one ago...

what have i got to lose???

thanks

---

### Post by Sef on 2006-12-30
you're welcome.   If you have any problems, please post them.

---

### Post by Hughesy on 2006-12-30
just to make sure "ubuntu-6.1-alternative-amd64" is the disk i should try?

---

### Post by Hughesy on 2006-12-30
> **Sef said:**
> you're welcome.   If you have any problems, please post them.

New install, Same problems....

> Do you have to use the 64-bit?   You might try the 32-bit.  

Tried that and was getting same problems....

---

### Post by Hughesy on 2006-12-30
bump

---

### Post by Hughesy on 2007-01-01
well guys, ubuntu wont work for me and i'm not getting any suggestions on how to make it work for me, so has anyone got another form of linux that they suggest i try?

---

