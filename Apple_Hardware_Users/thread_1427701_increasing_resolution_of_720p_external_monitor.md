---
title: "increasing resolution of 720p external monitor"
date: 2010-03-11
forum: Apple Hardware Users
---

### Post by boilertnerb on 2010-03-11
Hello everyone -

I've done enough power-off restarts and just overall damage to the point where i think i just need to start a thread and see if the answer finds me...

i've got a 37" 720p TV that i hook up to my macbook 1,1 via the mini-DVI port (dvi -> hdmi). 

the highest resolution i can get on my tv is 1360x768. i've tried all kinds of xrandr newmode, addmode, etc. etc, downloaded urandr (which doesn't even recognize that i have two monitors) to get this thing working but with no success. i'm not trying to do dual monitors, i just want to turn off my macbook screen and use the tv as my only monitor, but at a higher resolution. this seems like it shouldn't be that difficult...

can someone help here? 


if this is of any use:

~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       59.9 +
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 820mm x 461mm
   1280x720       60.0 +
   1360x768       60.0* 
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
TV1 disconnected (normal left inverted right x axis y axis)

---

### Post by a.walker on 2010-03-11
I don't think you will be able to get a higher resolution than 1366x768 on a 720P TV. That is the maximum resolution that your TV can display. See this wikipedia article: [http://en.wikipedia.org/wiki/720p](http://en.wikipedia.org/wiki/720p).

---

### Post by soltanis on 2010-03-12
You can't force a monitor to display higher resolutions than they natively support. In your case the number you quoted sounds about right; the 720 means it should support 720 pixels vertically, which 768 > 720 so clearly that worked out fine.

If you want more resolution go with a 1080p monitor, or there are also monitors which go up to twice that resolution (with dual link DVI). Not like you really need it but hey it's there.

---

### Post by boilertnerb on 2010-03-12
Alright thanks for the info. I guess i thought i could do it because when i used to run ubuntu on my ps3, the resolution was much higher (1920x1080) so i'm not sure what gives there.

either way - i guess i can settle with what i've got.

thanks again

---

### Post by truptrup on 2010-03-21
Most 720p TVs can accept 1080p signal, but they will resize it to fit on the screen so you will not see a difference between outputting 1080p and 720p. 

Actually 1080p may look worse because the TV has to scale it down. It would be best to output to your Tvs native resolution which looks like 1360x768

I'm sure its the same way with your ps3, the ps3 will output 1080p and the TV will have to resize it before displaying it.

[http://www.highdefforum.com/blu-ray-players/82139-ps3-detects-1080p-720p-tv.html]("http://www.highdefforum.com/blu-ray-players/82139-ps3-detects-1080p-720p-tv.html")

---

### Post by ZychoFlow on 2010-08-24
Most 720p televisions also get 1080i which is 1920x1080 interlaced scan i.e. lower your tvs refresh rate to 30hz and then increase the resolution to 1920x1080.

If it doesn´t work out that stick with the old resolution.

Good luck

---

