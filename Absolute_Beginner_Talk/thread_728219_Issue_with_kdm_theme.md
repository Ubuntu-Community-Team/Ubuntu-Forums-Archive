---
title: "Issue with kdm theme"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Smatt454 on 2008-03-18
So i downloaded this theme for kdm. 
[http://www.kde-look.org/content/show.php/Umbrella+Corp+%2B+Resident+Evil+1600x1200?content=63630](http://www.kde-look.org/content/show.php/Umbrella+Corp+%2B+Resident+Evil+1600x1200?content=63630)


I got it installed but the login boxes are in the lower right corner like in this picture
[http://mail.google.com/mail/?ui=2&ik=89f7cb9ee8&realattid=f_fdyv0uzy0&attid=0.1&disp=inline&view=att&th=118c35eeedc93936](http://mail.google.com/mail/?ui=2&ik=89f7cb9ee8&realattid=f_fdyv0uzy0&attid=0.1&disp=inline&view=att&th=118c35eeedc93936)
f
is there a way i can edit the kdmrc file or something so i can change the size and position of the login and password boxes?

this is my kdrc file

> 
[General]
ConfigVersion=2.3
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
PidFile=/var/run/kdm.pid
ReserveServers=:1,:2,:3
ServerVTs=-7
StaticServers=:0

[Shutdown]
BootManager=None
HaltCmd=/sbin/poweroff
RebootCmd=/sbin/reboot

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
AutoReLogin=false
ClientLogFile=.xsession-errors-%s
Reset=/etc/kde3/kdm/Xreset
Session=/etc/kde3/kdm/Xsession
Setup=/etc/kde3/kdm/Xsetup
Startup=/etc/kde3/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=true
ColorScheme=
EchoMode=OneStar
FaceSource=AdminOnly
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=
GreetFont=Sans Serif,22,-1,5,50,0,0,0,0,0
GreetString=Welcome to Kubuntu at %n
GreeterPos=50,50
HiddenUsers=
Language=en_US
LogoArea=Logo
LogoPixmap=
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,10,-1,5,50,0,0,0,0,0
Theme=/usr/share/apps/kdm/themes/umbrella
UseBackground=false
UseTheme=true
UserCompletion=false
UserList=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nolisten tcp
ServerCmd=/usr/bin/X -br

[X-:*-Greeter]
AllowClose=true
DefaultUser=smatt454
FocusPasswd=false
LoginMode=DefaultLocal
PreselectUser=None

[X-:0-Core]
AutoLoginAgain=false
AutoLoginDelay=0
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=smatt454
ClientLogFile=.xsession-errors

[Xdmcp]
Enable=false
Willing=/etc/kde3/kdm/Xwilling


---

### Post by (((X))) on 2008-03-19
second link leads to gmail.com

---

