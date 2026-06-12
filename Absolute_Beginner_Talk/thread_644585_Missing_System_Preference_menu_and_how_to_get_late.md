---
title: "Missing System Preference menu and how to get latest updates"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by JosephBus on 2007-12-19
1. Missing System->Preference Menu

2. How do I get latest update?

Thanks, Joseph

---

### Post by shadow-of-sin on 2007-12-19
Not sure about the missing menu but you can get the latest updates by typing this in the command line:
```
sudo apt-get update && sudo apt-get upgrade
```

BTW you should make your title more descriptive...

---

### Post by RomeReactor on 2007-12-19
Hi. Right-click on the menus and select "Edit Menus"; on the left pane, highlight **System**, and on the right see if "Preferences" is unchecked.

---

### Post by JosephBus on 2007-12-19
Shadow-of-sin:

Thx for yr msg.

Yes , I discovered my title was missing.

RE: latest upgrade , is that cmd provide full set of pgms in current distribution, or latest distribution? I guess I should have been more specific. I don't want to be on the bleeding edge.

RE: system->preferences, yess the total preferences file is missing.

Joseph

---

### Post by shadow-of-sin on 2007-12-19
> **JosephBus said:**
> 
RE: latest upgrade , is that cmd provide full set of pgms in current distribution, or latest distribution? I guess I should have been more specific. I don't want to be on the bleeding edge.

That command will only update your programs and install any updates for the version of Ubuntu you are currently running, it wont upgrade to a new version of Ubuntu.

---

### Post by RomeReactor on 2007-12-19
Try right-clicking in an empty space in the top panel and select "Add to Panel..." and look for **Menu Bar**; see if that menu shows "Preferences" (in which case you can delete the old one and move the new one to the correct location).

---

### Post by nowshining on 2007-12-19
when u go to edit menus - look at the bottom and click the revert button to set the default menu layout.

---

### Post by RomeReactor on 2007-12-19
> **nowshining said:**
> when u go to edit menus - look at the bottom and click the revert button to set the default menu layout.

Now that *is* useful; I didn't even notice that button...

---

### Post by JosephBus on 2007-12-19
RomeReactor: Thx 4 yr msg.
Upon: Menu  editor -> SYSTEM selected, get NADA on RHS.
SYSTEM is selected but RHS is blank (except for name field=System)
joseph

---

### Post by JosephBus on 2007-12-19
Shadow-of-Sin: Thank You, Sir

---

### Post by nowshining on 2007-12-19
> **RomeReactor said:**
> Now that *is* useful; I didn't even notice that button...
ur all welcome, i think feisty and backwards did NOT have that button and u had to manually go and reset em' by deleting the files in ur home folder in a hidden folder. :)

---

### Post by JosephBus on 2007-12-19
RomeReactor: Thx 4 yr msg.

Rt Click in empty space there only provides the Toolbar menu. No options around for "Add to Panel" but "Add submenu". That didn't go anywhere.

---

### Post by nowshining on 2007-12-19
> **JosephBus said:**
> RomeReactor: Thx 4 yr msg.

Rt Click in empty space there only provides the Toolbar menu. No options around for "Add to Panel" but "Add submenu". That didn't go anywhere.
right-click an open space on the taskbar called a penel or panels in gnome.

U can place em anywhere u want to, add a new panel, add other app icons and so forth. if u right-click and select properties u can change the background color - make transparent and so forth.

---

### Post by JosephBus on 2007-12-19
Nowshinning: Got logged off! Thx 4 yr msg.
No revert button, Interesting that RomeReactor has one.

---

### Post by nowshining on 2007-12-19
are u using ubuntu gutsy?

and i also got logged off of ubuntu :P as I to had to re-sign on.

---

### Post by RomeReactor on 2007-12-19
Try nowshining's suggestion:
> **nowshining said:**
> when u go to edit menus - look at the bottom and click the revert button to set the default menu layout.

EDIT: Sorry, didn't see that you already tried that...

---

### Post by JosephBus on 2007-12-19
No System->Preferences, no revert button,  KDE 3.5.6

Rt Click panel does not offer properties.

This all smacks of user options,not  as administrator??

---

### Post by Sef on 2007-12-19
> This all smacks of user options,not as administrator??

Preferences are options.

---

### Post by RomeReactor on 2007-12-19
> **JosephBus said:**
> No System->Preferences, no revert button,  **KDE 3.5.6**

Sorry for the misunderstanding; I thought you were running Gnome.

---

### Post by nowshining on 2007-12-19
> **JosephBus said:**
> No System->Preferences, no revert button,  KDE 3.5.6

Rt Click panel does not offer properties.

This all smacks of user options,not  as administrator??
ah we thought u were using gnome - ur using kde that's why are suggestions did not work. sorry  but a kde user is who u have to wait for.

---

### Post by JosephBus on 2007-12-19
Nowshining:

I don't know how to character my Ubuntu version other than:

KUBUNTU 7.04, KDE 3.5.6, + those updates I just did using RomeReactor's 
sudo apt cmds.

Gentlemen: I have to check out until manana. "I'll be BAK"...
Thank you for your wisdom. Joseph

---

### Post by nowshining on 2007-12-19
u could go into options in ur User CP and put ur distro as Kubuntu so others know what u are using.

so ur saying u got the updates right

if not

u'll have to open up kde's terminal and issue those commands.

---

