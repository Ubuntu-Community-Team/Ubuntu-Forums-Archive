---
title: "Gnome based &quot;daemon&quot;"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by peterlauri on 2008-03-12
Hi,

This is what I want to accomplish:

In the background, there will be a script performing some operations once per minute. IF some condition is reached, I want an blinking icon in the top right corner to blink (like then getting new messages in Pidgin).

Are there any nice tutorial of how to automatically launch these icons in the top right corner?

I assume I have to have some background script running that is a child of the Gnome process, and then launch this icon when the condition is met.

/Peter

---

### Post by magicfab on 2008-03-12
Perhaps Zenity can help with that ? From the description:

Display graphical dialog boxes from shell scripts Zenity allows you to display GTK+ dialogs from shell scripts; it is a  rewrite of the `gdialog' command from GNOME 1.
 .
 Zenity includes a gdialog wrapper script so that it can be used with legacy scripts.

---

### Post by peterlauri on 2008-03-12
Thanks. It solved it for me. Thanks.

---

