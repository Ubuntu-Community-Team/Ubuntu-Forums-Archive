---
title: "Ubuntu Freezes Randomly."
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-11-28
As I sit here typing this, currently my terminal is frozen after trying to CD to the Desktop. This happens often, especially with terminal and synaptic. Earlier, I had to reboot the computer in order to get into synaptic. Also, on random occasions as I type, my computer seems laggy to respond to the text input... in fact it's doing it now as I type this.

What could this be? This is a brand new laptop that has Ubuntu Gutsy 7.10 on it. It runs Vista absolutely fine... 

I'm using the X86 version of Gutsy. This computer has an X2AMD processor. Perhaps I should try that version????

---

### Post by Nano Geek on 2007-11-28
Are you using a Nvidia graphics-card?

---

### Post by Roasted on 2007-11-28
No. ATI.

ATI Radeon X1200. (Laptop, Toshiba Satellite A215)

---

### Post by Roasted on 2007-11-29
Now I'm confused...

I decided to take Linux Mint up for a try. Seeing as though on my laptop, where I was having the freezing issues in Ubuntu, is brand new, I figured I'd throw Mint overtop of Ubuntu since nothing was on Ubuntu I needed to save.

Needless to say, I seemed to be a bit more partial to Mint. However, I STILL get the exact same freezing issues. I have no idea what causes them. I know it's not pidgin, because I suspected pidgin at first yet I kept pidgin off and 2 minutes later, Mint was freezing on me again. What in the hell is going on?!!?

---

### Post by Nano Geek on 2007-11-29
It could be that Ubuntu (and Linux Mint too since it's based off Ubuntu) has some weird firmware bug with your hardware. If you have the time, you could try something completely different like Suse, PCLinuxOS, or Fedora.

There's also the possibility that your laptop's overheating and causing it to freeze up. If it's still under warranty you could have it checked.

---

### Post by HermanAB on 2007-11-29
Try the boot parameters noapic and nolapic.

You can also try killing hal add-on storage, since it has a known hiccuppy bug:
killall hald-addon-stor

'Hope one of those help!

Herman

---

### Post by Roasted on 2007-11-29
Nah, it's not overheating. When I put my hand to the side of the laptop, where there is a vent, the air coming out is barely even warm. I've sat on this thing on Vista and played counterstrike for 2 hours without a break and even then it doesn't overheat or get "too hot" by any means. I know it's not overheating.

I had planned on trying out Fedora Core 8 in the morning. However, I don't think I'll like it due to my experience with using the LiveCD last week. It just didn't interest me.

PCLinuxOS I've heard a bit about, though. I wonder if that's worth a try? Is it more of a beginners OS or just a general well rounded version of Linux? I was reading a review about PCLinuxOS and the reviewer said something about PCLinuxOS offering a more Windows XPish look... This, of course, scared me. It DOES have Gnome, right?? That I can customize to look just like Ubuntu's default style?

edit - I see PCLinuxOS is KDE. Ehh... blah. I'll pass, and stick with trying Fedora.

Does Fedora have a wiki like Ubuntu, where I can go to see detailed instructions on installing whatever I want?

---

### Post by Nano Geek on 2007-11-29
> **Roasted said:**
> Nah, it's not overheating. When I put my hand to the side of the laptop, where there is a vent, the air coming out is barely even warm. I've sat on this thing on Vista and played counterstrike for 2 hours without a break and even then it doesn't overheat or get "too hot" by any means. I know it's not overheating.

I had planned on trying out Fedora Core 8 in the morning. However, I don't think I'll like it due to my experience with using the LiveCD last week. It just didn't interest me.

PCLinuxOS I've heard a bit about, though. I wonder if that's worth a try? Is it more of a beginners OS or just a general well rounded version of Linux? I was reading a review about PCLinuxOS and the reviewer said something about PCLinuxOS offering a more Windows XPish look... This, of course, scared me. It DOES have Gnome, right?? That I can customize to look just like Ubuntu's default style?Yes, PCLinuxOS does use gnome. It is just uses blue and I think it has only one bar at the bottom of the screen, but besides that it's just like Ubuntu.

But any distro in the top 10 on DistroWatch.com should do well.

---

### Post by Sef on 2007-11-29
Boot up with the Desktop CD and then go to mem86test.  Run it overnight and see if it gives you any errors.   I had a similar problem and it turned out that my motherboard was bad.  The mem86test always stopped at #8 test.

---

### Post by Roasted on 2007-11-29
Why do I need to boot from the CD? Isn't it already included in the grub loader whenever I boot?

btw - Vista runs fine on this same machine. Except for the usual qwirks and stuff that Vista offers, it runs a lot smoother than Ubuntu and Mint. That's why I thought it was OS based and not machine based.

---

### Post by Roasted on 2007-11-29
Okay... so I've been running Memtest 86 for 10 hours and 48 minutes.

I don't know exactly what means what here. However, it has done 29 passes and has 0 errors. How long does this go?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-29
lol i dont think it stops
you ran it anuf

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-29
You should post your hardware specs so if anyone knows any ishus with it you can find out 
allso may wanna look into your self
i  think the command is ```
lspci
```
 I dont know what kindof drivers you grafix card has going in it generic or ones for your card but just go with the gineric and let it run and see if thats whats up

my wireless card in my pc made my box hang just frezz up i had to blacklist, but i could not rember how at the time so i just pulled the card.

---

### Post by Roasted on 2007-11-29
So wait... you're telling me my wireless card, which isn't supported by ubuntu/linux mint, may be the reason that it's freezing? 

Blah... Can't I just "disable" it in an easy fashion? What does it take to blacklist a driver?

---

### Post by Roasted on 2007-12-14
UPDATE: So I had turned the switch on for my onboard wireless driver in my laptop the other day... I forgot to turn it off. Bam, Ubuntu started freezing up. I came back to this thread to re-activate it due to my issues and I saw the post about wireless. I turned off the wireless on the switch on the front of the laptop. BAM. Done. 

Fixed. Thanks!!

---

### Post by Roasted on 2007-12-14
Nevermind. Just froze on me again.

Fedora is lookin sexy right about now...

Edit - Seeing as though I was constantly clicking out of things and forcing quit, I think I just needed to reboot to smooth it over. Since the reboot, it hasn't frozen on me yet. We'll see what happens!

I guess active pieces of hardware that have no driver associated with them, such as the internal wireless nic, is what was causing it. The second I turned it off it acted fine for a few more minutes till it started to do minor freezes again. But like I said, since the reboot it's been fine. We'll see if this holds up. If not I'll be posting back!

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-19
so how did it go

---

### Post by The Tronyx on 2007-12-19
Same laptop, same problem here...I'll be watching this thread.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-03
i think its cinda fix for now just press the button that disables the wireless card and that should stop the frezzing

---

### Post by The Tronyx on 2008-01-07
> **<<joe>> said:**
> i think its cinda fix for now just press the button that disables the wireless card and that should stop the frezzing

Boot the kernel with noapic nolapic nosplash

---

