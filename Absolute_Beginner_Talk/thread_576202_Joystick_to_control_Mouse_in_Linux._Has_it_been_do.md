---
title: "Joystick to control Mouse in Linux. Has it been done and documented wine JoyToKey.exe"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by tenkamuteki82 on 2007-10-14
Hello everyone,

Im creating this post in hopes to escalate the question about controlling the mouse COMPLETELY with a Joystick. In windows I use a freeware tool called JoyToKey.exe. It creates profiles for my control pad and I memorized my controller config specs and no longer use my mouse. Now I want to switch to Ubuntu or any deviation of linux for that matter but still be able to control the mouse the mouse with other devices (like a controlpad -- or other handicapped users).

Has anyone had any success fully using a control pad to move the mouse and left click and right click to control windows and such? If I can nail this.. then I can finally use linux full time... otherwise it will stay a VM for me so that I can use my control pad in windows... >_>

Any ideas?

---

### Post by tenkamuteki82 on 2007-10-14
So I did some googling and research. I found about wine. (It is amazing!!!)

I ran "wine" with "JoyToKey.exe" and it was able to load my profiles and even move the mouse! HOWEVER... it wont allow me to left click or right click anywhere in the desktop... Does anyone know if wine allows applications to bring the mouse to the main window managers? Anyone else know what i mean?

---

### Post by tenkamuteki82 on 2007-10-17
Wow this thread got 50 views in 3 days. Looks like I am not the only one researching this eh :)

Any others have any luck with setting up their control pad to work as a mouse? Ive been playing so much with /etc/X11/xorg.conf, as well as wine JoyToKey.exe (which can MOVE the mouse but not register any clicks with the window manager - gnome)....

Is there anyone out there who can help me? I would like to keep this thread going until we have a solution :):popcorn:

For your reference: My favorite windows app that is stopping me from switching to Ubuntu full time is JoyToKey (freeware), available at: [http://www.electracode.com/4/joy2key/JoyToKey%20English%20Version.htm](http://www.electracode.com/4/joy2key/JoyToKey%20English%20Version.htm)

Ive been attempting to work it with wine, which it seems to be ok but not registering clicks with wine. Maybe there are some wine gurus out there that can comment :)

Cheers~

Japanese: &#12371;&#12371;&#12429;&#12363;&#12425;&#12418;&#12358;&#12375;&#12354;&#12370;&#12414;&#12377;&#12290;&#12415;&#12394;&#12373;&#12435;&#12395;&#24863;&#35613;&#12375;&#12414;&#12377;

---

### Post by tenkamuteki82 on 2007-10-24
I added JoyToKey.exe as a requested application to the wine database list. I also pointed them to link to this forum entry in case any updates or suggestions or made. Hopefully we can make some progress and keep this application alive and working. 

Thanks to everyone from the Ubuntu and Wine teams for their great work and hopefully we can get this application to work.

---

### Post by jryprt on 2007-10-24
I have the same thing. I am a Quadriplegic with arm movement but no finger movement I use Joysticktomouse  [http://www.imgpresents.com/joy2mse/j2m.htm](http://www.imgpresents.com/joy2mse/j2m.htm) 
At the bottom of the page is a free trial [http://www.rjcooper.com/sam-joystick/index.html](http://www.rjcooper.com/sam-joystick/index.html)
for windows

I have tryed wine & it lets me move the mouse pointer but not click .


This is what keep me from going fulltime with ubuntu 
Need to get working joystick to mouse for disable 
Thanks

---

### Post by srt4play on 2007-10-24
Guys, there is no need for wine for this. I use js2mouse and it works great.

[http://cedric.vincent.perso.free.fr/Projets/index.html](http://cedric.vincent.perso.free.fr/Projets/index.html)

Here is a thread on the forums about it:

[http://ubuntuforums.org/showthread.php?t=92564&highlight=js2mouse](http://ubuntuforums.org/showthread.php?t=92564&highlight=js2mouse)

---

### Post by tenkamuteki82 on 2007-10-24
Ive tested js2mouse and it is very good as well. However unfortunately it has a few weaknesses that are not documented and user friendly:
1. Cryptic/No actual documentation - Sorry I know this may not be true but I have not located a user freindly page on how to set this spplication up. 
2. Not fully configurable like JoyToKey (I.E. how do I map a key on the joystick to more than one key?)
3. Does not support mouse speedup and slowdown (Many users find that by switching to a analog based pad, there are sometimes where you want to speedup and slowdown the mouse movement accross the screen - or if you have a large resolution, unfortunately js2mouse does not support this.

Another application which really has good potential was qjoypad, which is really excellent. The only thing it is lacking was #2 and #3 above. Those features are very important to users adapting to using an analog stick. But, nonetheless I liked this application a lot.


JoyToKey does all these operations from Windows, and would be awesome if for reasons I mentioned at the beginning of the thread is adapted to working on Linux. Hopefully it is a simple wine tweak to get it to work but I will keep you posted as things progress. If anyone wants to try it, download the freeware JoyToKey from the earlier post, and install wine (sudo apt-get install wine), and then run "wine JoyToKey.exe". 

Let me know your thoughts!:)

---

### Post by tenkamuteki82 on 2008-03-01
I still have not figured out how to emulate ALT+F4 or CTRL+C with any of the above mentioned software... Has anyone else tried these?

---

### Post by tenkamuteki82 on 2008-04-13
So after playing around and looking at some of the source code for other utilities it sounds like the reason that using wine + joy2key,exe does not work for CLICKING or sending any keyboard entry is because the application 'wine' does not allow 32 bit executables to hook onto any of the LINUX X Applications (like our window manager which I soo desperately want to send keyboard events too...

I am baffled on how to configure this in wine, or write a wrapper to allow the program to send events to the window manager (like alt + f4, or minimize or maximize etc...). If someone can help figure this out, I would be very greatful (as I use my PS3 controller as a wireless mouse at home and really want to fully migrate to ubuntu but have not figured out how to use the gamepad as a joystick ps3 or ps2 or any joypad for that matter).

Thank you for your help and keep the conversations continuing...!:popcorn:

---

### Post by Skipinder on 2008-04-26
> **tenkamuteki82 said:**
> I still have not figured out how to emulate ALT+F4 or CTRL+C with any of the above mentioned software... Has anyone else tried these?

I haven't tried js2mouse yet, but if all it is doing is making the joystick appear as a mouse then you should be able to bind the mouse buttons to keyboard presses with xbindkeys or with btnx. Check out [this]("http://wiki.archlinux.org/index.php/Get_All_Mouse_Buttons_Working") for more info.

---

