---
title: "bouncing Input Not supported (got Nvidia 5200)"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by DraeLee on 2006-10-21
ok I am a straight newb to linux and I am trying to learn this.  Even though I am getting bery frustrated.  ok heres my problem I have tried going thru the ubuntu guide for installing and i am at a wall.  I enabled the drivers (i think) lol cause i got the bouncing input not supported.  Please any help would be appreciated.  I am computer literate but i am linux illiterate.

i need help thx in advance

---

### Post by Kateikyoushi on 2006-10-21
When does it stop ? What is your hardware configuration ?
Try to install in safe video mode.

---

### Post by DraeLee on 2006-10-21
as of right now that bouncing box is going and going.  I have a nvidia 5200 128mb graphics card with an amd64 3200+ processor  uh im a little new to this so you might have to dumb it down for me lol

how would i install in safe mode on linux i dont eve know how to access safe mode in ubuntu?

---

### Post by Kateikyoushi on 2006-10-21
When you boot from the cd you can choose from several options like check the cd, check your memory, one should be install ubuntu in safe video mode.

---

### Post by DraeLee on 2006-10-21
ahhh ok i guess i could give that shot how big of a diff will that make?

---

### Post by DraeLee on 2006-10-21
ok im in safe mode right now so do i go through the whole process or do i need to do an uninstall or something.  sorry im very ned and need a little walking through

---

### Post by Kateikyoushi on 2006-10-21
Did you already install Ubuntu, and get this error message when you start it from the hard disc ?

---

### Post by xpod on 2006-10-21
Me thinks he is still just using the cd and is not sure what he should do now he has loaded ubunto in "safe mode".

I had to use "safe graphics mode" myself on that very first install back in july.
Just start the install routine again...dont need to uninstall anything it`s just using less power\resources or something like that.

Failing that you might need to give the "alternate cd" a go.
Thats as much as i know

---

### Post by DraeLee on 2006-10-21
ive had ubuntu installed for several days now i had an issue before with trying to install the drivers for nvidia and so this time i just went without them.  but now i am trying to install them when i did what the guides have said for enabling the glx (i think is what its called) i got the input not supported bouncing box on my screen.

Ive read several guides and none of them have worked fully for me.  I know that i must have eabled something because of the bouncing box.  In windows all you had to do was enable vga mode and then go about it, but in this its not that simple.  So i am at a lost with what to do about the drivers.

---

### Post by Kateikyoushi on 2006-10-21
I found a thread about the same problem with the same vga. [LINK]("http://ubuntuforums.org/showthread.php?t=192562&highlight=bouncing+input")

---

### Post by DraeLee on 2006-10-21
ok gonna read it now ill let you know and ty for the help

---

### Post by DraeLee on 2006-10-21
lol read that before i get down to this part here and then im at a wall.

Are you currently able to boot in the Desktop Environment (the GUI)?

If not:
Code:

sudo nano /etc/X11/xorg.conf

Set the driver back to "vesa" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

then
Code:

sudo /etc/init.d/gdm restart


Right where is says set driver back to vesa I dont know how to do it so i never get to finish the thread cause i have to stop there.

---

### Post by DraeLee on 2006-10-21
ive done this and i get blocked when it comes to turning the drives back to vesa i dont know how and it doesnt explain how to

---

