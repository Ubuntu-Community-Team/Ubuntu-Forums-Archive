---
title: "Keyboard key swapping possible?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by edwardcheng on 2007-04-19
The story: I got the backspace key wet - and it doesn't work anymore.

Are there any programs out there for Ubuntu that allow me to swap the backspace function to another key? (Currently I'm using Vista and have used "[Key Transformation]("http://softboy.net/key/index.htm")" to get past my hopefully last days using Ubuntu).

Please help me! :confused: 

**-Ed**

---

### Post by Arndt on 2007-04-19
> **edwardcheng said:**
> The story: I got the backspace key wet - and it doesn't work anymore.

Are there any programs out there for Ubuntu that allow me to swap the backspace function to another key? (Currently I'm using Vista and have used "[Key Transformation]("http://softboy.net/key/index.htm")" to get past my hopefully last days using Ubuntu).

Please help me! :confused: 

**-Ed**

There's the xmodmap program, to assign "key syms" to "key codes". Key codes are the identities of the keys themselves, and are small numbers. They vary between keyboards, but you can find them out with the xev program. Key syms refer to the character you want the key to send, and are listed in some file I don't remember right now, but you can list the assigned ones with xmodmap:

```
$ xmodmap -pk
```

Let's say you find out with xev that Insert has the key code 106. To assign backspace to that key, use the command

```
$ xmodmap -e 'keycode 106 = BackSpace'
```

There may exist something somewhat easier to use, but these are general X programs, not specific to Ubuntu (or even Linux).

---

### Post by edwardcheng on 2007-04-19
Thanks very much - sounds like it's valid. I'll try it when I've got ubuntu installed.

Thanks again,
**-Ed**

---

