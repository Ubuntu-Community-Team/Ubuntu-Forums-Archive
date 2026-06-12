---
title: "How do I add a shell-script to the menu?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Gen2ly on 2007-03-23
Sorry, I'm still pretty new to this and just became tired of looking.  Anyone, know how to add a shell-script to the gnome-menu?  I have this script called epublisher.sh.  I try to add it normally (right-click then select add to menu) but it doesn't work.  I tried

```
exec=/home/user/application
```

and it didn't work?

Could someone please help?

---

### Post by ardchoille42 on 2007-03-23
> **Dirk.R.Gently said:**
> Sorry, I'm still pretty new to this and just became tired of looking.  Anyone, know how to add a shell-script to the gnome-menu?  I have this script called epublisher.sh.  I try to add it normally (right-click then select add to menu) but it doesn't work.  I tried

```
exec=/home/user/application
```

and it didn't work?

Could someone please help?

You can add a shell script to the gnome menus with:
1. Open Applications -> Accessories -> Alacarte menu editor
2. In Alacarte, click the menu section that you want to add the script to in the left pane, 
3. Click File -> New Entry
4. Choose whatever you want for "Name"
5. In the "Command" box, put in
```

sh /full/path/to/script

```
6. give the entry an icon with the button in the Icon section
7. Click "Ok"
8. You're done :)

If the menu item doesn't show up in the menus immediately, do
```

killall gnome-panel

```
That will kill the panel, don't worry, the panel respawns immediately.

---

### Post by Gen2ly on 2007-03-24
Appreciate the reply ardchoille.  Unfortunately that didn't work for me, but you sent me to the right thought.  I ended up writing the command lines I needed to type in the terminal into a file and then making an executable of that file. 

Create a New File
```
sudo nano /usr/bin/ccPublisher
```

add
```
cd /home/todd/Applications/ccPublisher/
./ccPublisher.sh
```

save and close. then, to make it executable, do a
```
sudo chmod 755 /usr/bin/ccPublisher
```

now just type ccPublisher in alacarte when you add an item.

---

### Post by NJC on 2007-04-14
> **ardchoille42 said:**
> You can add a shell script to the gnome menus with:
1. Open Applications -> Accessories -> Alacarte menu editor
2. In Alacarte, click the menu section that you want to add the script to in the left pane, 
3. Click File -> New Entry
4. Choose whatever you want for "Name"
5. In the "Command" box, put in
```

sh /full/path/to/script

```
6. give the entry an icon with the button in the Icon section
7. Click "Ok"
8. You're done :)


Thanks ardchoille42!

---

