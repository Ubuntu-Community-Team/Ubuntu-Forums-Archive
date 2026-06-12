---
title: "flash9"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-01-04
i used the how to here : [http://www.ubuntuforums.org/showthread.php?t=202537&highlight=flash](http://www.ubuntuforums.org/showthread.php?t=202537&highlight=flash) 
and got everything good until i needed flash 9 and i went back to it and did it up right now i have no sound...?


any help???


thanks in advance

---

### Post by pissedoffdude on 2007-01-04
try getting flash 9 beta 2 from [http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html") now to remove the old flash do ```
sudo rm /usr/local/firefox32/plugins/libflashplayer.so
``` just in case you had installed flash 7 try ```
sudo rm /usr/local/firefox32/plugins/flashplayer.xpt
``` now we will install the flash 9 beta so ```
cd Desktop
tar zxfv FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/local/firefox32/plugins
```

---

### Post by antgul3382 on 2007-01-04
thanks for the help but i still have no sound???... whats wrong it was fine with flash 7 now it sux?!??1](*,)

---

### Post by antgul3382 on 2007-01-04
can anyone help or know of a place i can find it???](*,)

---

### Post by pissedoffdude on 2007-01-04
> **antgul3382 said:**
> can anyone help or know of a place i can find it???](*,)

u can get flash 7 here [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") just be sure to remove flash 9

---

### Post by antgul3382 on 2007-01-04
so  are you telling me i justed messed up my flash, and if i have flash 7 i can see and hear alm,ost everything and with flash 9 i cand see everything but hear nothing??? wtf is that???:evil:



ok you got me confused im not looking for flash 7 im looking for help on flash 9 i need the sound i got video but no sound

---

### Post by pissedoffdude on 2007-01-04
> **antgul3382 said:**
> so  are you telling me i justed messed up my flash, and if i have flash 7 i can see and hear alm,ost everything and with flash 9 i cand see everything but hear nothing??? wtf is that???:evil:



ok you got me confused im not looking for flash 7 im looking for help on flash 9 i need the sound i got video but no sound

Well u said that u can hear with flash 7 but not 9.  Im just trying to help here.  It seems like it worked fine with flash 7 but not 9.  Well since you want help with flash 9 try rebooting and then check if you have sound

---

### Post by TooRight on 2007-01-04
Maybe try uninstalling 9 and then use Automatix to reinstall it

---

### Post by Irony on 2007-01-04
Enable backports in synaptic and install flashplayer 9.

---

### Post by antgul3382 on 2007-01-04
autromtix doesnt have it i have a very limited list in there for some reason  and everything is enable in synaptic but no flash

---

### Post by pissedoffdude on 2007-01-04
> **antgul3382 said:**
> autromtix doesnt have it i have a very limited list in there for some reason  and everything is enable in synaptic but no flash

have u tried installing swiftfox and swiftfox plugins using automatix

---

### Post by zekopeko on 2007-01-04
try this repo.

# Treviño&#8217;s Ubuntu edgy Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" software: aMule, amsn, mplayer, moto4lin, flashplugin & flashplayer (9.x)&#8230;
# Further informations: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

---

### Post by antgul3382 on 2007-01-04
heeeeeeeeeeeeelp?!?!?!?!?!?!

---

### Post by antgul3382 on 2007-01-05
> try this repo.

# Treviño’s Ubuntu edgy Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" software: aMule, amsn, mplayer, moto4lin, flashplugin & flashplayer (9.x)…
# Further informations: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

im not sure what to do with this????

---

### Post by antgul3382 on 2007-01-05
well i had no luck with repositories, i dont really even know what they are. i installed swiftfox and plugins and it works fine with flash 9. what is the difference between swiftfox and firefox if any???:-k

---

### Post by Irony on 2007-01-05
Do;

[PHP]gksudo gedit /etc/apt/sources.list[/PHP]

and add the following line (Dapper);

[PHP]deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse[/PHP]

Then open up synaptic and hit the reload button then search for the flash plugin.

---

### Post by antgul3382 on 2007-01-05
i now have no sound with flash 9 on both firefox and swiftfox.!!!!!!!!also after install of switfox java doesnt work, i cant use azureus, wtf is the problem here???

---

### Post by Irony on 2007-01-05
Just noticed that you seem to have 64 Bit Edgy installed, so you need to post this in the 64 bit section and read 64 bit stuff regarding installs.

Personally I used 32 bit Dapper on my 64 bit chip because there's less problems with installing stuff.

---

### Post by 2_4GHz on 2007-01-05
> **Irony said:**
> Do;

[PHP]gksudo gedit /etc/apt/sources.list[/PHP]

and add the following line (Dapper);

[PHP]deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse[/PHP]

Then open up synaptic and hit the reload button then search for the flash plugin.

This fixed my Flash sound problem. I have been using Ubuntu for 2 months now.So I am still a newb.Actually I think this is my first post,since install. No problems here.8)  
It is great and so is the help on these forums. If folks would just take time too read and learn.
:-k

---

### Post by antgul3382 on 2007-01-05
ok its working good asgain with swiftfx......so does anyone know the difference between swiftfox and firefox????

---

### Post by Efwis on 2007-01-05
swiftfox is just a lighter version of FF. some say it runs faster, although I personally saw no difference between FF2 and Swiftfox.

As for your Flash 9 issues, remember Flash 9 is still in Beta. which means it is not completely stable and may not work correctly in some machines. (beta and Alpha = Testing)

---

