---
title: "Help installing Arch, for fun 8)"
date: 2011-12-20
forum: Any Other OS
---

### Post by CJ-1990 on 2011-12-20
G'day forum peeps 8)

I am a "noob" amongst you well-learned people here, but I like to think I have a larger knowledge of Linux than I did before, 6 problems troubleshooted by myself, constantly learning about new things 8)


To better myself and improve my knowledge of linux and computers in general, as a project, I would like to learn how to install Linux Arch onto my computer :)

I have recently gone through a tutorial on how to install Arch but have remained unsuccessful, I worked through said tutorial up until booting the installed Arch, which met me with an error message, which said to me that my computer could not find the boot loader...


Can anyone point me in the direction of a very detailed tutorial on how to install Arch? Thankyou for any help you can give me

Cheers

CJ

---

### Post by Barrucadu on 2011-12-21
[https://wiki.archlinux.org/index.php/Beginners'_Guide](https://wiki.archlinux.org/index.php/Beginners'_Guide)

---

### Post by MG&amp;TL on 2011-12-21
You don't necessarily have to have 'real' hardware to run Arch. Install Vbox, then muck about in that until you get it right, *then* install it for real. 

Gentoo is in a similiar vein, if you get fed up with the Archy-ness, and you feel like compiling everything.

---

### Post by CJ-1990 on 2011-12-21
@ Barracudadu:

Cheers for the linkage dood, I'll give it a look over :)

@MG&TL:

I was actually looking for an OS that wasn't as easy as Ubuntu, Mint, and Backtrack :)

So, with Gentoo, you have to compile everything? Basically work from the ground up?

That is exactly what I am looking for. For the learning side of things, and for the feeling I get when I've compiled everything correctly and it works, the triumph :)

Any links you can send me regarding how to install Gentoo? A tutorial perhaps?

Cheers

CJ

---

### Post by CJ-1990 on 2011-12-21
I researched Gentoo and wow am I amazed, it is EXACTLY what I am looking for 8)

Thanks a bunch for recommending it to me MG&TL (Y)

Compiling the entirety of my Gentoo OS installation is going to be my project for however long it takes me 8)

And at the end, I would have accomplished a feat that not many "normal" humans could achieve... And it will look hella good on my resume once I'm done studying IT and Business at uni 8P

---

### Post by Dangertux on 2011-12-21
> **CJ-1990 said:**
> I researched Gentoo and wow am I amazed, it is EXACTLY what I am looking for 8)

Thanks a bunch for recommending it to me MG&TL (Y)

Compiling the entirety of my Gentoo OS installation is going to be my project for however long it takes me 8)

**And at the end, I would have accomplished a feat that not many "normal" humans could achieve... And it will look hella good on my resume once I'm done studying IT and Business at uni 8P**

Just a heads up... Since you mentioned it -- this won't impress a Sr. nix admin, they'll just smile and say okay. Compiling software is pretty much an expected basic task.

---

### Post by satanselbow on 2011-12-21
With the greatest respect - if you are having a few issues getting an Arch install up and running Gentoo will completely fry your brain ;)

Sabayon might be a good midway point and serves as a good entry point to the Gentoo way of doing things.

The virtualbox suggestion is a good one although you cannot always expect the vbox to behave exactly as a real install might :(

---

### Post by m_duck on 2011-12-21
The trick to either Arch or Gentoo is reading. And lots of it. Both distributions have fantastic documentation, so with that, and some trial and error, all will be well.

---

### Post by mips on 2011-12-21
I don't see the point of compiling everything as it takes so long and when things break they break properly. You can also compile stuff in Arch if you want to.

---

### Post by jjex22 on 2011-12-21
> **CJ-1990 said:**
> I researched Gentoo and wow am I amazed, it is EXACTLY what I am looking for 8)

Thanks a bunch for recommending it to me MG&TL (Y)

Compiling the entirety of my Gentoo OS installation is going to be my project for however long it takes me 8)

And at the end, I would have accomplished a feat that not many "normal" humans could achieve... And it will look hella good on my resume once I'm done studying IT and Business at uni 8P

I think you're spot on with Gentoo ... its one of those things every linux lover has to try at least once - even if you don't like it, you learn so much by doing it.

I know this is "Solved", but...

One thing to bare in mind ... it takes a LONG time - first time I did it as a noob it took nearly 2 weeks! that was 'cause of countless restarts (first one was simply due to selecting the wrong keymap and not being able to do anything... ah the fun!)

One lesson I have learned with arch and gentoo... you really get the most out of them by taking your time with the install process.. yes its very long - esp. for gentoo, but if you want a custom system,,,, well you want time to customise it! 

I find it helps to install these, Gentoo especially from INSIDE ubuntu - no downloading a gentoo CD, having your PC running off that CD for a couple of days, for all intents and purposes out of action, just install it from Ubuntu's terminal! It sounds like it's going to be more difficult, but actually the steps are just the same as starting from the gentoo cd except you have to download the stage 3 tarball instead of selecting it off the CD; create partitions, mount, chroot, etc. and the bonus is you are still in ubuntu so you can do all the things you want to do and really take your time with the gentoo install! (including access the *ful* internet - not just links for help!) This Wiki helped me

[http://www.wikihow.com/Install-Gentoo-Linux-from-Ubuntu](http://www.wikihow.com/Install-Gentoo-Linux-from-Ubuntu)

Use it with the gentoo handbook, If you wanted to do this with arch, it's in their documentation, same with debian

Hope this helps!

Edit, when I say terminal, I really mean use the shells - you wont't accidentally close them at the wrong time (alt+ctrl+F1-6)

---

