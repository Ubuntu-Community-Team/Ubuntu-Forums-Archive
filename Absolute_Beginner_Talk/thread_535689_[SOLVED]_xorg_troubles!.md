---
title: "[SOLVED] xorg troubles!"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-08-26
ok i've had alot problems with my xserver but this one just has me stumped.  i was adding some stuff to be able to use S-Video out then when i restarted my comp i got the traditional xserver error and when i go into recovery mode i get the command line and do
> 
cd /etc/X11
dir
cp xorg.conf xorg.conf.20070803204934
/etc/init.d/gdm restart


that should've restored the xorg file to one of the previous files, i have tried several but none seem to work!  

then i did: 
> 
sudo dpkg-reconfigure xserver-xorg 

and that got me half way!  i get my custom log in screen but when i log in all i get is a white screen!

I am wondering if anyone can shed some light on this for me! 

Thanks in advance for any help or suggestions, Alain

and if any of you would like give some input on editing the xorg file for S-Video use with an intel 945 graphics that would excellent as i've had no luck so far.

---

### Post by ddrichardson on 2007-08-26
you have the cp args the wrong way round - that would back up your current xorg.conf

---

### Post by Majorix on 2007-08-26
Hehe another windows user. I understood that when I saw the "dir" in your tries to list the files :)

Anyways, you made a small mistake.

You have to replace the xorg.conf file with the old one as follows:
```
sudo mv xorg.conf.datetimeetchere xorg.conf
```

Then when you restart you will have the old xorg.

I can't help you with s-video though because I don't even know what it does :)

---

### Post by S15_88 on 2007-08-26
hahah oh man, thanks for pointing that out let me switch that around and give it a try!

---

### Post by S15_88 on 2007-08-26
i'm still getting the white screen even after doing the:
> 
sudo mv xorg.conf.datetimeetchere xorg.conf


---

### Post by S15_88 on 2007-08-26
man now i don't even get to my log in screen i'm still stuck with the xserver error and then command line!  blahhhhhh!  any ideas?  why does ubuntu dislike intel 945 so much, it is a lame-o graphics card but my laptop shell is too small to physically fit an ATI or nvidia in it!

---

### Post by bjarneh on 2007-08-26
sudo dpkg-reconfigure xserver-xorg

usually does the trick, never experienced any problems with an intel-card my self...
what does the .xsession-erros file say?

---

### Post by S15_88 on 2007-08-26
ok well i did sudo dpkg-reconfigure xserver-xorg again and got my log in screen back, but still when i log in all i get is a white screen!  how can i recover my desktop!

Thanks, Alain

---

### Post by ddrichardson on 2007-08-26
You say you added stuff to get s-video to work, was that just in xorg.conf or is there something added to session-manager?

---

### Post by S15_88 on 2007-08-26
just the xorg file, wat's ticking me off is that i log in from my custom log in screen and then i see my mouse pointer and then two black boxes start to appear exactly where my panels are then BAM! white screen haha and i've referenced a few previous xorg files but they don't even get me as far as just reconfiguring it.

Thanks again for the help!  hopefully i can resolve this soon cause if i boot to vista it sends me on an infinite reboot loop!  so i still have that to sort out after!

---

### Post by S15_88 on 2007-08-26
well i'm jus flat out of ideas i've tried everything!  anyone got any thoughts, all ideas welcome!

Thanks, Alain

---

### Post by fig_jam_uk on 2007-08-31
Just a thought do you have Beryl installed? As in the past when its had plroblems loading for me I have just got a white screen and pointer. Dont know if this will help but have you tried logging into failsafe mode, on login screen select options and the select display manager. Hope this helps.

---

