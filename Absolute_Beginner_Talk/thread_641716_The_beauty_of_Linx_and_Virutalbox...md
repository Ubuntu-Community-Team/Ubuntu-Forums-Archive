---
title: "The beauty of Linx and Virutalbox.."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Mular on 2007-12-15
Ok virtual box is utterly AMAZING!! So I got it working excellently and I think I am going to remove my windows xp parition (really just has programs installed and I couldn't figure out a way to get virtualbox to boot that up..)

So now the question is how do I remove my windows xp install without messing up GRUB? Can I just delete the partition? I did have it installed before ubuntu all on the same drive just partitioned..

Also does anyone know.. since hard drive space is a premium I installed the windows xp through virtualbox on my external drive and would like to move it to where my current windows install lies (on my internal partition) Is it possible does anyone know to move where the hard drive image is that virtualbox uses?

---

### Post by Nano Geek on 2007-12-15
You can just remove it with the Live-CD. It won't mess up GRUB, and I'll tell you how to remove the option to boot Windows from the GRUB menu if you want me to.

---

### Post by Mular on 2007-12-15
Thanks I did exactly that.. I figured it out how to get rid of the option it worked well..

What I really wanted to do was merge the partion I have /home on with the one I just deleted but I couldn't do it..

I think I messed up when I partitioned the drive to begin with, but basically gpart wouldn't let me merge the partitions. I think I made two primary partitions and /home and my old xp are on two separate primaries - if that makes sense =/

Oh well I just put the disc image for virtualbox on the old xp partition, sadly its 42gigs too but didn't feel like reinstalling ubuntu

---

