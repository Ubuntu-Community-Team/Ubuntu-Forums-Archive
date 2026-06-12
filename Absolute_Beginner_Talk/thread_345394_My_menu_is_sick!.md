---
title: "My menu is sick!"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-01-24
Hi,

In the overall scheme of things, this is a very trivial problem, but it's a bit worrying and I'd like to know how to fix it. In my games menu, when I click for Aisleriot solitare, what I'm actually getting is Freecell solitare.  (And when I click on Freecell solitaire, I also get Freecell solitaire).

Last night both of these were working OK, but this morning It's as if the menu has got corrupted and is pointing to the wrong game.

As I say, it's a very trivial problem, but I'd hate it if this started happening with more important apps.  Any ideas what's happened, and how to fix it?

Thanks!

---

### Post by scrooge_74 on 2007-01-24
Go to applications>Accesories>Menu Editor

you will have to point the app, to the correct bin

---

### Post by DougDorr on 2007-03-29
I am having this problem, too.  Just started two days ago.  I have two accounts on my PC, mine and my wife's.  AisleRiot and FreeCell work fine on my account.  On my wife's, if you click on AisleRiot, you get FreeCell; click on FreeCell, you get FreeCell.

I reinstalled gnome-games, still have the problem.  I located the program "SOL" and discovered that "sol" is AisleRiot and "sol --variant freecell" is FreeCell.  I copied "sol" to a usb drive from my account and executed "sol" from the usb drive -- AisleRiot started.  I switched to my wife's account, mounted the usb drive and executed "sol" and freecell started.  Hmmm...

If you right click on "Applications" and click on edit menus, you can check the properties of AisleRiot and Freecell.  All looks good.

Help.............

---

### Post by DougDorr on 2007-03-30
bump

---

### Post by DougDorr on 2007-04-05
Found it!  Go to Applications -> Games -> AisleRiot  and Freecell starts.  Click on Game -> Select Game and scroll down to Klondike.  Select Klondike.  Play and then select Game -> Quit.   :guitar:

---

