---
title: "Login B0rked D:"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Simran on 2007-05-24
hi,

I have managed to break my login somehow. Everytime the login screen appears as soon as i  press a key the screen goes black and the x server resets ( or looks like it does )

I thaught it could be a faulty theme so i used the cl to replace the new GDM login theme with the default ubuntu one but i still get the same problem. 

Any ideas D: ? 

Can offer more info if needed

Thanks Simran

---

### Post by lamalex on 2007-05-24
do any error messages pop up? Try this, go to the console to log in (control + alt + f[1-6]) and log in, then type
```

/etc/init.d/gdm stop
startx

```
and see if you can get back in.

---

### Post by Simran on 2007-05-24
nice one, thanks it bypassed the login screen and i'm in now :D!!!!!

Would i have to do this everytime to login ? 

Many thanks Simran

---

### Post by lamalex on 2007-05-24
look in the X server logs and see why your X server crashes. /var/log/Xorg.log is the xorg log

---

### Post by Simran on 2007-05-24
This is really odd, every time i try to type something the nautilus window closes and re opens  just like the GDM kinda reset. and terminal wont load up just says loading terminal then dissapears.

but i'll try that that file now

Simran

---

### Post by lamalex on 2007-05-24
your problem doesn't sound like an X problem anymore it sounds like something is messed up in nautilus possible. look in dmesg and see if it's giving you any errors.
```

dmesg

```

---

### Post by Simran on 2007-05-24
Using CTRL + ALT + F3 i type dmesg, is there a way to scroll up and see the whole thing :S ? and any pointers on what an error would look like ? 

I would paste the whole thing here if i could but i'm on another laptop next to the broken one posting here

saves me typing the whole thing out :P

your help is much appreciated, thanks

Simran

---

### Post by lamalex on 2007-05-24
page-up should move you up, or possibly it's shift+page-up. Just look for anything that looks like an error or says nautilus or gdm or anything like that. Are you using beryl/compiz or just metacity? look for any of those in there as well as possibly X server errors you could also dmesg |less

---

### Post by taurus on 2007-05-24
```
dmesg | more
```
Hit the space bar for the next 24 lines.

---

### Post by Simran on 2007-05-24
ok thanks, i had a look through nothing that stands out as an error or to my limited knowledge as an error. I am using the desktop effects that are in 7.04.

there are only a few bits like 
ibm_acpi: ec object not found
apm: BIOS not found 
ipw3945: association process canceled 

etc.. 

think its less hastle to format ?

Simran

---

### Post by lamalex on 2007-05-24
heh it's your data. For me formatting is a major hassle. Try disabling desktop effects as they may be the problem.

---

### Post by Simran on 2007-05-24
yeah disabled effects and still the same problem. 

I think i'll just format. 

got nothing to loose, just playing / breaking trying to learn thats.

thanks for your time anyways xD 

Simran

---

