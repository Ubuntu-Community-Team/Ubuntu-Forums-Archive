---
title: "xorg reports more buttons then phisically exist"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by thetan on 2006-11-21
Hi folks,

I'm under Ubuntu6.06. xorg.conf pointer section looks like:
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Buttons"               "7"
        Option          "Device"                "/dev/input/event9"
EndSection
xmodmap reporting about eleven buttons but only 9 of them phisically exist(3 standard buttons, 2 wheels (second one is not pressable) and two side buttons, so totally, nine)! 
This is very confusing and some applications work incorrectly: they are using XTestFakeButtonEvent().

Option "Buttons" doesn't seem has any effect. I tried 9, 10 and even 3 there. :)

If I try 
 xmodmap  -e "pointer = 1 2 3 4 5 8 9 6 7 10"
then it suggest me to specify all 11 buttons.

Does anybody know where to dig into? 
  Thanks!

---

### Post by polly1 on 2006-11-21
Hi

You can try this link [http://www.ubuntuforums.org/showthread.php?t=246770&highlight=Multi+Button+mouse](http://www.ubuntuforums.org/showthread.php?t=246770&highlight=Multi+Button+mouse)

I have also read that that you need to count the scroll-down and scroll-up in
addition to all the  physical mouse buttons, which may be the difference.

---

### Post by thetan on 2006-11-22
There are following controls on my mouse:
1) two wheels; one of them also could be pushed down (BUTTON2)
  totally we have 5 buttons here: two scroll directions on both wheels and an ability to press the first wheel. So far, 5.
2) left and right ordinary buttons
  So far, 2
3) two side buttons 
  +2

Total: 5 + 2 + 2 = 9.
They must be hide somewhere inside the mouse! :(
Well this is not the case when I miss the scroll-up|down functions.
Anyway, thanks for your reply!

---

