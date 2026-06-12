---
title: "fluxbox startup help"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by thoffland on 2006-02-07
I'm having difficulty getting apps to start when fluxbox starts. I've edited the init file and also the startup file, but neither will load the apps. 

Here's the end of my init file: 
```
ebar.right: Minimize Maximize Close

session.screen0.antialias: true

exec fbpager &
```

and here's the end of my startup file: 
```
sudo /etc/init.d/firestarter start &
exec xscreensaver &
/home/thoffland/.fluxbox/gkrellm &
/usr/bin/fbpager
# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
```

You can see I've tried various strings to get the programs to launch, but nothing seems to work. 

Any ideas?

---

### Post by frodon on 2006-02-08
This may help you : [https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

---

### Post by thoffland on 2006-02-09
[QUOTE=frodon]This may help you : [https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)[/QUOTE]

Thanks! I tried editing the startup file the way it mentioned, and rebooted but it still didn't happen. I dont know if it makes a difference but when the computer boots, I have to login then type 'startx' and then fluxbox comes up. 

I'm not sure if that would make a difference or not. 

That is a very handy page though... it's been bookmarked! 

Thanks again.

---

