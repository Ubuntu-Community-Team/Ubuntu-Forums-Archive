---
title: "rEFIt 0.14 released !"
date: 2010-03-10
forum: Apple Hardware Users
---

### Post by linuxopjemac on 2010-03-10
[http://mac.linux.be/content/refit-014-released](http://mac.linux.be/content/refit-014-released)

Maybe some of you guys like to try ?

---

### Post by jamesey on 2010-03-10
> **linuxopjemac said:**
> [http://mac.linux.be/content/refit-014-released](http://mac.linux.be/content/refit-014-released)

Maybe some of you guys like to try ?

**** yes! 

As soon as i get home from work I'm giving it a go.
I stopped using Ubuntu on my imac (9,1) because of frustrations with Grub. I despise macOS but love the specs of my imac and hope this fixes everything.

---

### Post by Dullstar on 2010-03-10
> **linuxopjemac said:**
> [http://mac.linux.be/content/refit-014-released](http://mac.linux.be/content/refit-014-released)

Maybe some of you guys like to try ?

I just found that on my own.  I was trying to get Linux on my iMac (I want to set up a triple boot) and .13 wouldn't install.  .14 works great!  The only flaw is that sometimes I have to hold down option if I want to make a CD appear in the boot options.  But then again, I *usually* don't need to have a boot CD in my computer.  I was a little reluctant about rEFIt at first, but even if you don't think you need it, I would recommend the program anyways, as it has a better interface than the built in bootloader (on the iMac) and you don't have to hold down a button after you use it a couple times (hold option down the first couple times you use rEFIt though).  I'm glad I installed it, especially because now I'm getting my triple boot to work properly.  I'm typing this from OS X right now, mainly because I don't have my wireless network information on me right now.  Plus, I need to finish a paper for math class (a Pythagoras essay), and I already have the printer drivers here (although I could get them on OS X).

---

### Post by binary10 on 2010-03-11
I've not had much luck with rEFlt 0.14 or 0.13...

I just keep going around in circles about 'how to' or 'is it even possible' to boot a perfectly bootable external usb drive with my ubuntu build, but running on my iMac instead of my laptop.

GPTs/MBRs... I've seen many references - I just got to find a decent guide. I don't want to install ubuntu on my iMacs internal drive. I just want to be able to boot my external usb drive.

I should have added my iMac is an i7 style and wireless keyboard which has been a pain to get it detect the keys pressed during boot up.

---

### Post by jamesey on 2010-03-12
refit .14 and lucid 10.04 alpha 3 works

i did this on my March 2009 20in imac (model 9,1)
1. install fresh mac osx, create a partition with disk utility
2. install refit
3. reboot into mac osx
4. reboot, hold option button, boot to 10.04 cd
5. delete partition with gparted
6. install 10.04 into "largest continuous free space"
7. wait for install to finish, reboot into mac osx
8. reboot and choose linux in refit
9. 10.04 starts up

bad things:
I still have that stupid issue of ubuntu not recognizing the wifi device, so i physically need to plug my imac into my router and do a software update. 

also, there is no sound from the onboard speaker. that'll never get ******* fixed.


good things: 
my blue tooth mouse just works after the basic setup. I was not expecting that.

---

### Post by wmittz on 2010-03-12
I upgraded to 0.14, didn't want to boot to Ubuntu, went back to OSX, pulled up the terminal, and re-blessed it as per directions, everything is working fine. On the  WIFI I have had trouble with backports. I had to go back and remove them and everything went back to working. On the sound in the for the option menu I used =imac24 and the sound started working. Hope this helps


Warren

---

### Post by jamesey on 2010-03-12
> **wmittz said:**
> I upgraded to 0.14, didn't want to boot to Ubuntu, went back to OSX, pulled up the terminal, and re-blessed it as per directions, everything is working fine. On the  WIFI I have had trouble with backports. I had to go back and remove them and everything went back to working. On the sound in the for the option menu I used =imac24 and the sound started working. Hope this helps


Warren
you dont have an imac from march 2009 (imac 9,1) do you? it's the only apple product that wont produce sound of its speakers with linux.

---

### Post by alexmurray on 2010-03-13
That's not 100% true - installing linux-backports-modules-alsa under karmic should enable sound for imac9,1 or upgrading to Lucid (current alpha version of Ubuntu) should also work.

---

### Post by jamesey on 2010-03-14
> **alexmurray said:**
> That's not 100% true - installing linux-backports-modules-alsa under karmic should enable sound for imac9,1 or upgrading to Lucid (current alpha version of Ubuntu) should also work.

iMac 9,1 is a special case. the backports-modules and latest alpha of Lucid don't get sound working through the onboard speakers.

---

### Post by gcndavidmn on 2010-03-14
Does 0.14 actually add anything to make it worth my time to upgrade?

---

### Post by kmag on 2010-03-14
I have a March 2009 iMac (9.1) with Lucid 10.04, grub 2.6.32.16.  No problems with refit .13 or refit .14.  Except for reboot everything else works fine, wi-fi, sound, camera etc.. Radeon drivers took a bit of wrangling to work properly though.  

I removed all alsa drivers, reinstalled all alsa drivers as root.  Once you get root sound working, create a new user.  Check your user permissions, they seem to be involved.

---

### Post by jamesey on 2010-03-15
> **kmag said:**
> I have a March 2009 iMac (9.1) with Lucid 10.04, grub 2.6.32.16.  No problems with refit .13 or refit .14.  Except for reboot everything else works fine, wi-fi, sound, camera etc.. Radeon drivers took a bit of wrangling to work properly though.  

I removed all alsa drivers, reinstalled all alsa drivers as root.  Once you get root sound working, create a new user.  Check your user permissions, they seem to be involved.

you sure that's an iMac 9,1? Mine has an nvida card and is 20 inches. I got it a week after it was released.

---

### Post by Tu1J4kXk8NUhMz on 2010-03-15
My testing has been fairly limited so far but looking good so far. I wish they would resolve the issue where rEFIt can only see what's loaded when it loads. In other words, I've never been able to get it to load in a CD or USB drive dynamically.

In fact, I am playing with an old MBP I have (not that old I suppose...my wife bought her own computer so I got mine back yay!). I'm trying to load rEFIt on its own partition (which is possible) and see if I can't get rid of Mac OS X altogether. I love OS X, but for some reason on this comp, it is the enemy (I've had lots of issues and no way to resolve them so far).

Wish me luck!

---

### Post by kmag on 2010-03-15
> **jamesey said:**
> you sure that's an iMac 9,1? Mine has an nvida card and is 20 inches. I got it a week after it was released.

There are 2 versions of the 21.5" iMac.  I have the one with the Radeon graphics and 1T HD.
This is the same graphics board as the Core 2 Duo 27" iMac.

as per Apple's website.  "ATI Radeon HD 4670 graphics processor with 256MB of GDDR3 memory"

Could you remind me of the command to view the version of my Mac?

---

### Post by binary10 on 2010-03-15
> **kmag said:**
> 

Could you remind me of the command to view the version of my Mac?

under OSX do a 'sysctl hw.model'

Mines a 'hw.model: iMac11,1'  (iMac i7 27in)

---

### Post by kmag on 2010-03-15
oops, iMac 10,1

---

