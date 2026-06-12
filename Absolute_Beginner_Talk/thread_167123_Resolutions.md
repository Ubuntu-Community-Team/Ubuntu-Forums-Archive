---
title: "Resolutions"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by TheLlamaIs on 2006-04-27
Hey there,
New ubuntu user here and I have a question, I'm sorry if it's already been asked/answered several million times but i sure can't find it.

I know how to change resolution on here, however, when I was installing I accidentally skipped over the page that let me select what resolutions I wanted to allow. I want a 1280 x 1024 however the highest mine is able to go is 1280 x 700 (thanks to the help of my brother). ubuntu says my monitor can't handle any more. I'm sure it can because in windows I use 1280 x 1024, however, I use a higher frequency. So I fired I'd change that too, but the only option i have is 60 Hz.

So basically my question is, how do I add more resolutions to the list, and furthermore, how do I add more frequencies to the list.

thanks for your help.

---

### Post by gingermark on 2006-04-27
[QUOTE=TheLlamaIs]Hey there,
New ubuntu user here and I have a question, I'm sorry if it's already been asked/answered several million times but i sure can't find it.

I know how to change resolution on here, however, when I was installing I accidentally skipped over the page that let me select what resolutions I wanted to allow. I want a 1280 x 1024 however the highest mine is able to go is 1280 x 700 (thanks to the help of my brother). ubuntu says my monitor can't handle any more. I'm sure it can because in windows I use 1280 x 1024, however, I use a higher frequency. So I fired I'd change that too, but the only option i have is 60 Hz.

So basically my question is, how do I add more resolutions to the list, and furthermore, how do I add more frequencies to the list.

thanks for your help.[/QUOTE]
Try ```
sudo dpkg-reconfigure xserver-xorg
```
This will essentially take you back though the installation process part dealing with (among other things) screen resolution. Try to have as many technical details about your graphics card and monitor to hand when you do it though.

---

### Post by TheLlamaIs on 2006-04-27
I went through that, I got to the page with resolution, I logged off and back on. The list of resolutions is still the same, and so is the frequency.

---

### Post by gingermark on 2006-04-27
Don't mean to be pedantic, but you say you got to the page with resolution and then logged off. I assume you logged off after the xorg.conf file was written (as opposed to imediately after the resolution screen)?

What graphics card are you using? What driver are you using?

---

### Post by TheLlamaIs on 2006-04-27
yes, i finished with the xorg.conf file first then logged off.

I've got a ghetto ATI Ragepro AGP 1x

---

### Post by gingermark on 2006-04-27
Are you using the ATI drivers? I know some people have had problems with them, but an official driver should allow the graphics card to work to it's full potential.

If not, what driver are you using?

---

### Post by Steggy on 2006-04-27
I'm not sure if the problem I just had is the same as yours (and I'm a complete newbie to Linux, so I just kind of gusseed my way through it.) 

I was able to use higher resolutions after I edited my /etc/X11/xorg.conf file under the section "Screen" and simply added "1280x1024" under each subsection.

I then restarted my computer, and I was able to change it to 1280 x 1024 resolution easily. (Maybe you'll only need to restart X, but I didn't know how to do that at the time, and I'm still in the Windows mindset of having to restart the computer after any change.)

Hope that helps!

---

### Post by gingermark on 2006-04-27
There is an ATI driver HowTo here: [http://ubuntuforums.org/showthread.php?t=75428](http://ubuntuforums.org/showthread.php?t=75428)
Please note I don't have an ATI card myself, so I don't know for certain of this is the problem, but it seems a reasonable place to start.

If you decide to follow Steggy's advice and edit the xorg.conf file manually make sure you back it up first.

Good luck!

---

### Post by TheLlamaIs on 2006-04-27
thanks, I'll give that a shot.

also, I've already got 1280 x 1024 under each sub-section.

---

