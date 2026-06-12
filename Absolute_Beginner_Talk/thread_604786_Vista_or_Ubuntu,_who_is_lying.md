---
title: "Vista or Ubuntu, who is lying?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2007-11-06
Hi was trying to see the memory of my graphics card, but i still to be getting different answers depending on whether i use Vista or Ubuntu.

Following this guide: [http://happylinuxthoughts.blogspot.com/2007/10/how-do-i-get-root-access-in-ubuntu.html](http://happylinuxthoughts.blogspot.com/2007/10/how-do-i-get-root-access-in-ubuntu.html)
Ubuntu says this:
[http://img100.imageshack.us/my.php?image=screenshotmiqianmiqianldg1.png](http://img100.imageshack.us/my.php?image=screenshotmiqianmiqianldg1.png)    

Whereas Vista says this
[http://img100.imageshack.us/my.php?image=capturevistaxs7.jpg](http://img100.imageshack.us/my.php?image=capturevistaxs7.jpg)

Who is right?

---

### Post by Happy_Man on 2007-11-06
In your case, Vista happens to be telling the truth, but I think that is only because you didn't enter the proper command. 

Just to break it down for you:

512 MB of dedicated RAM living on the graphics card

256 MB shared RAM it's using that's part of your computer's RAM storage.

---

### Post by oilchangeguy on 2007-11-06
> **Falc7 said:**
> Hi was trying to see the memory of my graphics card, but i still to be getting different answers depending on whether i use Vista or Ubuntu.

Following this guide: [http://happylinuxthoughts.blogspot.com/2007/10/how-do-i-get-root-access-in-ubuntu.html](http://happylinuxthoughts.blogspot.com/2007/10/how-do-i-get-root-access-in-ubuntu.html)
Ubuntu says this:
[http://img100.imageshack.us/my.php?image=screenshotmiqianmiqianldg1.png](http://img100.imageshack.us/my.php?image=screenshotmiqianmiqianldg1.png)    

Whereas Vista says this
[http://img100.imageshack.us/my.php?image=capturevistaxs7.jpg](http://img100.imageshack.us/my.php?image=capturevistaxs7.jpg)

Who is right?

gee, here's a thought. either google the model of card, or go to the makers website. don't look to your operating system for these types of answers.

---

### Post by Arthur Archnix on 2007-11-06
Are you sure that was the right link?

I'd go with windows. But make sure you've got the right driver installed for your nvidia card, or else Ubuntu may not be seeing all of your memory.

---

### Post by Falc7 on 2007-11-06
Which command should i have entered?

I tried googerling the video card, but seems they come in either 256 or 512 mb versions, at least thats how i understand it.

Yep, according to the update manager i have enabled the latest nvidea driver

---

### Post by stchman on 2007-11-06
> **Falc7 said:**
> Hi was trying to see the memory of my graphics card, but i still to be getting different answers depending on whether i use Vista or Ubuntu.

Following this guide: [http://happylinuxthoughts.blogspot.com/2007/10/how-do-i-get-root-access-in-ubuntu.html](http://happylinuxthoughts.blogspot.com/2007/10/how-do-i-get-root-access-in-ubuntu.html)
Ubuntu says this:
[http://img100.imageshack.us/my.php?image=screenshotmiqianmiqianldg1.png](http://img100.imageshack.us/my.php?image=screenshotmiqianmiqianldg1.png)    

Whereas Vista says this
[http://img100.imageshack.us/my.php?image=capturevistaxs7.jpg](http://img100.imageshack.us/my.php?image=capturevistaxs7.jpg)

Who is right?

My dad has an HP laptop with a GeForce 7600 Go video card and it has 256MB of RAM as well.  The 7600 Go has 256MB of dedicated memory, not shared.

What model is your laptop?

---

### Post by stinger30au on 2007-11-06
if the video card is inside a desktop pc, remove the cover off the pc and look at the card. there is usually a sticker on the card telling you the make/model/ram

---

### Post by Falc7 on 2007-11-06
Unfortunately mine is a laptop so i can't open it up and see

My laptop is an hp pavilion 9000 series, specifically this one 
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=120168580822&ssPageName=STRK:MEWN:IT&ih=002](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=120168580822&ssPageName=STRK:MEWN:IT&ih=002)

Could someone clear it up for me then, did this guy sell me the right laptop? Does it have 512 or 256mb of ram?

---

### Post by aidanr on 2007-11-06
lspci doesn't report the video memory (or at least the correct video memory) for me either but nvidia-settings does.

---

### Post by skymera on 2007-11-06
its bound to be a 256mb.

i never known a 512mb unless its a gaming laptop, which i doubt.

and the extra 512mb is coming from your RAM not the graphics itself :wink:

---

### Post by Falc7 on 2007-11-06
no one can agree :)
Is anyone absolutely sure?
Or should i phone some company or something?
I'rd just like to make sure that the ebay seller gave me what he said.

---

### Post by Arthur Archnix on 2007-11-06
You've had the answer for a while now. Vista is telling the truth. Vista is correct. 99.7% sure. For 100%, open the case and get the card information.

---

### Post by skymera on 2007-11-06
768MB in a laptop?

thats a joke, the nVidia 8800GTX is 768mb and no way that will fit in a laptop,
if its shared graphics its defo a 256mb card.

---

### Post by dhobbs on 2007-11-06
Install the nvidia-settings package and it should tell you what's going on in your card.

After doing my own searching on the interweb it looks like the basic Geforce Go 7600 comes with 256 MB of onboard RAM.

Having worked little to none with Vista I'm far from an expert but the little experience that I do have leads me to think that it doesn't know its head from its foot when it comes to graphics drivers and video card recognition.  If you can find the model number than you will know exactly what hardware version you got of the card.

---

### Post by Arthur Archnix on 2007-11-06
Did you look at the link?

[http://img100.imageshack.us/my.php?image=capturevistaxs7.jpg](http://img100.imageshack.us/my.php?image=capturevistaxs7.jpg)

512MB dedicated video. 256 shared. 7odd total.

The GeForce Go comes in a 512MB model.

What more proof do you need?

---

### Post by skymera on 2007-11-07
ive only read that card comes in a 256mb model.

---

### Post by PmDematagoda on 2007-11-07
I think skymera's, right, I found the laptop specifications and it says:-

> Video Graphics and
Video Memory
&#8226;
NVIDIA GeForce Go 7600 with up to 256MB of
TurboCache&#8482; Video Memory OR
&#8226;
NVIDIA GeForce Go 7600 with up to 512MB of
TurboCache&#8482; Video Memory

So I think it is Ubuntu that is right when it says that the dedicated memory is 256Mb.

If anyone wants to check the specifications themselves, they can do so here:-

[www.hp.com/hpinfo/newsroom/press_kits/2007/mobilitysummit/ds_dv9000t.pdf](www.hp.com/hpinfo/newsroom/press_kits/2007/mobilitysummit/ds_dv9000t.pdf)

---

### Post by Arthur Archnix on 2007-11-07
1. The Ge Force Go 7600 comes in a 512 model. 

[http://www.google.ca/search?hl=en&q=geforce+go+7600+512&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=geforce+go+7600+512&btnG=Google+Search&meta=)

2. Those saying Linux is right are - perhaps for the first time ever - saying that Linux Nvidia drivers are better than Windows. 

I don't even know if the OP is still here, but if so they should install the Nvidia binaries and use that to determine video card ram. Not lspci. And anyway, windows Nvidia drivers are better and more accurate.

---

### Post by NeoLithium on 2007-11-07
It's a 512MB video card.  The dedicated memory is what you should look at :)

---

### Post by Falc7 on 2007-11-07
Yep still here
How would i install the nvidia binaries?

Would this be it?

[http://mandrivausers.org/index.php?showtopic=4567](http://mandrivausers.org/index.php?showtopic=4567)

@neo, yep i'm beginnging to think 512 it is, awesome :-D

---

### Post by Arthur Archnix on 2007-11-08
No, those are Mandriva instructions. They might work, but you're better off trying it the Ubuntu way first.

First, try enabling the nvidia drivers through your restricted drivers manager. Only if that doesn't work should you then try this, which is a little more advanced:

[http://forum.linux-hardcore.com/index.php?topic=1222.0](http://forum.linux-hardcore.com/index.php?topic=1222.0)

You might also try searching the forum for other how-to's on getting the Nvidia driver up and running.

Oh, and it's possible it's already installed and up and running. In which case you just need to take a look around your preferences and such looking for the nvidia settings manager. I don't have nvidia, so I can't be more specific.

---

