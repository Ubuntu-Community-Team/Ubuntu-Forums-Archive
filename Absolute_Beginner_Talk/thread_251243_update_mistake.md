---
title: "update mistake"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by wadetuple on 2006-09-05
yesterday, a little message came up top right, telling me software updates were available. like the eager puppy i am, i clicked to install them and then today when i came to get online my internet access was not working. i tried re-installing the modem driver but got confused when the messages i was getting back didn't correspond with the ones on the method i was following.

So i figured i'd remove the updated kernel using synaptic, because the old kernel still seemed to be there, but when i was doing this the terminal gave me a really heavy message saying that there was a good chance that the world would end if i went ahead and removed the kernel that i was using.:oops:  I removed it anyway, re-booted and could then get myself online. But, my questions are:

have i done any damage to anything else by removing the update kernel?

is there an easy way to copy over the changes i made to modem drivers and firmware and anything else i need to get online from an old kernel to a new one?

i want to use the most up to date, comprehensive and stable versions of things, but i don't want to spend ages fiddling with command lines to re-configure drivers and the like when i make an update..

---

### Post by petri on 2006-09-05
Every kernel update makes GRUB write a new entry. You should have option at the grub to choose older kernel. If your grub doesn't show up (Ubuntu is the only OS in you PC) hit Esc and you'll see grub.

1. I don't think there is any bigger damage if your comp is running now?
2. Dont know

---

