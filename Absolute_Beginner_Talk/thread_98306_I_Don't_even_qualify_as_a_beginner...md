---
title: "I Don't even qualify as a beginner.."
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by choptop on 2005-12-02
Ok, I was browsing Ebay one day and some one was selling Ubuntu. As I looked at their ad, it looked interesting and was obviously some form of Lunix I thought I would try it out. 
I searched around and found this site and downloaded the install ISO. Formatted an Old MMX233 and loaded up the Ubuntu (5.10).
Now I have a command line and No idea what so ever what to do with it.
Who holds the keys to Ubuntu? Where do I find the command line arguments?
Is this a trip to the library for a 500 page text book just to get to GIMP?
(I would like to try out this one) When I type in "gimp" at the command line it says "no can do pardner"....
I don't need insults, just a gentle nudge in the right direction...

---

### Post by teaker1s on 2005-12-02
sudo dpkg-reconfigure xserver-xorg 

this will run a setup program and when the settings are right type

startx

this will boot you into a point and click enviroment If you need any more assistance we're happy to help:KS

---

### Post by MetalMusicAddict on 2005-12-02
Actually in a PC that old you might not have had enough space for the install. How big is the HD?

---

### Post by SweetDreams on 2005-12-02
[QUOTE=choptop]Ok, I was browsing Ebay one day and some one was selling Ubuntu. As I looked at their ad, it looked interesting and was obviously some form of Lunix I thought I would try it out. 
I searched around and found this site and downloaded the install ISO. Formatted an Old MMX233 and loaded up the Ubuntu (5.10).
Now I have a command line and No idea what so ever what to do with it.
Who holds the keys to Ubuntu? Where do I find the command line arguments?
Is this a trip to the library for a 500 page text book just to get to GIMP?
(I would like to try out this one) When I type in "gimp" at the command line it says "no can do pardner"....
I don't need insults, just a gentle nudge in the right direction...[/QUOTE]
Welcome to the forum! I guess you had problems running the GNOME Display Manger, and that's not good. You might want to load Ubuntu on a better system.:???:

---

### Post by choptop on 2005-12-03
GNOME Display Manger... Hmmm I didn't get this far for sure.
The ol' rig has a 6g hard drive so should be plenty of room. However I may have done the partition wrong as I only see 2G non dos when I look at it with dos fdisk.
 I'm going to give Teaker1s's command line a try and see where I end up.
Thanks for the help!

---

### Post by choptop on 2005-12-03
Well we have a problem Houston!
after:
sudo dpkg-reconfigure xserver-xorg 
 I get xserver-xorg is broken or not fully installed

---

### Post by Jenda on 2005-12-04
Yes, you made the partition too small. Are attempting a dual-boot? I wouldn't recommend that on a 6 gig rig. Did you run the install CD's partitioner?

---

### Post by linbetwin on 2005-12-04
2 GB is too little. Give Ubuntu at least 3 GB.
Also, how much RAM do you have and what is the power of your CPU?

---

### Post by xmastree on 2005-12-04
A 233MHz PC might have a problem running gnome. Maybe you'll be better with xfce. Search the forums for xubuntu.

---

### Post by linbetwin on 2005-12-04
[quote=choptop]Ok, I was browsing Ebay one day and some one was selling Ubuntu.[/quote]
I'm glad you didn't buy it!
> As I looked at their ad, it looked interesting and was obviously some form of Lunix
Lunix! LOL
> I thought I would try it out.
Good start!
> Now I have a command line and No idea what so ever what to do with it.
Who holds the keys to Ubuntu? Where do I find the command line arguments?
Is this a trip to the library for a 500 page text book just to get to GIMP?
(I would like to try out this one) When I type in "gimp" at the command line it says "no can do pardner"....
The problem is that Ubuntu is not properly installed on your machine. If it were, you wouldn't need the command line to start a program, because they're all listed in nice menus.
> I don't need insults
neither do we give them.

> just a gentle nudge in the right direction...

---

### Post by choptop on 2005-12-04
Maybe I'll have to reload it again or something. I had 98 running on just one partition, formatted it off to install Ubuntu. About half way through the install, Ubuntu insisted I partition the drive and suggested two partitions. I proceeded and something didn't go just right and it made me try a second time. I told it to go 50% but some how ended up with 4g and 2g and it looks like Ubuntu installed itself on the 2g partition.

---

### Post by xmastree on 2005-12-04
strange. I installed over a win98 setup and I was offered the option of completely erasing the drive. That's what you want to do.

---

### Post by steve.horsley on 2005-12-04
I think you probably need a little more than 2G free for Ububtu. I would suggest 3G mimum. The best thing to do is NOT to create a partition for it, but to leave empty space on the disk and let the installer use that. It will then create 2 partitions in that space - a system partition and a swap partition. By empty space I mean unused space, not part of a partition at all - an empty but formatted partition is still used space in the view of the installer.

---

### Post by newuser111 on 2005-12-04
[QUOTE=choptop]Well we have a problem Houston!
after:
sudo dpkg-reconfigure xserver-xorg 
 I get xserver-xorg is broken or not fully installed[/QUOTE]

it sounds like ubuntu didnt install properly

anyway, you should check how much free space you have in windows and defrag your hard drive before partitioning imho

partitioning wont delete data so if your free space isnt enough for your desired partitions it wont work, thats what sounds like happened, although i can only speculate...

if that isnt your only PC I would just install ubuntu as the only OS, but then again i can understand you may need acccess to win98

---

### Post by choptop on 2005-12-04
I guess from the replys I have not stated things properly.
I started by completely formatting off the drive. only c: existed just one naked drive, just like it came from the factory. Ubuntu install did the rest.
Ubuntu insisted on the partition, just like Steve Horsely mentioned.
I'l give it another shot when I get home.

---

### Post by erikpiper on 2005-12-04
Good luck! Just to check- did you do a server install? (You would know if you did- so I am just checking)

---

### Post by kalos on 2005-12-04
If your computer is not modern enough to run Gnome well, you can try [Xubuntu](https://wiki.ubuntu.com/InstallingXubuntu).

-kalos

---

### Post by xmastree on 2005-12-04
[QUOTE=choptop]I started by completely formatting off the drive. only c: existed just one naked drive, just like it came from the factory.[/QUOTE]I think you'll find that the disk came from the factory without any partitions at all. No c: there.

use fdisk from a win98 (or whatever) boot disk to delete all partitions. Although the ubuntu installer should be able to do this for you.

---

### Post by choptop on 2005-12-05
[QUOTE=xmastree]I think you'll find that the disk came from the factory without any partitions at all. No c: there.
[/QUOTE]

picky picky picky!
you are so correct.

---

### Post by tikal26 on 2005-12-05
I know someone else already suggested it but you might really like to take a look at Xubuntu. that way you don't have to install any thing you don't need. I am saying this because I wondering how much ram you have. I had and old ibm k6 computer and it ran gnome fine but after I installed Xubuntu I was amazed. Here are two sites that would help you get started if you decide to do so
[https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29](https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29)
and screenshots
[http://shots.osdir.com/slideshows/slideshow.php?release=517&slide=2](http://shots.osdir.com/slideshows/slideshow.php?release=517&slide=2)
they also have screensgots for ubuntu and kubuntu if you want to follow along

---

### Post by choptop on 2005-12-06
Some progress has been made but now i'm just a bit stuck.
After another try at fdisking and formatting my hard drive and reinstalling Ubuntu (I have not given up yet) things did not get any better. Still had some error that told me I may have to fix later.
I decided to download the ISO again. This was the problem, my first ISO was bad. 
Now everything loads up properly (about 2.5 hours) but I could not read the screen. Ubuntu made it all the way to the graphical interface but the monitor settings were wrong and I could not read the screen. After some searching here I found the command  "sudo dpkg-reconfigure xserver-xorg " and after several attempts of adjusting refresh rates and syncs, I have a Ubuntu graphical screen looking at me.

Now I have a new problem I could use some help with.
I now see a Ubuntu gui showing, in the upper left corner there is a popup baloon showing the states "new updates available..." but my mouse does not work,(I think it did while loading up the program somewhere) and I can't find any combination of keystrokes that will allow me to do anything.
How do I get back to the command line? I saw some mouse configurations when I was using "sudo dpkg-reconfigure xserver-xorg " I am guessing this is where I would repair my mouse.

---

### Post by choptop on 2005-12-06
Ok I found my way back to the command line ctrl / alt F2
now I just gotta figgure out how to make the rodant crawl

---

### Post by Estariel on 2005-12-06
It's been a loong time since I used the configuration tool to set this up, but as far as I remember it should ask for the mouse device at some step.

Try entering
```
/dev/psaux
```
there.

If that does not work try
```
/dev/input/mice
```

I'm currently not at my ubuntu box, thus i cannot tell you which of the two is used in ubuntu...

---

### Post by xmastree on 2005-12-06
[QUOTE=choptop] but my mouse does not work,

I can't find any combination of keystrokes that will allow me to do anything.[/QUOTE]Alt-F2 should bring up a box where you can type the name of any program you want to run.

I suggest typing ```
gedit /etc/X11/xorg.conf
```and look at the mouse driver properties in there.
This is the entry for my Logitech usb mouse:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```
Tell us what it says and what kind of mouse you have (serial/PS2/usb).

---

