---
title: "Absolute beginner reinstall"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by F Junk on 2005-09-23
Hello guys,
I am an absolute Linux and Ubuntu beginner.  :roll: 

I am trying to install my wifi card (Linksys WPC54G on a Vaio laptop).
I have tried many options, followed many tutorials, etc.
Now I still don't have the answer, but wonder if all the conding, sudo-ing etc, did not wreck my install.  ](*,) 

**Is there a way to clean up what I did, to start anew?** just so I'm sure what I do next works...

And if anyone has a *really good* how-to for beginners on how-to install the drivers (ndiswrapper) and how-to wpasupplicant, I'm interrested...

Other than that, well, I'm so glad I lost Win XP  \\:D/ 
This still needs to get a bit more user friendly (I mean, we got used to Microsoft, but I still find XP a tad more intuitive...)

Cheers,

F

---

### Post by fordfan753 on 2005-09-23
ndiswrapper is easy when you know how. First thing, install ndiswrapper-utils and wireless-tools.
Next, Get the .inf file out of the Windows drivers, and any other files that were in the folder or .cab, leave these files in the same folder or as they came. Next....
```
sudo ndiswrapper -i driver.inf
```
Insert your card, then
```
sudo ndiswrapper -l
```
(That's a lower case L for list)
You should see a thing that lists the driver, then says "driver detected, hardware detected" you're almost home and hosed!
Lastly...
```
sudo modprobe ndiswrapper
```
This will load the ndiswrapper module into your kernel, to get this to happen on boot add "ndiswrapper" into /etc/modules .
If your computer can see the card, but can't connect to anything you may have to run the dhcp client to get an IP address.
```
sudo /sbin/dhclient
``` 
If you need more help just ask!

---

### Post by fordfan753 on 2005-09-23
Interesting...I was just looking through synaptic, and Breezy actually has a GUI package aimed at making ndiswrapper easier! If you have Breezy try installing it, it's written in Python, and has a GTK frontend (does that make sense? I'm no programmer) so it has no major dependencies apart from python and ndiswrapper-utils. I haven't installed it, but it looks ok if you're having trouble with ndiswrapper, it is called ndisgtk.

---

### Post by F Junk on 2005-09-23
Thanks!

The ndiswrapper is the easiest part, though :)
I kinda figured it out (after multiple head banging sessions) already.

Regarding wpasupplicant, I read that it is included in Ubuntu in the Universe package?
what does that mean?
I tried the usual apt-get thing, but it said I don't have wpasupplicant anywhere...

Thank you for your help  ;-)

---

### Post by fordfan753 on 2005-09-23
Ahhh...universe stuff.
Ok, quick lesson....packages (stuff you get through synaptic) are found in repositories (big servers with lots of cool stuff)
There are different repositories.
So as not to confuse people, and to make their job easier only the essential repositories are activated in your Ubuntu.
These are the main repositories.
There are various other repositories, such as the universe, and multiverse repositories. Multiverse is not for everyone, but universe is really awesome.
To get universe all you have to do is....
```
sudo gedit /etc/apt/sources.list
```
and remove the # from the start of the following lines in the file....
```
# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
```
Then type
```
sudo apt-get update
``` 
Now search synaptic again, and you should have extra stuff in there, including the wpa package you want.

---

### Post by F Junk on 2005-09-23
You rock!
thanks for that, I was getting a bit frustrated.

You know, like when you get a new toy but have no idea how to make it work.

I'll have to try that tonite.

Again, thank you!

---

### Post by fordfan753 on 2005-09-23
[QUOTE=F Junk]You rock!
thanks for that, I was getting a bit frustrated.

You know, like when you get a new toy but have no idea how to make it work.

I'll have to try that tonite.

Again, thank you![/QUOTE]

No problem, I know all too well what it's like to have the new toy, but have no idea how to use it.

---

### Post by F Junk on 2005-09-27
Just to follow up on the WPA issue.

It is more or less solved (more than less, I have to admit).

The thing is that on start up, my comp doesn't connect to network.
Moreso, when I first try to launch firefox, it says that I'm not connected.

Then, after a while, the card works.

I assume that, as my laptop is quite old, it takes some time to load all the stuffs and have all peripherials working?

Do you have any idea as to whether this will be affected (in good or bad) by the next version of Ubuntu?

Anyways, thanks alot, I can now focus on the main purpose of this installation: setting my web server.
"Another pair of sleeves" (ed: 'a different ball game') as we say in France :)

---

