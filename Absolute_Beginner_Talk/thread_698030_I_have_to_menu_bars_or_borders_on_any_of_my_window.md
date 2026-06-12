---
title: "I have to menu bars or borders on any of my windows!!!"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by thesqudge on 2008-02-15
I first tried to install beryl, then it said i had to have kde installed, so i installed it from synaptic. but then i read how much it slowed down peoples machines so i decided not to install it, then i though i would uninstall kde because there was so much clutter in my menus, so i went back to synaptic and uninstalled kde, but the menu items were still there so i did a search for kde and uninstalled everything that was installed in the kde search...... probably should have restarted right after uninstalling the first kde package to see if that made all of the items go away but i didn't think of that at the time and i was working fine until i restarted my computer and now all of the menu bars and borders are gone from all of the windows! please help [-o<

---

### Post by MasterJS on 2008-02-15
If you are using gnome you might have unistalled metacity, which is the Window Manager for GNOME. ```
sudo apt-get install metacity metacity-common
```

---

### Post by thesqudge on 2008-02-15
Ok so I tried that code, it said it was already installed then I restarted x and no difference

---

### Post by MasterJS on 2008-02-15
mmm try ```
metacity --replace
``` that should try to restart metacity

---

### Post by thesqudge on 2008-02-15
OMG NO WAY! hahaha i opened terminal and i was like, pfft this is probably still not gunna help. then BAM! everything came back in like 1/18 of a second! haha ohhhhhh thanks so much!=D>

---

### Post by MasterJS on 2008-02-15
Your welcome! And its courtesy towards others if you mark your thread as solved

---

### Post by thesqudge on 2008-02-15
ahhh wait hold on! I restarted and now they're gone again?!.....

---

### Post by MasterJS on 2008-02-15
mmm try ```
metacity start
```

---

### Post by thesqudge on 2008-02-15
it said there was already a window manager in place and suggested using --replace..... but we've already tried that

---

### Post by MasterJS on 2008-02-15
that means you still have beryl installed. try ```
sudo apt-get remove beryl emerald emerald-themes
```

---

### Post by thesqudge on 2008-02-15
ok so i did that, i forgot to say when i was making this thread i read one of the similar threads and someone said that they installed emerald using terminal and it made it better](*,) but after i used that and emerald was uninstalled i restarted again and no difference

---

### Post by MasterJS on 2008-02-15
Alright how about you try the code "sudo apt-get remove beryl*" (without the quotations) The asterisk means it will try to remove everything related to beryl. Now you should have beryl and emerald completely removed. Now try ```
metacity --replace
```

---

### Post by thesqudge on 2008-02-15
ok so i did that and it said it couldn't find anything, and then i did the --replace thing and restarted and still nothing:(

---

### Post by MasterJS on 2008-02-15
alright, lets try remove metacity and installing it again. So remove it by ```
sudo apt-get remove --purge metacity metacity-common
``` this will remove metacity and its configuration files. Then do ```
sudo apt-get install metacity metacity-common
```

---

### Post by thesqudge on 2008-02-15
sorry i took so long... so uh i tried those and still nothing, i also tried to instal kde again and that took along time then gnome stopped working so i had to reinstall that through the terminal..... and stilll, nothing

---

