---
title: "Lilo won't let me boot windows"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by sorcre on 2006-05-07
When I start my PC I see the word "lilo" on a black screen. After 6 seconds, it boots linux without asking me what I want to boot. I tried pressing every key I can think of and it still boots linux. I could set the default boot to Windows but then how would I get into linux? Here is my config. 

NOTE: I installed Lilo instead of grub from the Ubuntu CD (5.10)

---

### Post by halitech on 2006-05-07
I'm not 100% sure but I think your delay of 50 is telling it to wait for half a second

  # Specifies the number of deciseconds (0.1 seconds) LILO should
  # wait before booting the first image.
  #
  delay=50

maybe try upping it to 500 which I *think* should be 5 seconds or 2000 which *should* be 20 seconds

PS. on second thought, not booting windows is a bad thing why? :D

---

### Post by sorcre on 2006-05-07
Thanks, but that's not it. It doesn't matter how long it waits, it still boots Linux.

---

### Post by halitech on 2006-05-07
my bad, misread your post :( 

if  you replace 

default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1

	initrd=/initrd.img

with 

default=Windows

Windows=/dev/sda1
	label=Windows
#	restricted
#	alias=2

I think that would work although I'm wondering now why your keyboard won't change what boots. Is it a USB or wireless keyboard? and does it work in Ubunt once it boots?

---

### Post by sorcre on 2006-05-07
They keyboard works fine at boot(I can press enter to skip the wait) The point is, there is no menu :( It just has the word "lilo" on a black screen then it says "booting linux"

If I change it to that, won't it only boot windows?

---

### Post by halitech on 2006-05-07
ummmmmmmmm, okay. I'm gonna bow out now. I'm not sure what is going on but yeah, making that change will boot you into windows everytime. There should be a menu as far as I know.

---

### Post by sorcre on 2006-05-07
Ah, I got it! Turns out there is a (hidden) menu... I have to press ESC + ~ for some reason :mad:  Heh, and they say slamming your keyboard never solved anything.

Thanks for trying though :D

---

### Post by n3tfury on 2006-05-07
Wow, if that's Lilo by default, that's pretty retarded.

---

### Post by sorcre on 2006-05-07
Lilo works very well under BSD. This is the first time I used it with linux.

---

### Post by halitech on 2006-05-07
wow, glad I went with GRUB although I only have Ubuntu so wouldn't really matter.

---

### Post by blejs on 2006-11-22
same problem here, can´t boot ubuntu anymore since i changed default=linux to default=windows. esc + ~ doesnt work for me.

no more wild wild africa for me, even sonys rootkit has more configuration options.

---

### Post by blejs on 2006-11-22
> **n3tfury said:**
> Wow, if that's Lilo by default, that's pretty retarded.

nope, thats ubuntu by default, but i agree that its retarded

---

