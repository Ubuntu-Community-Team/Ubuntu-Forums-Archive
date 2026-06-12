---
title: "Before I start a video upgrade"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by podunk on 2006-10-05
I am going to order a new video card today, getting a Nvidia since they support Linux.

When the card comes in, do i have to reset up the whole rig again? If not – what install uninstall procedure should I follow? I found tons of how tos on setting up cards, but none on changing cards.

Thanks in advance! :-)

---

### Post by Papa-san on 2006-10-05
You shouldn't need to uninstall any software, but it won't be a problem to clean out the old drivers. I would suggest you find out what drivers you are going to need,download the latest updated versions of them to your Desktop or somewhere you can find them easily, and have them ready for when you do change out your hardware. I have learned the hard way that even if something is supposed to work for us out of the box, that it doesn't always flow so smoothly! 

Doing it this way will hopefully eliminate any potential headaches. I have found that sometimes just having all of your ducks in a row beforehand assures that everything flows so smoothly, that the precautions aren't even needed. Funny how this works!

---

### Post by jaboua on 2006-10-05
That shouldn't be necesarry. If you allready have nvidia, you shouldn't have to do anything - if you're using some other card though, you might want to first switch to the "vesa" display driver ("sudo dpkg-reconfigure xserver-xorg" or edit /etc/X11/xorg.conf) so that you can get a gui when you start using the nvidia card - then when you get the nvidia card, install nvidia-glx and nvidia-kernel-common. Then you have to switch to nvidia drivers, either use the same method you used to enable vesa driver (remember to disable DRI if it's enabled and enable GLX if it's disabled) or just run "sudo nvidia-xconfig" to auto-reconfigure it for you.

---

### Post by bodhi.zazen on 2006-10-05
Depends on the nvidia card. Some cards require the nvidia drivers.

See here:

[Hardware](http://doc.gwos.org/index.php/Nvidia)

I found the open source drivers were not a good as the Nvidia driver on my 7600 GT

and here

[how to install nvidia driver](http://doc.gwos.org/index.php/Latest_Nvidia_Breezy)

IMO method 2 is best.

---

### Post by podunk on 2006-10-05
Thank ya'll! :-)

I'm replacing an old Nivida with a new one - I won't worry about it as much now.

---

