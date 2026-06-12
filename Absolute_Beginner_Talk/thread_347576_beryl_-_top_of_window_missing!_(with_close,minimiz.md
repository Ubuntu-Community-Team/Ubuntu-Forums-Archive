---
title: "beryl - top of window missing! (with close,minimize etc)"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-01-27
I tried to install beryl, and it's working fine, except that the top of every window is gone. I am currently using the beta nvidia drivers for my graphics card, done with: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29)

oh and this is on gnome.

thanks in advance.

---

### Post by Patrick-Ruff on 2007-01-27
that means that emerald isn't running.

try typing emerald & from the terminal.  

if that doesn't work something else is wrong.

---

### Post by Patrick-Ruff on 2007-01-27
also, you may want to try not using a beta driver ;)

---

### Post by moredhel on 2007-01-27
thanks for the quick reply, in the end i used [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

though you were right in the first place - i did emerald --replace or something like that and it fixed it, which is starting emerald :)

---

### Post by Patrick-Ruff on 2007-01-27
awesome, have fun :D. 

be glad you don't have ATI lol.

---

### Post by ReidP on 2007-01-28
Hey guys, I've having the exact same problem. When Beryl isn't loading, my normal Window Decorator is working, which by the way, I don't know what it is and the System -> Preference -> Theme loads themes, but doesn't change the way anything looks. So, when Beryl loads, I lose the top bar. When I type "emerald" in the terminal, it says that there is another program loaded, so I try "emerald --replace", which returns nothing, it just sits there, never showing another prompt. Even after adding emerald --replace to the Sessions - Startup Programs, it will still not load. Does anyone have any clue? I've searched the forums on both Ubuntu and Beryl, but can't find any answers.

---

### Post by RedPandaFox on 2007-10-23
I am having the same problem using 7.10, Before I upgraded from 7.4 I had a smiler problem when I used desktop effects, but when I disabled them it was fine, On 7.10 I tried it with beryl, and it took away my icons, then I uninstalled beryl, still the same problem, I tried emerald, still no help, any suggestions?

---

### Post by vertexoflife on 2007-10-23
I am just guessing, but could this have something to do with having Compiz By Default in 7.10? I had a problem with the top of my window dissapearing.

This is how I fixed it (In compiz)

1. Download ccsm (CompizConfig-settings-manager-)

( sudo apt-get install compizconfig-settings-manager )

2. Under Systems-Prefrences-> Advanced Desktop Effects Settings

3.Scroll down to Workarounds and try disabling Legacy Fullscreen Window Support

4. Report Back to us. =)

---

### Post by RedPandaFox on 2007-10-23
> **vertexoflife said:**
> 
2. Under Systems-Prefrences-> Advanced Desktop Effects Settings

3.Scroll down to Workarounds and try disabling Legacy Fullscreen Window Support


I did as you suggested but I cant find workarounds or Legacy Fullscreen Windows Support

---

### Post by vertexoflife on 2007-10-23
Um, try going to synaptic pacage manager and searching for 'compiz' and make sure that compiz-fusion-plugins-extra and compiz-fusion-plugins-main are installed.

---

### Post by RedPandaFox on 2007-10-23
Ok, i updated it, got to workarounds, workarounds was disabled at first so I left it disabled, and disabled Legacy Fullscreen Support, no help, tried enabaling workarounds and keeping L.F.S disabled, no change there either, then tried with workarounds enables, L.F.S enabled, still no change. 
With the top bar where the icons normaly are, it centers the text and id the text goes more than about 1/4 distance either side of the center, it cuts it out, like the bar has another part that hides it, it cuts it off mid letter even, could the windows be just hiding it for some reason?

---

### Post by rundee_f on 2007-10-24
ive experienced the same problem and i overcame it with this :

1. Go to your beryl manager
2. find window decoration (i forgot where coz im no longer on beryl)
3. in "command", type "emerald" (for emerald user) or "gtk-window-decorator" (for staandard border)
4. if that didnt work, uninstall ur beryl and install compizfusion.. :lolflag:

---

### Post by Tredici on 2008-01-28
Mine does the same thing, however it only does it when I use the alt tab command to scroll through the windows. I disabled the Legacy deal as said, and will update if the problem occurs again.

---

