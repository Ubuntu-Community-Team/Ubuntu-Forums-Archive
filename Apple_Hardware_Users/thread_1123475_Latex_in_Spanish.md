---
title: "Latex in Spanish"
date: 2009-04-12
forum: Apple Hardware Users
---

### Post by S.G. on 2009-04-12
Which packages do I need to be able to write directly in Spanish (like á ü and so on...)?
I've tried these two combinations:

\usepackage[applemac]{inputenc}
\usepackage[latin1]{inputenc} 

and

\usepackage[applemac]{inputenc}
\usepackage[spanish5]{babel}

And they don't seem to work.

Thanks in advance.

---

### Post by bruno9779 on 2009-04-12
It is not too clear what you want to do.
Spanish keyboards do not have the keys that you have specified: á and ü are typed by adding ´ or ¨ before a letter.

the only special characters you can type with one keystroke on a spanish keyboard are ñ and ç

---

### Post by S.G. on 2009-04-12
> **bruno9779 said:**
> It is not too clear what you want to do.
Spanish keyboards do not have the keys that you have specified: á and ü are typed by adding ´ or ¨ before a letter.

the only special characters you can type with one keystroke on a spanish keyboard are ñ and ç

To get LaTeX to print é, I don't want to write\'{e}, but directly é (that is, ´ and then e).

---

### Post by cyberdork33 on 2009-04-12
This is just a software question. I don't think it is Mac-specific. You will probably have better luck asking in the other areas of the forum.

---

### Post by S.G. on 2009-04-12
> **cyberdork33 said:**
> This is just a software question. I don't think it is Mac-specific. You will probably have better luck asking in the other areas of the forum.

All right, thanks. I'll try somewhere else.

---

### Post by mkvnmtr on 2009-04-12
On my spanish keyboard to get the accent above the e or a I have to press two keys at the same time. The letter of cource and the key beside the p.
éeééé Looks like it works on my english keyboard also when I have a spanish keyboard enabled in keyboard. That is in keyboard I have also enableded a spanish keyboard. Then I added the applet to the panel. I can switch between the two. On one computer that comes in spanish I have to guess where the english letters and symbols are. On the computer that came in English I have to guess which keys to use for the spanish accents. But in the end you get used to it.

---

### Post by tiagobt on 2009-04-12
Have you tried using just the following:
```
\usepackage[latin1]{inputenc}
```
?

This usually works for me. At least for Portuguese accents, which are pretty much the same as Spanish accents.

I don't know what the option "applemac" does, but I never needed it (although I use a MacBook).

---

### Post by S.G. on 2009-04-13
> **tiagobt said:**
> Have you tried using just the following:
```
\usepackage[latin1]{inputenc}
```
?

This usually works for me. At least for Portuguese accents, which are pretty much the same as Spanish accents.

I don't know what the option "applemac" does, but I never needed it (although I use a MacBook).

Thanks. I've already tried ```
\usepackage[latin1]{inputenc}
``` When I try to compile the document I get errors as if each word containing accents was math text...

Up to now I've never had problems with the combination:
```
\usepackage[latin1]{inputenc}
\usepackage[spanish5]{babel}
```

and thus I thought maybe it was the fact of having installed Ubuntu on a Macbook what was giving me problems...

Maybe it is Kile, I don't know. 

Thanks for the hint,

S.

---

### Post by cyberdork33 on 2009-04-13
I am not knowledgeable about latex at all, but I don't think it has anything to do with the specific hardware that you are on that I know of...
This might have more to do with whether or not latex supports those non-ASCII characters...

---

### Post by meho_r on 2009-04-13
> **S.G. said:**
> Thanks. I've already tried ```
\usepackage[latin1]{inputenc}
``` When I try to compile the document I get errors as if each word containing accents was math text...

Up to now I've never had problems with the combination:
```
\usepackage[latin1]{inputenc}
\usepackage[spanish5]{babel}
```

and thus I thought maybe it was the fact of having installed Ubuntu on a Macbook what was giving me problems...

Maybe it is Kile, I don't know. 

Thanks for the hint,

S.

Did you try with:

```
 \usepackage[utf8]{inputenc} 
```

However, some accents aren't available as single key and must be typed with combination of characters. Try with tipa package. Note that when you hover mouse cursor over a character in character palette in Kile, you'll get a hint if any additional packages are needed. And, of course, some characters are available only in math mode.

BTW, shouldn't be Kile's or Ubuntu's issue.

---

### Post by S.G. on 2009-04-13
> **meho_r said:**
> Did you try with:

```
 \usepackage[utf8]{inputenc} 
```

However, some accents aren't available as single key and must be typed with combination of characters. Try with tipa package. Note that when you hover mouse cursor over a character in character palette in Kile, you'll get a hint if any additional packages are needed. And, of course, some characters are available only in math mode.

BTW, shouldn't be Kile's or Ubuntu's issue.

Thanks!

That worked!

S.

---

