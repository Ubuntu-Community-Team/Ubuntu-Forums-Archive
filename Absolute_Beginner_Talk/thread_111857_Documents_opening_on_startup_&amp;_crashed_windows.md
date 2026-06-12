---
title: "Documents opening on startup &amp; crashed windows manager?"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by pbb on 2006-01-03
I tried out the option "Save current setup" on the logout screen, and since then I've been getting all the same windows opening at setup. How do I undo this?

To make things worse, I did it while I apparently had crashed my windows handler. That is, all my applications are now shown *without* borders and titlebar. So I am not able to move any windows around anymore. Every time I reboot Ubuntu now, all the same windows open up again, and I never get any windows with borders etc anymore :-(

I am not really sure how much these two problems are related, maybe they are two seperate things.

Does anyone have any suggestions how to solve this?

---

### Post by mcduck on 2006-01-03
[QUOTE=pbb]I tried out the option "Save current setup" on the logout screen, and since then I've been getting all the same windows opening at setup. How do I undo this?

To make things worse, I did it while I apparently had crashed my windows handler. That is, all my applications are now shown *without* borders and titlebar. So I am not able to move any windows around anymore. Every time I reboot Ubuntu now, all the same windows open up again, and I never get any windows with borders etc anymore :-(

I am not really sure how much these two problems are related, maybe they are two seperate things.

Does anyone have any suggestions how to solve this?[/QUOTE]
For the first problem you could try closing all windows, logging out and saving _that_ setup ;) 

With window borders I'd try changing the metacity theme (in System/Preferences/Theme).

---

### Post by pbb on 2006-01-03
Okay, your first remark helped me get rid of those auto-opening windows, thank you.

But the second problem remains. I have no "Metacity" in my list of themes, but no matter what theme I choose, the visual appearances change but I still get no borders or titlebar!

---

### Post by Suger on 2006-01-03
Can you open a terminal ? If you cant, open it and type metacity &

---

### Post by pbb on 2006-01-03
Thanks! Running metacity, and then logging out with "Save current setup", got everything working again!

---

