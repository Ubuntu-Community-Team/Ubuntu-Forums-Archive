---
title: "Live CD Boot Problems"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by jouno53 on 2007-10-01
I recently downloaded the Ubuntu iso file, followed all the instructions, and successfully burnt it onto a CD. Before that, I also ran the file integrity checker on the iso, which said the file was fine. After that, I ran the CD from within Windows and successfully got the splash screen that has all the different apps on it.

Now, the problems lies within booting Ubuntu. On our Dell Dimension 2300, I clicked F12 and got into the boot menu. I clicked the CD drive and successfully got the Ubuntu start page where you choose if you want to Start, Install, or Run Ubuntu in safe graphics mode. I clicked Start, and it started booting. After the DOS screen comes up with the "Starting Preliminary..." and all the other messages, it started displaying a never ending line of error codes and messages, that kept going... and going...

I have no idea what's wrong. The CD is fine, the iso is fine, and I even used the exact same method on a Dell Dimension 2400 in which Ubuntu booted and worked fine.

Is there any way to fix this? If it's a BIOS update I need, please lead me to it.

Thank you very much.

---

### Post by philinux on 2007-10-01
You dont run it from windows you go into the bios and make sure that the cdrom is booted before the hard drive. then you put the live cd in and it boots itself. no windows involved at all

---

### Post by houstonbofh on 2007-10-01
I am guessing Video detection problems.  Try some different video options in the boot.

---

### Post by jouno53 on 2007-10-01
> **jouno53 said:**
> I recently downloaded the Ubuntu iso file, followed all the instructions, and successfully burnt it onto a CD. Before that, I also ran the file integrity checker on the iso, which said the file was fine. After that, I ran the CD from within Windows and successfully got the splash screen that has all the different apps on it.

Now, the problems lies within booting Ubuntu. On our Dell Dimension 2300, I clicked F12 and got into the boot menu. I clicked the CD drive and successfully got the Ubuntu start page where you choose if you want to Start, Install, or Run Ubuntu in safe graphics mode. I clicked Start, and it started booting. After the DOS screen comes up with the "Starting Preliminary..." and all the other messages, it started displaying a never ending line of error codes and messages, that kept going... and going...

I have no idea what's wrong. The CD is fine, the iso is fine, and I even used the exact same method on a Dell Dimension 2400 in which Ubuntu booted and worked fine.

Is there any way to fix this? If it's a BIOS update I need, please lead me to it.

Thank you very much.
I know you can't boot Linux from within Windows, I was just letting you know that the CD works because it showed the apps thing in Windows.

But my problem is within the booting process, read the second half.

Anyways, I just did CD Integrity checker which said there were no errors detected.

---

### Post by jouno53 on 2007-10-01
> **philinux said:**
> You dont run it from windows you go into the bios and make sure that the cdrom is booted before the hard drive. then you put the live cd in and it boots itself. no windows involved at all
Which other video options should I use? I tried the safe graphics mode, but it froze in the loading process.

---

### Post by oilchangeguy on 2007-10-01
> **jouno53 said:**
> I recently downloaded the Ubuntu iso file, followed all the instructions, and successfully burnt it onto a CD. Before that, I also ran the file integrity checker on the iso, which said the file was fine. After that, I ran the CD from within Windows and successfully got the splash screen that has all the different apps on it.

Now, the problems lies within booting Ubuntu. On our Dell Dimension 2300, I clicked F12 and got into the boot menu. I clicked the CD drive and successfully got the Ubuntu start page where you choose if you want to Start, Install, or Run Ubuntu in safe graphics mode. I clicked Start, and it started booting. After the DOS screen comes up with the "Starting Preliminary..." and all the other messages, it started displaying a never ending line of error codes and messages, that kept going... and going...

I have no idea what's wrong. The CD is fine, the iso is fine, and I even used the exact same method on a Dell Dimension 2400 in which Ubuntu booted and worked fine.

Is there any way to fix this? If it's a BIOS update I need, please lead me to it.

Thank you very much.


first there is no dos screen in linux. or for that matter xp. dos is a microsoft product. and it died with win me. just because you see white text, and a black background, does not mean it's dos. and give your machine's spec's.

---

### Post by Levia_Neo on 2007-10-01
I am having the same problem, I have a working cd, but when I choose
to boot from the cd on the startup menue (after reseting my computer, booting from cd and such) The green loading appears at the top and a somewhat messed up green loading on the left (the top part of the o, a, n, and g letters are misplaced). Thats it, its as far as it gets. The hard drive use light is constantly on after that, not rappidly flashing as it does when loading things.
I have left it runing in this state for some time and still nothing happens.

---

### Post by oilchangeguy on 2007-10-01
> **Levia_Neo said:**
> I am having the same problem, I have a working cd, but when I choose
to boot from the cd on the startup menue (after reseting my computer, booting from cd and such) The green loading appears at the top and a somewhat messed up green loading on the left (the top part of the o, a, n, and g letters are misplaced). Thats it, its as far as it gets. The hard drive use light is constantly on after that, not rappidly flashing as it does when loading things.
I have left it runing in this state for some time and still nothing happens.

computer specs, and version of ubuntu, please.

---

### Post by jouno53 on 2007-10-01
Ok... well here's my specs:
Dell Dimension 2300
Windows XP Professional
768 MB RAM
Intel Pentium 4 1.80 Ghz
ATI Radeon 9250 128MB Graphics

I'm so terribly sorry that the word DOS offended you, I'll try not to use it incorrectly next time.

Could you please help me with my problem? The rapidly displaying list of numbers and errors upon booting is what my problem is.

---

### Post by oilchangeguy on 2007-10-01
> **jouno53 said:**
> Ok... well here's my specs:
Dell Dimension 2300
Windows XP Professional
768 MB RAM
Intel Pentium 4 1.80 Ghz
ATI Radeon 9250 128MB Graphics

I'm so terribly sorry that the word DOS offended you, I'll try not to use it incorrectly next time.

Could you please help me with my problem? The rapidly displaying list of numbers and errors upon booting is what my problem is.

why would you're using dos offend me? i'm just trying to inform you that dos is an old microsoft operating system, nothing more. can you post the error messages you're getting?

---

### Post by Levia_Neo on 2007-10-01
well its an hp pavilion 05
80 gb hard drive
no os currently due to technical problems(All my old files are still there):
 I had xp media edition before
pentium core duo .99 gig ram
graphics are intell integrated

I had fedora on it(The start of all my problems)so using a vista cd formated and deleted the space it took up(in doing so removed the xp kernel for booting)

I went to a best buy and was told to use unbuntu to get my files
(I plan on keeping it as my main os)

---

### Post by akiratheoni on 2007-10-01
Have you tried the alternate install CD?

---

### Post by Levia_Neo on 2007-10-01
you know what? I think i will try that....
I heard it was a text based installer, like GRUB or command based?
does it have help included?

---

### Post by jouno53 on 2007-10-02
Ok, sorry about that.

Anyways, after the usual boot messages are displayed, instead of booting into Ubuntu, an extremely rapidly displaying list of errors and numbers was displayed... too fast to post.

---

### Post by jouno53 on 2007-10-02
Ok, here's some new info.

I went into the boot menu and read the guide about how to set special boot parameters. I clicked esc and went into the text boot menu, where I tried the code for Dell computers. Didn't work. I then tried the code for if you're having hardware errors, didn't work.

A few days ago I used a Ubuntu live cd with a Dell Dimension 2400 and it worked perfectly. I'm starting to think it's the video card on my Dimension 2300. The 2400 (where Ubuntu worked) has integrated graphics, and the 2300 has an ATI Radeon 9250. The drivers are up-to-date, but it still is kind of buggy and may be the source of the problem.

Unless you guys know how I could handle this, I may just quit trying it on this computer. Is there another Linux dostro (I love that word) that is similar to Ubuntu that you would recommend me trying maybe? ... that has a Live CD of course.

---

