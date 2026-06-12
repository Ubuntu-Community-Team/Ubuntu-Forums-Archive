---
title: "Keyboard+Mouse Problem"
date: 2007-04-21
forum: Apple Intel Users
---

### Post by niklas-komani on 2007-04-21
Hello Community,
this problem has already been mentioned and i also mentioned it in my KVM topic, however I think it is severe enough that it deserves it's own thread.

**If I hold some key pressed I can't move the mouse **

This problem persists on normal Desktop and also in Nexuiz where I can't run and look around (i.e. aim) at the same time.

As a second note: after I release the key the mouse is visible at it's old spot but when moving it it jumps to the spot it should be if it hadn't stopped moving and the problem also exits when a  key is just pressed and the mouse is moved just about half a second later

---

### Post by ronocdh on 2007-04-21
> **niklas-komani said:**
> Hello Community,
this problem has already been mentioned and i also mentioned it in my KVM topic, however I think it is severe enough that it deserves it's own thread.

**If I hold some key pressed I can't move the mouse **

This problem persists on normal Desktop and also in Nexuiz where I can't run and look around (i.e. aim) at the same time.

As a second note: after I release the key the mouse is visible at it's old spot but when moving it it jumps to the spot it should be if it hadn't stopped moving and the problem also exits when a  key is just pressed and the mouse is moved just about half a second later
I am experiencing this same phenomenon. It hasn't bothered me at all, but I tested and yes, I have the problem. I'm running 7.04 64-bit on a C2D MacBook Pro 15".

I **am** able to type while retaining cursor functionality via the trackpad--but who wants that? ;) Also, function keys (ctrl, alt, etc.) do not inhibit cursor movement.

---

### Post by niklas-komani on 2007-04-21
Yeah right it doesn't bother me either when working, but it is going to be a problem for people who want to play games and maybe Office users
I'm using a Apple Keyboard with German Layout and a Logitech MX500 mouse

tab doesn't work
The following keys work other don't:
ctrl
alt
apple key
caps lock (LED isn't turned on but this is minor)
num lock 
sound and unmount keys

---

### Post by niklas-komani on 2007-04-21
Nobody else experiencng this?

---

### Post by ronocdh on 2007-04-21
> **niklas-komani said:**
> Yeah right it doesn't bother me either when working, but it is going to be a problem for people who want to play games and maybe Office users
I'm using a Apple Keyboard with German Layout and a Logitech MX500 mouse

tab doesn't work
The following keys work other don't:
ctrl
alt
apple key
caps lock (LED isn't turned on but this is minor)
num lock 
sound and unmount keys
This morning I somehow activated num lock and couldn't switch it off! The light behind it did work, which was peculiar, seeing as the caps lock light doesn't. Well, I couldn't even kill X because the delete key wasn't responding, so I had to log out with the mouse and then restart with the mouse, too. Humbling. :oops: =D

Please guys, test what's in this thread and see how your system handles it. Then post back with results and hardware. And while you're at it, check your firewire ports for Seamyst! ;)

---

### Post by niklas-komani on 2007-04-22
Ok I found the cause of the problem, if I do "sudo killall mouseemu" the problem with typing is gone, however you should be carefull doing this on a Macbook where you dont have a real ouse since this tool is needed for simulating a mouse I guess from the name^^ I will try to find which setting I need to change so it works the right way

---

### Post by niklas-komani on 2007-04-22
Though not tested i guess one can change /etc/default/mouseemu so that the typing is not held back for so long

---

### Post by Tyrdium on 2007-04-22
> **niklas-komani said:**
> Though not tested i guess one can change /etc/default/mouseemu so that the typing is not held back for so longJust tested it. No more delay!

sudo nano /etc/default/mouseemu
Uncomment "TYPING_BLOCK...", change 300 to 0, save
sudo /etc/init.d/mouseemu restart

---

### Post by ronocdh on 2007-04-22
> **Tyrdium said:**
> Just tested it. No more delay!

sudo nano /etc/default/mouseemu
Uncomment "TYPING_BLOCK...", change 300 to 0, save
sudo /etc/init.d/mouseemu restart
Perfect! Fixed, thank you!

---

### Post by gmc on 2007-04-23
Hey, there's an added bonus to your fix... my erratic touchpad now seems to work. I was having trouble with moving the pointer up and down (vertical pointer movement).

Thanks
Gord

---

### Post by bsantos on 2007-04-24
My issues were related to mouseemu also, I wonder when I installed it (I did a fresh Fesity install, but used a package list dump from my previous beta installation)... I don't understand why all of a sudden it went crazy and started giving problems. What it provides I already had with synaptics... I purged it and all seems well now.

Weird. :P

---

### Post by niklas-komani on 2007-04-24
Feisty seems to turn it on automatically on all Mac Systems since the Mac Laptops only have one Mouse button and mouseemu helps to simulate the other one.

---

### Post by bsantos on 2007-04-24
I see. I don't understand why it became a problem without any reason I could find. It blocked caps lock and num lock, weird...

---

### Post by gmc on 2007-04-25
Speaking of keyboard lights? 

Has everyone else lost their keyboard lights? Under 7.04, I can't tell if the capslock is engaged or not (until I type). Numlock is the same, no light. They worked under 6.10?

Gord

P.S. Thanks for reminding me about this problem, I'm making a list of problems I've noticed with Feisty.

---

### Post by bsantos on 2007-04-25
aptitude purge mouseemu?

---

### Post by Ilove2023 on 2007-05-15
> **ronocdh said:**
> This morning I somehow activated num lock and couldn't switch it off! The light behind it did work, which was peculiar, seeing as the caps lock light doesn't. Well, I couldn't even kill X because the delete key wasn't responding, so I had to log out with the mouse and then restart with the mouse, too. Humbling. :oops: =D


Hello, I've exaclty the same problem here.... sometime the F6 key get on and no way to switch it off... the keyboard is unusable... I had to reboot to :( (so frustrating!)

Did someone find a clue about that ?


BTW, the keyboard lights are always off.... except that F6 key ...

---

### Post by ronocdh on 2007-05-15
> **Ilove2023 said:**
> Hello, I've exaclty the same problem here.... sometime the F6 key get on and no way to switch it off... the keyboard is unusable... I had to reboot to :( (so frustrating!)

Did someone find a clue about that ?


BTW, the keyboard lights are always off.... except that F6 key ...
Maybe [Dirk's how-to]("http://ubuntuforums.org/showthread.php?t=442941") will be of use to you.

Post back with results, please.

---

### Post by Ilove2023 on 2007-05-15
I'll try as soon as possible.... (exam first ;))

---

