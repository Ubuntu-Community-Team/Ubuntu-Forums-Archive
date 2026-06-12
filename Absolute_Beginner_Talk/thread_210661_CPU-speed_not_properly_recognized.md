---
title: "CPU-speed not properly recognized"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2006-07-07
Hi all,

I got DD up and running for a couple of days,
got everything i want from it (can even play games :D )

But the problem i noticed is:
I have a amd64 3200+ (but a 386 system)
Kubuntu only thinks of it as a 1Ghz CPU, when it IS a 2Ghz CPU


Anyone knows something to properly set it?


Iarwain

---

### Post by woedend on 2006-07-07
are you sure powernowd isnt downcycling it?

---

### Post by slimdog360 on 2006-07-07
have you used windows (or another OS) on the computer? If so what frequency did it say

---

### Post by Iarwain ben-adar on 2006-07-07
Hi,

@woedend: how can i check that?

@slimdog360: i used windows a long time, and it always said it was 2Ghz...


Iarwain

---

### Post by woedend on 2006-07-07
try this
sudo /etc/init.d/powernowd stop
or, if it gives weird message
sudo killall powernowd

then check again.

if you search the forum for powernowd youll find a lot of interesting things...not sure its your problem but others have had similar complaints.

---

### Post by Iarwain ben-adar on 2006-07-07
*kneels down, and bows head*

You're my hero :D

Now, if i reboot, will it start again? or is it stopped 'til i start it again?


Iarwain

---

### Post by woedend on 2006-07-07
yes it will start again.
install sysv-rc-conf from the repos and remove all of the X's for the daemons( i believe there are two daemons, sorry I don't have ubuntu installed ATM :( )
If you need more detailed help msg me through one of the IM clients

---

### Post by Tails on 2006-07-07
or just install KpowerSave since you are using KDE, and configure in there, I use Dynamic mode which let the OS decide when it need full speed, I think it is a better approach since you **wont** need full speed all the time... :P (escapically in hot days... ;))

---

### Post by Iarwain ben-adar on 2006-07-07
Got it :D

Now the last (actually very stupid) question: how do i save the file?


Iarwain

---

### Post by woedend on 2006-07-07
@sysv or kpowersave?  sorry confused.
if referring to sysv-rc-conf, there is no save option its "automatic"

---

### Post by Iarwain ben-adar on 2006-07-07
Cool!

Thanks for all the help guys :D
@Tails: downloading Kpowersave atm :D


Iarwain

---

### Post by woedend on 2006-07-07
Iarwain,
while you have it and have used it...using sysv-rc-conf is a great way to speed up your system(specifically your boot time, I managed to cut it nearly in half at one point) by removing the services you KNOW you do not use/need(for me it was all laptop, printing, bluetooth related stuff, RAID, LVM, EVMS...).  Just be careful not to disable important things(IE read about each one before disabling).

---

