---
title: "Vista/Ubuntu Dual Boot"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by lenswipe on 2007-12-10
hi all

im having booting issues with vista/ubuntu but not in the same way The issues i have is that i tried to follow [this]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")


however at the part where it says about vista/longhorn

> On the "Ready to install" screen, you'll see that Ubuntu now has enough information to commence the installation. In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)". This means that regardless of whether Ubuntu found any user account to migrate, it certainly knows that Windows Vista is installed on the other partition and is aware of it. Click Install.

on my computer it just says Migrate Assistant:<<it should say vista/longhorn here insead of this text but it doesnt>>

it doesnt say vista/longhorn this presumably means that it hasnt detected windows vista and therefore may or may not delete it....

Horrible as windows vista is i need the data on that partition because thats where alot of my files are...

Please dont tell me to back up all my things because i really dont have time.


Please just telll me what i need to do and also if all my data is likeley to be wiped (i didnt choose the "use entire disk option" but the fact that it clearly couldnt detect vista makes me a little unsure.


Please help!!

---

### Post by AnonCat on 2007-12-10
Don't worry about the migration assistant, your Vista partition won't be overwritten even though the migration assistant doesn't see it.  If you want tips on how to successfully install and dual boot Vista with Ubuntu, I'd recommend this website for easy and clear instructions on how to install Ubuntu on a Vista system:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Pay particular attention to the instructions on how to install grub when installing Ubuntu.  For instance, if you installed ubuntu to partition #3, you'd setup grub to install on (hd0,3) instead of the default (hd0).  You'd then use the EasyBCD program for Vista (available off the website above) to configure Vista's bootloader to boot into either Vista or Ubuntu.  It's all explained on that website.

---

### Post by gletob on 2007-12-10
My advice would be just go ahead and install should be fine as long as you did your partitioning right the migration assistant is very buggy and for me has never recognized my windows install

---

### Post by lenswipe on 2007-12-11
I officialy got it working


thanks to everyone who helped...

---

### Post by EnergySamus on 2007-12-11
I am having the same issue! How did you get it resolved!?:popcorn:

Thanks
EnergySamus

---

### Post by lenswipe on 2007-12-11
> **EnergySamus said:**
> I am having the same issue! How did you get it resolved!?:popcorn:

Thanks
EnergySamus

i just ploughed straight ahead...


On the bit for the ubuntu install where it gives u the option of where to install it i just selected Free contiguous space or something like that. Also i reccomend reading [this]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

---

### Post by EnergySamus on 2007-12-11
So basically you:

1:Choosed "Continuous free space"

2:Even though the Migration Assistant didn't show anything, you went for it.

3:Now when you boot, you have the choice to boot into Ubuntu and Windows!


Is this what happened?

Thanks!
EnergySamus

---

### Post by buildsomethingcrazy on 2007-12-11
> **EnergySamus said:**
> So basically you:

1:Choosed "Continuous free space"

2:Even though the Migration Assistant didn't show anything, you went for it.

3:Now when you boot, you have the choice to boot into Ubuntu and Windows!


Is this what happened?

Thanks!
EnergySamus

You play more Super Metroid

---

### Post by EnergySamus on 2007-12-11
Dude, that is totally off topic... I asked a question!
But yes, I have Super Metroid.

---

### Post by EnergySamus on 2007-12-11
Anyway... That last post was weird!
Is that how you did it? 
I really want to install Ubuntu!
Thanks!
EnergySamus

---

### Post by lenswipe on 2007-12-12
> **EnergySamus said:**
> Anyway... That last post was weird!
Is that how you did it? 
I really want to install Ubuntu!
Thanks!
EnergySamus

yes thats how i did it and it works like a deam :) :popcorn: :popcorn:

hope this helps and good luck mate :p

lenswipe

---

### Post by EnergySamus on 2007-12-12
Thanks a lot man!
I am finally going to be able to dual boot Vista and Ubuntu!
I was having the same issue as you, there was no name under the Migration Assistant.
But you gave me some help... I am now unchained from my windows installation!
:KS:KS:guitar::guitar::lolflag::lolflag::):)

Once again, thanks!

EnergySamus


P.S: What are the partitions on your PC?

---

### Post by lenswipe on 2007-12-12
> **EnergySamus said:**
> Thanks a lot man!
I am finally going to be able to dual boot Vista and Ubuntu!
I was having the same issue as you, there was no name under the Migration Assistant.
But you gave me some help... I am now unchained from my windows installation!
:KS:KS:guitar::guitar::lolflag::)

Once again, thanks!

EnergySamus


P.S: What are the partitions on your PC?

rofl no problem man i like to help people whenever i possibly can - gained knowledge from the people on this forum therefore i feel it is my duty as a member of this forum to pass this knowledge on so everyone can benfit :)

[EDIT] I know exactly how u feel about ur windows installation the only reason i havent ditched windows completely is that it supports photoshop and im too lazy to download and configure wine....


in answer to your last question do you mean in size?

if so then im not sure.....



there are already 2 partitons there.

One called vista (C: drive)

and one called winre (E drive) which is about 2GB (i know WTF!?!?!) but thats just how my laptop came

hope this helps :)

[EDIT2] since getting ubuntu i liked it soo much i showed all my freinds at school and now ive supplied them all with copies on CD of Ubuntu i also have a dual boot to setup on 2 laptops and 2 other people just want to run Ubuntu as a live CD ( parental issues with the computer there im sure you all know how it is )  

so this is just a little note to the coders/developers...
[SIZE="6"][COLOR="Magenta"][COLOR="Red"]
**KEEP AT IT YOUR DOING A GOOD JOB AND YOU ARE VERY POPULAR PEOPLE AT MY SCHOOL KEEP UP THE GOOD WORK**[/COLOR][/COLOR][/SIZE]

---

### Post by EnergySamus on 2007-12-12
Thanks!

So your partitions are:

C: Vista
E: Winre
And The partition where Ubuntu is on

Is this right? And another question:

After Ubuntu installs, and it shows the window that tells you to reboot, will Ubuntu eject the CD itself, or will you have to do it manually?

Thank you alot!:popcorn:):P8-)
EnergySamus

---

### Post by Duck2006 on 2007-12-12
> **EnergySamus said:**
> Thanks!

So your partitions are:

C: Vista
E: Winre
And The partition where Ubuntu is on

Is this right? And another question:

After Ubuntu installs, and it shows the window that tells you to reboot, will Ubuntu eject the CD itself, or will you have to do it manually?

Thank you alot!:popcorn:):P8-)
EnergySamus

Yes it will eject the CD.

---

### Post by EnergySamus on 2007-12-12
Thank you lenswipe and Duck2006 for your help.

Now I will be Dual-Booting by Monday!

EnergySamus

---

### Post by lenswipe on 2007-12-15
> **EnergySamus said:**
> Thanks!

So your partitions are:

C: Vista
E: Winre
And The partition where Ubuntu is on

Is this right? And another question:

After Ubuntu installs, and it shows the window that tells you to reboot, will Ubuntu eject the CD itself, or will you have to do it manually?

Thank you alot!:popcorn:):P8-)
EnergySamus

yea the CD ejects itself

also how do u know about the winre partiton i have?

lol

although yes that is correct..

hope this helps :)

---

### Post by Hendrixski on 2007-12-15
> **lenswipe said:**
> 
so this is just a little note to the coders/developers...
[SIZE="6"][COLOR="Magenta"][COLOR="Red"]
**KEEP AT IT YOUR DOING A GOOD JOB AND YOU ARE VERY POPULAR PEOPLE AT MY SCHOOL KEEP UP THE GOOD WORK**[/COLOR][/COLOR][/SIZE]

Thanks :-)

BTW... I used to dual boot and then when I realized that I just wasn't using my windows partition, because it didn't have a lot of the useful programs I needed for work I realized that I wanted to actually put that hard-drive space to good use.  Soon, you'll do the same.  And I'd encourage you to join us in developing stuff for Ubuntu.  It's a lot of fun.

---

### Post by lenswipe on 2007-12-17
> **Hendrixski said:**
> Thanks :-)

BTW... I used to dual boot and then when I realized that I just wasn't using my windows partition, because it didn't have a lot of the useful programs I needed for work I realized that I wanted to actually put that hard-drive space to good use.  Soon, you'll do the same.  And I'd encourage you to join us in developing stuff for Ubuntu.  It's a lot of fun.

i would if i could :)

do i need to learn C#


thanks

---

### Post by EnergySamus on 2007-12-17
> **lenswipe said:**
> i would if i could :)

do i need to learn C#


thanks

Yeah, I would love to do that! :KS
Oh, I used an old computer as a test for the Dual-Boot.
It worked, and it should be running on my computer soon!:)
Ok... It is Monday, and I still haven't done it on my computer. But I will soon!
How do you develop?
Like lenswipe said, do you need to have any knowledge of C# or C++?:lolflag:

Thanks,
EnergySamus

---

### Post by lenswipe on 2007-12-17
> **EnergySamus said:**
> Yeah, I would love to do that! :KS
Oh, I used an old computer as a test for the Dual-Boot.
It worked, and it should be running on my computer soon!:)
Ok... It is Monday, and I still haven't done it on my computer. But I will soon!
How do you develop?
Like lenswipe said, do you need to have any knowledge of C# or C++?:lolflag:

Thanks,
EnergySamus

i can do a little C++ but i left the CD with the tutorial on at my brothers house 4000 miles away across the atlantic ocean so i have to wait till next time before i start again. And as for C# i really dont know about that :)

---

### Post by EnergySamus on 2007-12-17
4000 Miles?! You certainly couldn't walk :lolflag::lolflag::lolflag:
Do you know what program it is?
Thank you for all of your help during the past 2 weeks, it really helped!:KS:guitar:

Thanks,
EnergySamus

---

### Post by lenswipe on 2007-12-20
> **EnergySamus said:**
> 4000 Miles?! You certainly couldn't walk :lolflag::lolflag::lolflag:
Do you know what program it is?
Thank you for all of your help during the past 2 weeks, it really helped!:KS:guitar:

Thanks,
EnergySamus

no probs about the dual boot. The reason the CD is 400 miles away is because my brother lives in canada and i live in the UK - i was over to visit him and while i was over there i bought a book on C++ but i left the CD with the compiler and scource codes in his computer *irritation*

The compiler isnt a big deal but the scource codes were quite useful and i would like to get them back.....


Ill try and get him to send the CD when he sends the christmas parcels.... :D

---

### Post by NateMan on 2007-12-20
there are many good free c++ compilers. in linux there is gcc to compile and kdevelop is a nice gde. in windows you can get a copy of visual basic for free with a license, as long as its for personal use. There are numerous websites that have basic code problems along with tutorials on how to do them. I wouldn't let not having a book stop me!

---

### Post by EnergySamus on 2007-12-20
Thanks for your C++ and C# info. There are a few books at my local library that come with a CD! 
Here is some good news: I installed Ubuntu as a dual-boot with Vista into my main PC!
I really like the GRUB bootloader... It works well when booting multiple OSs.
The only problem that I had is that my main PC (it is a laptop, Acer Aspire 3690!!!) has a Broadcom Wi-Fi... Which means that my Wi-Fi was in the Restricted Drivers section. I connected my laptop to a DSL modem and downloaded the firmware from the Ubuntu Help/Community Documentation site. Now everything is working fine!
Once again, thanks! You have made the last three weeks easier for me... I guess I needed some confidence! The computer is only 4 months old... I didn't want it to break! But it worked!
:KS:KS:KS:KS:guitar::guitar::lolflag::lolflag:

Once again Thanks A LOT!
EnergySamus

P.S. The UK!? That is so cool! I live near San Fransisco, California! I've only been to London once... But I liked it a lot! Wait... right now it must be like 10:00 PM! Have you ever been to San Fransisco? It is quite cold and raining here!

---

