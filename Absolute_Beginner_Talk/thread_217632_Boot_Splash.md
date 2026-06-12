---
title: "Boot Splash"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by yanewby on 2006-07-17
Does Ubuntu have a booting screen when it is loading (rather like Microsoft showing the Windows XP logo when it starts)?

I am asking this as when my installation boots I see nothing but a black screen after the grub menu.  

Similarly, in other linux distros I have dabbled with when you switch off you see a list of instructions as to where the process of shutdown is up to.  In my installation I see nothing like this and have to wait until the PC "sounds" finished (ie the CPU fan is no longer turning).

If you need me to try anything please let me know the commands I would need to run (as this is my third day in Ubuntu).

---

### Post by MaximB on 2006-07-17
that's very strange...ubuntu have a boot screen that shows you exactly what it's doing and checking and if the proccess passed or failed.

---

### Post by NESFreak on 2006-07-17
dont know what's wrong with your splash but you could try removing the splash command when booting to see the textbased thing.

---

### Post by yanewby on 2006-07-17
How do I go about removing the splash?  I am new to all this and not sure how to proceed.

---

### Post by Metacarpal on 2006-07-17
Hi Yanewby - welcome to Ubuntu!

Here's what I believe will fix your problem:
(These instructions are for Gnome.  If you're using KDE/Kubuntu, let me know and I'll find out how it works there.)

Once you're logged in, go to your System menu, Administration sub-menu.  Choose "Synaptic Package Manager".  You'll need to enter your password (your main login password) when prompted.

Click Search and enter: usplash

When the results come up, locate the package named usplash on the list.  The box to the left of this should be dark gray, meaning the package is installed.  If it is not, click that box and choose "Mark for Installation".

If the box is already gray, click it and select "Mark for Reinstallation".  Then choose Apply.  This will re-download and reinstall the splash screen.  The next time you boot, you should see the Ubuntu logo and a series of status messages during the boot process.

---

### Post by yanewby on 2006-07-18
Thanks for your easy to follow instructions Metacarpel.

I reinstalled usplash as you suggested and instead of a black screen I know *sometimes* get what looks like a corrupted brown picture appear on the screen.  It is a series of vertical brown lines (no solid colour).  I would try to get a screenshot but it does not stay long enough on my screen before disappearing and going black again.  This happens both at boot-up and shutdown.

I also tried one of the additional artworks - the kubuntu one - but this has the same problem (except blue lines instead of brown).

Any other ideas?

---

### Post by Metacarpal on 2006-07-18
What are your system specs (processor, video card, RAM, etc)?

---

### Post by yanewby on 2006-07-19
I have an AMD 3000 XP CPU, 512Mb RAM and an on-board video card (built in to the motherboard).  How do I find out the name of the video card for you?

---

### Post by Metacarpal on 2006-07-19
Is your computer a custom-build, or stock model from a company?  If you have a model number, I can get the video card info.

If it's an on-board, though, we probably won't need it, as long as you know your video card's built-in RAM.  It's likely your problem can be solved by reconfiguring X-org.  Before you do this, it's a good idea to have the basic specs of your computer handy (including how much video RAM your video card has).

Go to your Applications menu > Accessories > Terminal

Type or copy/paste the following (note: in Terminal, you can't paste with Ctrl+v.  You'll need to right-click and choose Paste):

```
sudo dpkg-reconfigure xserver-xorg
```

This will take you through a series of questions on how you want your computer set up, from your video setup through keyboard, et al.  Most questions will have default answers, and it's okay to use those.

The one you're really looking for is when it asks if you want to have the system use the kernel's framebuffer instead of interfacing directly with the video hardware.  Select "Yes".

Since you'll be on the computer and doing this through Terminal, you should have no problems using your computer to come here and ask for help if you need it.  If you do need help reconfiguring X-org, you'll probably want to start a new post so it gets quicker attention.

Best of luck!

---

### Post by yanewby on 2006-07-20
Thanks for the additional help. Unfortunately none of it seemed to help :-( It got a little scary when X refused to start because I tried settings that were not compatible!

Still no splash screen but I think I can live with it - at least Ubuntu works fine!

---

