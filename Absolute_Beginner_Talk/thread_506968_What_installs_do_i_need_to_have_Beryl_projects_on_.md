---
title: "What installs do i need to have Beryl projects on my laptop? (nvidia)"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by DaH-RaT on 2007-07-22
Hello everyone, ubuntu has me hooked and i already switched almost completely!! :) one thing though.. i have 3 computers and one laptop, all my computers have ATI cards and ive had hair loss with those just to even get ubuntu effects to even work and god forbid beryl to work lol. so i switched to my laptop for last hope since it has an nvidia 7800 GTX  so simple so far! but before i go any further i wanted to ask if theres a specific pattern of installs i need to do and what i might need before installing beryl or is it as simple as Compiz boom, beryl boom done?

---

### Post by sailor2001 on 2007-07-22
check synaptics for compiz-fusion and beryl............if you are feisty 7.04 no problem.......just for kicks, get kiba-dock also

---

### Post by DaH-RaT on 2007-07-22
wow its that simple with nvidia??

---

### Post by DaH-RaT on 2007-07-22
is compiz-fusion the same as compiz? cuz the search only brings up comiz and the core etc. or do i need to add the repositories and keys

---

### Post by DaH-RaT on 2007-07-22
meh.. had to reformat cuz i couldnt find or fix my window borders problem..

---

### Post by zekopeko on 2007-07-22
here is a little guide if that happens again (the border thingy):

press ALT+F2

and type 

metacity --replace 

this will give you back the borders but no desktop effects.

i don't know why this happened but go to 

[www.opencompositing.org](www.opencompositing.org) or here in the subforum Desktop Effects & Customization and ask for support.

before that try searching the forums for answer.

---

### Post by zekopeko on 2007-07-22
> **DaH-RaT said:**
> is compiz-fusion the same as compiz? cuz the search only brings up comiz and the core etc. or do i need to add the repositories and keys

compiz is the core of the project (compiz-fusion and now ex-beryl).

compiz-fusion is a set of plugins for compiz-core.

---

### Post by DaH-RaT on 2007-07-22
thanks everyone, im really glad yall are here :)

---

### Post by jvc26 on 2007-07-22
Just to give you a heads up, Beryl no longer exists, Compiz and Compiz fusion now have taken up the slack. Note, Compiz was the original, beryl forked off compiz and now the two have merged, so as of Gutsy, beryl will be pretty obsolete.
Il

---

### Post by DaH-RaT on 2007-07-22
okay awesome deal :) man this is awesome nvidia all the way ftw, i do favor ATI over nvidia but when it comes to drivers you cannot ride the band wagon. thanks everyone  now off to tweaking :lolflag:

---

### Post by AlexenderReez on 2007-07-22
> **Illuvator said:**
> Just to give you a heads up, Beryl no longer exists, Compiz and Compiz fusion now have taken up the slack. Note, Compiz was the original, beryl forked off compiz and now the two have merged, so as of Gutsy, beryl will be pretty obsolete.
Il

no..beryl is still exist...but its support will expired soon...you can get it from shame or trevino repo...but it is better just straight to use compiz fusion:) ..for nvidia card,i think if you enable driver in restricted driver manager then it will download driver and enable support for you...but before start compiz or beryl,just to make sure-->
> glxinfo | grep direct

it should appears yes but if no then 

> sudo nvidia-xconfig --add-argb-glx-visuals


then restart xserver or computer...

:)

---

