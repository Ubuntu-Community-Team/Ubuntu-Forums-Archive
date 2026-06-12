---
title: "dialup modem problem"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by trailboss on 2006-01-17
I just loaded Ubunto but my modem is not found when I checked. I did try the auto scan and it was not found. I'm talking about dialup connection. What can I do?
thanks
Marshall

---

### Post by wolfmaniac on 2006-01-18
in the panel add the icon of connection monitor (red icon of a phone)
on dat icon right click and select properties
there you will find an option of detecting modem.

---

### Post by lanef on 2006-01-18
is your modem a hardware or a winmodem?

---

### Post by trailboss on 2006-01-18
I did see the auto detect and it did not find it. I was in the manage device area i think, it told me what modem I had, but it was not supported, so when i looked it had no drivers. I kinda been looking here in the search but still no luck. I did find one link to wiki.ubuntu or something page but all that looks kinda hard to do. My modem is a normal card, inner slot card 56k rockwell brand. I'd sure like to get"er going.
thanks guys
Marshall

---

### Post by L Campbell on 2006-01-18
[QUOTE=trailboss]I did see the auto detect and it did not find it. I was in the manage device area i think, it told me what modem I had, but it was not supported, so when i looked it had no drivers. I kinda been looking here in the search but still no luck. I did find one link to wiki.ubuntu or something page but all that looks kinda hard to do. My modem is a normal card, inner slot card 56k rockwell brand. I'd sure like to get"er going.
thanks guys
Marshall[/QUOTE]

If you go to [www.linmodems.org](www.linmodems.org) you can download a file that will give you information about your modem.

 You then send this information back to them and they can explain how to (or if) you can get your modem to connect.

Hope this helps you.

---

### Post by trailboss on 2006-01-18
If all fails and I have to try a different modem. Do i put it in and do the auto-detect? Will it find it and load the drivers? I do have a two other modems I can try, but I was wondering what will happen when I change cards?
thanks
Marshall

---

### Post by trailboss on 2006-01-24
Well looks like I did not have another modem, But I have been reading people getting their modem working. You would think since this is a major problem it would be in the forum for download. It would sure make things easy for newbies like me. I still can not get my modem working. The OS can read it but thats all.
Any help
Trailboss

---

### Post by trailboss on 2006-01-24
Hi all,
I'm not complaining about Ubuntu, i'm just a total newbie!!!!! I loaded Ubuntu with only one problem, the dialup modem. It seems to be alot of people having this same problem, as me. I have been reading on the internet and the problem is, the dialup modems are made with windows in mind. So the fixes if any, for some may be easy and for others like me a nightmare. Ubuntu is a complete system out of box, but with this one snag. Why not pull a programmer and put on this problem to make a fix that will solve this since most everyone trying Ubuntu will be windows users, and some will do full installs like I did. I really want to get on the internet, but not at a slower connection. I did find something but it said I would only get a 12k or something like that. I know there are alot of you who have gotten your computers working with dialup. I also did a linux modem search and it wasn't looking good there. Seems all modems were based around windows and that don't help Ubuntu or it's new users. 

Thanks all for reading and keep up the good work!!!  Help me :( 
Trailboss

---

### Post by lanef on 2006-01-24
hi, lucent/agere dsp winmodems have fully functional linux drivers.see linmodems.org for the driver.if you have a small computer shop in your area
you can pick up a lucent lt modem fairly cheap.i'm online now with one.

---

### Post by Mustard on 2006-01-24
All modems are not based around windows.  It's just cheap modems that are based around windows.

Ideally you should get an external modem that connects to your serial port.  One that is not controller-less, as winmodems are.  It's sometimes referred to as a 'true modem', as these are real modems.  Winmodems are just modems that take shortcuts to cut the price of the modem.  Not only do they take shortcuts, but they pass on the extra burden to the CPU to take up the slack.  If you are looking to have a successful linux installation on a dialup connection, then an external serial modem  is the way to go.

---

### Post by unisol on 2006-01-24
spare yourself the inconveince if you can afford it go to ebay they have some external serial hardware-based modems cheap. if you read the spec on the modems it will tell you if it is compatible with linux

---

### Post by gigi1234 on 2006-01-24
Hello All. 

I am a newbie to both Linux and Ubuntu but I did manage to get my Winmodem running in Breezy Badger 5.10. I have an IBM Thinkpad T21 with a Lucent Winmodem. 

First I would suggest looking at the site [www.linmodems.org](www.linmodems.org) for some very helpful suggestions. I was able to run ScanModem, then sent the folks at linmodems the results of the scan, and they told me to download the package ltmodem-8.31b1.tar.gz. From there I unzipped the package, entered the ltmodem folder, and ran the following:

sudo ./build_module
sudo ./ltinst2
sudo ./autoload
sudo .checkout

The absolute KEY, which I have seen mentioned on this forum elsewhere, is that you MUST update your repositories and install the GCC 3.4. compiler. This is ESSENTIAL or "build_module" will fail. This will be tough if you don't have some other way of connecting to the Internet besides your Winmodem. I was lucky and had access to a LAN. But maybe you could download GCC 3.4from another computer then install it? 

Maybe this will help someone, I don't know. 

Also, I know people scowl about Winmodems but if you can get it working without too much trouble then it is a perfectly acceptable option, in my opinion. 

Cheers! Gigi

---

### Post by bigkahuna on 2006-01-24
Unisol is right, save yourself a huge headache and buy an external modem that connects to your -SERIAL- port.  I spent weeks trying to get my Winmodem to work and all I got were bags under my eyes.  -If- you've been working with Linux for years and/or -if- you are really dedicated, you can get them to work... maybe, sometimes...

When I went shopping for a modem, I found that 99.99% of them are Winmodems, it didn't matter if they were internal or external USB modems, none of them would work.  The -only- way to go is with an external -SERIAL- modem.  I got a Best Data V.92 modem with cable for $10 on eBay last year.  When you find one that you think will work, check it's model number in Google (search for modelnumber linux).  If you see lots of posts in Linux forums problems that never get resolved, chances are that modem won't work.

As for autodetection, some times it works, sometimes it doesn't.  Chances are if you use an external serial modem, it will be connected at ttyS0 (most newer computers only come with one serial port now-a-days).

I've installed and re-installed my modem so many times now, I've created a cheat sheet to do it.  If you need a copy of it let me know.

Good luck!

---

### Post by trailboss on 2006-01-25
Da Big Ka,
I would like your cheat sheet. Also can you put on it, what serial modems that will work with linux? Do you have the links to the downloads. I was able to find a driver, but I could'nt figure out how to install it :(  hope your cheat sheet will tell me step by step, remember i'm a windows user and only know click and install:( 
thanks
Trailboss

---

