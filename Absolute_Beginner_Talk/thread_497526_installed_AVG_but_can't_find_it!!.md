---
title: "installed AVG but can't find it!!"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by GlennW on 2007-07-10
*I followed these instructions gleaned from an older thread on how to install AVG to FF 7.04.*


Installation

Download The Free AVG Advisor from here (.deb) to your Desktop.

Code:

cd ~/Desktop
sudo dpkg -i avg75fld-r45-a0973.i386.deb



Launcher

Making a launcher to start AVG

Code:

sudo rm -r /usr/share/applications/avggui.desktop
sudo nano /usr/share/applications/avg.desktop

[COLOR="Red"]I substituted gedit for nano since it's worked well for me in the past[/COLOR]

add:
Code:

[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;

save and exit.

You can now start AVG by going to Applications tab ---> System Tools.

[I]Needless to say, I tried this numerous times thinking that I had a syntax error or whatever. I still can't find it. 

I know that many say that linux is secure and that there's only 14 viruses out there for linux but I agree with some of you that we need to be prepared especially as we're making inroads into the OS market share.

Thanks for your help everybody.[/I]

---

### Post by AlexenderReez on 2007-07-10
how about reload gnome-panel --->

> killall gnome-panel

i'm using avg linux too...default place for launcher is at applications --->accessories

---

### Post by rickycodie on 2007-07-10
try clam av, i have never had problems with it and it's in the repositories

---

### Post by poohbear1616 on 2007-07-10
> I know that many say that linux is secure and that there's only 14 viruses out there for linux but I agree with some of you that we need to be prepared especially as we're making inroads into the OS market share.

Kind of my thinking also!!
Some 13 yr. old wiz kid somewhere could pop up and surprise a lot of folks someday...:lolflag:

---

