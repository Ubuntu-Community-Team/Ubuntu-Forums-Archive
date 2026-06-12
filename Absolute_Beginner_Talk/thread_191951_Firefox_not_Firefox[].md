---
title: "Firefox not Firefox[?]"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-06-08
hi, why wont the same page show identical on Windows XP and Ubuntu 6??

here is what I mean:

---

### Post by mostwanted on 2006-06-08
Has that page got any flash in it?

---

### Post by Jagot on 2006-06-08
Well it's utilising Flash so my guess is that it is using functions in version 8 which are not available in version 7, which is what we are stuck with in Linux.

---

### Post by u.b.u.n.t.u on 2006-06-08
[QUOTE=Kuraboy]hi, why wont the same page show identical on Windows XP and Ubuntu 6??

here is what I mean:[/QUOTE]


Hi, url plz and I'll have a look.

---

### Post by Jagot on 2006-06-08
I've checked it out.  It's at:

[http://www.guildwars.com/](http://www.guildwars.com/)

---

### Post by mostwanted on 2006-06-08
Yes, then it was Flash as I suspected.

Flash 8 doesn't exist for Linux, so it's not a Firefox problem, it's a proprietary software problem.

---

### Post by u.b.u.n.t.u on 2006-06-08
[QUOTE=Jagot]I've checked it out.  It's at:

[http://www.guildwars.com/](http://www.guildwars.com/)[/QUOTE]

Looks fine to me. I have adblock and flash block installed in firefox so only those areas are empty. The page renders properly.

---

### Post by ctgray on 2006-06-08
No it doesn't. It uses Flash 8 as mostwanted stated, which isn't available in Linux.

---

### Post by gardara on 2006-06-08
What flash are you guy's using with firefox?

I tried ```
sudo apt-get install flashplayer-mozilla

``` But got the error message ```
E: Couldn't find package flashplayer-mozilla
```

So I tried searching synaptic for alternatives and only found **libflash-mozplugin** and now firefox closes when I open sites with flash on them... :???:

---

### Post by mostwanted on 2006-06-08
[QUOTE=gardara]What flash are you guy's using with firefox?

I tried ```
sudo apt-get install flashplayer-mozilla

``` But got the error message ```
E: Couldn't find package flashplayer-mozilla
```

So I tried searching synaptic for alternatives and only found **libflash-mozplugin** and now firefox closes when I open sites with flash on them... :???:[/QUOTE]

it's called flashplugin-nonfree and it's version 7 of Macromedia's plugin.

---

### Post by bruce89 on 2006-06-08
[QUOTE=gardara]So I tried searching synaptic for alternatives and only found **libflash-mozplugin** and now firefox closes when I open sites with flash on them... :???:[/QUOTE]
Are you using AMD64?

---

### Post by gardara on 2006-06-08
[QUOTE=bruce89]Are you using AMD64?[/QUOTE]

nope, is libflash for amd64?

Anyways flashplugin-nonfree works :)

---

### Post by bruce89 on 2006-06-08
[QUOTE=gardara]nope, is libflash for amd64?

Anyways flashplugin-nonfree works :)[/QUOTE]
Never mind then.  There is no flashplugin-nonfree for AMD64, because Microbe (Macromedia/Adobe) can't be arsed to make one for AMD64.
> Iceland is my favourite place in the whole world!

---

### Post by gardara on 2006-06-08
>  Iceland is my favourite place in the whole world!

great to hear! :D

---

### Post by bruce89 on 2006-06-08
Nice auroras there.

---

