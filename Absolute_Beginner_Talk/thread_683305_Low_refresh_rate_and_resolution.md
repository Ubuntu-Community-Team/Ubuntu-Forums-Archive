---
title: "Low refresh rate and resolution"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Terrapin25 on 2008-01-30
Hi all

So far so good in my very first ever use of Xubuntu, though my screen res is faar to low along with the refresh rate - 60Hz! Headache!!

so on searching the forum i found this command

> sudo dpkg-reconfigure xserver-xorg 

to help me out. It raised the res up a bit but the screen refresh stuck at 60Hz and wont budge.

I have a 3dfx Voodoo 3 graphics card and a Hansol 710a monitor thats perfectly capable of 1024x168 at 75Hz on Windows and Mac

Any Ideas?

By the way, I am a Super n00b, that is, i really don't know too much about command line... if Anyones gonna suggest one, could you let me know where to type it etc?

Thanks!

---

### Post by overdrank on 2008-01-30
> **Terrapin25 said:**
> Hi all

So far so good in my very first ever use of Xubuntu, though my screen res is faar to low along with the refresh rate - 60Hz! Headache!!

so on searching the forum i found this command

 

to help me out. It raised the res up a bit but the screen refresh stuck at 60Hz and wont budge.

I have a 3dfx Voodoo 3 graphics card and a Hansol 710a monitor thats perfectly capable of 1024x168 at 75Hz on Windows and Mac

Any Ideas?

By the way, I am a Super n00b, that is, i really don't know too much about command line... if Anyones gonna suggest one, could you let me know where to type it etc?

Thanks!

HI and welcome, I personally have not used that graphics card but you may find some help here
[https://help.ubuntu.com/community/Voodoo3doesnotdo3d](https://help.ubuntu.com/community/Voodoo3doesnotdo3d)

---

### Post by Terrapin25 on 2008-01-30
Thanks a lot buddy, I will try that in the morning, I hope i can manage it ok, some of it looks a bit complicated, and its a nightmare staring at such a flickering screen

---

### Post by Terrapin25 on 2008-01-31
hmm, I have been trying to make sense of the link that is up there - [https://help.ubuntu.com/community/Voodoo3doesnotdo3d](https://help.ubuntu.com/community/Voodoo3doesnotdo3d)


But i really really havd no idea how to do what its telling me to do, when i run some of thos commands it says that the commands are not found, Any ideas?

Sorry, SuperN00B here!

---

### Post by overdrank on 2008-01-31
> **Terrapin25 said:**
> hmm, I have been trying to make sense of the link that is up there - [https://help.ubuntu.com/community/Voodoo3doesnotdo3d](https://help.ubuntu.com/community/Voodoo3doesnotdo3d)


But i really really havd no idea how to do what its telling me to do, when i run some of thos commands it says that the commands are not found, Any ideas?

Sorry, SuperN00B here!

HI and what command gives you what error? Please post the command and the error. If it is the first command giving error not found then you may need to add repo's
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Terrapin25 on 2008-01-31
Hey thanks for replying!

I managed to get it sorted, (I wasnt doing the commands properly - i.e i wasnt adding the correct paths etc beforehand and all sorts I was doing wrong. I managed to fix my problem by

```
sudo dpkg-reconfigure xserver-xorg
```

and choosing Advanced stup at the very end, and inputting my Horizontal and vertical refresh things seperately. I have got it running at a lovely 1024x768 @ 85Hz

Finally I can get onto enjoying Xubuntu! Its great! Thank you all for your help!

---

### Post by Toadmund on 2008-01-31
In my vertical refresh, it shows it at 50-160.
Terrapin25, what did you put in?

I am stuck at 'ugh' 60 hz.

---

### Post by Terrapin25 on 2008-01-31
Try googling for your monitor design and find out what the vertical and horizontal refresh rates are, and then input them at the end of that command line style thing. I put in up there

```
sudo dpkg-reconfigure xserver-xorg
```


I hope that helps in some way, but it depends on the monitor, I got cocky beforehand and put in some random refresh rate that it wouldnt come out of and thus I had to reinstall the whole OS again!


Let me know if that helps!

---

### Post by overdrank on 2008-01-31
> **Toadmund said:**
> In my vertical refresh, it shows it at 50-160.
Terrapin25, what did you put in?

I am stuck at 'ugh' 60 hz.

To add to Terrapin25 you may try the -phigh with that command also
```
sudo dpkg-reonfigure -phigh xserver-xorg
```

---

### Post by Toadmund on 2008-02-01
I've tried googling for my monitor which is a cicero 786n, apperently it is a 'future shop' brand name, made by either 'hansol' or 'proview' depending on what website I go to.
So that was not much help.

However, I do have 70Hz resolution now that I have updated my 'fglrx-amdcccle_8.452.1-1_amd64.deb'
and my
'xorg-driver-fglrx-dev_8.452.1-1_amd64.deb'

However, I still have the same problem as a few of us do, on reboot everything is forgotten and I either boot into a too low (the low numbers) resolution or into a black screen.

I am finally 'again' into '1024x768' that is until tommorow when I reboot again. ](*,)

Thanks anyway, I have tried all those suggestions.

---

