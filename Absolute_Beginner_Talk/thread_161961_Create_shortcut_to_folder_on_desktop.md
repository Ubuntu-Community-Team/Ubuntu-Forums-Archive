---
title: "Create shortcut to folder on desktop?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by Danny Boy on 2006-04-18
There is probably something really simple that I'm missing. 

I have a folder in my home directory called "stuff" how do I create a shortcut to that directory on my desktop? I've already tried creating a launcher and typing in the path. When I double click on the icon I get it asks me if I want to execute or view the file. I've tried both and it does nothing. 

Also, how do I create a shortcut to the trash on my desktop?

Thanks in advance, 

Dan

---

### Post by indytim on 2006-04-18
For creating shortcuts to folders , using Nautilus select the folder, using the right mouse button <copy>.  Go to your desktop and right mouse click <paste>.

For creating the traditional trash can on the desktop, there is an app via the repository called gtweakUI.  It'll allow you to do a lot of different things along with putting a trash can on the desktop.

:cool: 

IndyTim

---

### Post by sYs^ on 2006-04-18
Try this:

Opem up a terminal and

```
ln -s /home/your_username/stuff /home/your_username/Desktop/stuff
```

Edit: Ok, I was slow :D Then just an alternative way :>

---

### Post by Danny Boy on 2006-04-18
Thanks guys, 

  I actually found an way to make the shortcut. Right click > Make Link then I dragged the link to the desktop. So simple, yet I missed it. 

Tim, Just FYI the copy/paste combo copies the entire folder and it's contents making a double couple on your hd.

Other than that I'm having fun with gtweak as we speak. :mrgreen:

---

### Post by GarethMB on 2006-04-18
[QUOTE=indytim]For creating shortcuts to folders , using Nautilus select the folder, using the right mouse button <copy>.  Go to your desktop and right mouse click <paste> 

IndyTim[/QUOTE]Thats actually putting those files in the desktop. Taking up twice the space...

---

### Post by zugu on 2006-04-18
So, how do we create a shortcut to a folder on desktop?

---

### Post by Danny Boy on 2006-04-18
Right click on the folder/file select Make Link then drag the link to the desktop.

---

### Post by xenmax on 2006-04-18
In nautilus, drag the folder you want linked to by middle mouse button [if you dont have middle mouse button, clicking both left and right buttons simaltaneously works] and drop onto your desktop [ even if nautilus is maxmized, drag and hold near workspace and it should show desktop] and it will open a menu with options for move/copy/link . Select link option.

---

### Post by aysiu on 2006-04-18
Middle-click-drag it to the desktop and select **link here**.

---

### Post by hito1 on 2006-05-05
[QUOTE=aysiu]Middle-click-drag it to the desktop and select **link here**.[/QUOTE]

Worked really well, but how to change the icon so that it doesn't show the lockpad?

Thanks.

---

### Post by seshomaru samma on 2006-05-06
[QUOTE=Danny Boy]There is probably something really simple that I'm missing. 

I have a folder in my home directory called "stuff" how do I create a shortcut to that directory on my desktop? I've already tried creating a launcher and typing in the path. When I double click on the icon I get it asks me if I want to execute or view the file. I've tried both and it does nothing. 

[/QUOTE]

When you create a Launcher , theres a small tab (under where you write the path) where you can choose the type of link. The default is 'application', thats why it asks you if you want to execute it. Choose 'link' instead and your launcher will work fine.

---

