---
title: "[SOLVED] help for iwconfig script"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2007-11-12
good morning!

well Basically i need to do a script but it requires some input in order to work..

Basically this is what i think it should be 
(note Ive never done a script before, so I know is not right)
*********************************************************
#!/bin/sh
#wireless script activation	

what is the name of your network? get netid 

Do you need  a password WEP? get code
If yes type password if not press Enter:


sudo iwconfig wlan0 essid =netid mode Managed rate 54M key open s:code
Activating wireless network
sudo dhclient wlan0

exit
********************************************************

so i just need a few lines to make it work....see???
Thanks!!
lol

---

### Post by KentS on 2007-11-12
Can you use this?

```
#!/bin/bash
#wireless script activation

echo "What is the name of your network?"
read netid

echo "Do you need a password WEP?"
echo "If yes type password if not press Enter:"
read code

if [ -z "$code" ]; then
        sudo iwconfig wlan0 essid $netid mode Managed rate 54M key open
else sudo iwconfig wlan0 essid $netid mode Managed rate 54M key open s:$code

sudo dhclient wlan0

fi

```

---

### Post by gigaferz on 2007-11-12
sweet!
ill try it right now...

---

### Post by gigaferz on 2007-11-12
it works!!!

in gnome works good but in icewm, nothing happens....

the thing is to make wireless as simple as in windows......

I wouldnt mind but is for afriend....
thank you so much.....

---

### Post by KentS on 2007-11-12
That's strange. The script should be independent of the window manager. Do you have bash installed on the machine running icewm? If not, just change the first line in the script to the appropriate shell (e.g. #!/bin/sh , #!/bin/csh).
Have you tried running the script in a terminal to check for any error messages?
And just to be sure, you set the permissions so that it's executable? And the box running icewm uses Ubuntu? If not, "sudo" wouldn't make much sense.

---

### Post by gigaferz on 2007-11-12
well is i ubuntu feisty.

I installed icewm, and just removed openoffice evolution tomboy..etc...nothing  gnome-essential...

in the terminal runs fine i just type it like this 
./wirelessactivate

and gets it done.... I even put a wireless related icon (lol)
well at least is way better and easier to use than the actual command... (hopefully)

but ill do the csh option you mentioned...

thanks

well i reissued permission as an exec file, then I moved it to usr/local/bin
and i also renamed it to a ".sh"
on the icewm permissions i "checked" read, write and exec boxes at the 3 levels listed owner group & world
and on the edit option I tried addin "./" to make it run....mmhh... yeah thats pretty much anything 
at least no matter in wich dir i am it will run in the terminal.... 
we got ourselves a home made command...
lol


I am actually thinking to (based on this one) create a more "complete" script

im sure the total noobs could use it....
(works far better than the gui apps,dont you hate that?)
lol
(no,but seriously)

ever since dapper I've noted that ......
Edit X:

I think the problem here is Rox-filer..... yeah....

in terminal runs fine but this is what i did....>     owner@ubuntu3:/usr/local/bin$ sudo chmod a+x wirelessactivate
owner@ubuntu3:/usr/local/bin$ ls
wirelessactivate
owner@ubuntu3:/usr/local/bin$ sudo rox
owner@ubuntu3:/usr/local/bin$ Error : unrecognised wireless request "Managed"

owner@ubuntu3:/usr/local/bin$ sudo rox
owner@ubuntu3:/usr/local/bin$ Error : unrecognised wireless request "managed"

owner@ubuntu3:/usr/local/bin$ Error : unrecognised wireless request "54M"         

that was just clicking the file in a rox window....

well i just couldnt sleep knowing  i had no solution...

it ocurred to me, that if it only works in gnome-terminal,  well make a shortcut for the terminal and at the same time executing my script,,, 

simple ,huh,,
lol

gnome-terminal -e nameofscript

i edited the properties of the shortcut in the rox filer....

And also for people outthere trying to get a #@$ desktop background or wallpaper on icewm and rox filer  FOrget about editing anykind of configuration files,,, once you have the pinboard enabled rightclick anywhere and it should say at the bottom of the menu "backdrop"
click it and drop your wallpaper......
also i didnt knowabout it, but for all the people using feisty,  we have some really cool desktopbackgrounds...
go to  /usr/share/pixmaps/backgrounds/cosmos  

finally I'll leave this place alone and go to sleep ,,,but tomorrow.....

---

