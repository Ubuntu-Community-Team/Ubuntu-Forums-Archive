---
title: "Newbie : Getting to desktop"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by peanut 182 on 2006-07-22
Hi there,
I have managed to install ubuntu onto my second computer, i logged into and go to what i beleieve to be the shell propmpt, then comes the little issue.
What do i do now?
How do i get to a desktop?

I know the answer is propbly very clear and obvious but i have scanned though a fair new FAQs and cannot find anything about it.
As you can see this is my first attept at installing linux, allthough i have used a live CD before.

Thanks in advance 
Peanut

---

### Post by trent dillman on 2006-07-22
If you logged in to your user name, you probably (accidentally) did the server install. Try typing
```
sudo /etc/init.d/gdm start
```
in that console. If that doesn't work, do
```
sudo apt-get install ubuntu-desktop
```
then reboot.

---

### Post by Kilz on 2006-07-22
> **peanut 182 said:**
> Hi there,
I have managed to install ubuntu onto my second computer, i logged into and go to what i beleieve to be the shell propmpt, then comes the little issue.
What do i do now?
How do i get to a desktop?

I know the answer is propbly very clear and obvious but i have scanned though a fair new FAQs and cannot find anything about it.
As you can see this is my first attept at installing linux, allthough i have used a live CD before.

Thanks in advance 
Peanut

Ubuntu should have a desktop, it should start automaticly. It is possible you installed it in server mode. Servers do not have a desktop. 
To make sure you have a desktop installed you can try
```
sudo aptitude install ubuntu-desktop
```
Then restart the computer.
If you still are left with a login its possible you need to install video card drivers, in that case we will need to know what card you have to give you more info.

---

### Post by peanut 182 on 2006-07-22
Ok thanks you very much, very quick responce :D 
Ok its doing it now but its a slow computer so i will post when its done
Thanks a lot
Peanut

---

### Post by peanut 182 on 2006-07-22
Ok it did that and then i rebooted it but it still says log in, allthough the stuff it says is diffrent than before.
as it is a very old computer that i dont know much about im not sure about the graphics card but in the bios it says Video: EGA/VGA  but dont think this is the correct thing.
Any help on how to find it ?
thanks again
peanut

---

### Post by muep on 2006-07-22
Try the command:

lspci

Most graphics cards work with the vesa driver, though there will then be no hardware acceleration. For basic internet surfing and other non-gaming stuff, this is enough, though.

Run this:

sudo dpkg-reconfigure xserver-xorg

It launches a text-menu based configuration program for your X server. It asks you questions about your hardware and preferences. If you don't know the answer to a question, the default should work fine. If in doubt, you can ask here. When it asks for the driver, select vesa.

After the configuration, you can try:

sudo /etc/init.d/gdm restart

to see if the desktop system has started working. If not, try to reconfigure again.

Good luck :)

---

### Post by peanut 182 on 2006-07-22
ok when i tryed "sudo dpkg-reconfigure xserver-xorg" it says xserver-xorg is broken or not fully installed, allso when i try "sudo /etc/init.d/gdm restart" it says "/ect/init.d/gdm: command nto found"

So dose this mean i need to do a another clean install ?

thanks a lot for the help so far =D
peanut

---

### Post by hellmet on 2006-07-22
i think your install is broken for some strange reason..
u mite have to re-install dude

---

### Post by exif on 2006-07-22
aptitude might be able to fix up the install, there's some info at [https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide) but if this is a clean new install and you're not worried about the data on the computer at this point I'd suggest just re-starting the install. Make sure you have the desktop Live CD. It should be a pretty painless install.

---

### Post by peanut 182 on 2006-07-22
Ok , i will try this tomo as it is getting late , i am not worried about the data on the HD at all as it is a old one with no infomation on at all other than the install so far.
thansk for you help , will post tomo when i done as you suggested
thanks peanut

---

### Post by barisurum on 2006-07-23
I suggest installing xubuntu. It will run better on a low end machine. You can find info at ubuntu's homesite.

---

