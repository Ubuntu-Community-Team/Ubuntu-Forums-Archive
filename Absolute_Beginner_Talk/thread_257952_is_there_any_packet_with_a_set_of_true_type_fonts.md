---
title: "is there any packet with a set of true type fonts?"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-09-15
It's one thing that i must admit its anoying... on windows i didnt have any aliasing problems...

any true type pack of fonts on apt repositories?
the windows fonts would be cool as i am already used to them...

if not a packet how can i install and where can i find true type fonts?

I heard it has to do with the kind of screen... is there any differece betwin using a TFT or A CRT when it comes to display fonts?

thx in advance

---

### Post by Najand on 2006-09-15
If you have Universe Repository, you can have apt (Any of Synaptic, apt-get, aptitude) to install ms TTF Fonts for you. 
If you have Universe, Search for msttcorefonts in synaptic.
If you haven't, Click:
System -> Administration -> Software Properties
Then Check all unchecked options.
Close it...
Open Synaptic... Click Reload, then look for msttcorefonts.

---

### Post by pedrotuga on 2006-09-15
thanks...
aaa...
i am using currier on the console with monocromatic setting...
I intend to use a monocromatic scheme... so... any ideas on how to install tahoma font?

---

### Post by Najand on 2006-09-15
Do you mean Gnome-Terminal?

---

### Post by Najand on 2006-09-15
tahoma font is available in package: "msttcorefonts"

---

### Post by pedrotuga on 2006-09-15
> **Najand said:**
> tahoma font is available in package: "msttcorefonts"

??? i installed that package and so far i dont have tahoma

---

### Post by Najand on 2006-09-15
Ah! sorry... It seems it is not included... Are you on a dual boot computer? If so it is very easy to copy it from Windows and install it on Linux.

---

### Post by pedrotuga on 2006-09-15
> **Najand said:**
> Ah! sorry... It seems it is not included... Are you on a dual boot computer? If so it is very easy to copy it from Windows and install it on Linux.

yep... i am.
ok... so in wich folder should it go?

BTW... i set the render to monocromatic... used verdana everywhere exept for the fixed length one which i set to currier new.
It looks like really cool... so far no rendering problems.
in the gnome terminal i also use currier new... i got so used to putty that i cant get used to any other console look.

---

### Post by RoyArne on 2006-09-15
Tahoma can be downloaded from [http://fonts.appliedlanguage.com/tahoma_font.shtml]("http://fonts.appliedlanguage.com/tahoma_font.shtml"). You can place it in

**~/.fonts**

---

### Post by pedrotuga on 2006-09-15
> **RoyArne said:**
> Tahoma can be downloaded from [http://fonts.appliedlanguage.com/tahoma_font.shtml](http://fonts.appliedlanguage.com/tahoma_font.shtml). You can place it in

**~/.fonts**

i would like to have it avaluable to everybody...
but also, that directory does not exist,
ls -a
and it showe a brunch of folders but no .fonts

---

### Post by RoyArne on 2006-09-15
For a local install you can just **mkdir ~/.fonts**. I have never tried to install fonts globally (in /usr/share/fonts), but this page has some information: [http://www.indlinux.org/wiki/index.php/FontInstallation]("http://www.indlinux.org/wiki/index.php/FontInstallation")

---

### Post by jrcmuniz on 2006-09-15
> **RoyArne said:**
> For a local install you can just **mkdir ~/.fonts**. I have never tried to install fonts globally (in /usr/share/fonts), but this page has some information: [http://www.indlinux.org/wiki/index.php/FontInstallation]("http://www.indlinux.org/wiki/index.php/FontInstallation")

Have you tried:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Extra_Fonts](http://ubuntuguide.org/wiki/Dapper#How_to_install_Extra_Fonts)

from [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) ?

Hope this helps.

Joao.

---

### Post by pedrotuga on 2006-09-18
thax evedybody.. from now on i will install al the fonts on /usr/share/fonts

---

