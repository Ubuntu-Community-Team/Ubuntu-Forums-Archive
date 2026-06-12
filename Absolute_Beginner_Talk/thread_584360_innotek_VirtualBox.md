---
title: "innotek VirtualBox"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2007-10-20
Hello,

I deleted VMware because I heard it was not as good as Virtual box. SOOOooo I downloaded Virtual  
box and got the gutsy deb version. I installed it and got all the memory and the hd space all set up even told it to enable the cd etc...etc.. but when I hit start with the os in the cd drive I get this::


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by LaRoza on 2007-10-20
Add yourself to the vboxusers group, as it said.

---

### Post by Medieval_Creations on 2007-10-20
Have you restarted after you installed the VBox deb?

Go into "Users and Groups" and add yourself the vboxuser group.

Then you have to restart your PC.

That should take care of that error the next time you go and try to start VBox.

---

### Post by GSF1200S on 2007-10-20
You can use the following terminal code to get the permissions:

```
sudo chmod 666 /dev/vboxdrv
```

I know there is another code that can be used, and its prolly better to use it, but I cant remember.

I dont mean to jack the thread, but im having to put in the above said code every time I reboot for some reason. I could create a shell script to execute at startup, but theres gotta be another way..

---

### Post by LaRoza on 2007-10-20
> **Medieval_Creations said:**
> **LaRosa** jut be me.  :)


I think you just have to log off.

Did you mean mean "beat" or are you having an identity crisis?

---

### Post by Malice007 on 2007-10-20
I do not see a place to add myself

---

### Post by Malice007 on 2007-10-20
sudo chmod 666 /dev/vboxdrv


That Fixed it, but do I have to type that all the time when I want to run this?

---

### Post by Medieval_Creations on 2007-10-20
After you have selected Manage Groups and found vboxusers.

Select vboxusers and then click properties.

It will then open a sub-window that should have all the users on that PC and you check those you want to give access too.

then after a reboot the new permissions should be applied and your good to go.

---

### Post by GSF1200S on 2007-10-20
> **Malice007 said:**
> sudo chmod 666 /dev/vboxdrv


That Fixed it, but do I have to type that all the time when I want to run this?

Do what Medieval is telling you. Im on KDE, so that command was all I could think of- you would have to put that command in once everytime you restarted Ubuntu. Im on KDE, and I dont know where/if it has a group permissions setting, so Im screwed while I try to figure out how to fix it...

---

### Post by Medieval_Creations on 2007-10-21
> **LaRoza said:**
> I think you just have to log off.

Did you mean mean "beat" or are you having an identity crisis?

No, just meant you beat my by getting your reply in.

---

