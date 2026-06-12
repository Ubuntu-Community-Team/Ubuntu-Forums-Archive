---
title: "gimp and gimpshop?"
date: 2006-08-26
forum: Art &amp; Design
---

### Post by xprlt on 2006-08-26
hi, Im a noob. 
so I wanted gimpshop, and I was searching for a deb. package, and I found one  of some chinese site.
then I figured, first uninstall gimp. so I did. 
then I downloaded that chinese gimpshop, and it seemed to install properly. 
but then I didnt see it in my applications menu. 
so then I thought maybe I need to install gimp again, who knows, Im a total noob to linux , I basically havent gota clue. 
so I did, and it was in the app. menu, but then when I click it, it sais:

Your GIMP installation is incomplete:

Failed to open file '/home/suramya/Temp/GimpShop/gimpshop//share/gimp/2.0/menus/toolbox-menu.xml': No such file or directory

Plase make sure the menu XML files are correctly installed.


so, it doesnt work anymore. in symnaptic package manager I found all kinds of XML stuff , so I installed that, but that didnt help eighter. it probebly has nothing to do with it anyway. 

so after all that I tried to reinstall that gimpshop again, but that gives an error too.

maybe someone here can help me out, please? Im pretty much confused.

---

### Post by lwr on 2006-09-01
Mmm. I'm not sure why the GIMP would be trying to look in there. It certainly won't find that directory. It might be worth reinstalling the GIMP by finding it in Synaptic Package Manager, changing the tick-box to reinstall, then clicking apply.

As for Gimpshop, it might just be that it's not showing on the menu. Go to Application>Accessories>Alcarte Menu Editor, and see if it's in there.

Hope this has been of some help. By the way, where did you get the .deb file? I'll give it a go on my machine and see if it works.

---

