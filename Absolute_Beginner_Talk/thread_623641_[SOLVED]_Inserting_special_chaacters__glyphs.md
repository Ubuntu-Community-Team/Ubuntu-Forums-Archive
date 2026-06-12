---
title: "[SOLVED] Inserting special chaacters / glyphs"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by JayFunGee on 2007-11-26
Hi

I often have to use Spanish characters in various software. It is easy enough in both Scribus and OO Writer to insert the characters through the respective utilities (Insert special character / Insert Glyph). However, these methods are slow and cumbersome. I have tried using the gnome-applet for characters - it seems to be a bit less of a problem in OO, however, Scribus won't paste the characters - probably got something to do with the clipboard?

During my previous life (in MS slavery) I used to memorise all the ASCII values for characters I needed and inserted them using Alt+### (eg Alt+136 = ê). I would ideally want to use a similar method since it is a lot quicker and minimises mouse activity.

I have noticed that both Scribus and OO Writer reports a similar value for each character, but these are different from the old ASCII values. Probably UTF8 values?

Now my questions:
1. Could someone please explain if there is a similar shortcut way to insert non-keyboard characters.
2. Could someone please point me to a simplified Linux specific explanation of UTF8  (Wikipedia a bit too detailed)

btw I have a Toshiba Laptop with a UK-English keyboard layout - no separate numerical keyboard - will buy one if necessary, though it is a nuisance

Thanks

---

### Post by marinesrock.1990 on 2007-11-26
I did a little research, and it looks like you can customize your keyboard to input special characters.  It has to do with creating your own library.  I didn't read the article fully, but here's the link to it:

[http://www.linux.com/articles/44902]("http://www.linux.com/articles/44902")

---

### Post by The Cog on 2007-11-26
Unicode is a character mapping scheme, much like ASCII except that where ASCII only deals with 7-bit character values up to 127, Unicode deals with 16-bit character codes up to 65535. The first 127 codes of Unicode represent the same glyphs as ASCII does.

UTF8 is an encoding scheme for Unicode. In UTF8, character values less than 127 (the most commonly used ones in the Western world) are represented by a single byte of the same value. Higher character codes are represented by 2-byte sequences. You don't need to worry about the UTF8 conding scheme though - this should only ever be seen in files/network protocols. When using applications, you only have to eal with the Unicode values.

Accessories->Character Map gives you a really neat utility that allows you to see the glyph and code for a huge range of character values. In your case, you probably want to go menu View->By Unocode Block which then puts the characters all in numerical order, with the lowest values first. The two blocks you want are probably Basic Latin (0-7F) or Latin-1 Suppliment (80-8F). Double-clicking a glyph places the character in the Text To Copy field at the bottom, where you can copy it for pasting into other windows.

---

### Post by JayFunGee on 2007-11-27
Thanks marinesrock.1990 & The Cog for your replies!

The info was really helpful. Further to your answers I also found the following really helpful discussion:

[http://ubuntuforums.org/showthread.php?t=619076&highlight=character](http://ubuntuforums.org/showthread.php?t=619076&highlight=character)

---

