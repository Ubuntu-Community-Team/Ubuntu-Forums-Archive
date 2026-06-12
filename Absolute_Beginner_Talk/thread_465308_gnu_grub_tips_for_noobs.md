---
title: "gnu grub tips for noobs"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by dan171717 on 2007-06-05
here is a short guide to editing the entries in the gnu grub. it is a simple operation that nomatter how mutch of an noob you are you can do.

step 1. navigate to /boot/grub and make a backup of menu.lst somewere memorable

step 2.

type ```
gksudo gedit /boot/grub/menu.lst
```

step 3.

type your password if you have one.

step 4.

scroll near the bottom where  you will see for exaple

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e6dc7755-2c0d-453b-8b82-7df148630d72 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

step 5.

change the title to what you want

if you have done a kernel update then you will have a cluttered grub menu. it is tempting to delete them :p _*but dont!*_ just put a # after the title and the other things so our exaple looks like this

```
## ## End Default Options ##

#title		Ubuntu, kernel 2.6.20-16-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e6dc7755-2c0d-453b-8b82-7df148630d72 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-16-generic
#quiet
#savedefault
```

just remeber the golden rule about this or anything as root is not to change or edit what you dont understand.

happy editing!!;)

---

### Post by init1 on 2007-06-05
Nice guide. I might link to that if the issue appears in another thread.

---

### Post by Adramelech on 2007-06-05
Can be step 1: Make a backup copy?

---

### Post by sneeker on 2007-06-05
wait, wat does it do after you do it?

---

### Post by ubuntu27 on 2007-06-06
> **sneeker said:**
> wait, wat does it do after you do it?

"#" means to ignore it. 

So, if you add # to the entry of that Operating SYstem, then when you boot your computer, you won't be able to see them. It is hided. 

It is useful when you have too many Linux kernels and you only use one.

Example: See that both are Ubuntu, but with different Linux Kernel version?  # is added to the old one so you won't have to see them in the Grub many when you start the computer :)

**(Don't copy what's in here, I am showing just as an example)**

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e6dc7755-2c0d-453b-8b82-7df148630d72 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault


#title		Ubuntu, kernel 2.6.18-12-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.18-12-generic root=UUID=e6dc7755-2c0d-453b-8b82-7df148630d72 ro #quiet splash
#initrd		/boot/initrd.img-2.6.18-12-generic
#quiet
#savedefault

---

### Post by dan171717 on 2007-06-06
> **ubuntu27 said:**
> "#" means to ignore it. 

So, if you add # to the entry of that Operating SYstem, then when you boot your computer, you won't be able to see them. It is hided. 

It is useful when you have too many Linux kernels and you only use one.

Example: See that both are Ubuntu, but with different Linux Kernel version?  # is added to the old one so you won't have to see them in the Grub many when you start the computer :)

**(Don't copy what's in here, I am showing just as an example)**

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e6dc7755-2c0d-453b-8b82-7df148630d72 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault


#title		Ubuntu, kernel 2.6.18-12-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.18-12-generic root=UUID=e6dc7755-2c0d-453b-8b82-7df148630d72 ro #quiet splash
#initrd		/boot/initrd.img-2.6.18-12-generic
#quiet
#savedefault

thats what i said it means it hides all the old kernels and kernel recovery modes.

---

### Post by dan171717 on 2007-06-06
> **sneeker said:**
> wait, wat does it do after you do it?

it renames the enteries in the grub so when you turn on  te comp you wont see

ubuntu kernel 2.6.xxxxxxx

microsoft windows xp

you would see what you chnged the titles to. e.g.

ubuntu 7.04

evil corporation windoze xp

---

### Post by Outrunner on 2007-06-06
```
sudo gedit /boot/grub/menu.lst
```

would be 

```
gksudo gedit /boot/grub/menu.lst
```

We use gksudo instead of sudo for graphical apps

---

### Post by dan171717 on 2007-06-06
> **Adramelech said:**
> Can be step 1: Make a backup copy?

good point. make a backup if you want but i have done this a few times and never had problems.
i did say be carefull when using root.
it could only go wrong if you change anything other than the titles.i will add it to the guide

thanks for bring it up!

---

### Post by dan171717 on 2007-06-06
> **Outrunner said:**
> ```
sudo gedit /boot/grub/menu.lst
```

would be 

```
gksudo gedit /boot/grub/menu.lst
```

We use gksudo instead of sudo for graphical apps

thanks, i didnt know that. but it still works as fine as


sudo gedit ???

---

### Post by Outrunner on 2007-06-06
[There is a difference, actually.]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Papi-KB7VGW on 2007-06-06
Is there a reason that no one talks about using Root Terminal located in >Applications>System Tools?  That way you don't have to type sudo for any commands.

---

### Post by dan171717 on 2007-06-06
> **Outrunner said:**
> [There is a difference, actually.]("http://www.psychocats.net/ubuntu/graphicalsudo") thanks for that i will change it soon

---

### Post by dan171717 on 2007-06-06
> **Papi-KB7VGW said:**
> Is there a reason that no one talks about using Root Terminal located in >Applications>System Tools?  That way you don't have to type sudo for any commands. ah but in feisty and maby edgy the root terminal is not there by defalt?

i know about it and will put mine back.

i have noticed that there is a root terminal in dapper by defalt.

---

### Post by Papi-KB7VGW on 2007-06-06
Oh yeah, I just remembered that you have to select it thru Main Menu!  (Another Senior moment I guess)  It really has made my life easier.

---

