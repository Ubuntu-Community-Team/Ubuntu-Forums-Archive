---
title: "kde4 ==&gt;unity-gnome3 style"
date: 2011-05-27
forum: Art &amp; Design
---

### Post by nowardev on 2011-05-27
here it is (you need of lancelot!)

[http://wstaw.org/m/2011/05/27/UNity.gif](http://wstaw.org/m/2011/05/27/UNity.gif)



HOW TO USE :

```
sudo apt-get install  kubuntu-destkop 
```

install all the plasma widget 

```
sudo apt-get install plasma-widget*
```

load a kde4 session :) , 


run on terminal

```
qdbus org.kde.plasma-desktop /MainApplication showInteractiveConsole
```


[COLOR="Red"]**NOw  ALL PANELS MUST BE REMOVED**  [/COLOR]

 

then should appear this 


[http://nowardev.files.wordpress.com/2011/05/gnome4.jpeg](http://nowardev.files.wordpress.com/2011/05/gnome4.jpeg)

copy and paste the code, 

click on the button Execute!


a gif animated can be found here 

[http://nowardev.files.wordpress.com/2011/04/gnome-defaltt-panel-kde.gif](http://nowardev.files.wordpress.com/2011/04/gnome-defaltt-panel-kde.gif)

(that was for gnome2 panels )


**CODE TO GET UNITY STYLE **

```
var panel = new Panel
if (panelIds.length == 1) {
    // panel.location = 'bottom'
    panel.location = 'top'
}

panel.height = 25

launcher = panel.addWidget("lancelot_part");
launcher.writeConfig("iconLocation", "start-here-kde");
launcher.writeConfig("iconClickActivation", "true");
launcher.writeConfig("contentsExtenderPosition", "1"); 
launcher.writeConfig("searchHistory", "firefox");
launcher.writeConfig("showSearchBox", "true"); 
launcher.writeConfig("partData", "model=FavoriteApplications&type=list&version=1.0\nmodel=Folder%20applications%3A%2FMultimedia%2F&type=list&version=1.0\nmodel=Devices%2FRemovable&type=list&version=1.0\nmodel=Devices%2FFixed&type=list&version=1.0\nmodel=System&type=list&version=1.0\nmodel=OpenDocuments&type=list&version=1.0"); 

var firefox = panel.addWidget("quicklaunch")
firefox.writeConfig("iconUrls","file:///usr/share/applications/firefox.desktop")

var dolphin = panel.addWidget("quicklaunch");
dolphin.writeConfig("iconUrls","file:////usr/share/applications/kde4/dolphin.desktop");

var menubar = panel.addWidget("menubar")
//menubar.writeConfig("useButtonFormFactor", "false");

//panel.addWidget("panelspacer_internal")

//pager = panel.addWidget("pager");
//pager.writeConfig("rows", "2");


var systemsettings = panel.addWidget("quicklaunch");
systemsettings.writeConfig("iconUrls","file:////usr/share/applications/kde4/systemsettings.desktop")

var help = panel.addWidget("quicklaunch")
//qlaunch.writeConfig("iconSize", "24")
help.writeConfig("iconUrls","file:///usr/share/applications/kde4/Help.desktop")

var systemtray = panel.addWidget("systemtray")

var clock = panel.addWidget("digital-clock");
clock.writeConfig("showDate", "false");
clock.writeConfig("showDay", "false");
clock.writeConfig("showSeconds", "true");
clock.writeConfig("showYear", "false");
clock.writeConfig("showShadow", "false");
//clock.writeConfig("showTimezone", "true");
clock.writeConfig("plainClockFont", "Serif,12,-1,5,75,0,0,0,0,0");
clock.writeConfig("useCustomColor", "true");
clock.writeConfig("plainClockColor", "255,255,255");
clock.writeConfig("plainClockDrawShadow", "false");

lockout = panel.addWidget("lockout");
//lockout.writeConfig("showHibernateButton","true");
lockout.writeConfig("showLogoutButton","true");
lockout.writeConfig("showLockButton","false");
lockout.writeConfig("showSleepButton","false");
lockout.writeConfig("showSwitchUserButton","false");

var panel = new Panel
if (panelIds.length == 2) {
    // we are the only panel, so set the location for the user panel.location = 'bottom'
    panel.location = 'bottom'
}

panel.height = 45
panel.addWidget("showdesktop")
panel.addWidget("smooth-tasks")


pager = panel.addWidget("pager");
pager.writeConfig("rows", "1");

panel.addWidget("trash")
//panel.addWidget("smooth-tasks")
//panel.addWidget("launcher")
//panel.addWidget("pastebin")
//panel.addWidget("tasks")



```

---

### Post by CreativeReach on 2011-05-30
Very cool! got try that!

---

### Post by gamepoint on 2011-05-31
And how do i use the code exactly?:confused:

---

### Post by nowardev on 2011-05-31
well, install

```
sudo apt-get install  kubuntu-destkop 
```

install all the plasma widget 

```
sudo apt-get install plasma-widget*
```

load a kde4 session :) , 



run on terminal

```
qdbus org.kde.plasma-desktop /MainApplication showInteractiveConsole
```


[COLOR="Red"]**NOw  ALL PANELS MUST BE REMOVED**  [/COLOR]

 

then should appear this 


[http://nowardev.files.wordpress.com/2011/05/gnome4.jpeg](http://nowardev.files.wordpress.com/2011/05/gnome4.jpeg)

copy and paste the code, 

click on the button Execute!


a gif animated can be found here 

[http://nowardev.files.wordpress.com/2011/04/gnome-defaltt-panel-kde.gif](http://nowardev.files.wordpress.com/2011/04/gnome-defaltt-panel-kde.gif)

(that was for gnome2 panels )

---

