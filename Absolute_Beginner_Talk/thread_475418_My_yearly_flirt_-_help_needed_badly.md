---
title: "My yearly flirt - help needed badly"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Toxitalk on 2007-06-16
Linux for started back sometimein the early 90's where I first saw it bundled on a cover disk.

With joy, it installed and I played for about 2 days, before I broke it and I just couldnt get it out of Maintenance mode.

Since then every year I have for some reason gone down the same path, and due to this or the other issues, found I have had to revert back to windoze (which I really not that keen on using).

Now Ubuntu 7.04 I see on the front of a magazine and I put it into the dvd drive and it boots without having to install the os, great.

And infact im 99.99% happy that I can stick with it this time, but I do have one or two concerns which I want to address before taking the plunge.

My only machine now is a laptop with an embedded intel extreme graphics 2 chipset on it.I am also based on Oxfordshire in the UK.

My first question is. The taptop did have an partition as an emergency recovery partition (Im not sure if its still there though). If I install grub (or ubuntu eqivilent) is it likely to cause issues? And if so will it be beter for me to install as a dual boot, or let Ubuntu repartition the whole space. (This is important due to a factory reinstall requires me to contact the makers due to how they do there rcovery process(Packard Bell))

Second question. The live dvd booted with no problems. The desktop defaulted to 1024x768 but my laptop is a wide screen with a default resolution of 1280x800 which is not shown in the screen resolution list. Is it possible to confirm that I can use a resolution of 1280x800 in Ubuntu, and if so can someone give me a step by step noob guide.

Third question. BT Voyager modem. For a new user is it possible to use this modem with Linux. For the purposes of this thread assume I have no Linux Knowledge (I have some but its patchy and therefore better to assume I know nothing). If it is considered that the BT voyager modem is flakey or tricky to configure, can I have some router suggestions? (Im not interested in Wireless, due to security and speed concerns)

Final question. My internet connection is with AOL. Again from the position I dont know what Im doing in Linux, will it be possible to do this(idiots guide please). If its possible but quite techinical, the other two ISP's im interested in is BT, Virgin and possibly Fasthosts. If non of these would be ideal for a Linux Noob, can I have suggestions (We use Fasthosts for our work hosting and are really good, therefore Im assuming there ADSL serivce will be at the same level).

Please guys, save me from a life of microsoft...

---

### Post by roylond on 2007-06-16
Hi 
I cant answer all of your questions as I'm a noob as well.
I'm with Virgin and find no problems with connection with them.
You will need a new router though as I think you will find that the BT Voyager modem will only work with BT. I had one and when I went with Virgin it wouldn't work as apparently it has some rom chips which are preconfigured for BT.
I have heard but cannot confirm that you might expect problems with AOL in the UK.
You can add the resolution you want to a file I don't know which one or where to find it but someone with more knowledge than me should help you there.
Hope this is of some help.

---

### Post by scotty32 on 2007-06-16
im with NTL (virgin) and i have DSL and a router and everything works fine. i have no idea what ADSL is like but am sure you can get it connected.

as for the screen res, the file you want to edit is xorg.conf, open up the terminal (Applications > Accessories) and type the following (its case sensative):
```
sudo gedit /etc/X11/xorg.conf
```
you'll be asked for a password, this is your account, if your using the "LiveCD" i dont think there is a password.

though it might be better to use a more "user friendly" version, open the Terminal and type:
```
sudo dpkg-reconfigure xserver-xorg
```

then tick the resolutions you want, though you'll need to do other things like monitor settigns and graphics driver

---

### Post by andyclaxn on 2007-06-16
Hi,
I'm a newbie too, but have just been through the AOL thingy, and this is what I (eventually) did.

1    Buy a 2Wire 2700  (HG)  Modem and an RJ45 cable off Ebay, don't "Buy it now" on the modem, just bid £10 on one that finishes soon, mine cost me £8 but unfortunately I also had to pay £8-50 p&p. The RG45 cable cost me £1-50 and £1 p&p.

2    Plug in your modem, first to the electicity and then the telephone wall jack, use the same same dsl phone filters as you do with your voyager modem, and then just leave it alone for 5 minutes to talk to itself.

3 Use the RJ45 cable to connect the modem to your computer/laptop, and boot up.

4. Now start Firefox or whichever web browser you use, and in the address bar type or paste in:  

  [http://192.168.1.254](http://192.168.1.254)

this will take you to the modem setup screen, just follow the instuctions, I cocked this stage up a few times, but the key thing with AOL was that all you need to do is type in your AOL screen name and password when it asks for your Internet Service Provider's details. You don't need anything else, I kept trying to put too much in.

5. Once you have done that on each computer you have Ubuntu on, all your internet applcations should work straight away without any more signing on. You can go straight to AOL Email, or AOL UK etc, and set any page you like as your home page, and when you start your browser, it will pop straight up, no need to sign on except for your Email.

The one snag, is that you can't access AOL keywords to view your Detailed Bill etc. without AOL software installed, so if you stick with AOL you might want a very small  Windows XP dual boot just to have AOL 9.0 available. Seems a lot of bother just to check a bill. 

I have been really pleased with this setup, and also if you ever want to go wireless, this modem does that really easily and effectively as well. I find the internet a lot quicker than it used to be on Windows and AOL software.

Well, hope that helps
regards
Andy

---

### Post by andyclaxn on 2007-06-16
Hi
One more thing, to get a screen resolution on my widescreen laptop, all I did was install an ATI video card software package using Synaptic Package manager, worked first time, so try searching using your sound card name.
Cheers
Andy

---

### Post by Toxitalk on 2007-06-16
> **andyclaxn said:**
> Hi
One more thing, to get a screen resolution on my widescreen laptop, all I did was install an ATI video card software package using Synaptic Package manager, worked first time, so try searching using your sound card name.
Cheers
Andy

Are you saying the ATI software works for non ATI cards? Also I dont understand where the sound card bit comes in.

---

### Post by Toxitalk on 2007-06-17
> **scotty32 said:**
> im with NTL (virgin) and i have DSL and a router and everything works fine. i have no idea what ADSL is like but am sure you can get it connected.

as for the screen res, the file you want to edit is xorg.conf, open up the terminal (Applications > Accessories) and type the following (its case sensative):
```
sudo gedit /etc/X11/xorg.conf
```
you'll be asked for a password, this is your account, if your using the "LiveCD" i dont think there is a password.

though it might be better to use a more "user friendly" version, open the Terminal and type:
```
sudo dpkg-reconfigure xserver-xorg
```

then tick the resolutions you want, though you'll need to do other things like monitor settigns and graphics driver

Im using the liveDVD, I did the above and it detected the correct res in the cofig aplication, but when the config ended it did say it was wiriting the config file, but twhn I came out of it the res was not listed. DOes anyone know if this is because I am using the LiveCD and it cant write the config because it is a liveDVD?

---

### Post by ecs_pf5 on 2007-06-17
In the dim and distant (last year sometime) I recall reading a page on how to hack the BT voyager ADSL modem to work with Linux, IIRC it's slightly technical but it can be gotten working, at least with Knoppix. I don't know about getting it to work with another ISP

Here we go, it looks hopeful?..

[http://www.lack-of.org.uk/viewarticle.php?article=114](http://www.lack-of.org.uk/viewarticle.php?article=114)

The page mentions specific connection details so in theory you should be able to bend it to a different supplier.

This is all assuming your voyager is the same kind of voyager

It's tentatively looking good anyway? Don't take my word as gospel as I am a noob ;)

Or do what andyclaxn says and get somethinnnng more cooperative

---

### Post by Ozeuss on 2007-06-17
> **Toxitalk said:**
> Im using the liveDVD, I did the above and it detected the correct res in the cofig aplication, but when the config ended it did say it was wiriting the config file, but twhn I came out of it the res was not listed. DOes anyone know if this is because I am using the LiveCD and it cant write the config because it is a liveDVD?

whenever you make changes to xorg.conf, you have to restart X in order for that to take affect. i don't know how well that works in the livedvd. but i think you should'nt fear of screen resolution,  most of the time it's easily fixed. I use a wide screen external monitor for my laptop, and to fix the resolution issue i simply installed the intel driver from the repositories and then chose it with dpkg-reconfigure xserver xorg.

regarding the installation- if you install your ubuntu on a partition (leaving your other OS on its own partition), it should set up dual-boot with grub automatically.

---

### Post by alex_anthony on 2007-06-17
With the AOL BT Voyager Modem, I had one in the past.

If you call up AOL coplaining about the modem etc, you can get them to send you a free Wireless Router Modem (with ethernet if you prefer)

---

### Post by sumitc on 2007-06-17
The Bt Voyager Modem does create problems in Ubuntu.
About the dual boot,GRUB installer will be perfectly alright with the emergency boot partition...it should create aenu with the relvant partitions....

Sumit

---

