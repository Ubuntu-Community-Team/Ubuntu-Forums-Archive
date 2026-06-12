---
title: "No splash screen on boot up..."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Roen hayden on 2008-03-31
Hello i just installed ububtu 7.10 on a dell inspiron 1501 and when i boot up i have no splash screen.  And then after its done booting it comes to the login page.  

is the the HOW-to i have to follow to get  this to work?
[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

If this is the cause will it hurt my machine if I just leave it alone?

---

### Post by YotoshiWii on 2008-03-31
I'm on an IBM thinkpad T40 and i have no boot screen. I just learned to accept it, and no it wont harm your machine. :D

---

### Post by Roen hayden on 2008-03-31
> **YotoshiWii said:**
> I'm on an IBM thinkpad T40 and i have no boot screen. I just learned to accept it, and no it wont harm your machine. :D

yea ok i just wanted to know if it would harm my hardware or something  cause i could do that work around  but if it wont do anything then ill just leave it alone.  How long has yours been like that?  And can someone else confirm this I just want a second opinion.

---

### Post by YotoshiWii on 2008-03-31
for around 3 months or so. It doesnt really bother me at all. The OS works all awesome - so i'll let it slide that there is no boot screen. I mean, is that orange bar actually that vital to your OS? instead of watching it scroll back and forth during boot-up, make yourself a cup of Ubuntu.\\:D/

---

### Post by Roen hayden on 2008-03-31
> **YotoshiWii said:**
> for around 3 months or so. It doesnt really bother me at all. The OS works all awesome - so i'll let it slide that there is no boot screen. I mean, is that orange bar actually that vital to your OS? instead of watching it scroll back and forth during boot-up, make yourself a cup of Ubuntu.\\:D/



maybe it is important lol.  the only thing i can think of that would be bad is that if something does go wrong on boot up i wouldn't know cause the bar did not freeze.....

---

### Post by YotoshiWii on 2008-03-31
> **Roen hayden said:**
> maybe it is important lol.  the only thing i can think of that would be bad is that if something does go wrong on boot up i wouldn't know cause the bar did not freeze.....

Haha, i guess thats true. After my upgrade i shall fix my boot screen.:lolflag:

---

### Post by Roen hayden on 2008-03-31
> **YotoshiWii said:**
> Haha, i guess thats true. After my upgrade i shall fix my boot screen.:lolflag:

i just did it works great but when i restarted it hung so i had to force shut-down but now i have rebooted it couple of times. so its working now.

---

### Post by joshrobinson on 2008-03-31
try this

```
sudo gedit /boot/grub/menu.lst
```

towards the bottom you will see a section that resembles the following, just note im running hardy with a different kernel, so just look for a similar section

```
title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=af922c34-f5fe-41b4-a6c3-925b0b1fb558 ro quiet[COLOR="Red"] splash[/COLOR]
initrd		/boot/initrd.img-2.6.24-12-generic
quiet
```

make sure it says splash like mine does
then

```
sudo gedit /etc/usplash.conf
```
and input your resolution
then run this command
```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

### Post by kbless7 on 2008-04-01
Also, as it turns out, putting the correct screen resolution in the splash configuration file speeds up the booting process. By boot time went from 70 to 50 seconds just by changing the resolution.

---

### Post by blampars on 2008-04-01
> **kbless7 said:**
> Also, as it turns out, putting the correct screen resolution in the splash configuration file speeds up the booting process. By boot time went from 70 to 50 seconds just by changing the resolution.

i had the no boot screen problem as well, once i fixed it i did notice a significant decrease in boot time, not to mention that with all the messing around i've been doing its nice to watch the bar load just to make sure i'm not froze up at boot ;)

i'm actually trying to find the thread i seen previously that helped me fix my splash screen problem. there's a utility you can get that does it for you without you having to mess with config files yourself. I just can't remember what the name of it is, and I dont have the link to that thread. and i'm on my girlfriends xp machine right now so i cant look :(

---

### Post by pieisgood4589 on 2008-04-01
> **joshrobinson said:**
> try this

```
sudo gedit /boot/grub/menu.lst
```

towards the bottom you will see a section that resembles the following, just note im running hardy with a different kernel, so just look for a similar section

```
title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=af922c34-f5fe-41b4-a6c3-925b0b1fb558 ro quiet[COLOR="Red"] splash[/COLOR]
initrd		/boot/initrd.img-2.6.24-12-generic
quiet
```

make sure it says splash like mine does
then

```
sudo gedit /etc/usplash.conf
```
and input your resolution
then run this command
```
sudo update-usplash-theme usplash-theme-ubuntu
```


Yes, this way works, and the usual resolution would be the first variable - 1024
second variable- 768

---

### Post by darrensnospam on 2008-04-12
My monitor is 1680x1050 - widescreen.
Hello folks. I followed the instructions above and I can see that the resolution on my boot screen is much crisper but it's still squatted. Meaning that it's not as tall as it should be. Instead of the symbol being in the shape of a circle, it's more like an oval.
Thoughts?

---

### Post by darrensnospam on 2008-04-13
Found the answer here:
[http://www.gnome-look.org/content/show.php/Red+Hardy+Usplash?content=78762](http://www.gnome-look.org/content/show.php/Red+Hardy+Usplash?content=78762)

---

### Post by sayakb on 2008-04-13
This might be a non-conventional method, but it worked for a dell inspiron 1520: I installed startupmanager: ```
sudo apt-get install startupmanager
``` 
Then I started it from System->Administration->Startup manager. There I could change the resolution without messing with the .conf files. I tried different resolutions, while 1280x800 worked for me.

---

