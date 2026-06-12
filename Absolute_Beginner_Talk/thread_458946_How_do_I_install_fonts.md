---
title: "How do I install fonts?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by tomikotakahashi on 2007-05-30
Doing pretty well so far but, in an epic fail moment, how do I install fonts? TTF to be precise. It's probably really simple and I've SNAFU'd.

>>
<<

Thanks in advance.

---

### Post by eentonig on 2007-05-30
If only you need to use them. Just create a .fonts (of .Fonts, I'm not sure) directory and past them in there.

---

### Post by tomikotakahashi on 2007-05-30
> **eentonig said:**
> If only you need to use them. Just create a .fonts (of .Fonts, I'm not sure) directory and past them in there.

Where should I put the .fonts, anywhere?

---

### Post by mlentink on 2007-05-30
In your home directory

---

### Post by carloslosgrande on 2007-05-30
Have you had a look in 'add/remove applications'
Its right in there and real easy to do - just click and wait.
choose all and search for fonts, it'll pop right up.

---

### Post by tomikotakahashi on 2007-05-30
> **carloslosgrande said:**
> Have you had a look in 'add/remove applications'
Its right in there and real easy to do - just click and wait.
choose all and search for fonts, it'll pop right up.

Thankyou!

---

### Post by eentonig on 2007-05-30
> **eentonig said:**
> If only you need to use them. Just create a .fonts (of .Fonts, I'm not sure) directory and past them in there.

I agree, I was a bit short in my answer.

You should create it in your $HOME

Open a terminal and type.

> cd ~
mkdir .fonts


+:

This way, you can copy and past any ttf you find on the internet rigt in to this folder.

-:
It's only available to you.

Another way of working, to have the fonts available to everybody, is putting them in 
/usr/share/fonts

But you'll have to use sudo to put them there.

GUI style:
<alt><F2> 
> gksudo nautilus
browse to where you have the donwloaded fonts available. Copy and past in the 
/usr/share/fonts directory.

They will be available after the next login. (Anybody knows how to reload them without logging in again?

---

### Post by akahige on 2007-06-01
> **eentonig said:**
> 
browse to where you have the donwloaded fonts available. Copy and past in the 
/usr/share/fonts directory.

They will be available after the next login. (Anybody knows how to reload them without logging in again?

```
sudo fc-cache -f -v
```

They won't show up in the Details --> Go to font folder view, but they will be accessible through the font selection drop downs.

---

