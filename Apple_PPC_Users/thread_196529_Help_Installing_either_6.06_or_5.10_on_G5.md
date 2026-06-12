---
title: "Help Installing either 6.06 or 5.10 on G5"
date: 2006-06-14
forum: Apple PPC Users
---

### Post by jcgg on 2006-06-14
Any help would be appreciated. I tried to install 6,06 on my G5 running 10.3.9 (Darwin). Everything was fine goes through the boot sequence, X appears then changes to pointer and then the pointer freezes. Then the colling fans kick into high gear like I have never heard before.

Next I tried to install 5.10. I get to the boot prompt and then the system freezes and I am stuck. Once more the cooling fans kick into high gear and I have to turn my G5 off.

Thank you for any replies.

---

### Post by tidris on 2006-06-14
Are you able to boot from the 6.06 live desktop CD without problems?

---

### Post by jcgg on 2006-06-14
Yes, I have held the C key down and boot right into Ubuntu. Also, this is not a intel based Mac.

---

### Post by swartzfeger on 2006-06-14
jcgg,

I'm not sure based on the info that you gave. You did successfully install 6.06, correct? I'm assuming you did based on your boot comment. Also, did your system ever successfully boot to the KDE desktop, or has it always frozen in the same spot?

Is your 6.06 installed on the same disk as OS X, or is it on a dedicated drive?

Have you tried the rescue option or a re-install?

---

### Post by tidris on 2006-06-14
I would guess that X11 was not configured properly during installation. There are several threads in these forums explaining how to deal with that case.

What G5 model do you have? Knowing that might help to narrow down the possibilities.

---

### Post by jcgg on 2006-06-14
[QUOTE=swartzfeger]jcgg,

I'm not sure based on the info that you gave. You did successfully install 6.06, correct? I'm assuming you did based on your boot comment. Also, did your system ever successfully boot to the KDE desktop, or has it always frozen in the same spot?

Is your 6.06 installed on the same disk as OS X, or is it on a dedicated drive?

Have you tried the rescue option or a re-install?[/QUOTE]



No 6.06 did not install. The disk booted up but the installation stalled after the X appeared. It always freezes in the same spot. I have OS X already running on the hard drive, and Ubuntu would be installed on the same drive. As for rescue I have not used that becuse there is nothing to rescue.

---

### Post by jcgg on 2006-06-14
[QUOTE=tidris]I would guess that X11 was not configured properly during installation. There are several threads in these forums explaining how to deal with that case.

What G5 model do you have? Knowing that might help to narrow down the possibilities.[/QUOTE]


G5 model 1.8Ghz PPC G5 (3.0)

---

### Post by tidris on 2006-06-14
[QUOTE=jcgg]No 6.06 did not install. The disk booted up but the installation stalled after the X appeared. [/QUOTE]
I am confused. I though you had completed the 6.06 installation from the CD, and then when the machine tries to boot from the hard disk that is when it freezes.

---

### Post by swartzfeger on 2006-06-14
[QUOTE=jcgg]No 6.06 did not install. The disk booted up but the installation stalled after the X appeared. It always freezes in the same spot. I have OS X already running on the hard drive, and Ubuntu would be installed on the same drive. As for rescue I have not used that becuse there is nothing to rescue.[/QUOTE]

Which ISO image did you use to burn the CD -- Desktop, Server or Alternate?

---

### Post by jcgg on 2006-06-14
Desktop.

---

### Post by jcgg on 2006-06-14
[QUOTE=tidris]I am confused. I though you had completed the 6.06 installation from the CD, and then when the machine tries to boot from the hard disk that is when it freezes.[/QUOTE]


No the machine freezes after booting from the CD and trying to install Ubuntu.

---

### Post by kellogs on 2006-06-14
check if you have a G5 you can select diferent kernels to install... 
try all the g5 you have there.... I have a dual G5 so I used install-powerpc64-smp, with other options it crashed always.

---

### Post by swartzfeger on 2006-06-14
[QUOTE=kellogs]check if you have a G5 you can select diferent kernels to install... 
try all the g5 you have there.... I have a dual G5 so I used install-powerpc64-smp, with other options it crashed always.[/QUOTE]

And just for the record (and someone please correct me if I'm wrong), I don't think you need to do the "-smp" for dual PPC machines with 6.06 and is handled automatically (ie, I simply did 'install-powerpc64' and had dual processor support installed by default). I think I remember reading somewhere  that this was a change from breezy to dapper.

Btw, this is for PPC only... I think Intel core duos need to install a bit differently (ie, upgrade from the default x86 kernel to the i686 kernel via adept, IIRC).

---

### Post by tidris on 2006-06-14
[QUOTE=jcgg]Yes, I have held the C key down and boot right into Ubuntu.

Desktop.

No the machine freezes after booting from the CD and trying to install Ubuntu.[/QUOTE]
So, if I am understanding you correctly now, when you boot from the live desktop  CD (by holding the C key down) the computer freezes during the boot process before you can see the full ubuntu GUI desktop, right?

If that is the case, you might have better luck with one of the other installer CDs (server or alternate) which do not use a GUI during installation. I still feel it might be an X11 configuration issue.

---

### Post by jcgg on 2006-06-15
Thanks for all the help, the alternate ISO will work, except I forgot one thing. I have 150GB HD and it has data and the apple file system on maybe 5 gigs. Problem is if I partition a portion of the drive for Ubuntu I may lose some data. So no Ubuntu for me.

---

