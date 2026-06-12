---
title: "help i killed usplash"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by janbockaert on 2006-11-21
I think i read every thread about usplash in this forum, and none of them could help me so far. So please excuse me for yet another usplash thread.

Thing is, i lost my usplash; After installing kde (kubuntu-desktop), Kubuntu changed my usplash to the kubuntu-one. (and killed my gnome theme, but that i could solve)

i tried to fix it using this guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_alternate_boot_splash_screen](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_alternate_boot_splash_screen)

and that changed the spalsh when shutting down, but when powering the pc back on, i still had the kubuntu splash.

I should have stopped there, but instead, i tried this guide:
[http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash)

and after i was done with that guide, i lost usplash completely. All i get is a blinking cursor, and some text, before i see x. both on power on and power down.

after that, i typed in uspslash in this forums searchbox, and tried every solution that was available here. Grub seems to be ok, the alternatives seems to be ok, i reinstalled the usplash-artwork over and over again,... but nothing seems to work.

So, if anyone knows why kubuntu-splash did not want to leave on startup, and why this page: [http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash) helped me kill the splash completely, please let me know.

thanks Jan

---

### Post by CupofDice on 2006-11-21
First and foremost Usplash is the screen after Grub, and before the Login window right? All these names with splash can get a bit confusing.:) 
If so, I had a similar problem like you.
[http://ubuntuforums.org/showthread.php?t=269262](http://ubuntuforums.org/showthread.php?t=269262)
I vaguely (VAGUELY) remember doing this command
```
sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so sudo dpkg-reconfigure linux-image-$(uname -r)
``` from [http://ubuntuos.com/2006/02/howto-change-the-default-usplash-colors](http://ubuntuos.com/2006/02/howto-change-the-default-usplash-colors). Now understand that I am a noobie to linux, and I really can't remember how I fixed it. Either it was the command before, or maybe I was playing around with copying to see what would work. I don't think it was GrubEd since that has nothing to do with usplash, and I am pretty sure I didn't find a usplash.conf file in /etc on my livecd, so I remember that not helping. Also I am on Gnome. One more also.:( Now that I think about it I could have been using breezy at the time, and upgraded to dapper (which could have fixed the problem). Then again I could have been using dapper, but only had the breezy cd. Hmm. In other words use that command at your own will (though I think there is no risk in it). Hope it helps.:(

PS- Oh and check out gnome-splashscreen-manager and GrubEd. I now rely on these good safe reliable programs with 'GUIs':) after I was taught my lesson.

Edit- Just read that site you were following and recognize they have those commands there, so chances are you probably have used them already. Ala my shaky advice just because useless.:)

---

### Post by dpar on 2006-11-21
Hi.....I just did;

sudo update-alterntives --config usplash-artwork.so

then choose the default splash, then;

sudo dpkg-reconfigure linux-image-'uname -r'

Then it was back to normal

---

### Post by janbockaert on 2006-11-22
sudo update-alterntives --config usplash-artwork.so does not work for me. :( any other idea's? anything i could have done using the [http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash) howto? This howto has an undo command, but that one is also not working.

---

### Post by janbockaert on 2006-11-22
can it be that this code from the howto is preventing me from switching back to the original usplash?

sudo cp usplash-fix.so /usr/lib/usplash/usplash-fix.so sudo ln -sf /usr/lib/usplash/usplash-fix.so /usr/lib/usplash/usplash-artwork.so

---

### Post by Jimmy_r on 2006-11-22
Here we go again...Why do I have a feeling of Deja Vu? :p 

Do these commands:
```
cd /usr/lib/usplash/
ls -l
```
And post the output here.

---

### Post by janbockaert on 2006-11-22
I know, not the i'm not the first one :)

```
totaal 2624
lrwxrwxrwx 1 root root      35 2006-11-22 17:26 usplash-artwork.so -> /usr/lib/usplash/usplash-default.so
-rwxr-xr-x 1 root root   34637 2006-11-21 21:52 usplash-fix.so
-rw-r--r-- 1 root root 2643804 2006-10-25 14:40 usplash-theme-ubuntu.so

```

hope you can help

Jan

---

### Post by Jimmy_r on 2006-11-22
Try these:

```
sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-artwork.so

sudo update-initramfs -u
```

---

### Post by janbockaert on 2006-11-22
It worked, i have my usplash back! :) Thank you so much jimmy! (and everyone else) Your support is what makes ubuntu the number one distro.

Thanks, thanks, thanks!:KS

---

### Post by fcu423 on 2008-07-08
> **Jimmy_r said:**
> Try these:

```
sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-artwork.so

sudo update-initramfs -u
```
Hi man, i was changing the usplash image but i deleted the usplash-artwork.so.
I tried with dpkg-reconfigure usplash and nothing happened.
I reinstall the usplash en nothing happened too.

Then i saw your post and did what you said and the usplash-artwork.so was created again. But i can do 
> sudo update-alternatives --config usplash-artwork.so 
because it says: "there is no program that provides usplash-artwork.so"

I don't know what can i do with this, i need to restore that file.
I am reading and i am going to do it with starup manager, but i still want to fix that file.

Thanks if you or someone can help

---

