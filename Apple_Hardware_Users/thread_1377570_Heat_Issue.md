---
title: "Heat Issue"
date: 2010-01-10
forum: Apple Hardware Users
---

### Post by dogturd on 2010-01-10
My MBP 5,3 running 64bit 9.10 gets rather hot during use. If I touch the case near the left speaker and along the top by the screen it is sometimes almost too hot to touch. It gets that hot that when I have shut the MBP down I don't close the lid as I am scared that the hot case will damage the screen when closed together!
 
I'm scared I'm gonna cook the laptop or an egg on it :)

I've been reading some of the posts regarding this mentioning scripts and being able to alter the fan speeds to hopefully solve this problem. 

I'm still new to linux and I don't have a problem running or installing scripts but I need the confidence to do it knowing I am not going to cook the laptop.

1, Can someone point me in the right direction with regards to a linux app (gui if possible) that I can run that will show me fan speed and cpu temp also the graphics card temp if possible? 

2, What script do I need to run to cool the laptop down?

Thanks

---

### Post by mörgæs on 2010-01-10
1) Gkrellm is an option. You could add hddtemp, if you also want to monitor the heat of the hard drive.
2) There are problems with computers overheating in 9.10. Is it also hot with 9.04 on a live CD?

---

### Post by alexmurray on 2010-01-10
For monitoring temperature and fan speeds try [sensors-applet]("apt:sensors-applet")

---

### Post by tgalati4 on 2010-01-10
The melting point of aluminum is 660C so you should be OK.  Those apple engineers know their stuff.

I presume you tried to load lm-sensors?  [http://www.lm-sensors.org/wiki/iwizard/1](http://www.lm-sensors.org/wiki/iwizard/1)

---

### Post by zenspiderz on 2010-01-11
Why is it you just can't install a program that will do the job like with windows.  What is all this terminal crap? Are linux programmers lazy because they don't want to be paid? How hard can it be after you gone to all the trouble of making a program to add some basic link and gui so the user can actually use the damn thing?  I really want to like linux but this is getting ridiculous.  If i buy a car i don't want to have to assemble the engine myself.

---

### Post by llawwehttam on 2010-01-11
> **zenspiderz said:**
> Why is it you just can't install a program that will do the job like with windows.  What is all this terminal crap? Are linux programmers lazy because they don't want to be paid? How hard can it be after you gone to all the trouble of making a program to add some basic link and gui so the user can actually use the damn thing?  I really want to like linux but this is getting ridiculous.  If i buy a car i don't want to have to assemble the engine myself.

As you are new to the forums I will be less harsh to you but still It would be better if you could keep comments like that to yourself.

If you don't like linux and all you can do is complain then don't use it. Simple!

The programmers work really hard to provide free software and I think the way you describe them is very rude.

Read the new to linux link in my signature.

---

### Post by zenspiderz on 2010-01-11
Ok sorry i am just frustrated.  I do think linux is much better than windows.  Actually i HATE windows.  Which is why i am here really.  But i am just completely lost with some linux programs, they don't have a user interface and they don't run and do what they need to do by themselves without a bunch arcane scripting etc etc.  For example i think my pc is running hot and glitching because of that.  so i look on synaptic for a heat monitor program. and low and behold i see that i already have lm-sensors for that.  So where is the menu option for it? Nada.  Ok i install i bunch of other temp sensor progs i find in synaptic hoping that at least one of them will meet me halfway instead of hiding in the basement is a sulk.  But just like lm-sensors there is no menu option no interface nothing.  If it weren't for synaptic manager i wouldn't know the program was there at all.  So linux = 1/2 dozens diffent programs to do the same thing but not 1 user interface between them.  

So i have just wasted 1/2 hour for nothing.  

Bottom line is the world needs linux to stomp windows into the dirt, but linux falis as long as non-geeks can't use it.

---

### Post by mörgæs on 2010-01-11
That's the beauty of open source: Everyone can build and publish a program for a certain task, and everyone can modify it. That gives a lot of competing programs. There is not a monopoly deciding what is the best thermometer for your pc.

Regarding your problem: Gkrellm as I spoke about will collect data from all these sensors and show them on screen. Have you tried it?

---

### Post by zenspiderz on 2010-01-11
Ok i just tried it now and found how to make it display temp.  Thanks that works lovely.

---

