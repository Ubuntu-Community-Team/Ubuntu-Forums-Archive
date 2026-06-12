---
title: "[SOLVED] How to map the Fn key to a Super key"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Vadi on 2007-08-20
Hello,

I need to use the Super key for some combinations in Compiz Fusion, but my ThinkPad T40 doesn't have one. I searched about, and it seems people are replacing theirs with tab and shift keys, which is a bit problematic for me.

Is it possible to map the blue Fn key to fill the job of the Windows key? If so, how?

---

### Post by Nikron on 2007-08-20
> **Vadi said:**
> Hello,

I need to use the Super key for some combinations in Compiz Fusion, but my ThinkPad T40 doesn't have one. I searched about, and it seems people are replacing theirs with tab and shift keys, which is a bit problematic for me.

Is it possible to map the blue Fn key to fill the job of the Windows key? If so, how?

xmodmap and ~/.Xmodmap

man xmodmap  for more details

---

### Post by Vadi on 2007-08-20
I'm afraid I'm not that advanced yet. What do I do to find out the key code for my Fn key?

---

### Post by ronmarley1 on 2007-08-20
You might want to be careful mapping the Fn key as the Windows key.  For example, on my R51, the Fn+F7 key activates the external video out.  Also, Fn+Home and End effects the brightness of the LCD screen.

---

### Post by raijinsetsu on 2007-08-20
I found this [howto]("http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Determine_the_keycodes").
It shows you how to find the keycodes for the Fn key combinations, as well as how to edit your xmodmap :)

---

### Post by Vadi on 2007-08-20
What did you use personally as the Super key?

Oh and I found it's value to be 227. Now to set it right...

The above tutorial is somewhat confusing :/

---

### Post by yogo on 2007-08-20
After staring at my keyboard for a couple of minutes, where is the Fn key?

TIA

---

### Post by Vadi on 2007-08-20
I found this code...

       ! No Caps Lock
       clear lock
       ! Caps Lock as Win key
       add mod4 = Caps_Lock

That I should have in my Xmodmap in my home folder. But would replacing Caps_Lock with 227 do the trick?

---

### Post by Vadi on 2007-08-20
Should be bottom-left.

Here's a picture: [http://stuff.silverorange.com/images/t30/fnkey_small.jpg](http://stuff.silverorange.com/images/t30/fnkey_small.jpg)

---

### Post by brennydoogles on 2007-08-20
> **yogo said:**
> After staring at my keyboard for a couple of minutes, where is the Fn key?

TIA

Is it a laptop? If not, you may not have a Fn key.

---

### Post by Vadi on 2007-08-20
I've edited me Xmodmap to be:

```
keycode 227 = Super_L
```, but that didn't produce any visible effects.

Any ideas?

---

### Post by yogo on 2007-08-20
Thank goodness I do not have one, I was really getting ready to have my eyes examined.

On all laptops and desktops, I always have had Ctrl in it's place.

---

### Post by raijinsetsu on 2007-08-20
Did you restart your X server?
Log out then  press ctrl-shift-backspace. This will restart your X server. See if the key works then.

---

### Post by raijinsetsu on 2007-08-20
> **yogo said:**
> Thank goodness I do not have one, I was really getting ready to have my eyes examined.

On all laptops and desktops, I always have had Ctrl in it's place.

It's not new. It's been around since my old IBM thinkpad. It lets you access keys like "PgUp",  "PgDown", or system controls like LCD brightness and standby. Apparently, it works just like a ctrl or alt key :)

---

### Post by Vadi on 2007-08-20
Hm, no, still not working.

---

### Post by raijinsetsu on 2007-08-20
Sorry... Read some more of that post I gave you.
Did you run "/usr/bin/xmodmap $HOME/.Xmodmap"?

---

### Post by Vadi on 2007-08-20
I don't have an xmodmap directory in /usr/bin.

I edited ~/.Xmodmap, and then used xmodmap ~/.Xmodmap to apply changes.

---

### Post by raijinsetsu on 2007-08-20
Are you pressing any other keys with the Super key? I know that in KDE, it doesn't open the Programs menu, as it would in Windows.

---

### Post by Vadi on 2007-08-20
Yeah, I'm trying it with the negative plugin in compiz.

Still not working :(

---

### Post by dngpng on 2007-08-20
I've been trying to do so but no success.  According to what is said at [thinkwiki.org]("http://www.thinkwiki.org/wiki/Talk:How_to_get_special_keys_to_work#Bind_Fn_to_super_or_hyper"), 

> The event for the Fn key is generated at release (as opposed to holding it where it serves it's usual special function). Hence you can't use it as a modifier.

---

### Post by Vadi on 2007-08-20
Oh, alright. Caps it is then.

Issue solved!

---

