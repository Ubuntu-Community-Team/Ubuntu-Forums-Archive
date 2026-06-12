---
title: "ATI Radeon - Compatible"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-04-10
I am going to buy a new graphic card and i have a good price on a ATI radeon X1950 Pro card. 

So i am just wondering how this works in ubuntu/linux? :popcorn: 

I am using the OS to surf on net, chat, downloading, and watching movies/series. No gaming or so. Because i have a windows disk that i ONLY use to play games on nothing more.

Thank you.

---

### Post by igknighted on 2007-04-10
Not well.  Newer ATI cards (and nvidia cards) struggle with support, and especially the ATI ones.  I would expect the liveCD not to recognize that card at boot, so you would have to install drivers via the CLI before you could boot.

I would recommend if you want a new graphics card to look at an nvidia... I just got a 6600gt for around $70 USD, and even running beryl with everything on I get no lag, it runs great.  Something in this range should do you fine.

---

### Post by gingin on 2007-04-10
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Lets count as you will fide them there
God luck

---

### Post by U5tabil on 2007-04-10
i can only find drivers for the x1900 series and not the x1950 series. :( 

But i just want to know if it works or if there will ever come any better drivers for it?

Is it hard to install? as i say im not using any heavy programs in linux but in windows i need a better card so that i can play and since i have AGP i though that this x1950 pro was good. and i can get it for a really good price aswell. in windows it would probably work good. but as loong as i can surf, chat, download and watch movies in linux i am happy....

---

### Post by igknighted on 2007-04-10
> **U5tabil said:**
> i can only find drivers for the x1900 series and not the x1950 series. :( 

But i just want to know if it works or if there will ever come any better drivers for it?

Is it hard to install? as i say im not using any heavy programs in linux but in windows i need a better card so that i can play and since i have AGP i though that this x1950 pro was good. and i can get it for a really good price aswell. in windows it would probably work good. but as loong as i can surf, chat, download and watch movies in linux i am happy....

Well, to be honest you would be taking a chance.  It will eventually be supported, the question is when.  If you are lucky the open source drivers will be usable until ATI supports it, but theres no guarantee... try searching the forums to see if others have had problems or gotten it to work.

---

### Post by nsleiman on 2007-04-11
> **U5tabil said:**
> I am going to buy a new graphic card and i have a good price on a ATI radeon X1950 Pro card. 

So i am just wondering how this works in ubuntu/linux? :popcorn: 

I am using the OS to surf on net, chat, downloading, and watching movies/series. No gaming or so. Because i have a windows disk that i ONLY use to play games on nothing more.

Thank you.

Go for Nvidia, ATI is just a pain :) 

i have also an ATI card, wish i never had! (cant change it because its difficult to re-assemble a laptop :) )

---

### Post by freebird54 on 2007-04-11
I have had more trouble with my Radeon 9550 in WinXP than I ever had in Ubuntu - but your mileage may vary.....

I think they get a worse rap than they deserve, as they are quite capable once you get them going - and they have been bought out by AMD - who are not bad at responding to Linux concerns...  At least they HAVE a driver out there !

---

### Post by koztaz on 2007-04-25
> **freebird54 said:**
> I have had more trouble with my Radeon 9550 in WinXP than I ever had in Ubuntu - but your mileage may vary.....

I think they get a worse rap than they deserve, as they are quite capable once you get them going - and they have been bought out by AMD - who are not bad at responding to Linux concerns...  At least they HAVE a driver out there !

I will be very glad if you type a HOWTO for Rodeon 9550. Man please help me! No matter what I'm trying xorg.conf always says that there is the frekin MESA driver ](*,)

---

### Post by freebird54 on 2007-04-25
Here's a couple of possible fixes for the mesa drivers showing up...

Now - just a couple of little tweaks.

```
sudo mkdir -p /usr/X11R6/lib/modules/dri 
```


```
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 
```

and

```
gksudo gedit  /etc/modprobe.d/blacklist
```

and add in these 2 lines

```
# causes fglrx to fail and mesa drivers to load
blacklist ati-agp
```

Whew!  After all that a reboot is the safest way to be sure that everything gets a fresh start.  If you skip the last one, then just **<ctrl><alt><backspace>** is enough to test it out.

---

### Post by U5tabil on 2007-04-25
> **freebird54 said:**
> Here's a couple of possible fixes for the mesa drivers showing up...

Now - just a couple of little tweaks.

```
sudo mkdir -p /usr/X11R6/lib/modules/dri 
```


```
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 
```

and

```
gksudo gedit  /etc/modprobe.d/blacklist
```

and add in these 2 lines

```
# causes fglrx to fail and mesa drivers to load
blacklist ati-agp
```

Whew!  After all that a reboot is the safest way to be sure that everything gets a fresh start.  If you skip the last one, then just **<ctrl><alt><backspace>** is enough to test it out.

Ok so i should type that turn of my pc then switch my Geforce card with the ATI card and boot up? And if that fails will it start with my geforce card in? I really dont have time to install the system right now since i am quite busy at the time and i need the pc for this weekend aswell....

But thanks for the great info. I will try sooner or later :)

---

### Post by freebird54 on 2007-04-25
Nahh - that was to 'the other guy'... :D

Hope I didn't cause any bizarre buying decisions!

---

### Post by koztaz on 2007-04-26
Thanks dude. I'll try it when i get home. I hope this is the end of my 5 day suffering with my ATI card :)

---

### Post by U5tabil on 2007-04-26
So what was that for then? I am running a Geforce card now but everytime i want to play games and i need to boot to windows i need to switch from my Geforce to my ATI card....

---

### Post by freebird54 on 2007-04-26
U5tabil - Have you tried the fglrx driver yourself yet?  I think you have to go more by the chipset than the model number when deciding whether a driver will work for you or not.  Apparently in Feisty it is necessary to use the fglrx drivers on the X### series cards, but I haven't heard of that not being enough.  I used the fglrx drivers on my Edgy install, but not on the Feisty install, so I have some experience each way!  You are on Feisty, right?

If you are, then the sticky (Message that hangs around in the yellow section at the top of the forum) describes getting the fglrx driver on your system/running.  I can help with tweaks if necessary once it's there (as you saw from the 'thread highjacker').  That at least means not switching all the time.  it might mean some effort setting up the configuration file (/etc/X11/xorg.conf) - but editing a text file isn't TOO bad...

Let me know what you want to try now - but from what I know I would suggest the fglrx driver for now.  It does usually work, and they do seem to be working on it at least some of the time - as the version numbers keep going up!

---

### Post by U5tabil on 2007-04-26
> **freebird54 said:**
> U5tabil - Have you tried the fglrx driver yourself yet?  I think you have to go more by the chipset than the model number when deciding whether a driver will work for you or not.  Apparently in Feisty it is necessary to use the fglrx drivers on the X### series cards, but I haven't heard of that not being enough.  I used the fglrx drivers on my Edgy install, but not on the Feisty install, so I have some experience each way!  You are on Feisty, right?

If you are, then the sticky (Message that hangs around in the yellow section at the top of the forum) describes getting the fglrx driver on your system/running.  I can help with tweaks if necessary once it's there (as you saw from the 'thread highjacker').  That at least means not switching all the time.  it might mean some effort setting up the configuration file (/etc/X11/xorg.conf) - but editing a text file isn't TOO bad...

Let me know what you want to try now - but from what I know I would suggest the fglrx driver for now.  It does usually work, and they do seem to be working on it at least some of the time - as the version numbers keep going up!

Thank you that sound like to much, but it is really nice to know that people can help in here.

I am still running edgy though i am planning on feisty soon. But i really don't want to install that now since if something should go wrong i don't think il have the pc ready for saturday. Because on saturday i need the pc for a party, playing music and so on. So will try installing Feisty asap after that...

But again thank you for helping. I will get in contact when i come to the point.

---

### Post by cantormath on 2007-04-26
> **U5tabil said:**
> I am going to buy a new graphic card and i have a good price on a ATI radeon X1950 Pro card. 

So i am just wondering how this works in ubuntu/linux? :popcorn: 

I am using the OS to surf on net, chat, downloading, and watching movies/series. No gaming or so. Because i have a windows disk that i ONLY use to play games on nothing more.

Thank you.

DONT BUY ATI.  NVIDIA is gonna be less of a headache if there is any. Why take the chance.

---

### Post by U5tabil on 2007-04-26
> **cantormath said:**
> DONT BUY ATI.  NVIDIA is gonna be less of a headache if there is any. Why take the chance.

If you have read through the post you will see that i bought a ATI because i got it cheap and i needed something good to play games with....

---

### Post by cantormath on 2007-04-26
> **U5tabil said:**
> If you have read through the post you will see that i bought a ATI because i got it cheap and i needed something good to play games with....

Just posting the truth.....not necessarily solving your problem.

---

### Post by freebird54 on 2007-04-26
People make stranger decisions all the time.  Some even keep using Windows just because of games  :D

The trick here is to make it as simple as we can to get it working adequately now that he has it....

---

