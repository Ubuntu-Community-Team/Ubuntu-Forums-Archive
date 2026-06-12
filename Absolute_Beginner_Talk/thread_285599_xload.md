---
title: "xload"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by marx2k on 2006-10-27
This is the output I get at the terminal window when I try to run xload...

marx2k@UbuLappy:~$ xload
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

The xload window still loads but does not contain any text or numbers so the display is quite cryptic.  Does anyone have any ideas what to do here?

I tried this, but got this...
marx2k@UbuLappy:~$ xload -fn sans
Warning: Cannot convert string "sans" to type FontStruct
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

with the same visual result

---

### Post by marx2k on 2006-10-27
Looking at it, it may actually not display text/numbers after all even if it had a useable font set but Im wondering what that warning is about.  And is xload just supposed to be an graph and nothing else? No numbers to tell you what the graph represents or anything?

---

