---
title: "Something horrible: the way words are wrapped in Terminal or plain text mode"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-05-24
I've noticed this years ago, but I'm asking this now.

Why can't Linux properly wrap words when in text mode? I know that URLs (for example) can't be/shouldn't be wrapped, but what about other words? You people like seeing words truncated "just because there was no more space on the line"? I mean there should be some routine that stores the maximum number of characters in a line and then checks if the remaining space is enough for the current typed word (otherwise move the word to the next line); this is basic WORD-WRAP!

Sometimes, I see mixed output: shell output (like prompt, commands entered from the keyboard) + programs' output + whatever-I-type-when-the-shell-is-in-background-and-the-foreground-process-still-loads output. I know Linux treats the display as a file, but come on! Sometimes there is no way to discern between what I type and what different programs output; my screen becomes a mixed garbage!

Notice how the dash-separated-words above formed too long a word that was moved to the next line? That is what I want to see in Linux. Please, Linux, truncate words only when they're longer than a line!

---

### Post by Koech on 2006-05-24
I think you have a valid point. This is one thing about Ubuntu that needs to be solved, I'd like word wrap too and the ability to cut and paste in terminal too.

---

### Post by skinnygmg on 2006-05-24
you can cut and paste in the terminal if you use the edit menu in the toolbar

---

### Post by S{yndrom}e on 2006-05-24
uhh u can cut and paste into terminal.... its just nost shift+v, its crt+shift+v

---

### Post by matthew on 2006-05-24
Re: cut & paste in the terminal

Instead of ctrl-x, ctrl-c and ctrl-v 
use
ctrl-shift-x, ctrl-shift-c and ctrl-shift-v

---

### Post by engla on 2006-05-24
Well..
shell commands should not be wrapped, obviously. You can't risk extra spaces or linebreaks hiding in a long line of commands.

If you want to read more text than simple command lines, like files or shell output, use an editor like vi, emacs, or why not gedit.

---

### Post by zugu on 2006-05-24
[QUOTE=engla]Well..
shell commands should not be wrapped, obviously. You can't risk extra spaces or linebreaks hiding in a long line of commands.

If you want to read more text than simple command lines, like files or shell output, use an editor like vi, emacs, or why not gedit.[/QUOTE]

So I guess it's a *Powerful scripting* vs *Nice visuals* match and *Powerful scripting* wins. Geeks win :D. Still, the command line mode is the most conservative part in the whole system. This wrapping issue (though might have a well defined logic and some may consider it a minor one) will always be a turnoff for many potential new users. And why not, senior users.

---

### Post by Koech on 2006-05-24
[QUOTE=S{yndrom}e]uhh u can cut and paste into terminal.... [/QUOTE]
I meant you can't select text and cut or even paste over as I am used to. It's a bit of a bother but guess I have to get used to...

---

