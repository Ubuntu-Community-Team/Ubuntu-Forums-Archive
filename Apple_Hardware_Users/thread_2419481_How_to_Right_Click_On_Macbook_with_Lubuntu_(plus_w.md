---
title: "How to Right Click On Macbook with Lubuntu? (plus where's the delete button?)"
date: 2019-05-22
forum: Apple Hardware Users
---

### Post by jazzymac on 2019-05-22
Hi all,

Can anyone tell me how to **Right Click** On Macbook with Lubuntu?

I've tried the instructions for Unbuntu, but they don't work for Lubuntu. Also can't install any 'tweaks' apps in Lubuntu.
Just to say, an external USB mouse works with L+R clicks. It's just there's no right click available on the Macbook - neither a 'two finger click' or a ctrl + click work.
Shouldn't this be a 'stickie' on the forum?

Thanks for you help.

---

### Post by HermanAB on 2019-05-22
Delete should be fn-backspace.

---

### Post by jazzymac on 2019-05-23
Thanks HermanAB, the 'fn+&#8592;'  works great for delete. Fantastic.

If you know how to get a 'right click' working that would be great too!

All the best.

---

### Post by HermanAB on 2019-05-23
'Right click' should be 'two finger tap', but you may need to run the mouse pad configuration utility - whatever that is on Lubuntu I don't know.

---

### Post by jazzymac on 2019-05-23
> 'Right click' should be 'two finger tap', but you may need to run the  mouse pad configuration utility - whatever that is on Lubuntu I don't  know.
Thanks, but I don't think there is a 'mouse pad configuration utility' that has those options in Lubuntu.
However, currently it seems that fn + F12 gives a right click. Whilst it's not the most convenient, it seems to work!
I've tried re configuring it with 'mouseemu' but haven't had any luck, so for now F12 it is!

---

### Post by HermanAB on 2019-05-24
See the bottom of this
[https://askubuntu.com/questions/1023855/where-is-trackpad-config-in-lubuntu-17-10](https://askubuntu.com/questions/1023855/where-is-trackpad-config-in-lubuntu-17-10)

---

### Post by wildmanne39 on 2019-05-24
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by jazzymac on 2019-05-24
> See the bottom of this
[https://askubuntu.com/questions/1023...-lubuntu-17-10]("https://askubuntu.com/questions/1023855/where-is-trackpad-config-in-lubuntu-17-10")

Thanks, but this seems to be about disabling the trackpad rather than enabling a right click? My trackpad is working. On a mac two fingers on a track pad and click gives a right-click or a crtl+click gives a right-click. Neither of these two work on Lubuntu. For the time being fn+F12 give a right click which is great as before I didn't have that at all.

I've tried this code:
```

#MID_CLICK="-middle 0 68"         # F10 with no modifier
MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 87"        # F11 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
```

but this didn't assign the ctrl key, but instead stopped the fn+F12 working.
Further to this, the orginal poster put:

```
gksudo gedit /etc/default/mouseemu
```

and this no longer works. Instead you need to use:

```
 gedit admin:///etc/default/mouseemu 
```

This allows you to edit the mouseemu file but I still can get the ctrl+click to work.....

---

### Post by Joao Lacerda on 2019-12-23
Hi Frind, 

I had the same problem, take a look on this site. that was for me the solution. 

[https://itsfoss.com/fix-right-click-touchpad-ubuntu/](https://itsfoss.com/fix-right-click-touchpad-ubuntu/)

---

