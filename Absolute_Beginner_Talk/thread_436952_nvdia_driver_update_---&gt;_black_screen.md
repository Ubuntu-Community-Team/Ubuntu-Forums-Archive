---
title: "nvdia driver update ---&gt; black screen"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-08
Hey guys

i did a search and found 3 or 4 different solutions, but im not sure which is the right one for me

i went to run compiz, and it told me i had to update my nvidia drivers.

I looked at my laptop, and i noticed that it had 'nvidia graphics' stuck to the front, so i went ahead

rebooted, head the ubuntu login drums, got a mostly black screen (a bit lighter at the bottom right)

I see there are several solutions, which is right for me to rollback the drivers, as it were?

Regards

drowner.

---

### Post by drowner on 2007-05-08
Im sorry to be pushy, but you guys have helped me with many issues before, and i know you can help me with this one
Oh, and this XP boot im on now is crawling, I WANT MY UBUNTU BACK. and i promise not to break it this time

---

### Post by mikewhatever on 2007-05-08
Do you want help, or just to share frustration? If you do, please provide more information. For example, how did you update the nvidia driver? Was there a guide you followed? When do you get the black screen during boot up?
Have you tried booting into recovery mode?

---

### Post by drowner on 2007-05-08
Ahh sorry for being shirty ;)

I went to enable compiz (im using feisty)

and it informed me i needed new drivers, so i allowed it to get them

And then it did

I rebooted, and i got the Ubuntu splash ok

then, i heard the login drums, and it was black.

---

### Post by drowner on 2007-05-08
Oh, and i have now found out (i should have found this out beforehand, i realise) that my nvidia card is a GeForce  4 420GO, which is considered legacy now.  That would explain it.

---

### Post by drowner on 2007-05-08
OK, a good search and i found this:
[http://ubuntuforums.org/showthread.php?t=417188](http://ubuntuforums.org/showthread.php?t=417188)


COuld someone with a bit more experience and confidence recommend this as the right thing to do?

---

### Post by mikewhatever on 2007-05-08
If seems to have worked for some, so why not. Another option would be to restore the previous xorg.conf set up from backup, if there is one. You can try checking 
> ls /etc/X11

---

### Post by drowner on 2007-05-08
> **mikewhatever said:**
> If seems to have worked for some, so why not. Another option would be to restore the previous xorg.conf set up from backup, if there is one. You can try checking

there was no backup in there.

and i tried my hardest to use vi, which i assume is the right text editor to use..... lol it was a struggle ;)

ill give it a decent bash tomorrow. Im determined to get this thing running again.

---

### Post by drowner on 2007-05-08
RESOLVED! SUCCESS!

Thanks to this thread: [http://ubuntuforums.org/showthread.php?t=417188](http://ubuntuforums.org/showthread.php?t=417188)

I suspect this will work if you have a nVidia GeForce 4420 Go Card and are using Feisty.

Let me explain in a very basic way what I did:

1. When I heard the drums, and got a black screen, I logged in

2. Press Ctrl+Alt+F1 to get a terminal, and logged in again

3. ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
This backs up the file we are about to edit

4. ```
sudo nano /etc/X11/xorg.conf
```
Nano is a text editor you can use in the terminal. I tried with vi, but it was too difficult.

5. Look for the line 'defaultdepth' (no quotes) in the sections 'Screen'
You can use the commands down the bottom of your screen to search for the line.

6. Under the line default depth, I added the following line
```
Option "UseDisplayDevice" "DFP"
```
I had to add a few tabs to make it 'line up' with the text above.

7. Exit nano, and save the changes. The instructions for this are at the bottom of the screen

8. Typed
```
sudo shutdown -r now
```
which reboots the computer.

This worked perfectly well, for me!

Thankyou to hesicong2006 for the fix!

He suggests if this doesnt work, try again replacing "DFP" with "DFP-0" or maybe "UFP"

Regards,
drowner

---

