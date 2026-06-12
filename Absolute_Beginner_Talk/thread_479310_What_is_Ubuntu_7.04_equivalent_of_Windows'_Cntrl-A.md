---
title: "What is Ubuntu 7.04 equivalent of Windows' Cntrl-Alt-Del?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-20
If an application you've opened has frozen or is not working for some reason, how do you:
1) Get the application to stop doing whatever it is trying to do?
2) Close down the application, if (1) does not work?

For example, I opened the Update Manager to get two updates. But for the last ten minutes the application is open and "thinking" without initiating the process of getting the two updates. So it needs to be shut down and re-started, so that it will be able to function normally and get the updates. How do I do this?

---

### Post by ecs_pf5 on 2007-06-20
system > administration > system monitor? (gives you something like windows task manager)

or in really serious cases where everything is locked, try ctrl-alt-backspace (but that'll restart the GUI & kill most everything)

I'm a n00b - use my info with caution.

---

### Post by floke on 2007-06-20
(1) Open up a terminal and type 'top' to see all processes. Get the PID number eg 5847 - type 'q' to exit top. Then 'sudo kill -9 [PIDnumber]' - eg sudo kill -9 5847.

(2) System/admin/system monitor - select process and kill it

(3) In KDE = alt+esc = lists all processes - select and kill

(4) from the terminal - if you know the name of the app = use 'sudo killall firefox firefox.bin' (firefox consists of 2 processes so need to kill both)

(5) from the terminal (of alt+f2 launcher in kde) - type 'xkill' - then point the skull+crossbones at the offending window and zap it (note: this doesn't always kill the whole app - eg will kill firefox but not firefox.bin).

(6) Add the 'force close' applet to the panel. Select and zap.

Phew!

---

### Post by swarup on 2007-06-20
> **ecs_pf5 said:**
> system > administration > system monitor? (gives you something like windows task manager)

or in really serious cases where everything is locked, try ctrl-alt-backspace (but that'll restart the GUI & kill most everything)

I'm a n00b - use my info with caution.

Thank you. The System Monitor worked perfectly. Now my follow-up question is, is there any short-cut key to open the System Monitor, so you don't have to go via "administration"? I'd guess there must be some short-cut key for this.

---

### Post by Calash on 2007-06-20
> **Steve.K said:**
> (1) Open up a terminal and type 'top' to see all processes. Get the PID number eg 5847 - type 'q' to exit top. Then 'sudo kill -9 [PIDnumber]' - eg sudo kill -9 5847.

(2) System/admin/system monitor - select process and kill it

(3) In KDE = alt+esc = lists all processes - select and kill

(4) from the terminal - if you know the name of the app = use 'sudo killall firefox firefox.bin' (firefox consists of 2 processes so need to kill both)

(5) from the terminal (of alt+f2 launcher in kde) - type 'xkill' - then point the skull+crossbones at the offending window and zap it (note: this doesn't always kill the whole app - eg will kill firefox but not firefox.bin).

(6) Add the 'force close' applet to the panel. Select and zap.

Phew!

That is a great list.  I have been using ps -e to get a process list, then using kill to clear it out.  It is good to have other options.  The xkill one just made me laugh a little....the skull and crossbones was too funny :)

---

### Post by swarup on 2007-06-20
Yes, that is a very helpful list from Steve K. I've just now seen it. One question for you, Steve, regarding the last option you listed: How do you add the "Force Close" applet to the panel? And is the "Force Close" a safe and effective way to accomplish stopping an app? If so, that sounds quite convenient. Thanks.

---

### Post by swarup on 2007-06-20
> **Calash said:**
> That is a great list.  I have been using ps -e to get a process list, then using kill to clear it out.  It is good to have other options.  The xkill one just made me laugh a little....the skull and crossbones was too funny :)

What is "ps -e"? Do you just press the indicated keys? Is this only in KDE, or does it also work in Gnome?

---

### Post by swarup on 2007-06-20
> **Calash said:**
> That is a great list.  I have been using ps -e to get a process list, then using kill to clear it out.  It is good to have other options.  The xkill one just made me laugh a little....the skull and crossbones was too funny :)

I see. You're talking about a terminal command. I just tried it. This is basically another way of doing just what Steve K. mentioned in his option #1, right?

---

### Post by AndyCooll on 2007-06-20
> **swarup said:**
> What is "ps -e"? Do you just press the indicated keys? Is this only in KDE, or does it also work in Gnome?

ps -e is typed in the command line and lists running processes.

:cool:

---

### Post by AndyCooll on 2007-06-20
> **swarup said:**
> Thank you. The System Monitor worked perfectly. Now my follow-up question is, is there any short-cut key to open the System Monitor, so you don't have to go via "administration"? I'd guess there must be some short-cut key for this.

There isn't a shortcut key, AFAIK. However you can create one (unfortunately can't remember off the top of my head how to this, and I'm at work not in front of my Linux box). You could add a quick shortcut to your taskbar in the same way you may have added other shortcuts (Right click on taskbar and select add new link/shortcut)

:cool:

---

### Post by paparucino on 2007-06-20
> **swarup said:**
> What is "ps -e"? Do you just press the indicated keys? Is this only in KDE, or does it also work in Gnome?
It's a kernel command so it works with all window manager. 
Since the output is a long list, I suggest 
```

ps -e | more

```
It prints the first page then you can see the following lines by pressing ENTER

---

### Post by floke on 2007-06-20
> **swarup said:**
> Yes, that is a very helpful list from Steve K. I've just now seen it. One question for you, Steve, regarding the last option you listed: How do you add the "Force Close" applet to the panel? And is the "Force Close" a safe and effective way to accomplish stopping an app? If so, that sounds quite convenient. Thanks.

Right click on panel = add to panel = force-quit
;)

---

### Post by ckempo on 2007-06-20
I think I read somewhere that something like a CTRL+ALT+DEL shortcut to open System Monitor should be configured by default in Gutsy.

---

### Post by skirkpatrick on 2007-06-20
There's a way to do it in Gnomes configuration editor.  Search the forums as I was lazy last night and just used Automatix to set it up for my daughter.

---

### Post by Carlos Santiago on 2007-06-20
The easiest way:

Run the command:
```
xkill
```
Then you just have to click on the window of the application you want to kill.

---

### Post by swarup on 2007-06-20
> **Carlos Santiago said:**
> The easiest way:

Run the command:
```
xkill
```
Then you just have to click on the window of the application you want to kill.

That's helpful, thanks. I was looking for something quick and easy.

I presume that all these various ways of shutting down an app are safe and don't do any harm to the app, the OS, or the box.

---

### Post by mikehipson on 2007-06-20
hi, i dowloaded ubuntu onto a cd, and now i want to install it on my laptop.  currently my OS is XP home edition, and i can't seem to format the c:, when i go into my pc and right click on c: and then format, it says that i cant because something is running on there, and of course the only thing running is windows.  ubuntu says to just boot the machine from the cd, but i cant get my laptop to do that either.  it just automatically goes to xp.  has anybody had this problem before?  or maybe you have some ideas?

thanks
Mike

---

### Post by vexorian on 2007-06-20
Since I do programming most of the times I always end up freezing ubuntu thanks to malformed code, I learned gnome comes with a widget you can add to the panel, it is a button that when you click it allows you to target a window and it will kill the process.

---

### Post by finer recliner on 2007-06-20
@mike, please start a new thread in "absolute beginners" -- it is a more appropriate place for your question. and it is a very common question, so try searching the forum too.

---

### Post by swarup on 2007-06-20
> **mikehipson said:**
> hi, i dowloaded ubuntu onto a cd, and now i want to install it on my laptop.  currently my OS is XP home edition, and i can't seem to format the c:, when i go into my pc and right click on c: and then format, it says that i cant because something is running on there, and of course the only thing running is windows.  ubuntu says to just boot the machine from the cd, but i cant get my laptop to do that either.  it just automatically goes to xp.  has anybody had this problem before?  or maybe you have some ideas?

thanks
Mike

Booting from the cd should be very easy. Put the cd in the drive, and boot the computer. Just as the computer starts up, hit the F11 key or the F12 key. One of those will bring you to the boot menu. That menu will ask you what you want to use to boot up the computer. And one of those options will be your cd rom drive.

---

### Post by swarup on 2007-06-20
Are you wanting to wipe out XP and only have Ubuntu on the computer, or do you want to set up a dual boot with Ubuntu and XP?

---

### Post by silkstone on 2007-06-20
> **swarup said:**
> Thank you. The System Monitor worked perfectly. Now my follow-up question is, is there any short-cut key to open the System Monitor, so you don't have to go via "administration"? I'd guess there must be some short-cut key for this.

You can right-click on a panel, Add to Panel, and add the System Monitor. The panel icon also shows processor usage, which is handy.

---

### Post by swarup on 2007-06-20
> **silkstone said:**
> You can right-click on a panel, Add to Panel, and add the System Monitor. The panel icon also shows processor usage, which is handy.

Thanks. That's pretty cool.

---

### Post by apureevil1 on 2007-06-20
> **mikehipson said:**
> hi, i dowloaded ubuntu onto a cd, and now i want to install it on my laptop.  currently my OS is XP home edition, and i can't seem to format the c:, when i go into my pc and right click on c: and then format, it says that i cant because something is running on there, and of course the only thing running is windows.  ubuntu says to just boot the machine from the cd, but i cant get my laptop to do that either.  it just automatically goes to xp.  has anybody had this problem before?  or maybe you have some ideas?

thanks
Mike

Perhaps you need to enable boot from CD Rom in your BIOS, my laptop came with that function disabled, there is also the probability that the cd you created  (or have) doesn't work..I created a few coasters the first couple of times I burned the live CD ISO..(just my 1cents worth)

---

### Post by swarup on 2007-06-20
> **silkstone said:**
> You can right-click on a panel, Add to Panel, and add the System Monitor. The panel icon also shows processor usage, which is handy.

One question for those of us with older computers: it must take processor resources to keep that system moniter icon running there on the panel. If it is going to slow down my computer at all, I am thinking I would be better off removing it. (Although I do like the information it gives, and the easy access to open the System Moniter). Doesn't having the icon there on the panel mean just one more program running in the background?

---

### Post by ghandi69_ on 2007-06-20
Hey guys...

I always had the "skull and crossbones" as a shortcut in my GNOME panel.... However.. I do not see it as an option to add it to the KDE panel... Anyone know how to add it in KDE??.

---

### Post by Omnios on 2007-06-20
> **swarup said:**
> If an application you've opened has frozen or is not working for some reason, how do you:
1) Get the application to stop doing whatever it is trying to do?
2) Close down the application, if (1) does not work?

For example, I opened the Update Manager to get two updates. But for the last ten minutes the application is open and "thinking" without initiating the process of getting the two updates. So it needs to be shut down and re-started, so that it will be able to function normally and get the updates. How do I do this?

 Desktop  force quit. rIght click panel and choose ad to panel. 

 Look at Desktop & WIndows. Click Force Quit and add on the bottom.
Now when a app misbehaves you can click force quit on the panel then click the app to kill it.

 Also ctrl-alt-backspace will restart xserver.

---

### Post by swarup on 2007-06-20
This is in follow-up to my last posting just above. When I have the System Monitor app open and looking at the processes tab, it shows a lot of apps open. But the only app that shows it is taking significant CPU resources is the System Monitor itself.It takes anywhere from 30-60% of the CPU. Now, I do not know whether that is because I've actually opened the System Monitor app window, or whether even without doing so, just having the System Monitor icon up on the panel is going to take a lot of my CPU resources. If so, then I better remove that System Monitor icon from my desktop panel.

---

### Post by Benbow on 2007-06-20
Like SteveK I always use the "force to quit"button.
Right click on top panel brings up "Add to panel" icon menu. Down to Desktop & Windows, highlight "force to quit" button left click on "+Add" button. This places the "force to quit button" in your top panel and follow pop up's.
Simple and easy.

---

### Post by Yfrwlf on 2007-06-30
> **swarup said:**
> This is in follow-up to my last posting just above. When I have the System Monitor app open and looking at the processes tab, it shows a lot of apps open. But the only app that shows it is taking significant CPU resources is the System Monitor itself.It takes anywhere from 30-60% of the CPU. Now, I do not know whether that is because I've actually opened the System Monitor app window, or whether even without doing so, just having the System Monitor icon up on the panel is going to take a lot of my CPU resources. If so, then I better remove that System Monitor icon from my desktop panel.

There's a difference between the existence of a link/shortcut/icon, and running a program.  Just having a link to a program doesn't run that program. :)

---

### Post by swarup on 2007-07-01
> **Yfrwlf said:**
> There's a difference between the existence of a link/shortcut/icon, and running a program.  Just having a link to a program doesn't run that program. :)

In the case of ordinary icons I would readily agree, but in this case it seems somewhat different because the system monitor icon, when placed on the panel, is not a mere icon. It is actually doing work-- the icon is the shape of a monitor, and the CPU usage is continuously being depicted in graph form there. Plus if you run your cursor over the icon, the icon gives an actual number output of the amount of CPU currently being used. Which leads me to conclude that this is not a mere icon. Rather, putting the system monitor icon on your panel means having the program itself constantly open and running in the background. And that will always be taking a certain amount of the CPU's capacity, just to keep that icon up and running as a background program. Is this not correct?

---

### Post by Yfrwlf on 2007-07-04
> **swarup said:**
> In the case of ordinary icons I would readily agree, but in this case it seems somewhat different because the system monitor icon, when placed on the panel, is not a mere icon. It is actually doing work-- the icon is the shape of a monitor, and the CPU usage is continuously being depicted in graph form there. Plus if you run your cursor over the icon, the icon gives an actual number output of the amount of CPU currently being used. Which leads me to conclude that this is not a mere icon. Rather, putting the system monitor icon on your panel means having the program itself constantly open and running in the background. And that will always be taking a certain amount of the CPU's capacity, just to keep that icon up and running as a background program. Is this not correct?

Yep, I have an icon that opens the system monitor on my panel, so when I saw the system monitor panel applet that has the exact same icon I assumed it too was a mere link and never tried it out. :)  Sorry about that.

If you click on it once you add it to the panel, it then opens the actual "system monitor" program.  With *that* open, the panel app shows several spikes for me when the program is updating the list that take up about 40-50% CPU use it seems.  When it's closed though but the system monitor panel app is still there, it's shows very very low CPU use and may be from the fact I have an MP3 playing among other things.  So, while obviously it has to take up some processing to display/check the status of the CPU, it seems to be a very tiny amount.

---

### Post by swarup on 2007-07-05
> **Yfrwlf said:**
> Yep, I have an icon that opens the system monitor on my panel, so when I saw the system monitor panel applet that has the exact same icon I assumed it too was a mere link and never tried it out. :)  Sorry about that.

If you click on it once you add it to the panel, it then opens the actual "system monitor" program.  With *that* open, the panel app shows several spikes for me when the program is updating the list that take up about 40-50% CPU use it seems.  When it's closed though but the system monitor panel app is still there, it's shows very very low CPU use and may be from the fact I have an MP3 playing among other things.  So, while obviously it has to take up some processing to display/check the status of the CPU, it seems to be a very tiny amount.

That may be. Of course, it depends upon how powerful your CPU is. With my 433 mhz celeron chip, even just the icon with its mini monitor seems to take up a measurable amount of the energy of my chip. So for that reason, I felt it probably isn't beneficial to have it on the panel. But for others who have a newer chip, it probably doesn't matter.

---

### Post by scragar on 2007-07-05
you could try opening system monitor and going edit > Preferences and increasing refresh interval or removing smooth graphics, this should reduce load some what, while it's running. the alternative is to just not use it, but it's such a powerfull tool that uses only around 20MB of ram.

---

### Post by rodtrekker on 2007-07-07
I'm a newbie, but I found this:

**_ How to enable Ctrl+Alt+Del to open System Monitor in GNOME_**

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

See the following links for this and more remaps and special key information.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#In_X_Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty#In_X_Windows)
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration)

I have not tried it myself, but hope you find it useful.

Regards,
Rodney

---

### Post by dfreer on 2007-07-07
> **rodtrekker said:**
> I'm a newbie, but I found this:

**_ How to enable Ctrl+Alt+Del to open System Monitor in GNOME_**

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

See the following links for this and more remaps and special key information.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#In_X_Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty#In_X_Windows)
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration)

I have not tried it myself, but hope you find it useful.

Regards,
Rodney

I was just about to mention this, surprised no one else did. Notice this is for metacity only, if you use beryl you will have to map it again within beryl itself.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME)
For beryl:
[http://www.getautomatix.com/forum/index.php?showtopic=970&view=findpost&p=3409](http://www.getautomatix.com/forum/index.php?showtopic=970&view=findpost&p=3409)

---

### Post by swarup on 2007-07-07
> **dfreer said:**
> I was just about to mention this, surprised no one else did. Notice this is for metacity only, if you use beryl you will have to map it again within beryl itself.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME)
For beryl:
[http://www.getautomatix.com/forum/index.php?showtopic=970&view=findpost&p=3409](http://www.getautomatix.com/forum/index.php?showtopic=970&view=findpost&p=3409)

That is helpful what both of you have mentioned. I'm not really sure what metacity is and what beryl is, though. If I am using Ubuntu 7.04, then which am I using-- metacity or beryl??

---

### Post by godd4242 on 2007-07-07
> **floke said:**
> (1) Open up a terminal and type 'top' to see all processes. Get the PID number eg 5847 - type 'q' to exit top. Then 'sudo kill -9 [PIDnumber]' - eg sudo kill -9 5847.

(2) System/admin/system monitor - select process and kill it

(3) In KDE = alt+esc = lists all processes - select and kill

(4) from the terminal - if you know the name of the app = use 'sudo killall firefox firefox.bin' (firefox consists of 2 processes so need to kill both)

(5) from the terminal (of alt+f2 launcher in kde) - type 'xkill' - then point the skull+crossbones at the offending window and zap it (note: this doesn't always kill the whole app - eg will kill firefox but not firefox.bin).

(6) Add the 'force close' applet to the panel. Select and zap.

Phew!


About force close:

I've rarely gotten it to work very well, in fact each time I do it it leaves the process still running, but shuts down the window.

Therefore, if I crash firefox I can't restart it due to the process not having stopped yet.

Just felt like sharing...

---

### Post by dfreer on 2007-07-07
metacity is the default in Gnome, so almost certainly you are using metacity.
If not, the worse it will do is not work :P

Beryl is the 3D effects that it seems like everyone is wanting to have now :D

---

