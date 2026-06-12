---
title: "Need a Console Command When I Try to Boot Ubuntu"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by mike_pitman on 2008-04-20
[B]When I Try to boot my newly installed Ubuntu i get the loading screen then it goes black and besides some system checkpoints it stops booting making me believe im suppost to enter a command to continue the boot:confused: I have a AMD 64bit Computer and am using a ATI graphics card which ive heard is not very linux friendly. any advice would be greatly appreciated. 
Mike Pitman[/B]

---

### Post by zvacet on 2008-04-20
Ctrl+Alt+F2

Login (when you have to type password you will not see it typing,but type it anyway.It is security)

After that type 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

salect** vesa** driver and after restart you will have basic graphic.Then you can go and search driver for your video card.

---

### Post by mike_pitman on 2008-04-20
[B]Thanks for the help i would have never figured that out. when i select the vesa driver from the list i get another command line that looks like the one where i had to type in the sudo command](*,)  is there a command i need to put in so the computer will accept the changes?
mike pitman  [/B]

---

### Post by zvacet on 2008-04-21
Yo can try 

```
startx
```

or 

```
sudo shutdown -r now
```

That mean you want to reboot your system.

---

