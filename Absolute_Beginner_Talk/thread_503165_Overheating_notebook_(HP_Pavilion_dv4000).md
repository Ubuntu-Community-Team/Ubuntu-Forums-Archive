---
title: "Overheating notebook (HP Pavilion dv4000)"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by theraj on 2007-07-17
Here is my problem:

My notebook heats up way too fast for the amount of processes running (not too much).  I am using Ubuntu 7.04 Feisty Fawn.  My notebook is a HP Pavilion dv4030us (1.6 gHz Pentium M, 1.25 GB RAM, 100 GB hardrive with just Ubuntu installed). I believe my fans are working (I can hear them whirring). The reason why this issue is particularly troubling to me is two-fold: First, the notebook overheats to the point that it shuts down.  Second, this was not a problem at all when I had Windows XP a month ago.  I googled this issue and found a lot of people reccommending vaccumming the fan vents, but this is not the issue for me, as my notebook used to work fine on XP.

I have read some material on Ubuntu's inability to regulate CPU usage like Windows does, is this true?  Is there anything I can do to fix this problem?

Thanks in advance.

---

### Post by reset3x on 2007-07-17
Vacuuming did in fact help me with this... Also I read somewhere that Gutsy will have kernel improvements for issues like this and also battery life...

---

### Post by Rocket2DMn on 2007-07-17
You should indeed clean out your fans, you may want to even pop off the keyboard so you can get behind the fan.  I did this to my laptop last week and cleaned out a ridiculous amount - it dropped my CPU temp by 10 degrees Celsius on average.
Also, you will probably want to enable CPU frequency scaling.  I forgot how to go about this off the top of my head, I'll look briefly though.

EDIT: Here is a start: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#CPU](http://ubuntuguide.org/wiki/Ubuntu:Feisty#CPU)
Run a forum or google search and you will find more.  Make sure you take into account your processor type.

---

### Post by theraj on 2007-07-17
> **Rocket2DMn said:**
> 
Also, you will probably want to enable CPU frequency scaling.  I forgot how to go about this off the top of my head, I'll look briefly though.

EDIT: Here is a start: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#CPU](http://ubuntuguide.org/wiki/Ubuntu:Feisty#CPU)
Run a forum or google search and you will find more.  Make sure you take into account your processor type.

Will computer scaling effect performance at all?  I would not want to be handcuffing the potential computing power of my noebook.  Thanks for the info.

---

### Post by Rocket2DMn on 2007-07-17
Scaling slows down your processor clock speed when it's not being used.  This saves on battery power as well as heat output.  Most laptops in the last few years have this functionality.  You should not notice a loss in power since the speed will kick up when the processor is needed.  It may also kick down the processor speed if your laptop is in immediate danger of overheating, rather than having to shut the computer down.
This means overheating can still be a problem, but it should be OK when it's sitting idle or getting minimal to moderate use.
I feel your pain, I have a Dell 600m that has had major heat problems, esp. when I work the processor.  I also use a cooling pad and often have a large fan pointed at me and my computer during the summer since I have no A/C in Los Angeles.  However, Ubuntu has actually helped with the heat ouput somewhat once I get scaling setup.

---

### Post by rscott5 on 2007-07-17
I spent about 3 years working in a Computer Repair shop and on a few occassions I came across some HP laptops that had overheating problems like this where they would get so hot that they would shutdown. The strange part was that they worked fine when brand new, then eventually started having this problem. I contacted HP a bunch of times and between talking to them and sifting through forums, I found that a couple of their laptop models have known overheating problems where the fans simply cannot handle the heat output. I honestly can't remember the models of those laptops I came across, but I'm wondering if you switching to Ubuntu and having the overheating issue was just coincidence.

Sorry my post isn't exactly helpful, but I figured I'd just put in my 2 cents. Best of luck to you.

---

### Post by Rocket2DMn on 2007-07-17
My buddy's HP laptop actually just kicked the bucket a few weeks ago.  He would boot it up and then it would shut itself down due to overheating before the computer even finished booting.  We think it was some sort of power issues, but it wouldn't help to clean out those fans - you need all the airflow you can get.

---

