---
title: "Desktop Effects Cannot Be Enabled"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by AcademyKP03 on 2007-11-20
Okay, this is a long shot ... but just reinstalled 7.10 - where before i was using compiz fusion, fine ... no problems ... but now ... I can't even get the desktop effects to be "normal" - (currently NONE selected) - much less custom ....

any ideas?

---

### Post by overdrank on 2007-11-20
> **AcademyKP03 said:**
> Okay, this is a long shot ... but just reinstalled 7.10 - where before i was using compiz fusion, fine ... no problems ... but now ... I can't even get the desktop effects to be "normal" - (currently NONE selected) - much less custom ....

any ideas?

HI have you enabled the restricted drivers for you graphics card and what it the model of the card?

---

### Post by steeeeve_ on 2007-11-20
I kinda have the same problem mine says on low and I have 3d drivers and stuff installed as far as I know (inc direct 3d)

---

### Post by AcademyKP03 on 2007-11-20
> **overdrank said:**
> HI have you enabled the restricted drivers for you graphics card and what it the model of the card?

Yeah, I tried that -- says doesn't need to use restricted drivers.

Mobile 915GM/GMS/910GML Express Graphics Controller

Is that my card?

Before I reinstalled; was working great -- never had to do much technically to get it going .. just did the sudo instructions and worked ...

---

### Post by AcademyKP03 on 2007-11-21
any ideas?

---

### Post by olivero1 on 2007-11-21
There has been an update to the awn manager - try using the console to update your catalogs:
```
sudo apt-get update
```

I am still new to this so please bear with me.

---

### Post by AcademyKP03 on 2007-11-21
tried that -- no luck ....

It tries to load desktop effect -- but fails

---

### Post by AcademyKP03 on 2007-11-21
actually, just copy and pasted to terminal that sudo code .... didn't do anything afterwards; what do you mean use console?

thanks

---

### Post by olivero1 on 2007-11-21
My bad - it should be terminal

Applications>Accessories>Terminal

If that does not work another idea I had was to re-install compiz.

To do that follow these steps:

System>Administration>Synaptic Package Manager (enter your root password if prompted)

Click on search and enter : compiz

It should pull up the program, click on the green box and select re-install. If the check box is not green - click install. I believe this is installed by default - could be wrong on that though.

---

### Post by olivero1 on 2007-11-21
> **AcademyKP03 said:**
> actually, just copy and pasted to terminal that sudo code .... didn't do anything afterwards; what do you mean use console?

thanks 

Sorry -you did it correct, use Terminal. That gets the updates from the repositories. If I understand it correctly, when you run that command it will prompt you to install new updates in the notification area on your desktop (default setting is upper right hand corner). 

You may have all the updates.

---

