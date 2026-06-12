---
title: "Cant find the @-key"
date: 2006-09-30
forum: Apple PPC Users
---

### Post by duzchip on 2006-09-30
I've just installed Ubuntu on my old iMac and everything's been working out just fine until now. I cannot find the key-combo to get an "@" (without " that is). Could anyone please help me.

---

### Post by DirtDawg on 2006-09-30
What happens when you use "SHIFT + 2" ?

---

### Post by duzchip on 2006-09-30
Shift + 2 = "

---

### Post by DirtDawg on 2006-09-30
> **duzchip said:**
> Shift + 2 = "

Wierd. *Ubuntu and Kubuntu may have a GUI to mess with your keyboard layout, so if you're using Ubuntu or Kubuntu, check for that first*. If that fails, maybe the following will help:

Open the terminal and enter the command:
```
 xev 
```
Press the 2 button and it will give you the keycode (along with some other info. But just look for the keycode).

Then enter 
```
 xmodmap -pke 
```
This will list all the keys and what they're assigned to. Look for the number that matches the keycode from the info above.

You can use 
```
 xmodmap -e 
```
to reassign a new character to the key. Like: xmodmap -e "KEYCODE=KEYFUNCTION"

Unfortunately, I'm on a Windows box right now, I won't have access to my linux box until tommorow, and I'm not familiar enough with the subject to help you with the exact syntax offhand. **You may need to be cautious ** with the syntax so you don't set the keys to something you don't want, then forget how to set it back. On the other hand, if you're somewhat familiar with Linux, maybe this will give you someplace to start or something to work with.

Maybe someone else can fill in the gaps? Otherwise, I'll try to help tommorow if you still need it.

---

### Post by DirtDawg on 2006-09-30
Okay, my '2' key is keycode 11 on my Mac. xmodmap -pke lists key 11 like this: ```
 11 = 2 at 
```

So, assuming your 2 key is also keycode 11, you would use
```
 xmodmap -e "keycode 11 = 2 at" 
```

Of course check to see what the proper keycode is and also make sure you have another working " button somewhere. 

I hope this helps. Sorry if it's confusing.

---

### Post by ssam on 2006-09-30
on mine it usually is on the " key.

have a look in system -> prefs -> keyboard. the US keyboard map is closest to my UK powerbook.

---

### Post by duzchip on 2006-09-30
okey, got it to work thanks to your help. Thanks a lot everyone!

---

### Post by DirtDawg on 2006-09-30
> **ssam said:**
> on mine it usually is on the " key.

have a look in system -> prefs -> keyboard. the US keyboard map is closest to my UK powerbook.

HA! I figured there was a simpler way. I use Xubunut, can you tell?

Glad you got it working. :KS

---

### Post by Hiroshima on 2006-10-01
I had the same problem... but with the ] key on a Japanese keyboard (Kubuntu) not seeing a fixit option in K Menu>System Settings>Keyboard, I followed the above directions in a terminal... which worked until I restarted the computer, when it went back to the way it was before... Just after I said "-hey dad, look I fixed it for you."

After > xmodmap -e "keycode 51 = bracketleft braceleft kana_MU kana_closingbracket" do I need to do anything to save the settings?

Cheers, Hiroshima

---

### Post by DirtDawg on 2006-10-01
> **Hiroshima said:**
> I had the same problem... but with the ] key on a Japanese keyboard (Kubuntu) not seeing a fixit option in K Menu>System Settings>Keyboard, I followed the above directions in a terminal... which worked until I restarted the computer, when it went back to the way it was before... Just after I said "-hey dad, look I fixed it for you."

After  do I need to do anything to save the settings?

Cheers, Hiroshima

I'm sorry, yes there is. 
```
 xkbset 
```
You may need to install the xkbset package for this to work. :KS

---

### Post by Hiroshima on 2006-10-12
I tried this, but with no luck.

I also tried > xmodmap ~/Xmodmap.save

But niether seem to keep the changes after I restart.  

I am using Kubuntu, and after googling for a couple of hours, I can't seem to find any answers, just more questions.  Any help would be great!

Cheers, Hiroshima

---

