---
title: "Make Ubuntu boot automaticaly?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-25
B4 I had vista,xp and Ubuntu, and i had multiboot GRUB menu.
Now both xp and vista dont work, and I use only Ubuntu.
Can I make it boot automatically without GRUB OS selection appear

---

### Post by stchman on 2008-03-25
> **munch3 said:**
> B4 I had vista,xp and Ubuntu, and i had multiboot GRUB menu.
Now both xp and vista dont work, and I use only Ubuntu.
Can I make it boot automatically without GRUB OS selection appear

Set the timeout to 0 in the menu.lst in /boot/grub

You can also load StartUpManger as there are many Grub settings.

[http://www.stchman.com/tools/startupmanager_1.9.10-1_all.deb](http://www.stchman.com/tools/startupmanager_1.9.10-1_all.deb)

---

### Post by FrozenFox on 2008-03-25
Open the terminal, 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst
(replace gedit with kwrite if youre on kubuntu)

set the timeout option to however many seconds you want grub to wait before loading your default OS. if ubuntu is your default, you can set grub to timeout 0.

---

### Post by mali2297 on 2008-03-25
```

sudo nano /boot/grub/menu.lst 

```
Change the line
```

timeout         5

```
to
```

timeout         0

```

---

### Post by Iowan on 2008-03-25
Don't forget to **sudo update-grub** when you're finished...

---

### Post by om1 on 2008-03-25
easiest thing is to open add/remove and search for startup-manager and install it... it is very easy to use 

but if you want to learn how to do it manually follow their instructions for grub

---

### Post by stchman on 2008-03-26
> **om1 said:**
> easiest thing is to open add/remove and search for startup-manager and install it... it is very easy to use 

but if you want to learn how to do it manually follow their instructions for grub

I see that it is in the Gutsy repos but not the Feisty repos.

---

### Post by munch3 on 2008-03-26
I set timeout to 0 in Start-Up amnager (I got 8.04) works well now

---

