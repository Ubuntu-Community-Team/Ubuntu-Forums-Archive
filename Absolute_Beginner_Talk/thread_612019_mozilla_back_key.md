---
title: "mozilla back key"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by dlbrando on 2007-11-13
how do I make the backspace button function as a shortcut to the back button in mozilla?  I didnt see a listing for in in the keybord shortcuts

---

### Post by philinux on 2007-11-13
you need to edit 

```
about:config
```

search 

browser.backspace_action

change the value from 1 to 0

---

### Post by dlbrando on 2007-11-13
the code listed came up as a command not found

---

### Post by nhandler on 2007-11-13
You don't put the 'about:config' in a terminal. You put it in the firefox address bar. Then, you should see a search bar on the page that loads. In that box, enter "browser.backspace_action". Right click on "browser.backspace_action" and select "Modify" from the menu. Now, a small window should pop up. Replace the number 1 with 0 in the text box, and close the window. That's all there is to it.

---

### Post by philinux on 2007-11-13
sorry should have said its for the address bar

---

### Post by dlbrando on 2007-11-13
sweet, that had to be the most annoying thing.  I saw the code box and assumed it was for the terminal.  Thanks guys

---

### Post by philinux on 2007-11-13
it seems the code box is unnecessary now but before you got a big smiley where the :c was

---

