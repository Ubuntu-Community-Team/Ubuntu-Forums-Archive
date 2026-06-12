---
title: "Grub - no GUI?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by abijah on 2006-07-19
I have to 2 different kernels on my drive(using 6 partitions)

I want grub to give me the option to choose one on boot up.

I think i found Grub in [boot/grub/]
- which file(s) do i need to edited?
- how do i edit them? how do i get to be user "root"?
- tried "sudo" and "su", but i get asked for a password? I don't have one.

Please Help?!
](*,)

---

### Post by taurus on 2006-07-19
You need to edit /boot/grub/menu.lst so open a terminal (Applications -> Accessories -> Terminal) and type

```

sudo gedit /boot/grub/menu.lst

```
When it asks for a password, use the same one that you log in with...

---

### Post by pbaehr on 2006-07-19
The file that controls the startup menu is /boot/grub/menu.lst

That's the file you want to edit to add options to your menu.

You WILL need to use sudo. For example:
```
sudo nano /boot/grub/menu.lst
```
It WILL ask you for a password. It wants your user password. The same one you used to log in. This will give you the same privileges as a traditional root account.

---

### Post by abijah on 2006-07-19
Very nice!!

Y'all are awesome.  Thanks for the quick help!

Here's another question:
With a setup like this which has 2 kernels and 2 "/root" partitions
- how many "/boot" partitions should i have?
- I just realized i have 2 "/boot" partitions each with it's own and distinct "menu.lst"

---

### Post by pbaehr on 2006-07-19
I'm not sure since I don't have a setup like that, but I think whichever OS you installed last should have the functioning grub install. Obviously, only one of them is being accessed on boot. I'd recommend changing something minor (like the color) in each one to see which is actually in use.

---

### Post by sean_ on 2006-07-19
> **abijah said:**
> I have to 2 different kernels on my drive(using 6 partitions)

I want grub to give me the option to choose one on boot up.

I think i found Grub in [boot/grub/]
- which file(s) do i need to edited?
- how do i edit them? how do i get to be user "root"?
- tried "sudo" and "su", but i get asked for a password? I don't have one.

Please Help?!
](*,)

I'll help you out with the root. To set a root password for su read this. [http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password)

The sudo (like sudo apt-get install xmms or something like that) the password is you're usernames password.

---

