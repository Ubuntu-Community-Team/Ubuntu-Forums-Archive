---
title: "Problems with OS"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Eddy Van Halen on 2007-07-11
Hello again.

I've got some problems now after using Gparted.

I'm not sure what cause that, I deleted linux swap and ext3 ones.

And then added em as fat 32 - (actually no one told me so i wasnt sure if thats the right one)

Then, when i restart pc or turn it off and turn it on again. There are some error and i dont get a list to choose from what to load , at this case it should be windows xp.

can you help me? and tell me what i should've done or what ive done wrong.

Also before i had Two hard drives as now except theyre devided. How could I join em again, if ya get what i mean.

[http://img373.imageshack.us/img373/2151/screenshotls8.png](http://img373.imageshack.us/img373/2151/screenshotls8.png)

---

### Post by LaRoza on 2007-07-11
Did you delete the Linux partition?

If so, you lost grub. Use the Super Grub Disk to restore the MBR for Windows.

---

### Post by Espreon on 2007-07-11
Was Linux previously on the ext3 partion?!? If so than GRUB can't load properly, so you are gonna hafta reinstall Ubuntu, and uninstall GRUB from within Ubuntu. Search for a tutorial or something on howto uninstall GRUB properly.

---

### Post by davidjmayo on 2007-07-11
OK what are you trying to do?

Do you want to have a dual boot with ubuntu or were you trying to go back to only windows?

Not sure if the other guys looked at your screenshot. You have something on 3 partitions probably windows and some data and I guess you don't want to lose that.

Be careful before you even think about doing anything else. It might be an idea if you did a little research before jumping in doing things like you have. I quote you  "actually no one told me so i wasnt sure if thats the right one"

Now post back CLEARLY what you are trying to do and wait for some advice or you will get into an even bigger mess than you have already. 
I don't understand what you are trying to do with all those partitions!!

EDIT (update):
I just saw another of your posts (how do you delete linux [http://ubuntuforums.org/showthread.php?t=498354](http://ubuntuforums.org/showthread.php?t=498354)). looks like you wanted to remove ubuntu. Now you have partitions all over the place (I have seen 3 screenshots in your different threads and am getting some idea of what you are trying to do). Wait before you try anything. In one of the replies to you is a link to an example of someone who had big problems from repartitioning and using different software to do it. Don't worry if you didn't read it or don't remember or don't understand it. People here can help you. Please can you tell me what you are trying to do? Then we can go from there.

---

### Post by Eddy Van Halen on 2007-07-11
> **davidjmayo said:**
> OK what are you trying to do?

Do you want to have a dual boot with ubuntu or were you trying to go back to only windows?

Not sure if the other guys looked at your screenshot. You have something on 3 partitions probably windows and some data and I guess you don't want to lose that.

Be careful before you even think about doing anything else. It might be an idea if you did a little research before jumping in doing things like you have. I quote you  "actually no one told me so i wasnt sure if thats the right one"

Now post back CLEARLY what you are trying to do and wait for some advice or you will get into an even bigger mess than you have already. 
I don't understand what you are trying to do with all those partitions!!

I want to get rid of linux at the moment and stay with windows until everything is fixed.
Also, I want all the hard drives back as they were (not devided)
[http://img411.imageshack.us/img411/4729/screenshotrd7.png](http://img411.imageshack.us/img411/4729/screenshotrd7.png)

---

### Post by davidjmayo on 2007-07-11
We mis-timed this. When I was editing my reply you sent yours!!

I take it you want to go back to your original windows partition setup.

---

### Post by Eddy Van Halen on 2007-07-11
> **davidjmayo said:**
> I take it you want to go back to your original windows partition setup.

Yes

---

### Post by davidjmayo on 2007-07-11
OK you partitions are the same as they were before only because you show the screenshots from GParted  they say sda1 etc not C: D: etc. and now they are formatted as FAT32 not unallocated space. Actually you may have done yourself a favour as they are ready to use!!

Next step. Can you boot into windows at all 
Don't worry if you say no. We can fix that next.

---

### Post by Eddy Van Halen on 2007-07-11
[http://img165.imageshack.us/img165/5237/screenshot3wc0.png](http://img165.imageshack.us/img165/5237/screenshot3wc0.png)

Right, wait im gonna tel how i am getting on. Im chating to ma friend at the moment , he's helping me out.

what do you think i should do now

---

### Post by davidjmayo on 2007-07-11
You are about to resize your windows partition and delete the 2 data partitions you had before. They had labels like media and acer or something like that. I read you did a backup but are you sure you want to do this??

---

### Post by ev5unleash1 on 2007-07-11
You deleted the linux. The best way to fix it up is reinstalling windows and Ubuntu.

---

### Post by Eddy Van Halen on 2007-07-11
> **davidjmayo said:**
> You are about to resize your windows partition and delete the 2 data partitions you had before. They had labels like media and acer or something like that. I read you did a backup but are you sure you want to do this??

Everything is deleted already, i don't really care. Ive got everything on dvds  what i actually use(cause there's not much space on laptop so i burned em week ago to get some more space for downloading new discographys and so on

---

### Post by davidjmayo on 2007-07-11
So
1)> Right, wait im gonna tel how i am getting on. Im chating to ma friend at the moment , he's helping me out. what do you think i should do now


 Why did you ask what to next

2) You carry on regardless anyway so haven't learnt anything from this

3) You have wasted my time without a thank you and you say I don't care it's deleted.  I could have been spending my FREE  TIME (as in I'm not paid for this nor is anyone else on this forum) helping other people.

---

### Post by Eddy Van Halen on 2007-07-11
> **davidjmayo said:**
> So
1)

 Why did you ask what to next

2) You carry on regardless anyway so haven't learnt anything from this

3) You have wasted my time without a thank you and you say I don't care it's deleted.  I could have been spending my FREE  TIME (as in I'm not paid for this nor is anyone else on this forum) helping other people.

I've deleted it before you told me! Im talking to my friend which one is helping me with it too

right i think ive done everything i had to now im gonna try to instal os

---

### Post by Eddy Van Halen on 2007-07-11
> **ev5unleash1 said:**
> You deleted the linux. The best way to fix it up is reinstalling windows and Ubuntu.

RIght, 

That's what I tried

I deleted everything , by saying i dont care i meant the stuff that are in em because i backed up most of the important files week ago.

so i was left with two, one was devided into 16gb and the second half 40.

I turned off the pc. and installed windows but after that i still get the problem and message:

grub loading stage 1.5.
grub loading please wait
error 22.

so now im back from where i started.

anyone got advice. What should i do to fix the 'grab' thing?

davidjmayo  - by saying that i meant that i dont care about the files on disks

---

### Post by Eddy Van Halen on 2007-07-11
I think i found a way of fixing it.

But i need to get a proper windows XP cd or 98 :S damn

[http://www.microsoft.com/downloads/thankyou.aspx?familyId=e8fe6868-6e4f-471c-b455-bd5afee126d8&displayLang=en](http://www.microsoft.com/downloads/thankyou.aspx?familyId=e8fe6868-6e4f-471c-b455-bd5afee126d8&displayLang=en)
is this going to help me? I could write it into a cd and then boot it.

---

