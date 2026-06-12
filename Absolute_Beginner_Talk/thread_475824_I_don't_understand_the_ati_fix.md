---
title: "I don't understand the ati fix"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by roeboat72 on 2007-06-16
How do you work the ati fix?

I see the commands but where do you put them.

This is the first linux based OS i've ever used

---

### Post by bone43 on 2007-06-16
> **roeboat72 said:**
> How do you work the ati fix?

I see the commands but where do you put them.

This is the first linux based OS i've ever used

Which fix?

A little more detail please like what page you are looking at :D

The commands go in a Terminal is what i think you are asking that would be
Application->Accessories->Terminal.

---

### Post by roeboat72 on 2007-06-20
its the ati fix about the x#### cards not functioning correctly on 7.04

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

It just has these commands you must enter to fix it but i don't know where you enter them

---

### Post by bvanga on 2007-06-20
You just copy and paste it over or unless you want to type it out.

To open the terminal
Application-->Accessories-->Terminal

---

### Post by Tyke91 on 2007-06-20
I have heard that ENVY is good for solving graphics drivers installation issues... [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by roeboat72 on 2007-06-21
i've tried envy but it didn't seem to work, and for some reason i cannot get the terminal to let me type in my password, since it automaticly asks for it when i enter the first line. It won't let me type in my password the cursor just sits there and blinks.

---

### Post by Motoxrdude on 2007-06-21
> **roeboat72 said:**
> i've tried envy but it didn't seem to work, and for some reason i cannot get the terminal to let me type in my password, since it automaticly asks for it when i enter the first line. It won't let me type in my password the cursor just sits there and blinks.

Type your password normally even though it isn't showing up (it's suppose to do that)

---

### Post by pthib on 2007-06-21
I too have done the fix (The sticky in this forum on how to fix the drivers). I was wondering, how do I verify if the drivers installed correctly and it's working properly.  Also, if I wanted to install beryl after completing those steps, what is the proper way to go about doing it?  Thanks

---

### Post by Hobo Joe on 2007-06-21
> **pthib said:**
> I too have done the fix (The sticky in this forum on how to fix the drivers). I was wondering, how do I verify if the drivers installed correctly and it's working properly.  Also, if I wanted to install beryl after completing those steps, what is the proper way to go about doing it?  Thanks

Once you think you have it, paste the output of 
```

glxinfo

```
That should tell you everything you need to know

As for Beryl, you can install it through synaptic, or to be faster, you could just type:
```

sudo aptitude install beryl

```

Have fun! :)

---

### Post by Motoxrdude on 2007-06-22
> **Hobo Joe said:**
> Once you think you have it, paste the output of 
```

glxinfo

```
That should tell you everything you need to know

As for Beryl, you can install it through synaptic, or to be faster, you could just type:
```

sudo aptitude install beryl

```

Have fun! :)
Ati doesnt support aiglx. That will not work. You need to create another x session that is running xgl.

Follow this howto, works great.
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

