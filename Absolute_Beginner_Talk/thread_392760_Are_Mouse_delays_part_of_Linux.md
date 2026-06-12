---
title: "Are Mouse delays part of Linux?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by idontknow9999 on 2007-03-24
The big problem I have been having with Linux is the fact the mouse is slow on the click...

Ex: Selection icons.  Take your mouse from top left to bottom right, while half way down click and hold left click. You will notice there is a 0.1-0.3 second delay that is not in windows. This delay is not only annoying when using nlinux in general, but its a massive problem when playing starcraft (which is one of the big reasons why I stay in Windows).

Note: I am sure some of you might not even notice this who has been using Linux for a while. But for someone like me who has +100 APM in Starcraft who just came from Windows is a massive issue.

So basically what I am saying: 60-70% of my problems in Linux is this delay in the mouse. Is this fixable or is Linux just slower then Windows?

---

### Post by godd4242 on 2007-03-24
> **idontknow9999 said:**
> The big problem I have been having with Linux is the fact the mouse is slow on the click...

Ex: Selection icons.  Take your mouse from top left to bottom right, while half way down click and hold left click. You will notice there is a 0.1-0.3 second delay that is not in windows. This delay is not only annoying when using nlinux in general, but its a massive problem when playing starcraft (which is one of the big reasons why I stay in Windows).

Note: I am sure some of you might not even notice this who has been using Linux for a while. But for someone like me who has +100 APM in Starcraft who just came from Windows is a massive issue.

So basically what I am saying: 60-70% of my problems in Linux is this delay in the mouse. Is this fixable or is Linux just slower then Windows?

Alright
On the top left of your screen is your system drop down menu
go system > preferences > mouse
Toy with it at your leisure.

Lulz at is Linux slower than Windows by the way.

---

### Post by 23meg on 2007-03-24
It's almost certainly a specific issue with your configuration. Give us more information on your system so that we can hope to locate where it is.

---

### Post by idontknow9999 on 2007-03-24
> **godd4242 said:**
> Alright
On the top left of your screen is your system drop down menu
go system > preferences > mouse
Toy with it at your leisure.

Lulz at is Linux slower than Windows by the way.

I tried that, there is no information on click speed.

> **23meg said:**
> It's almost certainly a specific issue with your configuration. Give us more information on your system so that we can hope to locate where it is.

Well, its a logitech g7 mouse... I configured it a while ago...but I think that lag might of been there back then 2...

---

### Post by idontknow9999 on 2007-03-24
it looks like it might be a issue with my setup... I gave it a try in vmware on windows and it doesn't seem 2 be as bad (but hard 2 tell cause vmware is a tad slow)

---

### Post by kinematic on 2007-03-25
my mouse is more responsive then it ever was in windows.

---

### Post by sloggerkhan on 2007-03-25
I don't have this problem on any linux computer I've used. I personally use a razer copperhead and it work great.

---

### Post by idontknow9999 on 2007-03-25
> **kinematic said:**
> my mouse is more responsive then it ever was in windows.

Now you are just lying. Windows is at 100% speed... This is come from a gamer who does 100 apm avg and peeks at 200 APM...

---

### Post by idontknow9999 on 2007-03-25
well I was trying 2 install nvidia drivers... and guess what? It didnt work...

I downloaded them from nividia... Booted into a virtual console and it wanted X stop. So after I retarded my computer (because ctrl-alt-backspace wasn't working) I found out how 2 stop it. Went back into virtual console but this time it didn't want 2 install because it was missing a interface 2 the kernal or something retarded... 

I mean wtf... id like 2 have something work opn Linux on my first attempt just ONCE, is that really 2 much 2 ask for? 

At the rate I am going, it would be faster to write a OS that works then use Ubuntu :\

---

### Post by 23meg on 2007-03-25
Use [Envy]("http://albertomilone.com/nvidia_scripts1.html") if you can't install the drivers yourself.

---

### Post by idontknow9999 on 2007-03-30
I might try that latter... but it doesn't solve the problem of me not being able 2 install it (a programmer who has taken class in Linux).

and it is not a issue with my video card because there is no delay with the movement, simple a delay on the click...

---

### Post by idontknow9999 on 2007-04-11
This is the problem I am having:

[http://lists.freedesktop.org/archives/xorg-bugzilla-noise/2004-November/004205.html](http://lists.freedesktop.org/archives/xorg-bugzilla-noise/2004-November/004205.html)

edit: They are also talking about this problem here: [http://forums.fingerworks.com/archive/index.php/t-978.html](http://forums.fingerworks.com/archive/index.php/t-978.html) > 
With a normal mouse, in Linux: start with the pointer over a title bar. Move the mouse down as quickly as you can and click. Because of the physical delay in pressing the button, you will miss the titlebar and the drag won't work.

Try the same thing in Windows. It works every time.

Windows is interpreting mouse events at a higher level than X. If it sees a drag it moves the click to the start position.

or, start your mouse pointer on the background of something you reconize, then move (very fast in one direction) while clicking at the same time, you will notice a delay. That delay does not happen in Windows.

---

### Post by idontknow9999 on 2007-04-11
Maybe this will help the goru's out there:

> $ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-6/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-6/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6039fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=40001
B: SND=6


---

### Post by idontknow9999 on 2007-04-11
maybe I should re-install for the 5000th time and try 6.10?

Or fedora if I can figure out why it has 5 CD's :\

---

### Post by Uridian on 2007-04-20
i have the same problem.  it's so very frustrating grabbing a window, and missing.  i KNOW i'm hitting hit, there's just a delay in the click.  i'm using a Microsoft Intellimouse.

***edit***
no sooner did i make the post than i found the answer!  heh...

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/54191]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/54191")

now, no matter how fast i drag, i catch the window every time.  :)

---

