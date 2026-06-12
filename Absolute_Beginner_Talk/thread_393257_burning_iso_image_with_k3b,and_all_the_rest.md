---
title: "burning iso image with k3b,and all the rest"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Albert E. on 2007-03-25
Hi everyone,

I've being using (trying to use) ubuntu for several weeks now and i'm getting frustrated with all the problems i encounter at every step.

First,the software for the printer hasn't got all the options I have with the Windows SW(tried more than one programs) - like printing on both sides,etc.

Then I couldn't find a "normal" program to scan pictures (tried several,here too)- quality is bad,no option to edit the image -just zoom in/out available.

Today after i installed some updates the "log off", "terminal" and "help"buttons stopped responding so i had to restart in the rude way ,then they were fine -but it was all the same with Windows :(

And my question now actually is how to burn an iso to a disc (the file is an ISO already)????
I 've got K3b,it looks really great,i load the image,press "start" and 10-11 seconds later i get a "Cdrecord has no permission to open the device".

What permission is the thing talking about??? And which device? 

Please tell me that it is all because i'm such a noob and that ubuntu is much much better than windows (or other linux distros) because that hope is the only reason i still have it :(

---

### Post by PartisanEntity on 2007-03-25
If you mean the Ubuntu iso then yes, it is already in the iso format when you download it and most CD burning applications will know how to use it.

How did you install k3b and how are you launching it?

---

### Post by Albert E. on 2007-03-25
No ,it's not the ubuntu iso,it's a live CD for another distro.

I installed k3b just like all other programs - Applications -> Add/Remove. That is the first thing i am trying to burn with it,so i have no reason to believe that the program is OK. It's the fact that that is the third program with which i am trying that is making me think there is something else wrong...

---

### Post by nudnik on 2007-03-25
> **Albert E. said:**
> No ,it's not the ubuntu iso,it's a live CD for another distro.

I installed k3b just like all other programs - Applications -> Add/Remove. That is the first thing i am trying to burn with it,so i have no reason to believe that the program is OK. It's the fact that that is the third program with which i am trying that is making me think there is something else wrong...

You should be able to open K3b, and click on the ISO through the K3b browser. That normally activates the K3b ISO burning software, wait a minute or two for it to verfy the integrity of the file (scroll down the window which displays file info and you will see a progress bar making its way accross the screen) , set the burning speed if you wish, press "burn" and you should be done.

It sounds as though you may have installed K3b as something other than root, or you have somehow logged yourself in as someone other than your usual ID (I hate it when I'm not myself)

The "device" in question is your burner and the program attemting to open it is used in conjunction with K3b, which is totally normal.

---

### Post by Albert E. on 2007-03-25
I did it - chose speed,and all those things,waited for k3b to check the file,all looked fine. The burning process started and in 11 seconds there was that permission thing.
I tried staring k3b from a terminal: sudo k3b. It started,but there were error messages displayed in the terminal. That one time i got beyond those 10 secs, but there was an error after the first 33MB. 

I can't install any program unless I enter the root password,so i can't have installed it as another user.  Why do I have to run k3b as root  in order to get it working? Will it help if i change the permissions of the program? Or of the burner so that all burning programs can use it??

---

### Post by jeffathehutt on 2007-03-25
You shouldn't have to use k3b as root, so something must be wrong with the setup.

Check to make sure your user has the permission to use the device:
- Go to System->Administration->Users and Groups.  Highlight your username and click Properties.  Click on the User Privileges tab at the top, and make sure there is a checkmark by Use CDROM Devices.

---

### Post by Sweet Spot on 2007-03-25
Are you using the Gnome or KDE desktop ? In Gnome (which I use) all you have to do is right click on the ISO in question, and choose burn to disc. I do this constantly with movies and live CD's. Has never failed me.

---

### Post by Albert E. on 2007-03-25
Sorry for posting the same thing twice, i hadn't noticed.

I can run k3b as a user,but the burning process doesn't go beyond the eleventh second.The "CDROM devices" was marked.

I tried what you say you do,Sweet Spot, and got an "error" in the message bar the first time. The second it was "completed" in less than 15 seconds and the CD was empty :(

---

### Post by okubricko on 2007-04-12
I was having the same problem with a USB burner.   It turned out the problem was with the ownership of sg0

I had to do the following sudo chown root.cdrom sg_x_ (x being the number of your drive)

after that I had no problem burning.

---

### Post by leumicard on 2007-05-26
Try to use kde and see if the problem occur 
k3b is made for k3b not for gnome

---

