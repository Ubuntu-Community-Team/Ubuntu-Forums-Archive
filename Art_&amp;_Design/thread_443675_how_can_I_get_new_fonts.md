---
title: "how can I get new fonts ?"
date: 2007-05-14
forum: Art &amp; Design
---

### Post by alainhenry on 2007-05-14
I would like to install new fonts in Feisty.  I installed the msttcorefonts and got some Windows ones.  Ibut I'd like to find more fancy stuff.  Can anyone point me to whare I should start looking ?
Thanks
Alain

---

### Post by ComplexNumber on 2007-05-14
you can either:
a) look through synaptic and do a search for "font". 
OR
b) go [here]("http://gnome-look.org/index.php?xcontentmode=39"), then untar them and place them in ~/.fonts.

---

### Post by kpolice on 2007-05-14
[http://www.dafont.com/](http://www.dafont.com/)

---

### Post by alainhenry on 2007-05-15
Great, thank you!  

I don't have a ~/.fonts directory.  Do I just have to create it ? There is a .fontconfig though.  

Alain

---

### Post by ComplexNumber on 2007-05-15
> **alainhenry said:**
> Great, thank you!  

I don't have a ~/.fonts directory.  Do I just have to create it ? There is a .fontconfig though.  

Alain
you can either 
1) place them directly in ~/.fonts directory. if there isn't one, create it manually.
or
2) go to main menu -> System -> Administration -> Fonts, then click on 'Details' then 'Open font window' and place them in there. 

they both end up in the same place anyway. when you chose the 2nd option, it creates the .font directory if there isnt one already.

i personally just place them in .font because i find it easier.

---

### Post by alainhenry on 2007-05-15
OK, I managed to get one new font loaded.  Funny, it works with Inkscape, but OpenOffice does not display the newly loaded fonts.  

Just for the reference, you should go in "main menu" -> System -> Preferences -> Font, hit "Details" and then "Go to font Folder"
And the folder for the new fonts is ~/.fonts

Thanks

Alain

---

### Post by Oki on 2007-05-16
To replace the msttcorefonts try those new once from RedHat(very good, but still boring): [https://www.redhat.com/promo/fonts/](https://www.redhat.com/promo/fonts/)

---

