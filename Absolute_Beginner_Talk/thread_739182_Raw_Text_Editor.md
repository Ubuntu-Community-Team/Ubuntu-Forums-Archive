---
title: "Raw Text Editor"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-03-29
You know how notepad in Windows is just a raw text editor, that will display ANYTHING even if it does not understand it.

Is there a Linux text editor that just opens up anything that's dumped onto it?

I tried Ubuntu's built in text editor, but it's a fussy beast that complains if it can't fully understand the file.

There must be some sort of (in my own terminology) RAW file editor that just displays any file thrown at it?

thanks.

---

### Post by Dr Small on 2008-03-29
cat will open anything, as I have seen, and I think that nano and vim will too.

---

### Post by Inxsible on 2008-03-29
gedit in Gnome, Kate in KDE. Then there is also pico.

---

### Post by PiggiePaul on 2008-03-29
Thanks to you both for the suggestions.

For the record "Gedit" will not open up files.

I just tried loading a small PFD file into Gedit, and it complains it can't understand it. and won't display anything.

I'll look at the other suggestions.

---

### Post by Inxsible on 2008-03-29
> **PiggiePaul said:**
> Thanks to you both for the suggestions.

For the record "Gedit" will not open up files.

I just tried loading a small PFD file into Gedit, and it complains it can't understand it. and won't display anything.

I'll look at the other suggestions.but then again Notepad doesn't open PDF files right?

There are some formats which can be opened only by certain software.

---

### Post by LaRoza on 2008-03-29
Notepad is a bad editor. It is limited, for Windows, I use edit.com or Crimson Editor. The one good thing about it is that it is stupid (will open anything) and doesn't require a file lock.

If you want to open ANY file, use a hex editor, like gHex.

If you want a text editor to open anything, you can use Vim, emacs (don't!), or mc.

Vim: [http://www.vim.org/htmldoc/usr_23.html](http://www.vim.org/htmldoc/usr_23.html)
gHex is in the repository
Emacs is evil.

---

### Post by FuturePilot on 2008-03-29
Edit: Nevermind less is not a text editor, but it can still open just about anything.

You could try
```
less file.pdf
```
it doesn't look pretty though.

You could also use more, but less is more. :-s
Er, that hurts my head.

---

### Post by PiggiePaul on 2008-03-29
> **Inxsible said:**
> but then again Notepad doesn't open PDF files right?

There are some formats which can be opened only by certain software.

Yes, it does.... (just booted back into windows to try it)

It may display garbage at times but (unless I'm mistaken)  Notepad will display anything.

---

### Post by PiggiePaul on 2008-03-29
Just to add, thanks again for the other suggestions.

Just that sometimes I may want to open something just to look at the raw data, so like something that's not fussy and show shows anything you chuck at it, warts and all :)

---

### Post by Inxsible on 2008-03-29
I tried opening 3 different PDF files in Windows and it just opened it with junk. Hardly any use. :(

---

