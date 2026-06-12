---
title: "No video, I think?"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Serpent Joe on 2006-07-22
Hi there. I'm a recently graduated student of computer science, but embarrassingly enough I've never run Linux on any of my PCs. I downloaded and burned CDs for Ubuntu, Kubuntu, and Xubuntu in order to run them live and try them out. In all three cases, bootup proceeds normally up to a point (I choose to run live from a list of options and then watch a bunch of utilities load), and then both of my monitors (one DVI, one VGA) go black and appear to be receiving no input. The disc continues to spin in the drive for a few minutes, and Kubuntu even gave me a little sound which indicates a good chance that the only weak link is the video output.

I'm using the AMD64 OS versions in all three cases. My video card is a Sapphire manufactured AGP Radeon X800 GTO. It doesn't seem likely that the problem is anything arising from the downloading or burning process, since in each of the three cases the problem is exactly the same. Are there any known issues with this video card, or with the A64 version of Ubuntu? Do I need to redo the burns with drivers added? If anyone can think of anything that might resolve it, I promise I won't even care that you made me look stupid.

Thanks

---

### Post by GuitarHero on 2006-07-22
I would try the 32bit version of ubuntu.  64bit can be buggy.  Usually if its a video card issue you will get an xserver error, not just blank screens.  Make sure to burn the cd at a slow speed, fast burning has been known to cause install errors.

---

### Post by steve.horsley on 2006-07-22
Search these forums for "Radeon X800 GTO". I'm sure there will be a mention. It can probably be made to work.

On the live CD, try pressing Alt-Ctrl-F1 when you get the black screen, and see if this gets you a text login prompt. If so, you log in as **root** and can try these commands:
> /etc/init.d/gdm stop
dpkg-reconfigure -phigh xserver-xorg
/etc/init.d/gdm start

If you want to install anyway, you could use the text-mode installer CD - it's much more stable in my opinion, although you may still have to manually fix up the graphics afterwards.

It might be better for you to use the 32 bit version if you are starting out. Getting some of the audio/video codecs, flash plugins and other proprietary binaries in 64 bit can be a challenge, and I gather the performance difference isn't much.

---

