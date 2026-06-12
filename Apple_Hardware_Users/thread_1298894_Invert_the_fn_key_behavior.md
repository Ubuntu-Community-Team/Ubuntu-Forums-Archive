---
title: "Invert the fn key behavior?"
date: 2009-10-23
forum: Apple Hardware Users
---

### Post by bdash on 2009-10-23
Hi,

I'm on Karmic on a Macbook Pro 5,5. I got everything setup fine, except for the fn key. I have to press "fn" to get regular F1, F2, etc. I would like to invert that, have directly F1, F2 and press fn for "special" keys (brightness, sound...)

This page:
[https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard)

Sent me there:
[http://www.rickycampbell.com/swap-fn/](http://www.rickycampbell.com/swap-fn/)

But that doesn't work... Did anyone managed to invert this fn key behavior?

---

### Post by charger01 on 2009-10-23
Which version of karmic do you using?

Are lcd brightness and keyboard brightness works? And what abound sound? Everything works out of the box?

---

### Post by bdash on 2009-10-23
I'm using the most recent Karmic, as of today.

LCD brightness, keyboard brightness and sound work but none of them did out of the box. I had to install packages from the Mactel Jaunty PPA, and for sound compile Alsa from source. Also the keyboard brightness is not bound to the keys, I'm using scripts to adjust it.

---

### Post by kosumi68 on 2009-10-25
> **bdash said:**
> Hi,

I'm on Karmic on a Macbook Pro 5,5. I got everything setup fine, except for the fn key. I have to press "fn" to get regular F1, F2, etc. I would like to invert that, have directly F1, F2 and press fn for "special" keys (brightness, sound...)

This page:
[https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard)

Sent me there:
[http://www.rickycampbell.com/swap-fn/](http://www.rickycampbell.com/swap-fn/)

But that doesn't work... Did anyone managed to invert this fn key behavior?

With pommed installed, the configuration in /etc/pommed.conf overrides the kernel settings. Edit pommed.conf to contain the line
```

# General configuration
general {
	# fnmode: functions keys first (no need to use fn) or last
	# Value is either 1 or 2, effect is hardware-dependent
	fnmode = 2
}

```

---

### Post by bdash on 2009-10-25
Hi kosumi,

Thank you for your help. I tried but it's ineffective. I've also tried to remove pommed (and it seems I didn't need it anyway), but the original fix still doesn't work...

Is there any log I can check to see what drivers are in place, and get some more info about that ?

---

### Post by albelock on 2009-10-26
> **bdash said:**
> Hi,

I'm on Karmic on a Macbook Pro 5,5. I got everything setup fine, except for the fn key. I have to press "fn" to get regular F1, F2, etc. I would like to invert that, have directly F1, F2 and press fn for "special" keys (brightness, sound...)

This page:
[https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard)

Sent me there:
[http://www.rickycampbell.com/swap-fn/](http://www.rickycampbell.com/swap-fn/)

But that doesn't work... Did anyone managed to invert this fn key behavior?

Found in the comments in the blog post, try this:
```

options hid_apple fnmode=2

```


Alberto

---

### Post by bdash on 2009-10-26
It works, thank you albelock!

---

