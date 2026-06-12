---
title: "Newbie lookin for help :)"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-17
First off, I would like to say that I have been silently patrolling these boards looking for help the past few days and I am amazed by how polite and friendly the members are to one another. I have found several pages with info to help me, an absolute 100% Linux newbie get my feet wet. Ive jumped in and have had a blast so far trying to learn the very basics of Linux. I see what amazing potential it has and cant wait to learn more!

As mentioned , Ive found lots of help, but a few things Im still confused about.

1. I got mp3 support to work with the XMMS player but not with Amarok although it did tell me it was going to download the mp3 support.... maybe next time I restart Kubuntu it will work? Further though, is there anyway to get support for WMA files? I have a massive library of music but realized that 80% of it is in WMA format.

2. I follwed the guide stickied at the top of the beginners page about installing Flash support and downloaded the package, but when I go to a site to watch flash movies, it still wont read them. 

3. Im having wireless issues (seems like it takes a while to get this one to work from the reading ive done lol) I tried 1 way to get it to work but it was to no avail. I have a Compaq R4000 series notebook and when I first installed Kubuntu it recognized my card, but wouldnt let me enable it. I used a program called wrapper with something else (I think) to install the drivers for it which let me do all the steps....but now it wont find my card period! 

Ill start with those questions and see what comes of them! Thanks again, I look forward to learning so much!

---

### Post by Al3xK3aton on 2007-07-17
What flash movies are you trying to view?

---

### Post by ukulele_ninja on 2007-07-17
Actually I just tried another site and it did work. There is one that has the ending FMV that isnt working though

---

### Post by stchman on 2007-07-17
> **ukulele_ninja said:**
> First off, I would like to say that I have been silently patrolling these boards looking for help the past few days and I am amazed by how polite and friendly the members are to one another. I have found several pages with info to help me, an absolute 100% Linux newbie get my feet wet. Ive jumped in and have had a blast so far trying to learn the very basics of Linux. I see what amazing potential it has and cant wait to learn more!

As mentioned , Ive found lots of help, but a few things Im still confused about.

1. I got mp3 support to work with the XMMS player but not with Amarok although it did tell me it was going to download the mp3 support.... maybe next time I restart Kubuntu it will work? Further though, is there anyway to get support for WMA files? I have a massive library of music but realized that 80% of it is in WMA format.

2. I follwed the guide stickied at the top of the beginners page about installing Flash support and downloaded the package, but when I go to a site to watch flash movies, it still wont read them. 

3. Im having wireless issues (seems like it takes a while to get this one to work from the reading ive done lol) I tried 1 way to get it to work but it was to no avail. I have a Compaq R4000 series notebook and when I first installed Kubuntu it recognized my card, but wouldnt let me enable it. I used a program called wrapper with something else (I think) to install the drivers for it which let me do all the steps....but now it wont find my card period! 

Ill start with those questions and see what comes of them! Thanks again, I look forward to learning so much!

Good to see you are wanting to be an Ubuntu person.  I have some procedures that may help.

[http://www.stchman.com](http://www.stchman.com)

I hope they can be of some help to you.  As far as wireless we will need to know the type of card you have.  Please copy the output of an lspci command in this thread.

---

### Post by rillip on 2007-07-17
WMA support is possible, to an extent.  You'll just need to enable it from the repositories like you did with MP3.  I believe if you google it you'll find the Ubuntu FAQ entry on it.

Note that some files just aren't going to be worth your while to get working, if it's possible at all.  But in general it should work.  I doubt you're going to get encrypted videos, for example, to work, but by and large it should work.  Might try posting about the wireless in the networking forum.  As for Amarok, if you have the codecs installed, it shouldn't be an issue.  I'd try a restart and see if it's working (though this doesn't work in Linux like it does in Windows most of the time) and if not, try reinstalling

```

sudo apt-get --purge remove amarok
sudo apt-get install amarok

```

That ought to remove your Amarok and purge all its settings, then reinstall it, hopefully recognizing the mp3 codec.

---

### Post by ukulele_ninja on 2007-07-17
> **stchman said:**
> Good to see you are wanting to be an Ubuntu person.  I have some procedures that may help.

[http://www.stchman.com](http://www.stchman.com)

I hope they can be of some help to you.  As far as wireless we will need to know the type of card you have.  Please copy the output of an lspci command in this thread.



Im checking out your website right now, heres the readout from the lspci- 03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by stchman on 2007-07-17
> **ukulele_ninja said:**
> Im checking out your website right now, heres the readout from the lspci- 03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Ok , you will have to use ndiswrapper.  Since you have a 43xx this solution is from the Feisty guide.

[http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)

---

### Post by ukulele_ninja on 2007-07-17
I did try the ndiswrapper program but thats what caused it to not read my card anymore. Can i uninstall it then try again? Oh! and how exactly do i know what version of Kubuntu I have. Im thinking its fiesty but im not sure how to tell.

---

### Post by stchman on 2007-07-17
> **ukulele_ninja said:**
> I did try the ndiswrapper program but thats what caused it to not read my card anymore. Can i uninstall it then try again? Oh! and how exactly do i know what version of Kubuntu I have. Im thinking its fiesty but im not sure how to tell.

My site is geared towards the Gnome GUI.  Try this link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

This is directly from the Feisty guide.

---

### Post by ukulele_ninja on 2007-07-17
alright im following the steps, but when it says to install inswrapper, the kommand window says i have another synamptic or adept window open but i dont....

---

### Post by ukulele_ninja on 2007-07-17
Well it was a no-go on the installation procedure outlined in the feisty link... what now? lol

---

### Post by rillip on 2007-07-20
> **ukulele_ninja said:**
> alright im following the steps, but when it says to install inswrapper, the kommand window says i have another synamptic or adept window open but i dont....

post the output of the below ```
ps aux
```

most likely you've got apt and apt-get or dpkg and adept running at the same time, something like that.  Should be easy to spot.

---

