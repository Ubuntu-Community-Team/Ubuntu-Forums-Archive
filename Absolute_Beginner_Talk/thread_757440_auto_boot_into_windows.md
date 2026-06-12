---
title: "auto boot into windows"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by WW3 on 2008-04-16
is there a way to auto boot into windows without the option to choose the os to boot*? while still keeping the dual boot. thanks












*not my idea

---

### Post by Tatty on 2008-04-16
Are you saying you dont want the grub menu to appear at all?  

I believe you can edit the /boot/grub/menu.lst file to alter the selection time to 0, but how would you be able to select to boot a different operating system without a menu?

---

### Post by Lolicon on 2008-04-16
you just have to edit your bootup. I changed my GRUB which is basicly a text file that allows you to choose your OS. Its quick and easy, just move your windows to the top.

---

### Post by WW3 on 2008-04-16
i just want to hide the grub menu and auto login to windows os... and maybe sometimes ubuntu*

*secretly

---

### Post by Tatty on 2008-04-16
I just dont see how you are going to be able to boot into ubuntu if you hide the menu allowing you to do so.  But im no expert at grub, maybe someone can come up with a solution.

As I say, to hide the menu, you will need to alter your /boot/grub/menu.lst file to set the time the menu is up to 0

---

### Post by WW3 on 2008-04-16
i have to remove it or hide it or make it so my family can log into it... i just want to hide it

---

### Post by garyed on 2008-04-16
Also In your menu.lst file  after setting Windows as your default boot change: 

timeout  0
hiddenmenu

You should be able to take away the # in front of  #hiddenmenu.
The only way you can boot ubuntu this way will be to hit "esc" at the precise moment the word grub flashes on the screen. I usually hit "esc" a few times before just so I don't miss it.

---

### Post by Tatty on 2008-04-16
> **WW3 said:**
> i have to remove it or hide it or make it so my family can log into it... i just want to hide it

You can set it to boot into windows without hiding the menu you know...

---

### Post by ad_267 on 2008-04-17
Yeah what's wrong with just setting the default option to windows? You can hide the menu so you have to press escape to see it, but what's the point of a timeout of 0? Set it to at least 1 so that you can actually boot into Ubuntu if you want to

```
gksu gedit /boot/grub/menu.lst
```
then change this line:
```
default         0
```
to whatever number your windows is in the list

Remove the hash from in front of this if you want to hide the menu:
```
# hiddenmenu
```

And change the timeout to whatever you want, but 0 is a bad idea
```
timeout 8
```

---

### Post by garyed on 2008-04-17
I agree its better to set the time higher than "0" because it makes it difficult to get to the grub menu if you don't want to boot to the default OS but its probably the best  way to hide the menu
& it sounds like a major concern for the OP. Any number other than "0" will probably show a prompt to "hit  esc to view the menu" or something like that for whatever the timeout is set to.

---

