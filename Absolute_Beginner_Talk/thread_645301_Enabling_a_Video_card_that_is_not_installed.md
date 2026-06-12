---
title: "Enabling a Video card that is not installed"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by neuro42 on 2007-12-19
I am running an OLD system until I get the parts in for my PC, justcould not go with out internet anylonger

Its basically an upgraded pavillion 6510 ( I think)

433MHz celeron
11MB shared video
2x128MB PC100
27GB hdd

I installed Xandros yesterday, older version, and was using my TNT 16MB video card.

When I updated to service pack 2  rebooted to black screen

So I installed xubuntu (thinking it would be faster anyway)  everything is fine until the login screen is about to show up... then black screen

rather then reinstlal I decided to pull the pci card and renable the onboard video.

Lo and behold everything works (intel 810 chipset)

So I put hte card in and attah an monitor to vid card and to onboard... but with onboard disabled.

Everything runs like it should right up until I get to the point where the login should appear.  Then the Video card monitor goes black screen (LED stays green)  and the one connected to onboard kicks on but all garbage.


So. I did the add/remove  and added the nVidia legacy drivers... 

How doI configure xorg.conf from the text mode boot... or can I pre configure it for a card that is not installed?  I can not install it the card,because X wont load.

Help!

---

### Post by macogw on 2007-12-19
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by neuro42 on 2007-12-19
Great,

Going to give it a try now from text mode (gave me a error in terminal), and the  startx

Wish me luck! :lolflag:

---

### Post by neuro42 on 2007-12-19
Ok did not work in text mode till I set  -plow 

Ran into a problem setting hte video card though.  I installed it, and went through auto and manual detection.

Auto = integrated chipset  but monitor attached to PCI card LOL

Manual = lets me pick but there is  "error in format" when selecting PCI

lspci gives me this for the card I want

01:0e.0  

config wants
PCI:0:0:0     <--- that format  not that exactly

if I input more then one number or try to add a letter it tells me I am wrong... but also told me to try lspci in the first place 
I tried various formats even converted the hex to decimal lol

:mad:


Thanks for your help

---

