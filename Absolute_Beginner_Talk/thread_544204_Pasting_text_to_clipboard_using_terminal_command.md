---
title: "Pasting text to clipboard using terminal command?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-09-06
Just wondering if its possible to copy text into the clipboard using a terminal command.

---

### Post by paradoc on 2007-09-06
Hilight your text, then you can use Edit->Copy.

Open Text editor, 'Paste' is now available.....you're there!

Or maybe you're after a 'bash' short-cut....don't know of one

---

### Post by hyper_ch on 2007-09-06
and don't close the terminal before you haven't pasted the data... unlike windows the data in the clipboard will vanish when you close the application that you copied it from.

---

### Post by TomGier on 2007-09-06
Another option is to just highlight the text you want to copy (with your mouse or by using the keyboard), move your cursor over to target application and press the middle mouse button (resp. both buttons simultaneously on a two-button-mouse). That should do the trick, too.

Caveats: 
- if you close the application where you highlighted the text, your clipboard will vanish (as was stated before)

- as soon as any other text is highlighted, you get this instead of the text you'd like to have in the first place :). 

Cheers
Tom

---

### Post by vanadium on 2007-09-06
Contrl+Shift+Copy is the "keyboard" way.

I now see that this is probably not what the initial poster wanted: he is looking for a command that would allow to put some text to the clipboard.

---

### Post by dimension128 on 2007-09-08
I am looking for a way to do this also.
For example, I have a plain text document called 'readme'.
With a command, I want to pull all of the text (or a range) out of readme and put it on the clipboard.
I imagine this is probably possible, I just don't know where to look.

---

### Post by Phrawm48 on 2008-01-08
[I]Just wondering if its possible to copy text into the clipboard using a terminal command.
[/I]
Given the age of the question, you may well have figured out that the answer to this is *xclip*.

**NAME**: xclip - command line interface to X selections (clipboard)

**DESCRIPTION**: Reads  from  standard  in, or from one or more files, and makes the data available as an X selection for pasting into X applications. Prints current X selection to standard out.

This is in the Feisty repositories.  Probably earlier versions of Ubuntu repos too(?)

Cheers & hope this helps,
Ric
SFO

---

