---
title: "Can I install Xubuntu from the gparted LiveCD?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by freshofftheufo on 2006-11-29
I've been having so many problems with the Xubuntu LiveCD and the alternate CD (but checked for errors, neither booting properly ATM), so I've been googling for "how do I install Ubuntu from a different LiveCD", but I can't find anything.

Specifically, I want to use the gparted LiveCD ... if it's possible, because that's the only LiveCD I can seem to get to work properly. Can I?

Thanks in advance.

---

### Post by redDEADresolve on 2006-11-29
hop over to this thread  [http://ubuntuforums.org/showthread.php?t=299929&page=3](http://ubuntuforums.org/showthread.php?t=299929&page=3), specifically page 3.

I bought, as well as many others, a new Dell 1501 and wasn't able to get ANY flavor of linux running on it. When booting up the hard drive wasn't being recognized buy anything other than gParted LiveCD much like you. Maybe some of the tricks used to solve their problems will help you.

I got it by adding this boot param:
acpi=force irqpoll

Hit 'F6' at the initial ubuntu install menu, and you will be able to add it in with the other boot params. I typed it between the 2nd and 3rd parameters, or thereabouts; but I believe you can put it in anywhere between other boot params. Edit: When you press F6, a line of preset boot parameters is shown for you to edit. On further testing, you can just append ' acpi=force irqpoll' to the end of that line.

---

### Post by freshofftheufo on 2006-11-30
Ok, thanks. I'll try that when I get home.

---

### Post by freshofftheufo on 2006-11-30
That thread doesn't seem to be related. They're having problems on their Dell laptops with the harddrive, I'm pretty sure this isn't related and I'm not on a Dell D  :.

My Xubuntu alternate disk simply won't boot, as if it's not even in the drive (although it does spin up), and the Xunbutu LiveCD just crashes when I click on the menu option to install/run live.

I've been stuck for almost a week now :  (.

---

### Post by freshofftheufo on 2006-11-30
Update: I can boot the Ubuntu LiveCD fine (as far as my 128 megs of RAM will take me) and the Ubuntu alternate CD also works fine.

I've checked all 4 Xubuntu CDs I've burned (all at low speeds) for errors, but they just screw up in the same places. Why is it only Xubuntu that's not working for me???

I'm on an old Thinkpad, if that means anything.

---

### Post by redDEADresolve on 2006-11-30
Have you tried redownloading the alternative install CD and working from there. Maybe its the download that messed up if you've burned four discs and they all have errors on the same places.

Sorry about my post earlier not helping but the best thing you could do is post every bit of information about your compute and a detailed description of your problem so others can "see" what maybe be going on.

---

### Post by louieb on 2006-11-30
Here is something else to try. I have a P1 200 128 mb memory. It crashes on boot from most Linux CD's the work around is to use boot option [COLOR=Indigo]ide=nodma[/COLOR]

---

