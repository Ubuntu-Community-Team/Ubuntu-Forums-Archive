---
title: "Problem with drivers"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by ljcasey on 2007-04-25
Hi everyone. 

I am running Ubuntu Fiesty Fawn with a ATI X800 g'card.

- "out of the box" everything is fine, Beryl works, wonderful...if I run glxgears I get around 4k FPS. So I installed World of Warcraft, and it didnt really run properly, graphics were screwed up. 

- So I go to Administration > Restricted Drivers utility and install the ATI accelerator drivers, I run glxgears and get around 10k fps, a great improvement! I run World of warcraft...GREAT it works! however it locks up as soon as I login with a character, or sometimes at the startup screen, but the graphics is fine. But now Beryl will not work.. Missing XComposite? 

Can anyone shed some light what is going on? 

1. Why will Beryl not work with the accelerator graphics driver which appears to make things run much better?
2. Why does World of Warcraft lock up?

Thanks, 
Sorry if there is alot to take in there.

Lee

---

### Post by leibowitz on 2007-04-25
Because compiz (it's not beryl, but anyway it would be the same if you were using beryl) use something like GLX_PIXMAP... (I don't remember exactly) extension and ATI did not implement this extension in their proprietary driver.

So you have two choice: using the free open source driver developed by the community (and you can run compiz) or use the ATI proprietary driver and no desktop effects. It's writed somewhere on the ATI website, they don't support this (yet).

And I don't know about World Of warcraft. It may be wine, it may be so much things

---

### Post by ljcasey on 2007-04-25
Thanks for your input. I guess I will wait for better drivers, or just buy an nvidia, I am forever getting tired of ATI! :mad:

---

