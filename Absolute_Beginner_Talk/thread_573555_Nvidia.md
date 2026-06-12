---
title: "Nvidia"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-11
hi,

I can't download NVIDIA on my desktop on ubuntu 7.04. It's showing a message saying "can't translate character code. And then if i change to the other code it's also saying the same thing.

So what can i do to resolve this conflict??

Thnx

---

### Post by taurus on 2007-10-11
If you want to install nVidia for your graphic card, just do System -> Administration -> Restricted Drivers Manager -> Enabled.  No need to download and install it by hand.

---

### Post by arpeggi on 2007-10-11
> **taurus said:**
> If you want to install nVidia for your graphic card, just do System -> Administration -> Restricted Drivers Manager -> Enabled.  No need to download and install it by hand.

the only thing in that list is my wireless card. i'm in the same situation.

---

### Post by taurus on 2007-10-11
> **arpeggi said:**
> the only thing in that list is my wireless card. i'm in the same situation.

If you plan to download it from nVidia's site, make sure you download it as binary, not ASCII.  Also, you need a header file for your kernel before you can install nVidia by hand.

---

### Post by Het Irv on 2007-10-11
Have you acually downloaded the file and is it sitting on your desktop?
If so change the Properties so that it can be executed
Right-click, Properties, Permissions, Allow executing file as program.
Then try double clicking again.  If another box comes up click "run in terminal"

---

### Post by DJ_Peng on 2007-10-12
You may also want to try using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install the Nvidia drivers. I know some people hate Envy with the heat of a thousand nuns, but it's been a godsend for me on several occasions.

---

