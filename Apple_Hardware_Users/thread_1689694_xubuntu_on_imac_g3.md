---
title: "xubuntu on imac g3"
date: 2011-02-17
forum: Apple Hardware Users
---

### Post by shakan09 on 2011-02-17
ok first off im a total linux noob i apologize for that
so i have a imac g3 500mhz with 384 ram running 10.4.11 and i have the xubuntu 10.10 ppc alternate iso that i will soon be burning on to a disc.

 my first question is, will this even work for my computer or do i need something else?

secondly would it be possible to get a detailed, simple, step by step set of instructions to install xubuntu? ive looked at this page [_here_]("http://ubuntuforums.org/showthread.php?t=405934") and im not sure if this is for the alternate cd and exactly which set of instructions i need to follow (i think the cli install)

third im not sure which desktop thinger to install? i guess XFCE is the standard one for xbuntu?

thanks in advance sorry for being so noobish

---

### Post by snafu006 on 2011-02-17
You should do 10.04 ubuntu the installer works better and you can add Xubuntu after you install ubuntu so here is what you do

1 download ubuntu 10.04 PPC and burn to cd. Put cd in and hold the apple option key you should see the cd after that follow the install.

2 when the computer is done installing ubuntu and reboots on the black screen where it has yaboot PRESS TAB then type

Linux install video=ofonly this will get you to the low video so you can start to get the imac G3 running.

3 find tirminal and type sudo nano /etc/X11/xorg.conf
type your password and this is where you input a xorg.conf file here is my working xorg file    [http://ubuntuforums.org/showthread.php?t=1676488]("http://ubuntuforums.org/showthread.php?t=1676488")]
 
copy and past to a pindrive from a differnt computer and then use the pindrive on the imac open the drive fine the file open it copy the file and past to the xorg.conf press ctrl + o then ctrl + x. if all goes well when you reboot you should see the ubuntu screen. 

post me back and ill help you more

---

### Post by snafu006 on 2011-02-17
and ill post pic on what you need to do to

---

### Post by shakan09 on 2011-02-17
thanks for the help. this is prolly gonna get put off for a bit cause my imac wont burn anything (lazer can not be calibrated error) fml and idk if i can find someone to burn it for me. but pic would be greay i have this page book marked

---

### Post by snafu006 on 2011-02-17
you can burn it on a woindows pc it works i did that as long as your imac can read the cd you put in. And i will go step by step to help you get the old imac running ubuntu and thin xubuntu one thing i would say is get it up to 1 gb ram its cheep go to bestbuy or your computer store and get 2 512 ram sticks

---

### Post by shakan09 on 2011-02-18
is it really necessary to get more ram? i sorta dont have any money. anyway im downloading ihe 10.04 ppc desktop cd
how to i insert xorg.conf if i dont have another computer? can i just edit it like it says on the other guide?
after i install ubuntu how to i go to xubuntu?

---

### Post by snafu006 on 2011-02-18
to install xubuntu just go to terminal and copy past this sudo apt-get install xubuntu-desktop. for the ram part the computer is going to be a little slow its ok but slow and for the xorg.conf file yes you can do it thats way but if you can get on the net with that computer 

find a working xorg.conf file (copy the file) the one i posted is my xorg.conf file and it works

go to tirminal and type **sudo nano /etc/X11/xorg.conf** then enter password when the blank xorg.conf file comes up right click in the terminal just pasted the file then press ctrl + o and then ctrl + x

---

### Post by shakan09 on 2011-02-18
so after ive installed ubuntu copy and paste the xorg.conf file?
okay will i need to upgade to 10.10? and should i do this before or after i switch to xubuntu?
hey your in colorado springs thats funny cause im in denver

---

### Post by shakan09 on 2011-02-18
ok so i did
live video=ofonly (not ready to install yet)
and got the blank screen after it loaded then i did
sudo nano /etc/x11/xorg.conf
and it brought up the nano thing but i dont get how i change the modules so it boots up. sorry for being a noob

and on ur other post by pin drive did you mean usb drive? i have a psp which is pretty much a 16gb usb drive

**EDIT** i cant edit the xorg.conf cause there isnt one there

---

### Post by snafu006 on 2011-02-18
> **shakan09 said:**
> ok so i did
live video=ofonly (not ready to install yet)
and got the blank screen after it loaded then i did
sudo nano /etc/x11/xorg.conf
and it brought up the nano thing but i dont get how i change the modules so it boots up. sorry for being a noob

and on ur other post by pin drive did you mean usb drive? i have a psp which is pretty much a 16gb usb drive

OK so did you install ubuntu? and yes by pindrive i mean usb drive see this is what i did.

1 I installed ubuntu

2 On the second black screen ( where is has yaboot) i press TAB then typed Linux install video=ofonly this should get you to a low rez video screen.

3 Then by useing a my windows computer i copyed my xorg.conf file to my usb drive and places the usb drive in the Imac

4 Went to terminal typed the sudo nano /etc/X11/xorg.conf and opened it.

5 I opened my usb drive found the xorg.conf file and opend it copyed the txt.

6 Went back to the terminal and pasted the xorg.conf file by right clicking and pasting then press CTRL+o then CTRL+x

7 REBOOT THE COMPUTER

I am posting some pic for you and ill send you a message with my cell number so you can call me.

---

### Post by snafu006 on 2011-02-18
[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0104.jpg[/IMG]

[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0107.jpg[/IMG]

[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0108.jpg[/IMG]

[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0110.jpg[/IMG]

[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0111.jpg[/IMG]

[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0113.jpg[/IMG]

[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0115.jpg[/IMG]

[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0117.jpg[/IMG]

---

### Post by snafu006 on 2011-02-18
[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0118.jpg[/IMG]

[IMG]http://i1188.photobucket.com/albums/z420/snafu0062/IMG_0119.jpg[/IMG]

---

