---
title: "1024x768 highest possible screen resolution?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Mikkel Nielsen on 2007-04-21
Hi guys.

This being the absolute beginner talk forum I have an absolute beginner question.
I just got ubuntu version 7.04 today and I don't seem to be able to run a screen resolution higher than 1024x768 - is this really the highest possible resolution in ubuntu or is there some way around this ?

Love, Mikkel

---

### Post by Happy_Man on 2007-04-21
What size is your monitor? It depends on the monitor, not the OS, what resolution the screen is.

---

### Post by Mikkel Nielsen on 2007-04-21
My monitor is 19" as far as I remember, anyway the monitor should not be the problem, when I used Windows I was able to run 1600x1200.

Could it be because that I haven't yet installed the driver for my 3dfx card or graphics card or whatever it's called in english? :)

---

### Post by crimesaucer on 2007-04-21
I have that question too. Mine is set to "default", so that means it's using my 1280 x 800, right? Because that is my best possible screen size. 

I guess my question is that the "1024 x 768" setting underneath the "default" setting is just a back up setting, correct?

---

### Post by Mikkel Nielsen on 2007-04-21
I just read in another thread that you can download the program Envy which will then download the latest nvidia driver for you so I did that... but when I try to install it I get "Error: Dependency is not satisfiable: module-assistant" and I am not allowed to press the "install package" button.

Anyone?

---

### Post by Happy_Man on 2007-04-21
@ mikkel and crime:

You will need to edit your xorg.conf file. If you didn't know, it holds all your input/output device settings. Never ever mess with it unless you absolutely have to. 

```

dpkg-reconfigure xserver-xorg

```

When you get to the part about monitor resolutions, highlight ALL resolutions that your monitor can support using the spacebar. Then, once it finishes, press ctrl-alt-backspace. Your monitor should be running normally. 

@ Mikkel, again:

That's not a monitor problem, that's a repo problem, so maybe you should enable extra repos in Synaptic.

---

