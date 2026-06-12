---
title: "Flash Audio vs. Other Audio"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by budzooka on 2005-10-13
After searching I have an answer for Konqueror but not for the following:

If I use Firefox or Epiphany browsers in Ubuntu there is no audio for Flash. all other system sounds work fine, streaming audio, mp3's etc. What am I missing and how can I fix it?

Thanks in advance

budzooka

---

### Post by Kapre on 2005-10-13
[QUOTE=budzooka]After searching I have an answer for Konqueror but not for the following:

If I use Firefox or Epiphany browsers in Ubuntu there is no audio for Flash. all other system sounds work fine, streaming audio, mp3's etc. What am I missing and how can I fix it?

Thanks in advance

budzooka[/QUOTE]

budzooka - what release are your using? If your still on Hoary, try changing your sound settings (ESD, OSD, ARTS) because this also happened to me on Hoary (but not in Breezy).

K

---

### Post by Wolki on 2005-10-13
[QUOTE=budzooka]If I use Firefox or Epiphany browsers in Ubuntu there is no audio for Flash. all other system sounds work fine, streaming audio, mp3's etc. What am I missing and how can I fix it?[/QUOTE]

I assume you're using Hoary and esd (which is the default configuration).

Try the following:
Execute "sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1" in a terminal. Then restart firefox.

---

### Post by budzooka on 2005-10-13
[QUOTE=Wolki]I assume you're using Hoary and esd (which is the default configuration).

Try the following:
Execute "sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1" in a terminal. Then restart firefox.[/QUOTE]

Good assumption and thanks for the command line snack - worked like a charm!

Thanks again

budzooka

---

