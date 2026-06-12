---
title: "Is this a hardware problem??"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by telegramsam on 2007-01-26
Hi...

I've been trying to install 6.10 on an old HP with a TriGem MOBO that has onboard video.  When I'm in the Live CD, I can't get the screen resolution to change from 600 x 480 (I think) using the Gnome preferences menu.  

This wouldn't be so bad, except I can't run the install because I can't reach the "next" buttons at the bottom of the GUI.  

I tried some crappy old PCI video cards in the slots with the same results.

Can you change the Screen Res in the Live CD with a command line?  If so, what would the command be?

Thanks!

---

### Post by JayTee on 2007-01-26
while running the LiveCD open a terminal and type the following: 
sudo dpgk-reconfigure -phigh xserver-xorg
This will run the reconfigure of your xserver video settings for resolution. If this fails you can try and run the same command and leave out the -phigh but you will need to provide more info including what kind of video card you have. If you run this and your video card is not listed then choose VESA as that's as generic as you can get. Once you've run this press Ctrl-Alt-Backspace to restart the Xserver. It should let you change resolutions then. If this fails then you can try downloading the Alternate CD which is more text based and doesn't have the GUI issues. If you take that road and still have resolution issues when you boot from an installed system then try the first solution above and it should work for you. If not, you'll need  to get a newer graphics card.

---

### Post by telegramsam on 2007-01-26
I don't know what more information is available about the video card.  The old PCI ones have almost nothing for identification on them, and I seriously doubt they're supported.  The onboard is an Intel 680i chipset, which I would THINK would be supported, but being a TriGem board, which are notorious for being junky, I wouldn't be surprised if Ubuntu didn't support it--as a matter of PRIDE!! LOL.

I'll try the command line thing--if that doesn't work, I'll just invest in a cheapie video card or something.

Thanks for your help!

---

