---
title: "Automatically Start Gnome Shell after log in"
date: 2009-10-22
forum: Art &amp; Design
---

### Post by alex_kent_18 on 2009-10-22
Hi,

Anyone knows how to start Gnome shell automatically after logged in?

I couldn't find an article though I searched around Internet about this. 

FYI, my ubuntu version is 9.10 beta.

Thanks in advanced.

---

### Post by Tibuda on 2009-10-22
From standard Gnome, open System > Preferences > Startup apps (or session apps), and add an entry for Gnome-Shell running ```
gnome-shell --replace
```

---

### Post by AJB2K3 on 2009-10-22
Go into the user>sessions control pannel and change it there.

---

### Post by msktje on 2009-10-22
AJB2K3 can you please explain a little more detailed where to change it?

---

### Post by alex_kent_18 on 2009-10-23
Thanks for your prompt replies. I'll try 'em out and will post an update here.

:)

---

### Post by alex_kent_18 on 2009-10-23
It works. What a remarkable effort. Thanks indeed.

> **danielrmt said:**
> From standard Gnome, open System > Preferences > Startup apps (or session apps), and add an entry for Gnome-Shell running ```
gnome-shell --replace
```

---

### Post by manoriax on 2009-10-24
To make it run natively you have to open a terminal and write:
```
sudo update-alternatives --config x-window-manager

```Select "mutter" there. After this write
```
sudo cp /usr/share/applications/gnome-shell.desktop /etc/xdg/autostart
```hit enter and after a restart say hello to gnome-shell running as native window manager.

---

### Post by jorrieboy on 2009-10-26
> **manoriax said:**
> To make it run natively you have to open a terminal and write:
```
sudo update-alternatives --config x-window-manager

```Select "mutter" there. After this write
```
sudo cp /usr/share/applications/gnome-shell.desktop /etc/xdg/autostart
```hit enter and after a restart say hello to gnome-shell running as native window manager.

It helps for my.
Thanks!!!:guitar:

---

### Post by leandromartinez98 on 2009-10-27
Is it possible to include it as one of the desktops alternatives in the splash screen?

---

### Post by McDuff on 2009-10-29
is it possible to revert this? i tried it selecting &#8220;metacity&#8221; with
```
sudo update-alternatives --config x-window-manager
```
and disabling gnome-shell in autostart programs. but when i login now, i get a blank desktop with no window-decorations and no panels. seems that no metacity gets started. have i missed something?

---

### Post by manoriax on 2009-10-29
Did you select metacity in auto-mode?
After you changed it to metacity in auto-mode, run > sudo rm /etc/xdg/autostart/gnome-shell.desktop
And everything should be working fine, again.

---

### Post by AJB2K3 on 2009-10-30
> **msktje said:**
> AJB2K3 can you please explain a little more detailed where to change it?
Unfortunatly My ubuntu is @8.10 and my current laptop is vista.
But it was an option called autologon in "users and sessions" pannel.

---

### Post by indivermont on 2010-02-21
Have you tried adding gnome-panel to the startup applications? I would try logging into a failsafe gnome session and then adding gnome-panel to the startup list.

---

### Post by Teethador on 2010-03-14
Hello All

The title "Automatically Start Gnome Shell after log in" actually means that when you log on to the system a Gnome Shell will be waiting for you on the desktop already open? Or does this mean that the Gnome Shell will be running in the background?

I added the gnome-shell --replace in the the System->Preferences->Startup Applications clicked "add" then added Gnome Shell as Name and then gnome-shell --replace in the command field and then clicked save.

Restarted the machine several times and nothing happens except during Startup there is a small delay. What I expect to happen is that there will be a Gnome Terminal windows waiting for me on the desktop already open and running when I log in.

This is the 1st thing that I have to the OS so it is 100% vanilla.

Ubuntu v.9.10 release in October 2009.

Thanks in advance for your patience.
Teethador

---

### Post by manoriax on 2010-03-14
See one of my previous postings: [http://ubuntuforums.org/showpost.php?p=8158674&postcount=7](http://ubuntuforums.org/showpost.php?p=8158674&postcount=7)

---

### Post by Teethador on 2010-03-20
Manoriax, thank you for your reply.

This is the message that I received from the command prompt.

t@t-laptop:~$ update-alternatives --config x-window-manager
There is only one alternative in link group x-window-manager: /usr/bin/metacity
Nothing to configure.

There was nothing to do, or see, or choose. The next step, I looked to see if 'mutter' was installed.
It was not. Then I wondered what is 'mutter' and why do I need it?

Can you answer those questions? What is 'mutter' and what does it do and why do I need it? The opinions online are rather negative about this software...

Checked to see what was in the /usr/share/applications file and gnome-shell.desktop is not there. Is it update/rewritten when 'mutter' is installed? What is there is gnome-terminal.desktop

What is the difference between gnome-shell.desktop and gnome-terminal.desktop? Why can I not just copy gnome-terminal.desktop to the /etc/xdg/autostart folder?

Lots of questions. Thanks in advance for the help.

---

### Post by arundracula on 2010-03-23
> **manoriax said:**
> To make it run natively you have to open a terminal and write:
```
sudo update-alternatives --config x-window-manager

```Select "mutter" there. After this write
```
sudo cp /usr/share/applications/gnome-shell.desktop /etc/xdg/autostart
```hit enter and after a restart say hello to gnome-shell running as native window manager.


I've done this... But Some how I reverted this(for me only) by selecting the maximum Visual Effects..

But for a new user/another user.. it remains the same and gives no cursor  problem..
Is there any way to revert this to normal?

Please help.. Its Urgent..

---

### Post by manoriax on 2010-03-23
> **Teethador said:**
> Manoriax, thank you for your reply.

This is the message that I received from the command prompt.

t@t-laptop:~$ update-alternatives --config x-window-manager
There is only one alternative in link group x-window-manager: /usr/bin/metacity
Nothing to configure.

There was nothing to do, or see, or choose. The next step, I looked to see if 'mutter' was installed.
It was not. Then I wondered what is 'mutter' and why do I need it?

Mutter is the new window manager that will replace metacity in Gnome 3.0. You need it to run gnome-shell and I think you can't install gnome-shell without mutter. If you have gnome-shell installed, but not mutter, you should try to install mutter manually from the package repositories.

> **Teethador said:**
> Can you answer those questions? What is 'mutter' and what does it do and why do I need it? The opinions online are rather negative about this software...

Checked to see what was in the /usr/share/applications file and gnome-shell.desktop is not there. Is it update/rewritten when 'mutter' is installed? What is there is gnome-terminal.desktop
Seems that you do not have gnome-shell installed.

> **Teethador said:**
> What is the difference between gnome-shell.desktop and gnome-terminal.desktop? Why can I not just copy gnome-terminal.desktop to the /etc/xdg/autostart folder?
The gnome-terminal has nothing to do with the window manager. It's the command prompt where you can enter all the nice Linux commands. ;)

> **arundracula said:**
> I've done this... But Some how I reverted this(for me only) by selecting the maximum Visual Effects..

But for a new user/another user.. it remains the same and gives no cursor  problem..
Is there any way to revert this to normal?

Please help.. Its Urgent..

I think selecting the maximum visual effects from the menu changes the window manager back to metacity (and compiz), which does not support gnome-shell, because it's just a different window manager. You could try to run
```
sudo update-alternatives --config x-window-manager
```again and select mutter there.

---

### Post by arundracula on 2010-03-23
> I think selecting the maximum visual effects from the menu changes the  window manager back to metacity (and compiz), which does not support  gnome-shell, because it's just a different window manager. You could try  to run
     Code:
     sudo update-alternatives --config x-window-manager 
again and select mutter there.     

I am saying that I want to avoid gnome-shell by changing to the default window manager.


I run that command earlier to make gnome-shell to start at login and everytime I login I am supposed to see the gnome-shell. But  some times nothing at all. only the wall paper and icons...- no panels or no gnome-shell.

So I want to reset all to the default Ubuntu 9.10. First I want to remove gnome-shell from startup and then set the window manager to the default. How to do that?

---

### Post by manoriax on 2010-03-23
Oh, sorry.

Try to run
```
sudo update-alternatives --config x-window-manager
```
and select metacity in the auto-mode there. After that run
```
sudo rm /etc/xdg/autostart/gnome-shell.desktop
```

---

### Post by arundracula on 2010-03-23
Thanks. It worked.

But now, I can't enable the visual effects to medium or maximum.. It shows Desktop effects could not be enabled.. Previuosly it was working. My graphic card is nVidia 9800GT.

Writing an xorg file will help? I tried sudo nvidia-settings and Save to X Configuration file showed segmentation fault.

---

### Post by livizy on 2010-04-03
> **arundracula said:**
> Thanks. It worked.

But now, I can't enable the visual effects to medium or maximum.. It shows Desktop effects could not be enabled.. Previuosly it was working. My graphic card is nVidia 9800GT.

Writing an xorg file will help? I tried sudo nvidia-settings and Save to X Configuration file showed segmentation fault.

I think that the gnome-shell replace the compiz ,so you lost your visual effects.
And I suggest you install a app called "fusion-icon" in order to swith to compiz when you are in gnome-shell.

---

### Post by arundracula on 2010-04-04
I deleted the Screen section from xorg and rewrote xorg from nvidia control panel. Now all problems are solved..

Thanks to everyone

---

### Post by blackest_knight on 2010-08-19
Anyone tried gnome-shell with ubuntu-netbook remix in lucid its so good :)
a perfect compromise between netbook and desktop. Gnomeshell lists apps alphabetically but if you open a second screen you get the menu's from netbook interface.

Unfortunately gnome applets don't appear to be an option but its very clean and uncluttered

---

### Post by Harry33 on 2010-08-21
> **alex_kent_18 said:**
> Hi,
Anyone knows how to start Gnome shell automatically after logged in?
I couldn't find an article though I searched around Internet about this. 
FYI, my ubuntu version is 9.10 beta.
Thanks in advanced.

The correct way to automatically start gnome-shell is to install package gnome3-session. That package is in mavericks official repos. You can at least install it in Lucid (10.04), and perhaps in Karmic too.

This way you can choose from the login screen either gnome3 (gnome-shell) or ubuntu desktop envoronment (gnome-panel).

---

