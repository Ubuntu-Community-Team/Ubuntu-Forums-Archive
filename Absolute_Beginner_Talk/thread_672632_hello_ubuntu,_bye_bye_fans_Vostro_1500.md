---
title: "hello ubuntu, bye bye fans //Vostro 1500"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by slwory on 2008-01-19
Let me start by saying that I am new to Ubuntu and any OS other than Windows. I have searched the forum for my problem but couldn't find an answer. I installed Ubuntu Dapper Drake onto my old home PC which I don't use anymore to see what it was like. I love some things about it while hating others.

Things I like.. Work spaces, the eye candy (I upgraded it step by step to 710 btw). The file management and the method of installing things was foreign to me. For example, I couldn't get flash working. But managed to get Eclipse and Opera.

Anyway, everything worked fine. Internet connection (wired), sound, speed, dual boot with XP, eyecandy, programs. The specs of that PC were P4 3.0ghz, 120 hdd 7200rpm, geforce 4000mx (something like that!) (agp).

So I thought, this is great, I'll try it on my laptop. I don't have anything important on my laptop so decided that I might as well just partition it straight away. I found out that the live cd wouldn't work. But thanks to these forums I was up and running in no time. Now I have dapper working and my wireless connection worked straight away (without tweaking). I was delighted. Problems: sound and fans. I can deal with sound later but I really need to get my fans working.

I booted into XP and my fans aren't working in there either. "acpi -t" tells me my laptop is at 51 degrees C. I tried to follow the instructions found in threads about vostros and fans but they didn't help. Is it possible I turned my fans off?

Please can someone help or even suggest some things they think might work. I can't use the laptop without fans :(

p.s it's dapper drake installed on laptop

[b]EDIT: I found out I just needed to turn the repositories on and THEN do this:

# Goto Terminal and then type the following commands.
# sudo apt-get install i8kutils gkrellm gkrellm-i8k
# sudo modprobe i8k force=1
# sudo gedit /etc/modules
# Add the following line to the end of the file: i8k force=1. Save and exit.
# Go to System > Preferences > Sessions > Startup Programs
# Click ADD and put the command: gkrellm
# Log out and log in. Gkrellm should start up. Go to plugins and enable the I8K plugin.

[/b]

---

### Post by JoshuaRL on 2008-01-19
First of all, Flash:

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

As for the fans, that's usually handled in the BIOS.  Also, you might try to upgrade to the newest version.  There might be better support for whatever kind of laptop you have.  And this I took from a thread about my Inspiron 5100:

> 
 recommend installing gkrellm and the gkrellm-i8k plugin, lets you set at what temps the fans should go on and off and also gives you info about temps etc

if you get an error with i8k you must do the following
sudo modprobe i8k force=1
sudo gedit /etc/modules
add the following line to the end of the file: i8k force=1


I know it may seem hot, but are you sure that your laptop is having heat-related issues?  Maybe it just runs hot.  I've had laptops that you swear you could warm your drink on, but ran just fine.  Something to think about.

---

