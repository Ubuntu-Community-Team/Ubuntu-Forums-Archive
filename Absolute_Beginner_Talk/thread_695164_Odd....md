---
title: "Odd..."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Peryl on 2008-02-12
When I log in to Windows, I can connect to my wireless network from across the house. (about 10% connection)
 but when I go into Linux, my wireless card refuses to connect no matter what

---

### Post by ispy on 2008-02-12
my friend is having the same problem... with about 90% connection signal as well... he boots into Vista and gets internet though, which makes no sense. any help?

it's a Compaq Presario, i don't know the model. it's really turned him off to Ubuntu though, and I want to fix it so i can show him a world without walls or fences...

---

### Post by Presto123 on 2008-02-12
Did you install the drivers and enable it in Restricted Drivers Manager?

---

### Post by Yellow Pasque on 2008-02-12
Do you mean it refuses to connect from that location, or refuses to connect in general?

---

### Post by ispy on 2008-02-12
oh yeah, that's the thing i forgot, it looks like his restricted driver isn't supported or there's a bug in it...

it says something like bccxx cannot be enabled or something like that... i'm not exactly sure.

is there an open source alternative?

---

### Post by Presto123 on 2008-02-12
> **ispy said:**
> my friend is having the same problem... with about 90% connection signal as well... he boots into Vista and gets internet though, which makes no sense. any help?

it's a Compaq Presario, i don't know the model. it's really turned him off to Ubuntu though, and I want to fix it so i can show him a world without walls or fences...

Most likely he has the Broadcom. I have a Compaq Presario with the Broadcom WIFI and it is known to be a beast at times.

Do you know what you did to attempt to get the card to work?

---

### Post by Presto123 on 2008-02-12
> **ispy said:**
> oh yeah, that's the thing i forgot, it looks like his restricted driver isn't supported or there's a bug in it...

it says something like bccxx cannot be enabled or something like that... i'm not exactly sure.

is there an open source alternative?

Yes, there is. There is a program that many people swear by called Ndiswrapper and it's link is:

ndiswrapper.sourceforge.net/

---

### Post by ispy on 2008-02-12
i went into the restricted drivers manager, and it wasn't checked. so I checked it, and it freaked out on me. let me see if I can get him to boot it up for me. i'll be able to give a more detailed description.

EDIT: what's odd is the OpenSUSE live cd i tried on his computer had no problem...

---

### Post by Peryl on 2008-02-12
I pretty sure the Belkin 54g is a atheros card and the wusb54gv4 by linksys isnt broadcom either, i think you might be confused? 

It used to work and then one day it just died on me

---

### Post by Presto123 on 2008-02-12
> **ispy said:**
> i went into the restricted drivers manager, and it wasn't checked. so I checked it, and it freaked out on me. let me see if I can get him to boot it up for me. i'll be able to give a more detailed description.

EDIT: what's odd is the OpenSUSE live cd i tried on his computer had no problem...

Nah...they're different distros with different levels of support. Something that works in one may not work in another due to different teams of developers.

Yeah...if you get him to boot it up, post the output for the wireless from this command (Enter into Terminal):

```
lspci
```

---

### Post by ispy on 2008-02-12
he's tutoring at school right now, but i'll tell him to when i get ahold of him. i'll post the output then.

thanks for the help!

---

### Post by Presto123 on 2008-02-12
> **Peryl said:**
> I pretty sure the Belkin 54g is a atheros card and the wusb54gv4 by linksys isnt broadcom either, i think you might be confused? 

It used to work and then one day it just died on me

No...I was replying about the other poster's inquiry. Try that alternative program if you are having issues (Ndiswrapper). You both will probably have to blacklist the current driver you have and use a Windows driver with Ndiswrapper.

Search around the forums for how to blacklist wireless drivers, I don't remember how to do it, myself.

---

### Post by Presto123 on 2008-02-12
> **ispy said:**
> he's tutoring at school right now, but i'll tell him to when i get ahold of him. i'll post the output then.

thanks for the help!

Not a problem. I may or may NOT be able to help later on depending on the issue. I would suggest also posting a new thread as many people are more apt to help with an unanswered post.

---

