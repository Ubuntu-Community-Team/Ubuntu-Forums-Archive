---
title: "a little advice/help please"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by newb_not_noob on 2006-07-30
ok, the 6.06 installation disk wasent working very well, so i got the alternate. thats installed fine. i just restarted the system and it seems to be taking an abnormally long time "loading hardware drivers"

i wonderd if their was a fault or anything. its bin "loading" for about 5 mins so far...

---

### Post by nalmeth on 2006-07-30
What hardware are you running (specs)?

Let us know what happens

---

### Post by newb_not_noob on 2006-07-30
er, 128 ram. 5ish GB hard drive i think, dell latitude CPi laptop. pentium 2 3400

---

### Post by newb_not_noob on 2006-07-30
bin "loading"  for around 15 mins now. think i might turm it off for the night and let it cool. its bin on all day and it is a laptop

---

### Post by newb_not_noob on 2006-07-31
ok, its STILL not working..

---

### Post by newb_not_noob on 2006-07-31
tried booting from cd, changing screen resoloution then booting from hard drive through the cd. stil taking an age, and the processing light has stopped blinking

---

### Post by newb_not_noob on 2006-07-31
YYYYYYYYEEEEEEEES!!!!!! shes...ALIVE. but am i going to have to boot from cd so i can change the screen resolotion every time?

---

### Post by adamkane on 2006-07-31
Edit xorg.conf.

```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by newb_not_noob on 2006-07-31
erm.. im afraid that means very little to me. where to i type that?

---

### Post by adamkane on 2006-07-31
Applications -> Accessories -> Terminal

---

### Post by RRS on 2006-07-31
Applications>Accesories>Terminal

That opens a terminal window to use the command line.

After preceding a command woth "sudo" you'll be asked for a password, use the one you created for user during installation.

If unsure of what settings to enter in the file, run the same command in the live cd and copy the ones from it's file.

Also, when you enter your password in the terminal it won't be visible, just type it in and "enter", don't believe it's needed in the live cd though.

---

### Post by newb_not_noob on 2006-07-31
and that will allow me to change the resoloution on boot up?thanks v much

---

### Post by HanZo on 2006-07-31
open a terminal
first make a copy of your xorg in case something goes wrong
```
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
```
then edit it
```
sudo gedit /etc/X11/xorg.conf
```(xorg.conf is the config file for X, contains info on keyboard, mouse, graphic card and other stuff X needs to know)
sudo enables you to have root access to files so it this will ask you for your password.
in xorg you will have to look for the resulution section... but I think that's pretty selfexplanatory.
in case you screw it up start ubuntu in console mode (in grub select the recovery mode... or what it is called like) then simply type:
```
cd /etc/X11
sudo cp xorg.conf_backup xorg.conf
```
this restores your original xorg.conf

---

### Post by newb_not_noob on 2006-07-31
cheers... im trying to set the screen resoloution on startup to 640x480x24, and i diddent use the live cd, i used the alternate because the live cd diddent work. could someone perhaps give me slightly more detailed instuctions? thanks

---

### Post by newb_not_noob on 2006-07-31
its booting up ok now...occasionally.its being very tempramental. sometimes it will boot and others it will just sit their "loading hardware drivers" im buying more RAM for the laptop so that might help it boot up faster i hope. any ideas why is is being like this?

---

### Post by avtolle on 2006-07-31
I suspect it's because it needs more RAM to run more efficiently. You need, according to the documentation, at least 192 mb to run GNOME (IIRC); obviously, the more, the merrier. After upgrading memory, it should run better; if it doesn't let us know.

---

### Post by newb_not_noob on 2006-07-31
thanks. iv only got 128 atm, so 256 should make it faster and more reliable

---

### Post by HanZo on 2006-08-01
I have it running on an old p3 with 128 of ram... and it runs well... painstakingly slow at times... but without any problems

---

### Post by newb_not_noob on 2006-08-01
quick update-i found out that ubuntu only seems to get past "loading hardware drivers" 1/3 times (yes, i did sit their for a while booting it up and shutting down again) i expect my ram upgrde should make booting up more reliable and faster?

---

