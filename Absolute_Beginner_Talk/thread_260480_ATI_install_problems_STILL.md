---
title: "ATI install problems STILL"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-18
Ok i've followed eveyrhint you guys have given me to install ati and i'm still stuck with messa...  I have the ATI control ap under my application menu,  but it's still runnin mesa.... Please help

---

### Post by Devile on 2006-09-18
Can someone please help.... i just want to watch a movie

---

### Post by Devile on 2006-09-18
I followed all teh steps by ATI but when i try to do the last step:
Launch the Terminal Application/Window and run  /usr/X11R6/bin/aticonfig --initial to configure the driver.

there is no file....

---

### Post by Kilz on 2006-09-18
> **Devile said:**
> Can someone please help.... i just want to watch a movie

You cant watch a movie without ati drivers? Well anyway. I have had problems installing the 8.28.8 drivers. You might have better luck installing the 8.26.18 version[ i386]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run") or [amd64 version]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run"). [Then use this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually") but edit the file name to the onder version.

---

### Post by powder on 2006-09-18
Post your xorg.conf.

---

### Post by WalmartSniperLX on 2006-09-18
well in a way hes right, you need the drivers for accurate opengl video streaming, which unloads the cpu. 

The 8.28.8 drivers, to be honest, blow :D  It has lots of problems, but its ATI and theyre known for driver problems. 

I would suggest getting an older driver. Remember if you have a desktop, get the desktop, laptop get the laptop driver, etc I dont want to treat you like a noob but you never know when you might make a small mistake like getting the wrong driver, and have it lead to disaster. 

You can also get the ati drivers from the Synaptic Package manager

DOwnload xorg-driver-fglrx and see what happens

 I think in the terminal, *sudo apt-get install xorg-driver-fglrx  * may do it too

Correct me if im wrong :D

---

### Post by Devile on 2006-09-18
> **Kilz said:**
> You cant watch a movie without ati drivers? Well anyway. I have had problems installing the 8.28.8 drivers. You might have better luck installing the 8.26.18 version[ i386]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run") or [amd64 version]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run"). [Then use this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually") but edit the file name to the onder version.


I followed your link to a T with the newest drivers and it WORKED!!!! perfect, thanks very much ....

---

### Post by Kilz on 2006-09-18
> **Devile said:**
> I followed your link to a T with the newest drivers and it WORKED!!!! perfect, thanks very much ....

Thats good, but the 8.28.8 drivers have a real low fps. You can see it if you use ```
glxgears -printfps
```
With the 8.28.8 drivers I get 150 to 175 fps. With the 8.26.18 I get 1470- 1520 fps. If it works for you cool, but be aware the older drivers are a little better.

---

### Post by Frank Golden on 2006-09-19
> **Kilz said:**
> Thats good, but the 8.28.8 drivers have a real low fps. You can see it if you use ```
glxgears -printfps
```
With the 8.28.8 drivers I get 150 to 175 fps. With the 8.26.18 I get 1470- 1520 fps. If it works for you cool, but be aware the older drivers are a little better.

Hi Kilz,
  Some food for thought. After reading your comments I tried a little unscientific experiment. I had just recently updated to the ATi 8.28.8
drivers and had not really seen any problems.
So as I had a partimage copy of this install on file, I uninstalled the
8.28.8 drivers and reverted to the 8.26.18 drivers. I then made a partimage
copy of that so I could freely switch between either install.

Below is the result of running glxgears -printfps and fgl_glxgears
on the 8.28.8 (newest drivers). The red text is with the test Windows maximized and the black text is with test Window minumized.

```
frankgolden@frankgolden-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)

frankgolden@frankgolden-laptop:~$ glxgears -printfps
[COLOR="Red"]629 frames in 5.0 seconds = 125.606 FPS
625 frames in 5.0 seconds = 124.990 FPS
625 frames in 5.0 seconds = 124.990 FPS
625 frames in 5.0 seconds = 124.990 FPS
624 frames in 5.0 seconds = 124.789 FPS[/COLOR]
39177 frames in 5.0 seconds = 7835.394 FPS
53425 frames in 5.0 seconds = 10684.827 FPS
53253 frames in 5.0 seconds = 10650.588 FPS
53270 frames in 5.0 seconds = 10653.859 FPS
53398 frames in 5.0 seconds = 10679.547 FPS
53025 frames in 5.0 seconds = 10604.913 FPS
frankgolden@frankgolden-laptop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
[COLOR="Red"]1291 frames in 5.0 seconds = 258.200 FPS
1884 frames in 5.0 seconds = 376.800 FPS
2281 frames in 5.0 seconds = 456.200 FPS
2290 frames in 5.0 seconds = 458.000 FPS
2257 frames in 5.0 seconds = 451.400 FPS[/COLOR]
4854 frames in 5.0 seconds = 970.800 FPS
5513 frames in 5.0 seconds = 1102.600 FPS
5526 frames in 5.0 seconds = 1105.200 FPS
5526 frames in 5.0 seconds = 1105.200 FPS
5536 frames in 5.0 seconds = 1107.200 FPS
5526 frames in 5.0 seconds = 1105.200 FPS
5474 frames in 5.0 seconds = 1094.800 FPS
```

The next results are with the older drivers (8.26.18)
The same text colors apply.

```
frankgolden@frankgolden-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5879 (8.26.18)

frankgolden@frankgolden-laptop:~$ glxgears -printfps
[COLOR="Red"]9788 frames in 5.0 seconds = 1957.401 FPS
9770 frames in 5.0 seconds = 1953.853 FPS
9758 frames in 5.0 seconds = 1951.519 FPS
9761 frames in 5.0 seconds = 1952.135 FPS
9737 frames in 5.0 seconds = 1947.096 FPS[/COLOR]
20193 frames in 5.0 seconds = 4038.564 FPS
53492 frames in 5.0 seconds = 10698.363 FPS
53375 frames in 5.0 seconds = 10674.968 FPS
53571 frames in 5.0 seconds = 10714.019 FPS
53172 frames in 5.0 seconds = 10634.379 FPS
frankgolden@frankgolden-laptop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
[COLOR="Red"]1485 frames in 5.0 seconds = 297.000 FPS
2297 frames in 5.0 seconds = 459.400 FPS
2288 frames in 5.0 seconds = 457.600 FPS
2273 frames in 5.0 seconds = 454.600 FPS
2261 frames in 5.0 seconds = 452.200 FPS[/COLOR]
4112 frames in 5.0 seconds = 822.400 FPS
5559 frames in 5.0 seconds = 1111.800 FPS
5559 frames in 5.0 seconds = 1111.800 FPS
5542 frames in 5.0 seconds = 1108.400 FPS
5530 frames in 5.0 seconds = 1106.000 FPS
5534 frames in 5.0 seconds = 1106.800 FPS

```

As I said before, unscientific test but at least for the results with
the test Windows minumized I don't see much of a difference.
But then again [http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

As I mentioned before the new drivers seem to work for me so I think I
will stick with them. Any comments?

---

