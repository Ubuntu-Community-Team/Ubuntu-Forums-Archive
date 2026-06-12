---
title: "Ubuntu to Leopard error"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by NStoker on 2008-02-01
I've just reciently got ubuntu, I'm still a newb at it.  I changed my visual effects to high, and once I did that My themes went to a very basic one, I had the Mac Theme as I was making my computer look like a mac, Now I can't even change the theme. So I'm really confused.  So if you could help me that would be great! 

Thanks!!

---

### Post by NStoker on 2008-02-01
Does anybody know how I could go about fixing this?

---

### Post by eapache on 2008-02-01
Have you tried changing effects back to normal? And what does it do when you try to change your theme.

Also, what video card do you have? It might not support high visual effects.

---

### Post by NStoker on 2008-02-01
hmmm.... when I put the effects on None, it goes back to the mac setup, but once i put it to normal or extra it goes back to a standard one that won't change,  My video card is a NVidea Geforce 6800

Thanks!!:)

---

### Post by NStoker on 2008-02-01
And when I try changing it, It just won't change, even to a theme built into ubuntu.  Any thoughts?:confused:

---

### Post by NStoker on 2008-02-01
Dangit, I really did mess it up, lol.  I was playing with emerald and my minimize/maximize/ and exit are all messed up,  when I try changing it under appearance it wont change anything.  And I can't figure out how to change the icons! Thanks for the help!:)

---

### Post by eapache on 2008-02-01
Try```
metacity --replace
```

---

### Post by NStoker on 2008-02-01
It didn't do anything, Maybe I'll just be stuck on None under visual effects? Since it's only been a few days since i installed UBUNTU maybe I could just reinstall ubuntu? Do you think that could be a possibility? and if so how hard is it to reinstall it.
Thanks!:)

---

### Post by eapache on 2008-02-02
Reinstalling is just as easy as intsalling the first time. I would suggest just sitcking with no effects, as they aren't really necessary. You could also try installing a restricted driver under System>Administration>Restricted Drivers

---

### Post by jordanmthomas on 2008-02-02
```
killall emerald
gtk-window-decorator &

```
Try this with compiz enabled.  It looks to me like your metacity theme is the mac theme you speak of, but compiz is set to use emerald instead of your metacity theme.

If you have ccsm installed, you can run it and set your window decorator within it.

---

### Post by NStoker on 2008-02-02
Jordan, when i type that command this is what i get,   

nicolas@nicolas-desktop:~$ killall emerald
emerald: no process killed
nicolas@nicolas-desktop:~$ gtk-window-decorator &
[1] 6157
nicolas@nicolas-desktop:~$ 

It didn't help at all, Any more suggestions??:)

---

### Post by fiddledd on 2008-02-02
> **NStokhttp://ubuntuforums.org/images/uf/editor/separator.gif
[url]http://ubuntuforums.org/images/uf/editor/separator.gifer said:**
> Jordan[/url], when i type that command this is what i get,   

nicolas@nicolas-desktop:~$ killall emerald
emerald: no process killed
nicolas@nicolas-desktop:~$ gtk-window-decorator &
[1] 6157
nicolas@nicolas-desktop:~$ 

It didn't help at all, Any more suggestions??:)


You need root privelages for that command, add sudo to the start:

     sudo killall emerald

---

### Post by NStoker on 2008-02-02
Thanks guys it works great!!

---

