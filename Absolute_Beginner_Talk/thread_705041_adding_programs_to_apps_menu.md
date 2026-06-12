---
title: "adding programs to apps menu"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by rockerphil on 2008-02-22
ok, here's the deal, i have successfully installed Firefox in my Fluxbuntu (standard default browser is Kazehakase) and am able to launch it from my terminal, but i can't figure out how to add it to my apps or applications menu, i looked under my System menu, but all i've got there is "Networking" and "Screen Resolution" any suggestions? plz bear in mind that i'm still pretty new to Linux

---

### Post by gyf on 2008-02-23
hi phil
 i am also fairly new to linux but im pretty sure you can add your own launcher to the applications menu by: Right Click on "Applications" menu tab -> Click "Edit Menus".

Then choose a pre-existing menu to put it under (for a web browser the "Internet" menu seems suitable) or you can create your own menu by clicking "New Menu".

After you have chosen the menu you wish to put the launcher under select "New Item". Then create the launcher:
Type: Application
Name: Name of the program
Command: what you would normally type in the terminal

Then click ok and the application should now be under the Applications tab under the sub menu you chose it to be under (if you chose a sub menu at all)!

---

### Post by wolfen69 on 2008-02-23
```
sudo apt-get install fluxconf
```

---

### Post by ShodanjoDM on 2008-02-23
> **gyf said:**
> hi phil
 i am also fairly new to linux but im pretty sure you can add your own launcher to the applications menu by: Right Click on "Applications" menu tab -> Click "Edit Menus".

Then choose a pre-existing menu to put it under (for a web browser the "Internet" menu seems suitable) or you can create your own menu by clicking "New Menu".

After you have chosen the menu you wish to put the launcher under select "New Item". Then create the launcher:
Type: Application
Name: Name of the program
Command: what you would normally type in the terminal

Then click ok and the application should now be under the Applications tab under the sub menu you chose it to be under (if you chose a sub menu at all)!

If you run GNOME (i.e. standard Ubuntu), then that is the way to add applications entry in the menu. However since the OP uses fluxbuntu, (which runs fluxbox), then it's different :)

@phil you can edit manually the menu entries. Or use fluxconf like wolfen69 posted. It's been a while since I used fluxbox, so I can't remember the exact details. Sorry.

---

### Post by gyf on 2008-02-23
ohhh right im sorry about that :(

---

### Post by ShodanjoDM on 2008-02-23
> **gyf said:**
> ohhh right im sorry about that :(

No need to be sorry. You have good intention, and that counts.
Here, have some :popcorn::)

---

### Post by rockerphil on 2008-02-23
hey y'all, the assistance is much appreciated, but i'm still lost as far as adding the programs to my applications menu, i tried running fluxconfig but all that gives me is a tool to configure fluxbox (which i'm still a bit scared to use at the moment) can anyone plz tell me how to manaully edit the menus or if there is a way to do it through my terminal? any assistance is greatly appreciated

---

### Post by RedSquirrel on 2008-02-23
See the Fluxbox menu link in my signature. It might help you to get a better understanding of how the Fluxbox menu works and how to customize it. I don't use Fluxbuntu so I'm not sure how they've setup the menu over there, but you might get some ideas anyway.

---

