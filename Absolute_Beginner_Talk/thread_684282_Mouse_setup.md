---
title: "Mouse setup"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2008-01-31
The last few days i have been trying to find out how to get my extra mouse buttons to work.

My system recognizes buttons 1,2,3,4,5

it sees the two side buttons as "2,3" and it doesn't see the side scroll feature.

my mouse is a rocketfish 2,4 laser mouse

[http://www.rocketfishproducts.com/pc-84-3-rocketfish-24ghz-wireless-laser-mouse.aspx]("http://www.rocketfishproducts.com/pc-84-3-rocketfish-24ghz-wireless-laser-mouse.aspx")

im running Ubuntu 7.10 gutsy




I have looked for howtos on this subject, but none of them seem to work.

---

### Post by LostMagix on 2008-01-31
*bump*

---

### Post by LostMagix on 2008-02-01
*bump*

---

### Post by LostMagix on 2008-02-01
*bump*

---

### Post by LostMagix on 2008-02-01
I got my side buttons to be recognized, but now my scroll isn't working even tho it is recognized.

I need some help.

---

### Post by jan quark on 2008-02-01
just a guess

fire up the terminal and run the following command

```
sudo gedit /etc/X11/xorg.conf
```

now search for this or a similar section
> Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

pls post yours thx

---

### Post by LostMagix on 2008-02-01
```
Section "InputDevice"        
	Identifier      "Configured Mouse"        
	Driver          "mouse"        
	Option          "CorePointer"        
	Option          "Device"                "/dev/input/mice"        
	Option          "Protocol"              "ExplorerPS/2"        
	Option          "Buttons"               "9"        
	Option          "ZAxisMapping"          "4 5"        
	Option          "ButtonMapping"         "1 2 3 6 7 8 9"        
	Option          "Emulate3Buttons"       "false"
```


when i run XEV when its like this, it reconizes my v^scroll as "5 6" but when i change my ZAxisMapping to "6 7" my scroll changed to something eles

I installed a program called "imwheel", here are a few of the codes for that....


/etc/X11/Xsession.d/63xmodmap

```
 killall imwheel
 xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
```



/etc/X11/imwheel/startup.conf

```
# Configuration file for setting imwheel startup parameters.

# Set this to "1" to make imwheel start along with your X session.
IMWHEEL_START=1

# Specify the command line parameters to pass to imwheel.
# Simply uncomment the bottom line, and if necessary replace
# the default options with your own. A button spec of "0 0 8 9"
# will grab the thumb buttons of most mice. "0 0 0 0 8 9" should
# work for mice with a scroll wheel with two axes. Keep in mind
# that each button number must be separated by a space.
#IMWHEEL_PARAMS='-b "0 0 0 0 8 9"'
```




~/.imwheelrc

```
".*"
None, Up, Alt_L|Left
 None, Down, Alt_L|Right
  
 "(null)"
 None, Up, Alt_L|Left
 None, Down, Alt_L|Right
```


What do you think?

---

### Post by LostMagix on 2008-02-01
I got my v ^ scroll working as it should, as are my side buttons, but i still havnt figured out how to get the side scroll to work

---

### Post by LostMagix on 2008-02-01
I have been tring to do this...

[http://ubuntuforums.org/showthread.php?t=682437&highlight=mouse+buttons]("http://ubuntuforums.org/showthread.php?t=682437&highlight=mouse+buttons")


but to no avail....

---

### Post by LostMagix on 2008-02-01
I just got done with me 13th howto and its still not right, i need some help here!!!

---

### Post by LostMagix on 2008-02-01
71 views and one person posts....


Im thinking this must be VERY simple or extremely complicated...

---

### Post by jan quark on 2008-02-01
if it only were simple.... 

besides .. why does your mouse have so many buttons? :) only causing trouble.:)
just joking and I don't forget you, still searching a solution in the background but it is not a piece of cake as it seems

---

### Post by LostMagix on 2008-02-01
I was planning on getting a 3 button mouse when my old one broke, but this one just felt right.

If i knew how big of a problem it was gonna be, i would have never got it, but now thats its here i can go all half *** with it, ya know?

Reading back into some of the other threads, i dont think i have seen one case where the tilt click thing was worked.

---

### Post by LostMagix on 2008-02-01
So far the adding of hardware is the only thing i dont like about Ubuntu (or linux in general) if we could make that a bit easer this would be the perfect OS in my opinion.

---

### Post by LostMagix on 2008-02-01
Im close to giving up on this, i have clocked a good 30 hours on this problem.....

---

### Post by LostMagix on 2008-02-01
Last bump of the day....

---

### Post by LostMagix on 2008-02-01
still no luck.....

---

### Post by LostMagix on 2008-02-01
*bump

---

### Post by LostMagix on 2008-02-02
*bump

---

### Post by LostMagix on 2008-02-02
*bump

---

### Post by LostMagix on 2008-02-02
*bump

---

### Post by LostMagix on 2008-02-02
*bump

---

### Post by LostMagix on 2008-02-03
*bump

---

### Post by LostMagix on 2008-02-03
*bump

---

### Post by LostMagix on 2008-02-03
*bump

---

### Post by LostMagix on 2008-02-03
*bump

---

### Post by LostMagix on 2008-02-03
*bump

---

### Post by LostMagix on 2008-02-03
This will be my 9th day working on this, how can a f**king mouse be so complicated?

---

### Post by LostMagix on 2008-02-03
This will be my last bump but i will be checking on this thread for the next few days.

---

