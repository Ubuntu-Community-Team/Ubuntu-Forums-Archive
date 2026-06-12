---
title: "Compiz has broken something :|"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by talvon on 2008-02-26
I installed some extra compiz functions on top of  the onces that come with ubuntu to look at, but it messed a lot of stuff up and all my themes now have a red border for some reason, and I want to go back to the glossy theme :P

Is there a safe way to completely remove compiz? I just did it but it wouldn't load any windows, and the desktop config windows didn't have the buttons in the top right and the entire top bar was missing and the windows were unmoveable. Luckily kde was still working properly and I could install gnome-compiz from there.

Could somebody please post an untouched list of all compiz related installs on a fresh ubuntu installation? I would like to take all the others off, as there are some strange effects being used at the minute, and as mentioned above I don't want the red theme. I want to go back to the no-effects blue theme :P

---

### Post by TheLions on 2008-02-26
first disable compiz by disabling visual effects
then go in the synaptec, in find type compiz and on all installed objects use "select and completly remove"
press apply
and then install this packets: 
[[IMG]http://img117.imageshack.us/img117/627/prikazzaslonayx8.th.png[/IMG]](http://img117.imageshack.us/my.php?image=prikazzaslonayx8.png)

---

### Post by KhaaL on 2008-02-26
You could type *metacity --replace* to get back your borders and disable compiz.

And if you want to start over from scratch, you can delete the files in ~/config/compiz/compizconfig  and see if that does you any good. BEWARE though, this will remove your settings!

---

### Post by S15_88 on 2008-02-26
try going into synaptic and marking anything compiz for re-installation...i don't know whether the newly installed compiz will have the default settings or your previous settings but you can give that a try if you want.

Thanks, ALain

---

### Post by Therion on 2008-02-26
Before you go all nuts uninstalling stuff, you could try installing this [Compiz Icon](http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/) which would allow you to change both your Window Decorator and your Window Manager really easily with a tray icon.  It sounds like Emerald is currently set as your default Window Manager instead of Compiz.

---

### Post by talvon on 2008-02-26
I tried the fusion icon thing but the actual icon itself didn't show and I couldn't work it properly :( Maybe I'll try it again when I want to impress some people with the compiz effects lol

Ended up going back to metacity and then doing TheLions method, I removed everything and then installed as shown in the picture.

Thanks a lot guys I'm back on normal effects with the blue border :P Crisis averted and next time I'll double check before uninstalling random things lol

---

