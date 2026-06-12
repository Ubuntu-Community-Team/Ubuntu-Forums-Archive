---
title: "Ubuntu hangs on startup"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by logicus on 2007-03-18
hi there

My name is Peter and I'm a complete ubuntu N00b.
So please be gentle.

Anyway, the other day I decided I wanted to try out Ubuntu and everything went like a breeze.
I also installed a very cool windows mananger: Beryl. I even managed to make it startup automatically.
Nice.
However, since I'm a curious as a teenager on his first date, I cant stop tingering and I tried to change Beryl to show relflections. BOOM
Everything froze and now when i try to boot in Ubuntu everything hangs. I need to find out how to remove beryl from the startup manager without using the GUI and then I need to find out how to make Beryl use it's default setup again.

I hope you guys can help me.

Sincerely

Peter

---

### Post by AtrejuT on 2007-03-18
at what point does it stop?
can you press Ctrl+Alt+F1?
You should get to a console. 
Log in there, then you should be able to either remove beryl by
```

rm ~/.config/autostart/beryl-manager.desktop

```
or you can remove the beryl settings (it should use the default settings then) by
```

rm -R ~/.beryl

```
helps?

atreju

---

### Post by meborc on 2007-03-18
if you can't hit ctrl+alt+F1 you can always boot to the recovery mode and use the guide by AtrejuT :)

---

### Post by logicus on 2007-03-18
Thanks , guys

It really helped.

I foresee that I will return to this forum numerous times.

:) 

Thanks again.

Sincerely

Peter

---

