---
title: "Ubuntu isn't loading of my live disk"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Rensole on 2007-05-31
ok I recently downloaded ubuntu 7.04 onto my computer and burned it to a cd at 4x speed. when i try running it on my laptop it starts up with the regulary loading bar.  Then  it shows  a black screen and begins to install i suppose, and after gooing thru a list of different things ( sory but i cant read what its showing, too fast) it beeps and reverts to a pure black scrren with no writing and ceases to do anything. What should I do

p.s sorry for making it so vague. Also im running it on a AMD Turion with nvidiageforce graphics card, 105 gb hard drive 750 Ram, and my current OS is the cursed Vista...

---

### Post by doobit on 2007-05-31
> **Rensole said:**
> ok I recently downloaded ubuntu 7.04 onto my computer and burned it to a cd at 4x speed. when i try running it on my laptop it starts up with the regulary loading bar.  Then  it shows  a black screen and begins to install i suppose, and after gooing thru a list of different things ( sory but i cant read what its showing, too fast) it beeps and reverts to a pure black scrren with no writing and ceases to do anything. What should I do

p.s sorry for making it so vague. Also im running it on a AMD Turion with nvidiageforce graphics card, 105 gb hard drive 750 Ram, and my current OS is the cursed Vista...

It shouldn't be having any problem, but it's possible you have a bad CD. Hit Alt+F1 when you see the loading bar and that should show you some errors or something you can report here. The live CD doesn't actually install until you tell it to, so don't worry there.

---

### Post by kernel tom on 2007-05-31
definately a bad cd... i had similar problems because i finalized my cd... then when booting it only made it part of the way...

next time u make the cd, do not finalize it

see if that works

---

### Post by pappapump on 2007-05-31
Are you using the 64 bit version of ubuntu and not the x86 version?
That alone will cause you to hang with a turion.
Also remember that most laptop CD-Roms are prone to heat failure over time since a lot of them are located close to the CPU.
Typically they will run fine at first but gradually start having time-outs and read failures.
Remember that the Live-CD has exclusive control over the CD-Rom from start to finish and this places a lot of demand on that weak little CD-Rom, so keep your fan vents on the back and bottom of the laptop clear of all obstructions during bootup and install.

---

### Post by silentjudas on 2007-05-31
actually his hard drive mysteriously lost around 40 gb, the same as the default for linux. so i dont know what happened...

---

### Post by Rensole on 2007-05-31
microcode "bcm43xx_microcode5.fw" not available or load failed is the last thing on the screen that is an error when i load it regulary, when i did the alt F1 this is the only error i saw fly by as well.

---

### Post by Rensole on 2007-05-31
Oh its a Turion 64x2, so its not gonna work then?

---

### Post by pappapump on 2007-05-31
That sounds like an interrupted bios loader.
Looks like you crashed your bios.

---

### Post by silentjudas on 2007-05-31
i think we got it


his is a 64 bit pros. thats why....


but that still doesnt explain how he lost 40 soemthing gb's....anyone know that one?

---

### Post by pappapump on 2007-05-31
Thats gonna happen with the improper version of Ubuntu trying to address a x64 cpu as an x86.

---

### Post by silentjudas on 2007-05-31
> **pappapump said:**
> Thats gonna happen with the improper version of Ubuntu trying to address a x64 cpu as an x86.

what, the erroring or the missing 40 gb? lol

---

### Post by Rensole on 2007-05-31
ok i created a new disk this time 64 bit version but im still getting the same error

then it continues and ends doesnt move from this point:

*mounting local filesystems         [ok]
*Activating swapfile swap           [ok]
*congifuring network interfaces  [ok]

---

### Post by shae on 2007-05-31
You do not have to use the 64bit disk.  I have a Turion x2 and am using 32 bit without a single problem.  It looks like it is having an error because of your wireless card.  If you are just looking to install Ubuntu 7.04, I recommend using the alternate installer CD as well as 32 bit.    32 bit is easier to set up codec wise right now.  If you want to try the live disk, however, I recommend trying it on a different computer.

---

### Post by iamgeorge on 2007-06-14
I have a Compaq 6515b laptop with Turion 64 X2, and I get the same error.  I've tried it with the live CD and with the alternate CD, both the amd 64 versions.  

With the live CD, it doesn't get passed that X server error.  With the alternate CD, it lets me install it, but then when it tries to boot up into Ubuntu, I get an error saying X server failed to load.  I can then use the command prompt to navigate around, but every minute or so, if gives me the same error.  I can press enter to get back to the prompt, but it will give me the error again eventually.

Has anyone who had this problem gotten it to work?  It sounds like I could try to install with the 32-bit version, but I'd like to use take advantage of my 64-bit processor.

---

### Post by dptxp on 2007-06-14
64 bit works fine on AMD 64 Turion laptop. I had no problems with Ubuntu, Kubuntu or Xubuntu.

You got a bad CD (most likely)


Download (repair iso) using bittorrent.

Download Bittorrent.
Download the corresponding torrent file (25-30kb).

Open it with Bittorrent.

No need for full new download, point the target address to the dir where your old copy is. Do this BEFORE you click on the torrent file to open it. The corrupt files in iso shall get corrected.

Burn using InfraRecorder . Use 'Burn Image' command in Actions. Do nothing else.
It burns real fast at about 20X , dynamically changing speed. DO NOT set speed.

You will have a correct CD. I have done this for 10 iso. All work.

This is the fasted and safest way.

---

### Post by iamgeorge on 2007-06-14
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

This was it.  I had an ATI X____.  Thanks for the help.

---

