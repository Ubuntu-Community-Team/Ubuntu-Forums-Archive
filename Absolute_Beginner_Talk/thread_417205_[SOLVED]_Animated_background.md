---
title: "[SOLVED] Animated background"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-04-21
Is there a way to install/cutomize an [COLOR="Blue"]animated background[/COLOR] for the Ubuntu desktop?

---

### Post by the8thstar on 2007-04-29
I'm just posting this line to propel my subject back in the frontline.

Windows Vista has it... can we do it too? If so, how?

---

### Post by thefoolisme on 2007-04-29
I believe you might be referring to Beryl or Compiz, with their spinning cubes and wobbly windows, etc. If that's the case, I would recommend researching those two.  I haven't tried setting them up personally, so I can't help you there, but there is a lot of info on these forums and on the web.

---

### Post by riminicat on 2007-04-29
xwinwrap, I haven't figured out how to get it to work yet, I'm a noob and am just now figuring out the terminal thing

---

### Post by riminicat on 2007-04-29
xwinwrap will play movies as wallpapers, if you can get it to work

---

### Post by seshomaru samma on 2007-04-29
for xwinwrap [here]("http://ubuntuforums.org/showthread.php?p=2342997") is a tutorial

---

### Post by Artstew on 2007-04-30
> **riminicat said:**
> xwinwrap will play movies as wallpapers, if you can get it to work

So will VLC media player! I love that player, is there anything it CANT do?  I don't know if Xwinwrap is more integrated or if it runs in the background, but I bet you could put VLC on loop in background process if you knew what you were doing... which I don't. It's just a thought, maybe not the most direct approach... but I bet it would work.

---

### Post by paraflou on 2007-07-09
After hours of research i can't find out how to fix an animated background!!!
xwinwrap is a good idea because u can play viedos or screensavers as background, with one difference!!!
Xwinwrap makes one layer in front of dekstop and plays videos. So, its kinda tricky animated background.
Thats what i did till now. 

Does anyone know if xwinwrap has options that can actually make an animatied background???

Is there in beryl sth familiiar to dreamscene of Vista? An animated background? not video or screensaver!!!


p.s. 
xwinwrap repositories can be found in  [here ]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/")

xwinwrap -ni -o 0.2 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet -vo gl2 -ao alsa /home/deus/Desktop/ocean.avi -loop 0    (an example of how xwinwrap works)

---

### Post by Agent86 on 2007-08-07
I have a related question. I'm running Ubuntu Dapper, and I'm wondering if there's any way to use an animated .gif file as a desktop background. I'm currently using the .gif as a background, but it doesn't animate. It animates fine when viewed in Firefox or EoG, but as a background it just sits there. If it doesn't work in Dapper but it works in any later release, I'd like to know that, too.

---

### Post by cobrn1 on 2007-08-07
Can you set a webpage as the background?

If so then it's simple a case of making a very simple webpage (saved on your pc) that has the gif image and setting that as the background. Only problem is I don't know if ubuntu supports a web page as the background (windows does, and this is what I used to do, but the I got bored/distracted and chose a still background...)

---

### Post by Agent86 on 2007-08-07
> **cobrn1 said:**
> Can you set a webpage as the background?That sounded like it was worth a try, but Gnome ignores me unless I set anything but an image file (.jpg, .png, .gif, etc.) as a Desktop Background.

---

### Post by cobrn1 on 2007-08-07
> **Agent86 said:**
> That sounded like it was worth a try, but Gnome ignores me unless I set anything but an image file (.jpg, .png, .gif, etc.) as a Desktop Background.

bummer :(

Sounds like VLC or the other thing might be your best hopes then...

---

### Post by trash on 2007-08-07
I think you want to install E17 , as far as I remember it was the only wm to do this but i could be wrong... I never bothered to try it because my machine couldn't do it justice.

---

### Post by overdrank on 2007-08-08
High I have been playing with xwinwrap for a while and the screen savers work good with  the ATI xgl session. But on my new x300 not all of them work. Nvidia does work with out the xgl session but is a little buggy but kewl. Have not had luck with the videos yet but still working with it. :KS

---

### Post by Agent86 on 2007-08-08
> **trash said:**
> I think you want to install E17 , as far as I remember it was the only wm to do this but i could be wrong... I never bothered to try it because my machine couldn't do it justice.Yes, I did a little more checking and I think you're right, Enlightenment seems to be the way to do it.

VLC and xwinwrap seem to be overkill methods for displaying a 8-frame .gif. I'm sure it would be great if I wanted to display movies, but I think I'll stick with the static display for now.

---

