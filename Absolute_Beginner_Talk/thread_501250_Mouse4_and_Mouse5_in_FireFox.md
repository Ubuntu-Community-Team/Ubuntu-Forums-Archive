---
title: "Mouse4 and Mouse5 in FireFox"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Diki on 2007-07-15
I've found a couple tutorials on these forums which apparently made the mouse 4 and mouse 5 buttons of mice function in FireFox, to be used as the Back/Forward buttons.

I have a **Microsoft Wireless Laser Mouse 5000** and found this code, which the user who wrote it claimed it worked on his **Microsoft Wireless Laser Mouse 6000** though it does not work for me:

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

Any help getting this to work for me will be appreciated.
Thanks.
(If it matters, I am using Ubuntu v7.04 - Feisty Fawn)

---

### Post by Hypnoguardian on 2007-07-15
To get it working in nautilus and lots of other programs, not just firefox, [this]("http://dotnet.org.za/matt/pages/39097.aspx") worked for me. I know it won't work for everyone but it's worth a try.

---

### Post by Hypnoguardian on 2007-07-15
Oh, and a few tips. In step 5 you can try "67" instead of "6 7". That works for some people. If your 5 buttons work but not the right ones just change the numbers in "ButtonMapping" and "ZAxisMapping" around until it's correct. The hard bit is to get 5 buttons working. Changing which buttons do what is easy. You need to experiment because all the 5 button mice are different, which is probably why this hasn't been implemented in Linux "out of the box".

---

### Post by wildgene789 on 2007-07-21
> **Diki said:**
> I've found a couple tutorials on these forums which apparently made the mouse 4 and mouse 5 buttons of mice function in FireFox, to be used as the Back/Forward buttons.

I have a **Microsoft Wireless Laser Mouse 5000** and found this code, which the user who wrote it claimed it worked on his **Microsoft Wireless Laser Mouse 6000** though it does not work for me:

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

Any help getting this to work for me will be appreciated.
Thanks.
(If it matters, I am using Ubuntu v7.04 - Feisty Fawn)


Hey dude where do i add that code sry im a new. please explain how i open the file too lol

---

