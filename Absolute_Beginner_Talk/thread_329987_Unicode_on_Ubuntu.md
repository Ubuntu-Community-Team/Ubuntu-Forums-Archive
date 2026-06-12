---
title: "Unicode on Ubuntu"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by noisc on 2007-01-02
Hey everyone,

This question may not even have anything to do with Ubuntu,but....

I've been trying to type some Unicode characters here in Ubuntu, and I'm not having any luck. I'm not entirely sure what keyboard sequence I'm supposed to be typing. So suppose I want to type the copyright symbol. The Unicode site ([http://www.unicode.org/charts]("http://www.unicode.org/charts")) says, under the 'Latin-1' section, that the copyright symbol has code 00A9. So what do I press/hold in order to get that to show up in, say, OpenOffice Writer? I've read things online about holding ALT or holding CTRL+SHIFT. Neither of these seem to work for any Unicode symbol. Anyway, please be detailed on any suggestions you give since I'm not really getting anything working and I've tried a lot of things. Is it as simple as installing a package or some fonts?

Also, I know that to input the codes, I've got to use the numeric pad. Now, I've got a laptop, and it's going to get really frustrating having to enable and disable the numeric keypad instead of just using the numbers above the letters. Is there a way to just use the numbers above the letters?

And one more thing: which text programs will this Unicode thing work in? Will it work in the OpenOffice programs, Emacs, and vim?

Any help would be appreciated.

And if you're wondering what it is I'm trying to do anyway, I want to type some Sanskrit (Devanagari).

---

### Post by goatflyer on 2007-01-02
According to:
[http://www.cl.cam.ac.uk/~mgk25/unicode.html#input](http://www.cl.cam.ac.uk/~mgk25/unicode.html#input)
  you can just hold Ctrl-Shift and type the Unicode hex digits.  I tried it and it works in terminal and gedit.  It failed to work in Mousepad.

You could also try some of the other suggestions in that link.

Have fun

---

### Post by noisc on 2007-01-03
Thanks for the reply.

Unfortunately none of those methods work for me. I've tried the Ctrl+Shift thing and it doesn't work in terminal, or gedit, or anything else (don't have mousepad installed).

I can get it to work in vim because vim's key input method is different: ctrl+v, u, then the hex code.

I have some really strange effects in terminal:
ctrl+shift+0 does a paste
ctrl+shirt+8 types "A" (without quotes)
ctrl+shift+2 types "B"
ctrl+shift+6 types "C"
ctrl+shift+4 types "D"
ctrl+shift+D quits terminal
ctrl+shift+7 scrolls to the top of the screen (the "Home" key)
ctrl+shift+9 scrolls one page up (the "PgUp" key)
ctrl+shift+3 scrolls one page down (the "PgDn" key)
ctrl+shift+1 scrolls to the bottom (the "End" key)
ctrl+shift+C copies text (this one I understand: it's one of the shortcuts defined under "Edit->Keyboard Shortcuts"

I don't understand how I can type unicode characters using the ctrl+shift method if I have these shortcuts in the way, but I don't know how to disable them or anything.

Is there setting or something I have to change to get the ctrl+shift method to work?  Maybe my Ctrl and Shift keys aren't mapped to the appropriate keys?

---

### Post by Efwis on 2007-01-03
did you try the character map under applications>accessories?

you choose the item you want, then you can copy and paste by hitting the copy button on character map, and right clicking on whatever program you are using and choose paste.

Even under Linux, the Unicode command for the copyright symbol (alt+0169 using the ten-key pad) isn't working for me in gedit, or OOo.

---

### Post by noisc on 2007-01-03
I have tried that, and sure, that works. But that's exactly what I don't want to do. I don't want to have to sort through character map every time I want to input a special character. If I can use Unicode, I can just make a list of characters that I'll need (I estimate around 15, max), and memorize the codes. (The alternative method is to make a text file with the characters I need pasted from character map and then just copy+paste from the file every time I need one. That's less desirable for me.)

Well, I suppose this isn't worth making such a big fuss over, but it's really silly that I can't get this relatively simple thing to work.

---

### Post by goatflyer on 2007-01-03
When I am terminal and hold ctrl-shift while pressing A9, I see the A9 underlined, and when I release ctrl-shift, the A9 turns into a copyright symbol.

My locale is utf-8, and I'm using gnome-terminal in ubuntu dapper.
```

$ set | grep LANG
LANG=en_CA.UTF-8
LANGUAGE=en_CA:en

```

Lets try to figure out the diff between my setup which seems to work, and yours which seems not to.

---

### Post by Efwis on 2007-01-03
> **goatflyer said:**
> When I am terminal and hold ctrl-shift while pressing A9, I see the A9 underlined, and when I release ctrl-shift, the A9 turns into a copyright symbol.

My locale is utf-8, and I'm using gnome-terminal in ubuntu dapper.
```

$ set | grep LANG
LANG=en_CA.UTF-8
LANGUAGE=en_CA:en

```

Lets try to figure out the diff between my setup which seems to work, and yours which seems not to.

question, you mention pressing A9, now what button would that be?

---

### Post by goatflyer on 2007-01-03
'A' then '9'

The characters are underlined so long as I still hold ctrl and shift together

---

### Post by Efwis on 2007-01-04
> **goatflyer said:**
> 'A' then '9'

The characters are underlined so long as I still hold ctrl and shift together

thanks, that worked for me also, doesn't work in OOo though, but it does work in terminal and Gedit.

Now I learned something new too.

---

### Post by goatflyer on 2007-01-04
In OOo it works, you have to press space after your hex codes.

In Abiword it also works, you have to press space, but you don't see the hex digits as you type them.

---

### Post by noisc on 2007-01-04
> **goatflyer said:**
> When I am terminal and hold ctrl-shift while pressing A9, I see the A9 underlined, and when I release ctrl-shift, the A9 turns into a copyright symbol.

My locale is utf-8, and I'm using gnome-terminal in ubuntu dapper.


Ok, I *think* I have the gnome desktop ('About GNOME' is listed under the System menu). Sorry, but I don't know what 'locale' I'm using. Perhaps if someone could tell me what that is and how to change it, that might fix the problem. (Hey, this is a newbie forum, right? I'm not supposed to know what I'm doing ;) )

I just run the 'Terminal' application (Applications -> Accessories). I hold down left ctrl and left shift, I press A then 9 (on the numeric keypad). Nothing shows up, the command line is still blank. I release ctrl and shift, and it's still blank. Nothing. 

[QUOTE="goatflyer"]In OOo it works, you have to press space after your hex codes.[/QUOTE]

That doesn't work for me, either. Again, nothing shows up, whether I press space before or after I release ctrl+shift. (Well, of course if I press space after releasing ctrl+shift, a get a blank space).

By the way, what does OOo stand for? I know you mean OpenOffice, what's the last o for? And does OOo refer to the word processor or the whole suite?

---

### Post by amerikkanu on 2008-01-09
Hi, if you'd like to type in Sanskrit (either transliteration or &#2342;&#2375;&#2357;&#2344;&#2366;&#2327;&#2352;&#2368; / Devan&#257;gar&#299;), you might want to check out my tips 'n tricks post [here]("http://ubuntuforums.org/showthread.php?t=646207&highlight=sanskrit+input").  Once you've set up SCIM with my tweaks, you can then input Devan&#257;gar&#299; or transliteration very intuitively and in any program system-wide.  Best of luck (and feel free to contact me if you run into any problems setting it up).  &#347;ubha&#7747; bhavatu.

---

### Post by abehrens on 2008-03-10
Applications that use newer GTK+ libraries (which includes all applications written for Gnome) require a "U" before the Unicode digits. Either of the following sequences should work:

[INDENT]Ctrl-Shift-U, *hex codes*, Spacebar

Hold down Ctrl-Shift, U, *hex codes*, release Ctrl-Shift[/INDENT]

---

