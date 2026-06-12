---
title: "Start up Applications--too many or about right??"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-21
I'm wondering if the items I have enabled on startup are all correct or not. I am trying to free up some memory--all I have is 256 M RAM, and this new dvd recorder prefers more than that. Anyway don"t know if shutting down some of the un-needed startup items will help or not. Here is a screenshot of my start-up items. Really wondering about the three different Actions schedulers. Anyway any help would be appreciated. The reason for the post is that when I hook up the dvd (internal installation) I get a solid hd indicator light on my tower, and when I disconnect it the light goes back to normal. Thanks for the help.

---

### Post by ahaslam on 2007-01-21
Shutting down unneeded services may save a couple of megs, but won't make a big improvement. Regarding the schedulers, I don't run any but most people may wish to keep kron.

The best way to free up some ram is to switch to a lighter DE, I highly suggest xfce or openbox for a real difference. You don't have to use it at all times, it's just a case of logging in to the desired DE for your task.

Tony.

---

### Post by jerrynewt on 2007-01-21
Some of you think you are newbies--I can't even figure out how to post a screen shot!! Need some directions please--Thanks still!!

---

### Post by jerrynewt on 2007-01-21
Thank you for the quick reply--sounds good. I'll give it a try. Still can't figure out how to post a screen shot (red faced), but will keep trying. Thanks again

---

### Post by Praxicoide on 2007-01-21
It's in the applications----->accessories tab, on your bar.

As for xfce, you can try typing the following in the terminal (also in the accessories menu)

```
sudo aptitude install xubuntu-desktop
```

then close session, and log back in choosing Xfce.

---

### Post by ahaslam on 2007-01-21
Use **sudo aptitude install xfce4 thunar** instead, wont screw up the artwork & you'll save a few meg ;)

PS. regards the screenie, when editing a post click 'Go Advanced' you'll then see a little paper clip icon in the top ;)

Tony.

---

### Post by Shatrat on 2007-01-21
To post a screenshot use the Take Screenshot thingy he talked about in the Applications menu and then in the Advanced posting button down below and use the little paper clip thingy to attatch the image.  It will let you specify the file on your computer and then you upload it through the web interface and it will show up as attached to this post.

---

### Post by oilchangeguy on 2007-01-21
please advise the brand, and model of your dvd burner. i'd like to check out it's system requirements. because there's no way it should be killing your computer. also did you try what i suggested in your previous thread on this subject?

---

### Post by jerrynewt on 2007-01-21
Thanks guys-- this forum is the best.

---

### Post by jerrynewt on 2007-01-21
The dvd burner is HP LightScribe dvd 840. Specs say minimum requirements are 256 RAM-Pent 111 800Mhz processor. I have 256 RAM, AMD Athlon 700Mhz processor--don't know if that is creating the problem or not. Yes tried the suggestions and no difference. The dvd is on different ide chnl than hd, and both cd and dvd burner are set to cable selection.

---

### Post by Shatrat on 2007-01-21
Are you having trouble with the burner? Have you tried burning a disk?
I imagine those are the requirements for using the burner in windows XP, and windows XP in less than 256 mb if ram is probably a non-starter with or without the burner.

---

### Post by oilchangeguy on 2007-01-21
if those specs are correct, then you've found your problem. your computers cpu doesn't have the power to run this drive. i'd return it, and see if you can locate one with lower system requirements (no light scribe, just burner). not sure what you'd run to see all the running processes (like in xp, ctrl-alt-del, shows all the running processes) so you can see what's maxing out your cpu.

---

### Post by jerrynewt on 2007-01-21
Ok guys thanks for the guideance-Think I'll get another dvd burner like you said. This double layer burner is just too much for the old comp. I can up the RAM to three sticks of 128 Mb and that is all it will take without some major overhaul (it has two 128Mb chips in now). That is according to HP (Compaq) customer service.

---

### Post by %hMa@?b&lt;C on 2007-01-21
do you have DMA enabled?
sudo hpdarm -di /dev/dvd

---

### Post by oilchangeguy on 2007-01-21
dma won't make any difference. his computer does not meet even the min. requirements to run this drive.

---

### Post by jerrynewt on 2007-01-21
I am using system monitor to look at the cpu usage and processes. With hdd light constantly on the cpu usage is between 9 and 12 % constant and memory usage is about 63%. Under devices tab I see /dev/hda1--directory / --type ext3 --total space 30 Gig --used 9%.

---

### Post by oilchangeguy on 2007-01-21
you'd probably be better off just replacing the drive. because any way you slice it, your computer does not meet the min. requirements for this drive. if there's a computer store in your area that sells used parts, you can get a stick of 128mb ram cheap. but that still won't change the cpu not being at least 800mhz. (pull a stick of ram to make sure if it's pc100 or pc133 before you purchase more)

---

### Post by jerrynewt on 2007-01-21
Yeah kind of figured I would have to get downgraded dvd recorder. Just a thought- I have a dvd recorder in my Gateway machine and it's not lightscribe. I might try switching them out and see what happens although the cpu processor problem will be the same. Oh well guess I'll just bite the bullet and get another writer more suited for the old machine. Can't tell you how much your input has  helped guys. Looking forward to the day I can say goodbye to windoz forever!!! Thanks again.

---

