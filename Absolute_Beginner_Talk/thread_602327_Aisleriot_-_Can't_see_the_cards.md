---
title: "Aisleriot - Can't see the cards"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by TheGus on 2007-11-04
Since I updated to 7.10, I can't see any cards in Aisleriot Solitaire. My main game is Spider, but changing the game doesn't help. I know the cards are there, or at least the program thinks they are, because the hint button offers specifics: (i.e., place the jack of clubs on the queen of hearts, etc.)

---

### Post by yvesg on 2007-12-15
I got the same problem, but did not find any solution. When starting aisleriot from a terminal, it says:

> ** (sol:6574): CRITICAL **: aisleriot_board_set_card_theme: assertion `card_theme != NULL && card_theme[0] != '\0'' failed

** (sol:6574): WARNING **: Theme not loaded yet; cannot set size!

---

### Post by soutys on 2008-01-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/186753](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/186753) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Here's the solution:
[LIST]
[*]open **gconf** (*Configuration editor*) and find/go to the **/apps/aisleriot/cardstyle** key/resource
[*]my *aisleriot* uses **bonded** theme so you can type this name firstly and re-run application
[*]if there is still a problem try this:
[LIST][*]open **gnome-terminal**
[*]type **locate gnome-games-common/cards** (I hope there will be no problems with 'locate' tool :D)
[*]you should see something like this:[INDENT]```
/usr/share/gnome-games-common/cards
/usr/share/gnome-games-common/cards/bonded.svg
...
```[/INDENT]
I have only one aisleriot theme so there is only one .svg file named **bonded** - this could be Your missed theme...
Change the cardstyle key/resource value to your theme name (I said, **name**, please don't add any paths nor extensions)
[*]re-run your 'sol' app...
[*]Have a lot of fun... :D
[/LIST]
[/LIST]

I hope it will help someone...

---

