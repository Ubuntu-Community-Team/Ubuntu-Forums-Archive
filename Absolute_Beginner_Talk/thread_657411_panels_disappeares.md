---
title: "panels disappeares"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by bird_gal on 2008-01-03
Hi there,
I am new here, so please be patient;)

I am using Ubuntu and that's about all i know about my computer...

It froze the other day, and I had to shut it down using the on/off button. Ever since then, the top and bottom panels disappear as soon as I click on the "log off/switch off-etc menu" icon. Even if I don't do anything then (i.e. don't log off or switch the computer off) the panels will disappear and i have to turn them back on using usr/share/applications. The panels will reappear with all previous setting saved. ******* computer;)

I saw that other people seem to have the same problem, but I am not quite comfortable to follow the "crazy" instructions given in other threats as I'm a complete computer idiot and I don't know what will actually happen if i do.

Can someone lead me through step by step? 

Thanks for your help!
cheers
Nora

---

### Post by bird_gal on 2008-01-03
apparently this is the panel I'm using:
GNOME Panel 2.20.1

Nora

---

### Post by spiderbatdad on 2008-01-03
From what you're saying, it sounds like your panels randomly vanish and do not reappear by mousing over them. You have to restart to get your panels back?

---

### Post by bird_gal on 2008-01-03
The panels disappear (along with the log off icon, by the way. I can't log off/switch off after the panels disappeared, I need to turn it off with the on/off button), and they are not there when I turn the computer back on.
HALP;)

---

### Post by spiderbatdad on 2008-01-03
i think you need to try this: open your terminal by going to Applications>>Accessories>>Terminal. And enter the following command exactly.```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bird_gal on 2008-01-03
I did that. When I wanted to restart and clicked the switch off  icon, the panels disapperaed again. I switched off manuall. Now I can't log on to Ubunutu anymore!!!! it says my password or login name are wrong!! Have to use my windows partition!!! What the...!?

---

### Post by spiderbatdad on 2008-01-03
if your password or username is wrong, that is a totally separate issue. You are entering the wrong information. I'm not sure what is going on with your panel. Are you using advanced desktop effects? If so, did you install a windows manager? Possibly there is a conflict between something like ccsm and metacity causing your desktop to go bonkers.  You could also try something simple like right clicking on the icon and de-select the lock, then right click again and remove it. Then click on the panel and choose add to panel, and add the icon again.

---

### Post by bird_gal on 2008-01-03
I've never had problems loggin on before, it started after I entered the command in the terminal and restarted the computer!!! 
My log-in info hasn't been changed since my last log-in so what I'm entering can't be wrong. I's gotta have something to do with what I just did (which was just what you suggested). I can't log on at all so my least problem are the panels right  now. 
Do you have any idea why I can't log-in?!:confused:
I'm freaking out! I need my computer!

---

### Post by spiderbatdad on 2008-01-03
[http://ubuntuforums.org/showthread.php?t=649022&highlight=forgot+password](http://ubuntuforums.org/showthread.php?t=649022&highlight=forgot+password)

that command had nothing to do with your login issue. You are mistaken.

---

### Post by bird_gal on 2008-01-03
well, still can't log in.

---

### Post by spiderbatdad on 2008-01-03
boot into recovery mode and enter ```
passwd yourusername
``` where "yourusername" is your username. notice password is "passwd"

---

### Post by bird_gal on 2008-01-03
OK, i did that. 
It said that the password was changed, but then I didn't know what to do after that since it just gave me that standard terminal command (whatever it is it always says at the beggining of a line). So i had to turn the computer off with the on/off button again. 
When i tried to log in it still said (as before): "Incorrect username or password. Letters must be typed in the correct case." 
Do i need to do something else in that recovery mode start up screen?
thanks heaps

PS: in the recovery mode it checked all sorts of things and put [OK] behind the line. However, "setting sensors limits" said [fail]. That means anything?

---

### Post by spiderbatdad on 2008-01-03
you should now be able to start your computer and enter the username you used when changing the password and the NEW password. If you still get an error, then as hard as it is to believe, you are doing something wrong.

---

### Post by bird_gal on 2008-01-03
yay, logged on again.

I think I know what the log on problem may have been: my keyboard has gone bonkers! 

it's a german laptop with a german key layout. it has somehow changed to the american version!! since my password had a y in it, the computer typed z instead (reverse on american vs. german keyboards). 

What the hell is my computer doing? any idea how to change it back to german layout?

Haven\t even tried the panels again... too scared what might happen there!!;)

thanks for your help so far...:)

---

### Post by spiderbatdad on 2008-01-03
ha. that happened when you ran the previous command.:lolflag: If you run it again without the -phigh option it will guide you through the setup...including keyboard. I  have not had good luck with the guided setup, and there may be an easier way to reset the keyboard. You might try an new post with that title..."Change keyboard language?"  Sorry about that. It did not occur to me you might be using a keyboard in another language that is detected as an american keyboard thingy thingy.

---

### Post by bird_gal on 2008-01-03
grrrr...;)

thanks! will try and change language, it\s abitch like this! (as you can tell by all the weird letters i\m using...) might be an easier way, will see if there\s anything in the forum about it.
and THEN i'll figure out what's wrong with my panels!

cheers
nora

---

### Post by seventhc on 2008-01-03
couldn't you just set it from System>Preferences>Keyboard

---

### Post by spiderbatdad on 2008-01-03
+1  in the layout tab, selecting "add" offers language configurations.

---

### Post by bird_gal on 2008-01-03
that's how i had to get the german setting in the first place. it is there now and i made it default, it just doesn't apply...
started second threat about this, here it is;
[http://ubuntuforums.org/showthread.php?p=4068523#post4068523](http://ubuntuforums.org/showthread.php?p=4068523#post4068523)

cheers guys:)

PS' i need to go shoe shopping to calm my nerves but will be back here later and thankful for any advice:):)

---

### Post by bird_gal on 2008-01-03
OMG i soooo did it!!! I "fixed" the panel problem!!
I recently downloaded LimeWire and made a panel shortcut for it. When i deleted that just now, my panels are behaving all of a sudden!
:guitar:
thanks for all your help guys!! ...remember, I'm still fiddeling around with my keyboard settings...;)

---

