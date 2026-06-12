---
title: "Bluetooth Keyboard Buttons"
date: 2008-05-14
forum: Apple Hardware Users
---

### Post by gforster on 2008-05-14
I have searched the forum for answers to this particular problem, but I have nothing, so i figured the best place is to ask here. 

I have my bluetooth keyboard (slim aluminum) working under Hardy just fine. It connects and everything which is what most people have had trouble with. What I would like to do is enable the expose and  dashboard buttons to work with compiz. Under my advanced desktop effects settings, when I go to "scale" (the expose effect), and enter in the expose/F3 button, it says that it is disabled. It does recognize Fn + F3 as F3 , so I know that it is not a broken button. Same thing with the dashboard/F4 button. 

Can anyone point me in the direction to "enable" these buttons?

Somewhat related, I would like my play/pause/ff buttons to work with amarok.  They work great under rhythmbox. Any suggestions there?

Last but never least, if I were to desire to switch fn and control buttons, how would i do so?

Oddly, I like the way the f buttons work (holding fn to enable). BTW, I love this keyboard other than its little quirks!

---

### Post by cyberdork33 on 2008-05-14
there are quite a many bug reports with the aluminum keyboards.

the Fn+F3 behavior is how things work on a Macbook (Pro). For some reason, the aluminum keyboards are recognized as the same keyboard that is in a Macbook (Pro) and thus operate similarly. F3 has some other default function on a portable...

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/201711](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/201711)
[https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/207127](https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/207127)
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/214786](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/214786)
[https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162083](https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162083)

---

### Post by gforster on 2008-05-14
Thank you for those links, but I've already read many of them and the other wasn't helpful for my specific situation. The problems they mention are not problems for me. My Fn key works just fine, the way I expected it to (as on a macbook pro).

I know the expose button is recognized as a button in some form or another, because when I press it while trying to set the binding, the text changes to "disabled." The dashboard button does the same thing. So, somewhere in some configuration file, that button has been disabled. I just don't know where.

In my keyboard shortcuts I notice a few different buttons named 0x** - is there a place that I can test the output of all my buttons to see what they are mapped as?

---

### Post by cyberdork33 on 2008-05-15
xev will give key outputs.

Those are special functions so i have no idea how they should work or if they even will. There is a cool little keyboard application that is supposed to allow you to use the special keys on many keyboards and map them to the correct function. I don't know if it will work for you, but it might be worth a try.
[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

---

### Post by gforster on 2008-05-16
Hmm . . .xev gives me output for the expose button (F3 without Fn), but none for the dashboard button (F4 without Fn). They both give output for the buttons while pressing Fn as expected. I don't necessarily want to make this work like a pc keyboard, I'd like to make it work like a mac's first. Right now, the only things I can't get working that way are dashboard and expose buttons. Once that is settled, then I might possibly want to start playing with custom configs for it. Anyway, here is the output of my xev for the expose button.  Can someone help me with what it means and what I need to do to "enable" it so that it is recognized in Compiz-fusion or at least the rest of ubuntu?


```
KeyPress event, serial 28, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x0, time 78235758, (123,393), root:(604,442),
    state 0x2000, keycode 166 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 28, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x0, time 78235758, (123,393), root:(604,442),
    state 0x2000, keycode 166 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by cyberdork33 on 2008-05-16
> **gforster said:**
> I don't necessarily want to make this work like a pc keyboard, I'd like to make it work like a mac's first. Right now, the only things I can't get working that way are dashboard and expose buttons. Once that is settled, then I might possibly want to start playing with custom configs for it. 
Those buttons are "special function" buttons. They would be equivalent to the special functions on any keyboard and thus, are likely not configured to do anything in linux. In other words, you will have to make a "custom config" to make it work. Keytouch should allow you to utilize such "special" keys on any keyboard PC or Apple. I am not suggesting you change your keyboard to work like a PC... I am trying to show you a tool that may allow you to use the button that you want to use for whatever function you want.

If the "dashboard" button gives no output, then modifications are probably needed to the kernel to get it working. (i.e. modify source code).

---

### Post by gforster on 2008-05-16
I am so sorry, I guess I forgot to copy in my reply about keyTouch (Typing out my responses first and copy/paste helps when I'm on a flaky/weak wireless connection). Anyway. . .

As to keyTouch, there are no preconfigured apple keyboards. I have been searching around forums as others have wanted to use it with their apple keyboards. It looks like there is an editor to be used with it, but I'm not quite sure how just yet. I am trying to find a guide, but haven't found one yet (I have to actually get some work done sometime:)) 


Thanks again for your help. This is one major reason I left the windows world - the community of help and the fact that even a novice like myself can, at times, be helpful to others as well.

---

### Post by cyberdork33 on 2008-05-16
> **gforster said:**
> I am so sorry, I guess I forgot to copy in my reply about keyTouch (Typing out my responses first and copy/paste helps when I'm on a flaky/weak wireless connection). Anyway. . .

As to keyTouch, there are no preconfigured apple keyboards. I have been searching around forums as others have wanted to use it with their apple keyboards. It looks like there is an editor to be used with it, but I'm not quite sure how just yet. I am trying to find a guide, but haven't found one yet (I have to actually get some work done sometime:)) 


Thanks again for your help. This is one major reason I left the windows world - the community of help and the fact that even a novice like myself can, at times, be helpful to others as well.Yes, unfortunately, as can be seen by the various number of bugs, these keyboards are not quite up-to-par in the linux world yet. I am not all that familiar with the details on how keyboards work in Linux, so i can't help too much more, but you may be able to do something with xmodmap, though it is not quite as friendly as keytouch.

---

