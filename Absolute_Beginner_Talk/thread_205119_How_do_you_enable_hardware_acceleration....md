---
title: "How do you enable hardware acceleration..."
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Shadix on 2006-06-28
..on a R200 ATI card assuming that it isn't automatically enabled. (A command to check would be nice)


I just fixed my FLGRX for my Radeon 9250 card and I intend to install XGL.

---

### Post by harishg on 2006-06-28
Check the /etc/X11/xorg.conf file.It will tell you the details you need.Also make sure to backup that file before updating in case the drivers dont work.

---

### Post by Shadix on 2006-06-28
I guess I'm blind or just stupid because I don't have any idea what you are talking about.  I checked through my xorg.conf and didn't find any details that would help in enabling hardware acceleration.


Is it enabled automatically if the FGLRX installation is good or is there a procedure I need to go through to enable it?  What do I need to do?

---

### Post by airwolf on 2006-06-28
To check if 3D hardware acceleration is working, you can use the following command:

```
glxinfo |grep rendering
```
This should output "direct rendering: Yes".
If it gives the same but with "No", hardware 3d acceleration is disabled.

---

### Post by shoot2kill on 2006-06-28
if it is disabled, how can it be enabled

---

### Post by stupidkid on 2006-06-28
Huh? Are hardware acceleration and direct rendering the same thing? (please excuse my n00biness).

---

### Post by Shadix on 2006-06-29
Precisely the point of this topic :\...  How do you enable it.

---

### Post by cowley on 2006-06-30
hi, i have nvidia 5200 and always thought my card was working as it should but when i enter glxinfo |grep rendering i get no.  i use compiz and have used 3ddestop all ok.  how do i enable this? or do i need to? 

thanks

simon

---

### Post by richbarna on 2006-06-30
[QUOTE=cowley]hi, i have nvidia 5200 and always thought my card was working as it should but when i enter glxinfo |grep rendering i get no.  i use compiz and have used 3ddestop all ok.  how do i enable this? or do i need to? 

thanks

simon[/QUOTE]

I've got nVidia 5200 on two setups a quick easy check is to open the terminal and type glxgears.
If they are rotating smoothly, you are ok.
If they are struggling to turn, you need to install or update your nVidia drivers.

Here:- [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by cowley on 2006-06-30
hi, i have the drivers from automatix, the gears turn ok, i wouldnt say they struggled, but wasnt exceptionally smooth either.  also the fan came on too (dell inspiron 5150 laptop) heres the output on the terminal:

cowley@cowley-laptop:~$ glxgears
11317 frames in 5.0 seconds = 2245.248 FPS
11058 frames in 5.0 seconds = 2196.547 FPS
11309 frames in 5.0 seconds = 2251.039 FPS
11286 frames in 5.0 seconds = 2255.007 FPS
11286 frames in 5.0 seconds = 2249.836 FPS
11190 frames in 5.0 seconds = 2232.323 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
cowley@cowley-laptop:~$

i just dont understand y it says no rendering on the command: glxinfo |grep rendering

thanks

simon

---

### Post by richbarna on 2006-06-30
[QUOTE=cowley]hi, i have the drivers from automatix, the gears turn ok, i wouldnt say they struggled, but wasnt exceptionally smooth either.  also the fan came on too (dell inspiron 5150 laptop) heres the output on the terminal:

11286 frames in 5.0 seconds = 2255.007 FPS
[/QUOTE]

Using glxgears isn't a pro benchmarking tool, and also other factors have to bee taken into account, ie RAM, Processor etc.

If you are getting 2255 FPS on an nVidia 5200, you are doing better than most ;)

PS I'm not sure about the rendering.

---

