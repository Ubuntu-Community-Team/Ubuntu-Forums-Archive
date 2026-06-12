---
title: "Video Player Help"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2006-12-28
I have been using Ubuntu since the last 3/4 days, and I must say I'am impressed. I have already completed "tasks" like installing printer, accessing windows partition, connecting to the net using ppoe, updating video drivers for my Geforce fx 5200 AGP card, installing frostwire, and some other program installation. To get each task right has sometime taken me two to three hours and sometimes I got it right the first shot. Now the final hurdle remains -- that of viewing VCD. My hardware is as follows - 80gb Hard disk on hda, LG RW drive on hdc, and Samsung DVD on hdd, Pentium IV, 8X AGP Nvidia Geforce 5200 (drivers installed).  Now I tried all the players possible and with varying results.
1) The default Movie Player would not start and say not possible to read file.  Please see pics of totem errors.
2)Mplayer too will not start. Please see pic of Mplayer error. However I'am able to start player form the command line >mplayer vcd://[0-n], the video is a bit grainy and gave poor controls through arrow keys. Also the default drive changes betwen hdc and hdd.
3)Gxine started only once a few tries after installation, since rebooting it has stopped working. Please see pic of Gxine error.
        I have not tried playing DVD, audio CD works fine , even mpeg clips are ok with totem. I'am at loss as how to proceed any help will be appreciated.

---

### Post by pseudonym on 2006-12-28
You sure you've enabled full mpeg playback? I think some work 'out of the box', but for most you will need to install some extra packages. It's all explained in the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") wiki.

---

### Post by mahiyar on 2006-12-28
You mean to say even playing VCD's come under the restricted formats, I thought that applied to just DVD's.

---

### Post by deadgobby on 2006-12-28
Nope, some one had to copy write it. 
;)

---

### Post by mahiyar on 2006-12-28
Ok did what pseounym told me to do however no difference in all the player's behaviour. Two things remain -- Reboot. -- Downnload win32 codecs. Any other suggestions?

---

### Post by deadgobby on 2006-12-28
You should not need to reboot.... You can install the following scrips.
Automatix
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
Easy Ubuntu
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
 These will load up codecs with ease.
Gobby

---

### Post by mahiyar on 2006-12-28
Man thanks for the help. I will do as u say. Actually it is not so bleary, I'am able to play Mplayer from command line, and gxine also plays on and off (if i did not have the needed codecs than wouldn't I be able to play even anything).

---

### Post by mahiyar on 2006-12-28
Has anybody tried EasyBuntu for media player (it says even your granny can ...)
Mahiyar

---

### Post by mahiyar on 2006-12-30
It seems odd that I am replying yo myself, but just to wrap things up. I installed the automatix as suggested and got the required codecs. I needed to tweak mplayer a little by selecting the correct video driver from preferrences box, I kept mine to "gl2" (xvidic would not work). So now xine plays DVD's. Mplayer plays both VCD and DVD, and also from the command line.

---

