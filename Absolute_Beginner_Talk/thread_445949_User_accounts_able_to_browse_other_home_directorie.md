---
title: "User accounts able to browse other /home directories"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by dcwilliams on 2007-05-16
When I installed Ubuntu I created an admin account. After it was installed I created a second guest like account with limited capabilities. 

When I opened a command prompt, the guest account was able to browse and open files in the /home/<adminuser> account.

Basically, I want to upgrade the RAM in my laptop. I want to create an account so that the technician can boot up and log in to verify that everything is working, but I do not want him to be able to make changes to the system or access my personal files. 

Is there a way to do that?

---

### Post by taurus on 2007-05-16
If you don't want people to view the content of your $HOME directory, just change the permissions.

```
chmod 700 /home/<username>
```

---

### Post by oilchangeguy on 2007-05-16
adding ram is an easy diy (do it yourself) project. unscrew the cover on the bottom of the machine. remove the present ram module(s). install the new one(s) close the cover. reboot, and you're done.
in laptops the ram moduls are usually laying on their sides at a slight angle. and are held in place by a clip on either side. to remove, simply hold the clips out of the way, stand the ram module up, and lift it out of the computer. to install new ram. stand it up it the slot, lay it down in the slot until it clicks in pace. and you're done. repeat if needed, close the cover, and reboot.

---

### Post by Inxsible on 2007-05-16
GUI way to do it would be:

Right click your home folder then

Properties --> Permissions tab

The owner and group will be your username.  In the 'Others' section, Select 'None' for Folder Access
and 'None' for File Access. Click Close and you are done !

---

### Post by Pollywoggy on 2007-05-16
> **dcwilliams said:**
> When I installed Ubuntu I created an admin account. After it was installed I created a second guest like account with limited capabilities. 

When I opened a command prompt, the guest account was able to browse and open files in the /home/<adminuser> account.

Basically, I want to upgrade the RAM in my laptop. I want to create an account so that the technician can boot up and log in to verify that everything is working, but I do not want him to be able to make changes to the system or access my personal files. 

Is there a way to do that?

You can of course do what is recommended in another post, 'chmod 700 /home/<username>'
but some Linux distros have an option to make all new home directories private (chmod 700) when they are created.  Individual users can still change their own permissions if they wish.

I don't believe Ubuntu has this setting for making all new user directories private, I checked and I don't see it.

---

### Post by dcwilliams on 2007-05-16
Thanks everyone.

chmod

Sigh.

I  knew the answer, but didn't know that I knew it. I have used chmod quite a bit, but usually chmod +x.

---

### Post by dcwilliams on 2007-05-16
> **oilchangeguy said:**
> adding ram is an easy diy (do it yourself) project. unscrew the cover on the bottom of the machine. remove the present ram module(s). install the new one(s) close the cover. reboot, and you're done.
in laptops the ram moduls are usually laying on their sides at a slight angle. and are held in place by a clip on either side. to remove, simply hold the clips out of the way, stand the ram module up, and lift it out of the computer. to install new ram. stand it up it the slot, lay it down in the slot until it clicks in pace. and you're done. repeat if needed, close the cover, and reboot.

I have changed ram in an IBM thinkpad. There was 1 small panel on the back for RAM, another for the hard disk, 1 screw, pop the old one out and add the new one in. With the COMPAQ there is only 1 panel on the back, and it has a flexible circuit board there (almost like plastic wrap). Taking off the entire back panel of the laptop looked like quite a job.

---

### Post by LaRoza on 2007-05-16
The previous instructions for installing RAM were correct, but left a lot of room for frustration.

First, find out what kind of RAM you need, a surefire way to do this is to see what you already have.

Then find out what size you want, and if your computer can handle that much, newer computers can handle more than you would buy in most circumstances.

Look out for any special way the DIMMS must be inserted, sometimes certain slots need to be filled before others.

After installing, check to see if your computer detects the increased RAM.

Also, remember RAM cards are very sensitive to ESD, it won't necessarily render them useless, but you could easily damage them unknowingly without taking the proper precautions especially for notebook computers.

---

### Post by louieb on 2007-05-16
> **dcwilliams said:**
>  but I do not want him to be able to make changes to the system or access my personal files. 
Is there a way to do that?
The short answer is [B]no.
[/B]Any tech worth a lick that has **physical access **the computer would be able to see and do whatever they want. I guess you'll just have to stand over his shoulder.

---

### Post by aysiu on 2007-05-16
I agree with louieb.

If the technician is an ethical one, he'll not bother to look at your personal files and just upgrade the RAM.

If he's not ethical and he has physical access to your computer, he can see anything he wants unless you encrypt your files.

---

