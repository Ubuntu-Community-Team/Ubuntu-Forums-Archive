---
title: "wine installing"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2006-12-30
synaptic wont let install wine, someone told me something about repositories.  how do i enable disable them???  also does wine even work on 64 bit ubuntu???  thanks in advance

---

### Post by Paradoxed on 2006-12-30
To enable the repositories, go to System/Administration/Synaptic Package Manager/
the click Settings, Repositories, and check (tick) all the boxes.

You can then search for wine and install.

---

### Post by antgul3382 on 2006-12-30
ok did that, searched for wine all there was were libwine (2 of them) i clicked them both and got this

> libwine:
 Depends: wine  but it is not installable


---

### Post by Paradoxed on 2006-12-30
type this in the terminal and see what it does

sudo apt-get install wine

---

### Post by rocknrolf77 on 2006-12-30
You need to do a ```
sudo aptitude update
``` first.

---

### Post by rbhigday on 2006-12-30
> **Paradoxed said:**
> To enable the repositories, go to System/Administration/Synaptic Package Manager/
the click Settings, Repositories, and check (tick) all the boxes.

You can then search for wine and install.

Thanks for this I was wondering how to get to the repositories everyone mentioned, and I could never find. :-D

---

### Post by antgul3382 on 2006-12-30
i update then:



slave@slave3:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate




what di i do?

---

### Post by Paradoxed on 2006-12-30
Okay you need to go to your Synaptic Package Manager/Settings/Repositories

click on 

third party 

click on 

add custom

and paste this in

[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

thereafter you should 

sudo aptitude update


Go back to the Synaptic Package Manager and search 

wine

---

### Post by antgul3382 on 2006-12-30
> Okay you need to go to your Synaptic Package Manager/Settings/Repositories

click on

third party

click on

add custom

and paste this in

[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

thereafter you should

sudo aptitude update


Go back to the Synaptic Package Manager and search

wine

ok i go to do that and first off theres no add custom button just add, then i paste it in there and the add source button is shaded as it was before i pasted so i cant add it....

heeeelllllp!!!!!

thanks again

---

### Post by antgul3382 on 2006-12-30
imm all sert found info on hq page  thaks people!!!!

---

### Post by antgul3382 on 2006-12-30
ok i forgot to metion 64 bit ubuntu is there a way to install it???

---

### Post by rbhigday on 2006-12-30
> **antgul3382 said:**
> ok i go to do that and first off theres no add custom button just add, then i paste it in there and the add source button is shaded as it was before i pasted so i cant add it....

heeeelllllp!!!!!

thanks again

I got the same thing you did :???:

---

### Post by antgul3382 on 2006-12-31
can anyone help us get wine on 64 bit ubuntu??? pleeeeeeeeeez???? thanks in advance

---

### Post by The Joe on 2006-12-31
I should imagine you just get the normal Wine for 64-Bit. If not sniff around Wine wiki.

---

