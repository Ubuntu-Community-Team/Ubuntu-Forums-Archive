---
title: "Help: Drag highlighted text to custom panel icon"
date: 2009-09-28
forum: Assistive Technology &amp; Accessibility
---

### Post by Buckwheat469 on 2009-09-28
I'm using Ubuntu 9.04 and I thought it would be fun to have Festival speak text for me. I've configured a shortcut icon to perform the command, but I can't get the dragged text to run in the program. I'm dragging text from Firefox, but this could imaginably work for any application.

I have:
echo "%u" | festival --tts

I know the "%u" doesn't work, so what would be the proper command to get dragged text to run in the command?

Thanks!

*Posted to accessibility because of the TTS part.

---

### Post by Buckwheat469 on 2009-09-29
Nevermind. I found out it's impossible to do because Ubuntu's drag and drop mechanism tries to build a file unless the text is dragged directly into an application. It throws up an error stating that the destination is not a directory if dropped on a desktop icon, and doesn't even try to drop the text on a panel icon.

---

