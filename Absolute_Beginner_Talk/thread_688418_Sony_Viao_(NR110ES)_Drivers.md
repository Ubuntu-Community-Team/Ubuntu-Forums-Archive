---
title: "Sony Viao (NR110E/S) Drivers"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by kayel_justice on 2008-02-05
Hey guys. I'm noob so pleas heave patience..lol...I have a NR110E/S with originally Vista on it and I wiped it clean with 7.10. Do I have to install new drivers now with the new install? And if so, do I specifically have to use Ubuntu or are other OS Drivers compatible. As you see I need help, I can't wait to start using my new laptop.

Process:
Installed 7.10 Ubuntu
Tried to move files and such from external hard drive to laptop
Did not read.
No Bluetooth
I seems as though my USB ports aren't working, or not reading.

Any suggestions or did anyone else have these problems?

Thanks in advance

---

### Post by kayel_justice on 2008-02-05
Well it seems the the USB ports work, but it just won't read my external hard drive. It was a piece of crap anyway

---

### Post by rkd on 2008-02-05
If there is data on that external drive that you want to use, I think you don't need to give up on it so quickly.

So if you want to get that data, tell us what you saw when you tried to access the external drive.

If you really don't care about the data, it's okay to drop it. We have lots of other people to help. But we'll help you if you want help.

---

### Post by kayel_justice on 2008-02-05
Sure, thanks I would luv to get it working. But I was seriously concerned with the proprietary drivers my system says I'm running.  Under  >System >Restricted Drivers , it says:

"Proprietary Drivers do not have public source code that Ubuntu developrs are free to modify. They run risk to you because they are only available on the types of computer chosen by the manufacturer and security updates to them depend solely on the responsiveness of the manufacturer."

Atheros Hardware Access Layer (Hal). It's running this to make it work properly.

My graphics look fine to me, is this normal?
Also, I'm trying to install compiz. I found a youtube vid, but I do not see compizconfig-settings-manager.
Is there a thread anyone knows of that will help me install compiz cuz I'm a windows user and all I do it double-click usually.

Ah... so many questions...thanks for your patience.

---

### Post by bumanie on 2008-02-05
I think yo go to System --> Applications --> desktop effects.
If you want more options in terminal type
> sudo apt-get install compizconfig-settings-manager

---

### Post by kayel_justice on 2008-02-05
hey.....Sheesh, this is tougher than I thought!.

sudo apt-get install compizconfig-settings-manager = "Couldnt find manager"

OK, so I download compiz 0.4
I did a search for it in terminal,
There's only about like 5 options.
Is there a certain place that the downloaded file should be?

---

### Post by bumanie on 2008-02-05
Try this link [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by rkd on 2008-02-05
Those warnings about proprietary drivers are correct, but probably unnecessarily alarming.  For someone who has come to Ubuntu from Windows, you have come from an environment where essentially all drivers were proprietary to an environment where only a few drivers are proprietary.  

So while it is true that proprietary drivers have a small potential for being dangerous (because you can't know what they are doing), that is nothing new for people coming from Windows, and, overall, you have less exposure to them in Ubuntu.

For people who want to escape the proprietary world entirely, it is good to identify those drivers as being proprietary so those people can avoid using them, but I think the warnings don't need to be quite so strident.

Concerning the error trying to install compizconfig-settings-manager: Go to System->Administration->Software Sources and make sure the universe repository is selected (should be the second item in the first tab) -- long name Community-maintained Open Source software. Then do ```
sudo apt-get update
```Then try the install command again.

---

### Post by kayel_justice on 2008-02-05
Thanks a Lot! I'll get back to you guys to update you on whats going on. Sorry for the late response, I have a 9-5 job and had to go finish work.

OK So i'll try those things out guys and I'll keep you posted!

---

### Post by bumanie on 2008-02-05
While at updating sources lists, do them all at once. go here
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
After that, basically all software you need from the repositories will be available. Sorry, I haven't installed for a while and forget the repositories. I instinctively put them in and forget first time users probably don't know about them.

---

