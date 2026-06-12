---
title: "wireless card"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by imacbo on 2007-03-27
ok i suck. I bought a card that came with the drivers for debian drivers on it but i dont know how to enter stuff in to the terminal. every time i try to do it like it says in the cd it gives me an error message. is does not auto run. and when you open the debian file it says. I am using ubuntu 6.1 and this is what the read me file says 
the driver is a ralink 2.4 and 2.6 rt61 a/b/g wlan card
build instructions
1. for 2.4 kernel: $tar -xvzf RT61_linux_STA_Drv_x.x.x.x.tar.gz      when i enter this it says -xvzf: command not found

what am i doing wrong do i need to enter this somewhere other then the terminal.

---

### Post by imacbo on 2007-03-27
come on some one has to know how and what i need to do because i sure as h3ll dont. please someone help me. what do i do first and where do i go next

---

### Post by charles.g.moore on 2007-03-27
make sure that you are typing **tar** before -xvzf

it should say tar -xvzf filename

---

### Post by imacbo on 2007-03-27
iade sure to write it just as it is on the post and on the cd. and i still get the same problem. it says    -xvzf: command not found

---

### Post by thebucksstop on 2007-03-27
> **imacbo said:**
> 
1. for 2.4 kernel: $tar -xvzf RT61_linux_STA_Drv_x.x.x.x.tar.gz      when i enter this it says -xvzf: command not found

what am i doing wrong do i need to enter this somewhere other then the terminal.

Make sure when you copy that command into the terminal (select it outside terminal and middle click with the mouse in terminal to paste) that you're not also copying the $ sign. The command should begin tar and end tar.gz

---

### Post by thebucksstop on 2007-03-27
Just saw your reply. 

The -xvzf are the options for the command. To see what they mean/do, type man tar, or tar --help

Can't help you more than that - on my Windows box at work atm.

---

### Post by charles.g.moore on 2007-03-27
oh sorry it is because it is a gz

gunzip file.tar.gz gives you a file .tar then
tar -xvzf filename.tar

---

### Post by imacbo on 2007-03-27
ok i was putting the $ in the code when i took it out it told me there was no such file or directory

---

### Post by charles.g.moore on 2007-03-27
Open up the CD with the drivers using nautilus
Create a file in your home folder called drivers through nautilus
Drag the files from the CD to the new file
Fire up a terminal
cd /home/drivers
once in the drivers file
ls
gunzip file.tar.gz
tar -xvzf filename.tar
ls
cd into new directory
sudo ./configure
sudo make
sudo make install

Tell me if that works

---

### Post by imacbo on 2007-03-27
ok where is nadulis at?

---

### Post by thebucksstop on 2007-03-27
Basically, Nautilus is the default file-manager in GNOME. It also creates and manages the desktop.

---

### Post by imacbo on 2007-03-27
why is  there no way to auto install from a damn cd that makes no sence to me. i thought this was suppose to be a simple system

---

### Post by charles.g.moore on 2007-03-27
It is a simple system...

Type alt-f2 then nautilus to open nautilus, I dont remember if it is on your desktop or not. think of nautilus as your 'my computer' icon

Dont get frustrated just keep going

---

### Post by thebucksstop on 2007-03-27
It generally is pretty simple. The process you've just been going through is similar to having to use WinZip or similar to extract files from an archive before being able to play with them. The terminal does take a bit of getting used to, but the reason most people post terminal commands is just that its generally simpler and more accurate to give a list of commands, rather than go to places>computer>filesystem etc... Some manufacturers/retailers do write scripts that will just install it for you, but because linux is so customisable, its hard for programmers to anticipate everyone's individual setup.

It is worth persevering with though, my machine's running much faster now than it used to under M$, and the community's generally pretty helpful at sorting things out with you. Hope you stick around!
C

---

### Post by imacbo on 2007-03-27
LOL ok i must be a total bonehead because i cant seem to do a freaking thing right with this system. Hell I dont even know how to install a freaking driver maybe i sure just give up and go back to windows. because i must not be smart enough to run linux. i dont know what i am doing wrong or what i need to do to get my internet working on my computer. i am having to use one computer withh internet on windows so i can try to fix my stupid linux

---

### Post by brennydoogles on 2007-03-27
> **imacbo said:**
> why is  there no way to auto install from a damn cd that makes no sence to me. i thought this was suppose to be a simple system

It is a simple system, but because it is new to you (and me) it can be tricky, as it doesn't play by the same rules as windows. Follow the directions in the above posts, and if you still have problems, take a screenshot of what you are doing (in edgy you can do that by  Applications-->Accessories-->Take a Screenshot) and post it on here. That will help figure out what you need to do differently. Hope everything works out well for you!

---

### Post by charles.g.moore on 2007-03-27
It's cool just relax,

type alt-f2 then type nautilus that will open up your 'my computer'
if there is an icon on your desktop for the cd click that to open that window, once you do that follow the instructions above where you drag the driver files onto your nautilus window

---

### Post by imacbo on 2007-03-27
> **charles.g.moore said:**
> Open up the CD with the drivers using nautilus
Create a file in your home folder called drivers through nautilus
Drag the files from the CD to the new file
Fire up a terminal
cd /home/drivers
once in the drivers file
ls
gunzip file.tar.gz
tar -xvzf filename.tar
ls
cd into new directory
sudo ./configure
sudo make
sudo make install

Tell me if that works

ok i got to the ls but after that it would not work it keep saying command not found

---

### Post by charles.g.moore on 2007-03-27
alright we are getting close

when you do an ls do you see a name that is blue?
that is the new directory
type *cd new_directory_name*
once in follow the rest of the directions

---

### Post by thebucksstop on 2007-03-27
No worries, I certainly had all those issues at the start - I still do!! I guess Ubuntu and Linux can need a slightly different way of thinking about things, but once you can make that leap it sort of clicks into place. I must say I'm still struggling with it all - that's why I wind up hanging around these forums - there's always something to fiddle with.

I'd ask about your internet troubles, but I doubt I'll be any help at all on that, sorry dude.

---

### Post by thebucksstop on 2007-03-27
> **thebucksstop said:**
> No worries, I certainly had all those issues at the start - I still do!! I guess Ubuntu and Linux can need a slightly different way of thinking about things, but once you can make that leap it sort of clicks into place. I must say I'm still struggling with it all - that's why I wind up hanging around these forums - there's always something to fiddle with.

I'd ask about your internet troubles, but I doubt I'll be any help at all on that, sorry dude.

well that was pretty delayed....ignore me!

---

### Post by imacbo on 2007-03-27
ok i am in there but i dont know where i need to pick up on the directions

---

### Post by imacbo on 2007-03-27
ok i got to where i was in the blue folder but i do not know where to go next. or what to do next....also thanks guys for all the help. sorry about lossing my cool but man i was getting upset

---

### Post by imacbo on 2007-03-27
ok I got to where I was in the file that was the blue color. but i cant seem to get past that what do i need to do please

---

### Post by charles.g.moore on 2007-03-28
type 
ls
you should see a bunch of files, now go back to the previous posts and start at ./configure

---

