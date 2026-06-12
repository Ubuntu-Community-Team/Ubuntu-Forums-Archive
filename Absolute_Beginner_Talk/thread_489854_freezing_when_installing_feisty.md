---
title: "freezing when installing feisty"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by pinky88 on 2007-07-01
sorry for double posting on the same topic,but the subject of my other one probbly wasn't attractive..and i'm desperate ;)

so, here's the problem...


ok i tried to install feisty 7.04 ,and when installation was complete,i tried to remove the CD ,and nothing happened,tried a few more times and nothing happened again, so i pressed the restart button, i got a blank screen with brown background for a while,and then it changed to a navy/black background with a cursor that resembles a white clock that moves with the mouse )i'm new to linux,maybe this is like the windows egg-timer!!) ,anyways, this screen has stayed put for over half an hour,and no matter what i press (including the power button) it just won't go away. the laptop seems completely frozen..does anyone know a way out?????? i can't reboot or re-install as far as i know coz i can't get out of the blank screen.someone might know hpw to get out ??? i hope!

thanks :)

---

### Post by buzzmandt on 2007-07-02
force shut down by holding the power button in for about several seconds (5 i think)

had very similar problem, here's what i had to do
download iso for alternate cd...when booting the alternate cd at the first screen press F6, at the end of the line that comes up enter the following code at the end of the line after the --
"noapic nolapic" (without the quotes)

press enter and install

---

