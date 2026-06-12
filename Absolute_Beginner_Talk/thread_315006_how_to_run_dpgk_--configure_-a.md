---
title: "how to run dpgk --configure -a"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by broekskw on 2006-12-08
ok now this problem(keep trying to get sound going now have this error comming up in terminal all the time) how do you run this from terminal , i did try a command that give me a message  dpgk -requested operation requires superuser privilege. ok so how do i become superuser?????. alos this package is on my auto update but also get the same message to manually run;help](*,)

---

### Post by taurus on 2006-12-08
Applications -> Accessories -> Terminal
```
sudo dpgk --configure -a
```

---

### Post by broekskw on 2006-12-08
thanks but command not found in terminal,boy did i screw this thing up?????](*,)

---

### Post by taurus on 2006-12-08
Can you tell me exactly what you typed in a terminal?

---

### Post by obsidion on 2006-12-08
> **broekskw said:**
> ok now this problem(keep trying to get sound going now have this error comming up in terminal all the time) how do you run this from terminal , i did try a command that give me a message  dpgk -requested operation requires superuser privilege. ok so how do i become superuser?????. alos this package is on my auto update but also get the same message to manually run;help](*,)

you run as superuser from the command line by putting sudo before the command

---

### Post by broekskw on 2006-12-08
yes i just copied your command and past and then hit enter

udo dpgk --configure -a

and then i also tried 

dpgk --configure -a and keep getting 

pgk -requested operation requires superuser privilege.

thanks:mrgreen:

---

### Post by taurus on 2006-12-08
> **broekskw said:**
> yes i just copied your command and past and then hit enter

udo dpgk --configure -a

and then i also tried 

dpgk --configure -a and keep getting 

pgk -requested operation requires superuser privilege.

thanks:mrgreen:
It's 

```
sudo dpgk --configure -a
```
](*,)

---

### Post by broekskw on 2006-12-08
ok thanks got it to work with your help. took a look at your command and it should read  sudo dpkg --configure -a  and not sudo dpgk. so thanks again:mrgreen: :mrgreen: 

now back to trying to install my](*,) ](*,) ](*,) ](*,) ](*,)  sbawe64 sound driver

---

### Post by broekskw on 2006-12-08
one more question the command sudo makes you the superuser??

---

### Post by civic_si on 2006-12-08
yes it makes you the superuser, you will get used to entering it after a while.

---

### Post by brt on 2006-12-08
> **broekskw said:**
> one more question the command sudo makes you the superuser??

no. 

"sudo program" just executes the "program" as superuser

if you want to switch completly to superusermode (having a superuser-shell) use sudo -s, but staying as superuser is a risky thing, so sudo programm name is the preferred way :)

---

### Post by obsidion on 2006-12-08
> **civic_si said:**
> yes it makes you the superuser, you will get used to entering it after a while.

  Another keypress you may find very useful in a terminal is the tab key, this will autocomplete. Very useful for installing a package with a long name or just finding all the commands that are similar eg typing dpk and hitting tab twice will give you a whole list of special commands.

---

### Post by broekskw on 2006-12-08
thanks all for all your help.but i think it's time to do a fresh reinstall of ubunto 6.10 to see if then it will find my sound card.i have tried everything possible to get both sound blaster sbawe 64 and sound blaster sb16 to work but keep getting 

 aplay -l
aplay: device_list:222: no soundcards found...


and have tried to install manually but no go. so thanks to all here for trying to get me going.still not giving up on ubuntu just yet](*,) ](*,) 
:mrgreen: :mrgreen: :mrgreen: :mrgreen: :mrgreen:

---

