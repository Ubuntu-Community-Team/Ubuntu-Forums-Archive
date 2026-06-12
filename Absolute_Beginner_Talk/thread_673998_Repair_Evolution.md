---
title: "Repair Evolution ?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Wharf Rat on 2008-01-21
Hello  all.
Perhaps someone can help me with Evolution.  
I was responding to an email when Evolution locked up.  After a bit of trying to close the window, I was asked if I wanted to wait or Force Quit.  The first time I waited for 2-3 minutes.  Then I forced Quit.  Now, Evolution will not start.   I did a Ctrl-Alt-Back space to restart my session but it remains the same.

I want to avoid deleting and reinstalling if possible so I don't loose any data.  
** I know, us Windows users are conditioned to reinstall everything ** 
I am learning that in Linux you seldom re-install anything as there are ways to fix everything.

---

### Post by CupofDice on 2008-01-21
Reinstalling shouldn't get rid of your data because it only takes out the files on root, not in your home directory where your data is stored. Have you tried running evolution through the terminal?

---

### Post by Golem XIV on 2008-01-21
If nothing works, try renaming the .evolution folder (note the period in front).  It's a hidden folder, so you'll have to press Ctrl-h in Nautilus to see it (or select "Show hidden files" from the View menu).

Start Evolution again.  If it works, you can import the stuff from the renamed folder.  If not, you can reinstall Evolution and then import.  Note that you will probably have to reconfigure your mail account(s).

---

### Post by Wharf Rat on 2008-01-21
Funny.  After two reboots. Evolution seems to work just fine.
????

Thank for the advice anyway.

---

