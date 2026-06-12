---
title: "External Cinima Display Macbookpro 5,3 issue"
date: 2012-05-05
forum: Apple Hardware Users
---

### Post by matthewwallace on 2012-05-05
After a couple of days of digging through posts I have Ubuntu 12.04 running on my macbookpro 5,3 and loving it. The final issue I need to solve is using an external display.

I have an Apple 23' display connected via the mini diplay jack on the mbp. I open the display settings and it only detects the laptop display.

I have the INVIDIA drivers installed and it seems to be working just fine. Not sure what my next move should be to get the display working.

---

### Post by Hatsune Miku on 2012-05-05
A few questions for you before we try some solutions :)

1. Are you booted using the EFI or BIOS mode?
2. Are you using a Thunderbolt connection? Or the regular mini DVI?
3. Are you using the reccomended? or the latest NVIDIA drivers?
4. Are you using the NVIDIA X server settings? Or the Ubuntu one?

---

### Post by matthewwallace on 2012-05-05
> **Hatsune Miku said:**
> A few questions for you before we try some solutions :)

1. Are you booted using the EFI or BIOS mode?
2. Are you using a Thunderbolt connection? Or the regular mini DVI?
3. Are you using the reccomended? or the latest NVIDIA drivers?
4. Are you using the NVIDIA X server settings? Or the Ubuntu one?

1. I'm not sure if I'm using EFI or BIOS mode
2.I am using DVI
3. I am using reccomended and I've tried post installed updates
4. Not sure what these settings are and where to change them

---

### Post by Hatsune Miku on 2012-05-05
Alright lets try the first solution :)

1. Go to the Dash home and search for "NVIDIA"
2. Click on the NVIDIA Icon, that should bring up the NVIDIA X server settings
3. select the "X server display configuration"
4. On the bottom of the screen click on "Detect Displays"
5. Post back here to see if the system can find the display, if it does ill write u a guide to configure it how u want :)

---

### Post by matthewwallace on 2012-05-05
> **Hatsune Miku said:**
> Alright lets try the first solution :)

1. Go to the Dash home and search for "NVIDIA"
2. Click on the NVIDIA Icon, that should bring up the NVIDIA X server settings
3. select the "X server display configuration"
4. On the bottom of the screen click on "Detect Displays"
5. Post back here to see if the system can find the display, if it does ill write u a guide to configure it how u want :)

That worked and I was able to configure it so that both displays work, however it seems to cause some issues with different items such as the HUB and Dock on the left don't have transparency anymore and some of the other visual "effects" such as blurs and animations such as opening, minimizing and even extras like wabble windows don't work anymore. 

Is there a configurations that would allow for all the pretty stuff to work?

---

### Post by Hatsune Miku on 2012-05-05
> **matthewwallace said:**
> That worked and I was able to configure it so that both displays work, however it seems to cause some issues with different items such as the HUB and Dock on the left don't have transparency anymore and some of the other visual "effects" such as blurs and animations such as opening, minimizing and even extras like wabble windows don't work anymore. 

Is there a configurations that would allow for all the pretty stuff to work?

That I am not sure; no idea how the Unity UI is supposed to work with duel screens. If you want you just turn the other one off and use ur computer in clamshell mode, its what I do :)

---

